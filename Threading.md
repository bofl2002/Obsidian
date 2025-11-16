[[Distruberede Systemer]]


# Multithreading og synkronisering i C#

## 1. Hvad der sker, når du opretter en tråd

Når du skriver:

```csharp
new Thread(Work).Start();
```

sker følgende i .NET:

1. CLR opretter en ny operativsystem-tråd.
2. Tråden får sin egen stack (typisk 1 MB).
3. En Thread-instans bliver oprettet med metadata som kultur, prioritet og lokale værdier.
4. Tråden registreres i garbage collectorens interne trådliste.
5. Tråden begynder at køre den angivne metode.
   
At oprette en OS-tråd er en dyr operation, og det er derfor man i moderne C# næsten altid bruger ThreadPool, Tasks eller async/await.

## 2. Memory visibility og volatile

Tråde har hver deres CPU-cache. Når tråd A ændrer en værdi, betyder det ikke automatisk, at tråd B kan se ændringen med det samme. Den kan se en forældet værdi.

Eksempel:

```csharp
bool running = true;

new Thread(() =>
{
    while (running) { }
}).Start();

Thread.Sleep(1000);
running = false;
```

Tråden kan i værste fald køre for evigt, fordi CPU'en cacher variablen.

Løsninger:

- Brug af volatile
- Brug af lock (laver memory barriers)
- Brug af Interlocked

## 3. Hvordan lock fungerer i detaljer

Når du skriver:

```csharp
lock(obj) { }
```

oversætters det til:

```csharp
Monitor.Enter(obj);
try
{
}
finally
{
    Monitor.Exit(obj);
}
```

Monitor.Enter gør følgende:

1. Forsøger at tage låsen ved at spinne kortvarigt for ydeevne.
2. Hvis det mislykkes, blokeres tråden og sættes i en ventekø.
3. Når låsen frigives, vækkes en ventende tråd.
4. Lock indfører memory barriers, som sikrer at ændringer i hukommelsen bliver synlige for andre tråde.
 
## 4. Monitor.Wait og Monitor.Pulse

Monitor.Wait og Monitor.Pulse bruges, når tråde skal kommunikere.

Monitor.Wait:

- Frigiver låsen midlertidigt.
- Placerer tråden i en ventekø.
- Genoptager tråden, når den modtager et Pulse, og låsen er fri igen.
   
Monitor.Pulse:

- Vækker en enkelt ventende tråd.

Monitor.PulseAll:

- Vækker alle ventende tråde, men de vil stadig vente på låsen.

Monitor.Wait skal altid omringes af en while-løkke som tjekker tilstanden igen.

## 5. ReaderWriterLockSlim

Denne lås giver mulighed for mange samtidige læsere, men kun én skribent.  
Intern logik styrer:

- Læsetællere
- Skrivetæller
- Opgraderingslås
- Fairness mellem tråde 

Bruges når der er langt flere læseoperationer end skriveoperationer.

Eksempel:

```csharp
rw.EnterReadLock();
try
{
    // læs data
}
finally
{
    rw.ExitReadLock();
}
```

## 6. Semaphore og SemaphoreSlim


Semaphore begrænser hvor mange tråde, der må være i et bestemt område samtidig.

Forskelle:

Semaphore:

- Understøtter brug mellem processer
- Mere tung, baseret på operativsystemet

SemaphoreSlim:

- Hurtigere
- Ren managed-kode
- Understøtter async
   

Eksempel:

```csharp
var sem = new SemaphoreSlim(5);

await sem.WaitAsync();
try
{
    // maks 5 tråde samtidig
}
finally
{
    sem.Release();
}
```

## 7. Interlocked

Interlocked bruger CPU-instruktioner der garanterer atomiske operationer uden brug af lock.

Eksempler:

```csharp
Interlocked.Increment(ref counter);
Interlocked.CompareExchange(ref target, newValue, expectedValue);
```

Det er det hurtigste og mest deadlock-frie valg til simple numeriske værdier.

## 8. Task Parallel Library

Tasks er en abstraktion for arbejde. De er ikke tråde, men planlægges på ThreadPool.

En Task:

- Kan køre på enhver tråd
- Understøtter async/await
- Er god til parallelisering og I/O-bound arbejde

## 9. async/await internt

Når du skriver async/await:

1. Koden før await kører normalt.
2. Ved await deles metoden i to dele.
3. Den anden del gemmes som en “continuation”.
4. Når den asynkrone operation færdiggøres, vækkes continuation og køres på en ThreadPool-tråd (medmindre SynchronizationContext er specifik, f.eks. UI-tråd).
   
Async/await bruger ingen tråde, mens der ventes på I/O. Det gør denne tilgang meget skalérbar.

## 10. Producer–consumer med Channels

Den mest moderne måde at implementere producer–consumer i C# er channels:

```csharp
var channel = Channel.CreateBounded<int>(10);
```

Producer:

```csharp
await channel.Writer.WriteAsync(item);
```

Consumer:

```csharp
await foreach (var item in channel.Reader.ReadAllAsync())
{
    Process(item);
}
```

Channels er lock-free, meget hurtige og bygget til async workloads.

---

Hvis du ønsker det, kan jeg også:

- Udvide endnu dybere med CPU-arkitektur og memory barriers
- Forklare hvordan ThreadPool optimerer sig selv med hill-climbing algoritmen
- Lave en samlet PDF eller PowerPoint
- Lave eksempelkode til hvert koncept
- Forklare deadlock detection, contention analysis og performance tuning


## Threading

**Introduktion til Tråde i C#**

C# understøtter **multithreading**, hvilket betyder, at flere dele af en applikation kan køre samtidig. Hver tråd repræsenterer en uafhængig eksekveringssti i programmet.

**Eksempel på en simpel tråd**

Når et C#-program starter, oprettes en **hovedtråd** automatisk af CLR (Common Language Runtime). Man kan oprette ekstra tråde for at køre flere opgaver samtidigt.  
Her er et simpelt eksempel på at starte en ny tråd:

using System;
using System.Threading;
class ThreadTest
{
  static void Main()
  {
    Thread t = new Thread (WriteY);
    t.Start(); // Starter en ny tråd, der kører WriteY()
    for (int i = 0; i < 1000; i++) Console.Write ("x");
  }
  static void WriteY()
  {
    for (int i = 0; i < 1000; i++) Console.Write ("y");
  }
}

I dette eksempel:

- Hovedtråden skriver "x", mens den nye tråd skriver "y".
- Begge tråde kører uafhængigt og samtidig, hvilket fører til et blandet output af "x" og "y".
- t.IsAlive kan bruges til at tjekke, om en tråd stadig kører.


**Tråde og Dataadgang**

Tråde har hver sin **egen hukommelsesstack**, hvilket betyder, at lokale variabler ikke deles mellem tråde.  
Dog kan tråde **dele data**, hvis de arbejder på de samme objektinstanser, hvilket kan føre til race conditions.

**Eksempel: Delt Data**

class ThreadTest

{
  bool done; // Delt felt mellem tråde
  static void Main()
  {
    ThreadTest tt = new ThreadTest();  
    new Thread (tt.Go).Start();
    tt.Go();
  }

  void Go() 
  {
    if (!done)
    {
      done = true;
      Console.WriteLine ("Done");
    }
  }
}

Her kan "Done" blive printet enten én eller to gange, afhængigt af hvordan trådene eksekveres.
Løsningen er at **låse** adgangen til den delte ressource ved at bruge lock:

class ThreadSafe 

{

  static bool done;
  static readonly object locker = new object();
  static void Main()

  {
    new Thread (Go).Start();
    Go();
  }

  static void Go()
  {
    lock (locker) // Kun én tråd ad gangen kan eksekvere denne blok
    {
      if (!done)
      {
        Console.WriteLine ("Done");
        done = true;
      }
    }
  }
}



**Tråd-styring**

**Join og Sleep**

- t.Join() venter på, at en anden tråd afslutter.
- Thread.Sleep(milliseconds) pauser en tråd i den angivne tid.
- Thread.Yield() giver frivilligt CPU’en til andre tråde.

Eksempel:

Thread t = new Thread(Go);
t.Start();
t.Join();
Console.WriteLine("Tråden er afsluttet!");
Dette sikrer, at hovedtråden ikke fortsætter, før t er færdig.


**Tråde vs. Processer**

- **Processer** er fuldstændigt isolerede fra hinanden, mens **tråde deler** processens hukommelse.
- Operativsystemet skifter hurtigt mellem tråde (timeslicing).
- På en **enkel-core CPU** kører tråde én ad gangen, men skifter hurtigt.
- På en **multi-core CPU** kan flere tråde køre samtidigt.

**Hvornår skal man bruge tråde?**

Multithreading bruges til:

1. **Responsiv brugergrænseflade** – UI-tråde kan håndtere brugerinput, mens en anden tråd udfører tungt arbejde i baggrunden.
2. **Effektiv udnyttelse af CPU** – I/O-operationer (fx netværkskald) kan overlades til en anden tråd, så CPU’en ikke spilder tid.
3. **Parallel beregning** – Opdel en beregning i mindre dele, der køres samtidigt.
4. **Speculativ udførelse** – Start flere mulige løsninger parallelt og brug den første, der er færdig.
5. **Håndtering af samtidige forespørgsler** – Servere bruger tråde til at håndtere flere klienter samtidig.

**Ulemper:**

- Øget kompleksitet (deadlocks, race conditions).
- CPU- og hukommelsesomkostninger.
- Svært at debugge.



**Oprettelse og Start af Tråde**

Man kan starte en tråd på flere måder:

**Standard metode**

Thread t = new Thread(new ThreadStart(Go));
t.Start();

**Med en metodegruppe (kortere syntax)**

Thread t = new Thread(Go);
t.Start();

**Med en lambda (mest fleksible)**

Thread t = new Thread(() => Console.WriteLine("Hello from thread!"));
t.Start();



**Overførsel af data til en tråd**

**Metode 1: Lambdaudtryk**
Thread t = new Thread(() => Print("Hello from thread!"));
t.Start();

**Metode 2: ParameterizedThreadStart**
Thread t = new Thread(Print);
t.Start("Hello from thread!");
static void Print(object message) 
{
  Console.WriteLine((string)message);
}

**Begrænsning:** Kun ét argument kan overføres, og det skal castes.

**Baggrundstråde vs. Forgrundstråde**

- **Forgrundstråde** holder programmet kørende, selvom Main() afsluttes.
- **Baggrundstråde** afsluttes automatisk, når Main() afsluttes.

Thread t = new Thread(Go);
t.IsBackground = true; // Gør tråden til en baggrundstråd
t.Start();

**Trådprioritet**

Tråde kan have forskellige prioriteter:

t.Priority = ThreadPriority.Highest;

Men OS bestemmer stadig, hvornår tråden kører.

**Fejlhåndtering i tråde**

Hvis en tråd kaster en undtagelse, crasher hele programmet, hvis den ikke håndteres.  
Løsning:

static void Go()
{
  try
  {
    throw new Exception("Fejl!");
  }
  catch (Exception ex)
  {
    Console.WriteLine("Undtagelse fanget: " + ex.Message);
  }
}

**Trådpuljer**

I stedet for manuelt at oprette tråde kan man bruge en **trådpulje**, som genbruger eksisterende tråde:

ThreadPool.QueueUserWorkItem(Go);

**Fordele ved trådpuljer:**

- Hurtigere end at oprette nye tråde hver gang.
- Begrænser antallet af samtidige tråde, så systemet ikke bliver overbelastet.

Alternativt kan man bruge **Task Parallel Library (TPL)**:

Task.Factory.StartNew(() => Console.WriteLine("Hello from task!"));

## Threading scheduler

En **threading scheduler** er en komponent i et operativsystem eller runtime-miljø, der styrer hvordan og hvornår forskellige tråde (threads) får tildelt CPU-tid.

**Hovedfunktioner


**Trådstyring**: Scheduleren beslutter hvilken tråd der skal køre på hver CPU-kerne på ethvert givet tidspunkt.

**Prioritering**: Den håndterer trådprioriteringer og sikrer, at vigtige opgaver får tilstrækkelig CPU-tid.

**Kontekstskift**: Scheduleren udfører kontekstskift - gemmer tilstanden for én tråd og indlæser tilstanden for en anden.

## Almindelige Scheduling-strategier

**Round Robin**: Hver tråd får en fast tidsplade (time slice) på skift - simpelt og retfærdigt.

**Prioritetsbaseret**: Tråde med højere prioritet kører først. Risiko for "starvation" af lavprioritets-tråde.

**First-Come, First-Served (FCFS)**: Den første tråd i køen kører til den er færdig.

**Shortest Job First**: Tråde med kortest forventet køretid prioriteres.

**Multi-level Queue**: Forskellige køer for forskellige trådtyper (f.eks. interaktive vs. batch-jobs).

## Preemptive vs. Non-preemptive

**Preemptive scheduling**: Operativsystemet kan afbryde en kørende tråd og give CPU'en til en anden tråd. Dette er mest almindeligt i moderne systemer.

**Non-preemptive (cooperative)**: En tråd kører indtil den frivilligt giver CPU'en fra sig eller bliver blokeret.

## Praktiske eksempler

I moderne systemer som Windows, Linux og macOS bruger kernel-scheduleren avancerede algoritmer der kombinerer flere strategier for at optimere både responsivitet og gennemløb. Python's threading bruger OS'ets scheduler, mens Java's ThreadPoolExecutor implementerer sin egen arbejdskø-baserede scheduling ovenpå OS-scheduleren.

## Synchronization Essentials

Selvfølgelig! Her er en mere detaljeret forklaring af de vigtigste koncepter omkring synkronisering af tråde i C#.

**Synkronisering af Tråde**

Når flere tråde arbejder samtidigt, er det vigtigt at koordinere deres handlinger for at undgå fejl som race conditions (hvor flere tråde forsøger at ændre en fælles ressource samtidigt). Synkronisering kan opdeles i fire hovedkategorier:

**1. Simple Blocking Metoder**

Disse metoder får en tråd til at vente på, at en anden tråd afslutter sit arbejde eller på, at en bestemt tid er gået:

- **Thread.Sleep(ms)** – Sætter tråden på pause i et givet antal millisekunder.
- **Thread.Join()** – Tvinger en tråd til at vente, indtil en anden tråd er færdig.
- **Task.Wait()** – Blokerer, indtil en opgave (Task) er færdig.

Disse metoder er nemme at bruge, men de kan føre til ineffektivitet, fordi de tvinger tråde til at vente, selv hvis de ikke behøver det.

**2. Locking Konstruktioner**

Locking bruges til at sikre, at kun én tråd ad gangen kan udføre en bestemt handling. De mest anvendte mekanismer er:

**Eksklusive Locks (Kun én tråd ad gangen)**

- **lock (Monitor.Enter/Exit)** – En simpel mekanisme, der sikrer, at kun én tråd ad gangen kan eksekvere en bestemt kodeblok.
- **Mutex** – Ligner lock, men kan bruges mellem flere processer.
- **SpinLock** – En mere avanceret lås, der bruger spinning i stedet for at blokere direkte.

**Ikke-eksklusive Locks (Flere tråde kan tilgå samtidigt under visse betingelser)**

- **Semaphore** – Tillader et begrænset antal tråde at tilgå en ressource.
- **SemaphoreSlim** – En mere effektiv version af Semaphore.
- **Reader/Writer Locks** – Tillader flere læsetråde samtidigt, men sikrer eksklusiv adgang for en skrivetråd.

Brug af låse er effektivt til at beskytte data, men for mange låse kan føre til **deadlocks**, hvor to tråde blokerer hinanden i en uendelig ventetilstand.

**3. Signaleringsmekanismer**

I stedet for at en tråd venter aktivt (spinning) kan den vente på et signal fra en anden tråd:

- **EventWaitHandle** – En tråd kan stoppe, indtil en anden tråd giver et signal (Set()).
- **Monitor.Wait/Pulse** – Tråde kan vente på en betingelse (Wait()) og blive vækket af en anden tråd (Pulse()).
- **CountdownEvent** – Bruges til at vente på, at et vist antal hændelser er fuldført.
- **Barrier** – Koordinerer et sæt tråde, så de synkroniserer på bestemte punkter.

Signaleringsmekanismer undgår det ineffektive polling-problem ved at lade tråde sove, indtil de bliver vækket.

**4. Nonblocking Synkronisering**

I stedet for at blokere tråde kan man bruge processorens primitive instruktioner til at sikre trådsikker adgang til data:

- **Thread.MemoryBarrier** – Sikrer, at CPU’en ikke omarrangerer instruktioner i en problematisk rækkefølge.
- **Thread.VolatileRead / VolatileWrite** – Bruges til at læse og skrive en delt variabel korrekt i multithreading.
- **volatile (C# nøgleordet)** – Sikrer, at en variabel altid læses fra hovedhukommelsen og ikke caches af CPU’en.
- **Interlocked** – En klasse, der tillader trådsikre operationer som Increment(), Decrement(), Exchange() og CompareExchange().

Nonblocking mekanismer er hurtigere end låse, fordi de undgår kontekstskift mellem tråde, men de kræver mere avanceret programmering.

**Blocking vs. Spinning**

Når en tråd skal vente på en betingelse, kan den enten:

1. **Blokere** – Den venter passivt ved at give CPU’en tilbage til operativsystemet (Thread.Sleep() eller WaitHandle.WaitOne()).
2. **Spinne** – Den udfører en loop, hvor den gentagne gange tjekker betingelsen:
3. while (!proceed);

Dette er ineffektivt, fordi CPU’en bruger tid og strøm på at køre loopet, uden at tråden laver noget nyttigt.

4. **Hybrid-løsning** – En kombination af spinning og blokering:
5. while (!proceed) Thread.Sleep(10);

Dette reducerer CPU-forbruget, men kan stadig være ineffektivt. Derfor er det bedre at bruge **korrekt synkronisering**, som Monitor.Wait/Pulse eller AutoResetEvent.

**ThreadState**

ThreadState-egenskaben giver information om en tråds tilstand. De vigtigste tilstande er:

- **Unstarted** – Tråden er oprettet, men ikke startet endnu.
- **Running** – Tråden kører aktivt.
- **WaitSleepJoin** – Tråden er blokeret (venter, sover eller venter på en Join).
- **Stopped** – Tråden er færdig.

Eksempel på at filtrere en tråds tilstand:

public static ThreadState SimpleThreadState(ThreadState ts)

{
    return ts & (ThreadState.Unstarted | ThreadState.WaitSleepJoin | ThreadState.Stopped);
}

Men **ThreadState bør ikke bruges til synkronisering**, fordi en tråds tilstand kan ændre sig mellem læsning og handling.

**Konklusion**

Synkronisering af tråde er afgørende for at undgå fejl og sikre effektivitet i multitrådede applikationer. De vigtigste metoder er:

- **Blocking metoder** (f.eks. Sleep(), Join()) er simple, men ineffektive.
- **Locking konstruktioner** (f.eks. lock, Mutex) beskytter data, men kan føre til deadlocks.
- **Signaleringsmekanismer** (f.eks. Monitor.Wait/Pulse, AutoResetEvent) er mere effektive end aktiv spinning.
- **Nonblocking mekanismer** (f.eks. Interlocked, volatile) er avancerede, men giver den bedste ydelse i nogle scenarier.

Valget af synkroniseringsmekanisme afhænger af applikationens krav, og korrekt brug af disse teknikker forbedrer både ydeevne og pålidelighed.

## Monitor.Enter og Monitor.Exit

I C# bruges lock-statement ofte til at sikre, at kun én tråd ad gangen kan få adgang til en kritisk sektion af koden. Bag kulissen omskrives lock af C#-compileren til en Monitor.Enter- og Monitor.Exit-kald.

Eksempel:

lock (_locker)
{
    if (_val2 != 0)
        Console.WriteLine(_val1 / _val2);
    _val2 = 0;
}

Omskrives af compileren til:

Monitor.Enter(_locker);
try
{
    if (_val2 != 0)
        Console.WriteLine(_val1 / _val2);
    _val2 = 0;
}
finally
{
    Monitor.Exit(_locker);
}

Hvis Monitor.Exit kaldes uden først at have kaldt Monitor.Enter, opstår en exception.

**Problemet med exception mellem Monitor.Enter og try**

Hvis der sker en exception mellem Monitor.Enter og try-blokken (fx en Thread.Abort eller OutOfMemoryException), vil Monitor.Exit aldrig blive kaldt. Det fører til en **lækket lås**, hvor en tråd låser ressourcen permanent.

For at løse dette, introducerede CLR 4.0 en forbedret version af Monitor.Enter, der bruger en lockTaken-parameter:

bool lockTaken = false;

try

{

    Monitor.Enter(_locker, ref lockTaken);

    // Kritisk sektion...

}

finally

{

    if (lockTaken)

        Monitor.Exit(_locker);

}

Denne version sikrer, at lockTaken kun bliver true, hvis låsen faktisk blev taget.

---

**Sammenligning af Låsemekanismer**

Her er en oversigt over forskellige låsemekanismer i C# og deres formål:

|**Konstrukt**|**Formål**|**På tværs af processer?**|**Overhead**|
|---|---|---|---|
|**lock (Monitor.Enter/Exit)**|Sikrer, at kun én tråd ad gangen får adgang til en ressource|Nej|~20 ns|
|**Mutex**|Som lock, men kan bruges på tværs af processer|Ja|~1000 ns|
|**SemaphoreSlim**|Tillader et begrænset antal tråde at køre samtidigt|Nej|~200 ns|
|**Semaphore**|Som SemaphoreSlim, men virker også på tværs af processer|Ja|~1000 ns|
|**ReaderWriterLockSlim**|Tillader flere samtidige læsere, men kun én skriver|Nej|~40 ns|

**Konklusion:**

- Brug lock til hurtige, korte sektioner, hvor kun én tråd ad gangen skal have adgang.
- Brug SemaphoreSlim til at begrænse antallet af samtidige tråde (fx ved databaseforbindelser).
- Brug Mutex, hvis du har brug for at låse en ressource på tværs af processer.

---

**TryEnter – Undgå blokering**

Monitor.TryEnter er en ikke-blokerende version af Monitor.Enter. Den forsøger at tage en lås, men hvis låsen ikke kan tages inden for den angivne timeout, returnerer den false.

Eksempel:

if (Monitor.TryEnter(_locker, TimeSpan.FromSeconds(1)))

{

    try

    {

        Console.WriteLine("Lås opnået!");

    }

    finally

    {

        Monitor.Exit(_locker);

    }

}

else

{

    Console.WriteLine("Kunne ikke opnå lås inden for tidsgrænsen.");

}

Dette kan være nyttigt, hvis du vil undgå at blokere tråde unødvendigt.

---

**Valg af Synkroniseringsobjekt**

Når du bruger lock, kan du låse ethvert objekt, der er en reference-type (class, men ikke struct). Det anbefales dog **ikke** at låse this eller en statisk Type, da det kan føre til uforudsete deadlocks.

Dårlig praksis:

lock (this) { /* potentielt farligt */ }

lock (typeof(MyClass)) { /* kan føre til uventede deadlocks */ }

Bedre praksis:

private readonly object _locker = new object();

lock (_locker) { /* sikrere */ }

Fordelen ved at bruge et privat _locker-objekt er, at det ikke kan tilgås uden for klassen, hvilket reducerer risikoen for deadlocks.

---

**Atomicitet og Fejlhåndtering**

Låsning sikrer **atomare operationer**, hvilket betyder, at operationen ikke kan afbrydes midt i udførelsen.

Eksempel på **ikke-trådsikker** kode:

static int _x;

static void Increment() { _x++; }

Flere tråde kan samtidig forsøge at øge _x, hvilket kan føre til race conditions.

Trådsikker version:

static readonly object _locker = new object();

static int _x;

static void Increment()

{

    lock (_locker)

    {

        _x++;

    }

}

Alternativt kan man bruge Interlocked til en mere effektiv løsning:

Interlocked.Increment(ref _x);

Dette er ofte hurtigere end lock, fordi det bruger hardware-understøttede atomare instruktioner.

---

**Deadlocks – Hvordan de opstår, og hvordan man undgår dem**

En **deadlock** opstår, når to tråde venter på hinanden, og ingen kan fortsætte.

Eksempel på en deadlock:

object locker1 = new object();

object locker2 = new object();

new Thread(() => {

    lock (locker1)

    {

        Thread.Sleep(1000);

        lock (locker2); // Blokerer her

    }

}).Start();

lock (locker2)

{

    Thread.Sleep(1000);

    lock (locker1); // Blokerer her

}

Begge tråde venter på hinanden, og programmet hænger uendeligt.

**Hvordan undgår man deadlocks?**

1. **Lås altid objekter i en fast rækkefølge**

- Fx altid lock (locker1) før lock (locker2).

3. **Brug TryEnter med timeout**

- Hvis en tråd ikke kan opnå en lås inden for en bestemt tid, kan den undgå at vente uendeligt.

5. **Reducer låsetid**

- Hold låsen i så kort tid som muligt for at minimere risikoen.

---

**Mutex – Når du har brug for tværproces-synkronisering**

En Mutex er som lock, men virker også mellem forskellige programmer/processer.

Eksempel:

using (var mutex = new Mutex(false, "Global\\MyUniqueAppMutex"))

{

    if (!mutex.WaitOne(TimeSpan.FromSeconds(3), false))

    {

        Console.WriteLine("En anden instans kører allerede.");

        return;

    }

    Console.WriteLine("Programmet kører.");

    Console.ReadLine();

}

Ved at bruge en global mutex sikrer vi, at kun én instans af programmet kan køre ad gangen.

---

**Semaphore – Begrænser samtidige tråde**

En Semaphore kan begrænse antallet af samtidige tråde.

Eksempel:

static SemaphoreSlim _sem = new SemaphoreSlim(3);

static void Enter(object id)

{

    Console.WriteLine($"{id} ønsker at gå ind.");

    _sem.Wait();

    Console.WriteLine($"{id} er inde!");

    Thread.Sleep(1000);

    Console.WriteLine($"{id} forlader.");

    _sem.Release();

}

for (int i = 1; i <= 5; i++)

    new Thread(Enter).Start(i);

Kun tre tråde kan køre ad gangen, mens de andre venter.

---

**Konklusion**

- Brug lock for enkel trådsynkronisering.
- Brug Monitor.TryEnter for at undgå blokering.
- Brug Interlocked for hurtige atomare operationer.
- Brug Mutex, hvis synkronisering kræves på tværs af processer.
- Brug SemaphoreSlim til at begrænse samtidige tråde.

## Monitor i C#

Selvfølgelig! Her er en mere detaljeret gennemgang af **Threading med Monitor i C#**, hvor vi dykker dybere ned i, hvordan Monitor fungerer, hvornår den bruges, og giver mere tekniske eksempler.

---

**🔹 Hvad er Monitor i C#?**

Monitor er en **synkroniseringsmekanisme**, der sikrer, at kun én tråd ad gangen får adgang til en **kritisk sektion** af koden. Den bruges til at beskytte delte ressourcer i et **multitrådet miljø** og forhindrer race conditions.

Monitor fungerer ved at låse et specifikt objekt, så kun én tråd kan arbejde med det ad gangen. Når en tråd er færdig, frigiver den låsen, så en anden tråd kan få adgang.

**Hvordan adskiller Monitor sig fra lock?**

I C# er lock en enklere måde at bruge Monitor på. **lock bruger internt Monitor.Enter() og Monitor.Exit()**, men sikrer, at Exit() altid kaldes (også hvis der opstår en exception).

**Eksempel med lock:**

class Program {

    static object locker = new object();

    static void WriteData() {

        lock (locker) {

            Console.WriteLine("Tråd {0} skriver data...", Thread.CurrentThread.ManagedThreadId);

            Thread.Sleep(1000);

            Console.WriteLine("Tråd {0} er færdig.", Thread.CurrentThread.ManagedThreadId);

        }

    }

    static void Main() {

        Thread t1 = new Thread(WriteData);

        Thread t2 = new Thread(WriteData);

        t1.Start();

        t2.Start();

        t1.Join();

        t2.Join();

    }

}

🔹 **Fordel ved lock**: Mindre kode og sikker håndtering af låse.  
🔹 **Fordel ved Monitor**: Mere fleksibel, da man kan bruge Monitor.Wait() og Monitor.Pulse().

---

**🔹 De vigtigste Monitor-metoder**

Monitor-klassen har flere vigtige metoder til synkronisering:

|**Metode**|**Funktion**|
|---|---|
|Monitor.Enter(obj)|Låser et objekt (starter en kritisk sektion).|
|Monitor.Exit(obj)|Frigiver låsen (afslutter en kritisk sektion).|
|Monitor.Wait(obj)|Tråden venter, indtil den får et signal.|
|Monitor.Pulse(obj)|Vækker én tråd i ventekøen.|
|Monitor.PulseAll(obj)|Vækker alle ventende tråde.|
|Monitor.TryEnter(obj)|Forsøger at låse et objekt uden at vente for evigt.|

---

**🔹 Monitor i praksis: Eksempler**

**1️****⃣ Grundlæggende Monitor (Enter & Exit)**

Dette eksempel viser, hvordan **Monitor.Enter()** og **Monitor.Exit()** bruges til at sikre, at kun én tråd skriver til konsollen ad gangen.

using System;

using System.Threading;

class Program {

    static object locker = new object();

    static void WriteData() {

        Monitor.Enter(locker);

        try {

            Console.WriteLine("Tråd {0} skriver data...", Thread.CurrentThread.ManagedThreadId);

            Thread.Sleep(1000);

            Console.WriteLine("Tråd {0} er færdig.", Thread.CurrentThread.ManagedThreadId);

        }

        finally {

            Monitor.Exit(locker);

        }

    }

    static void Main() {

        Thread t1 = new Thread(WriteData);

        Thread t2 = new Thread(WriteData);

        t1.Start();

        t2.Start();

        t1.Join();

        t2.Join();

    }

}

🔹 **Hvad sker der her?**

- Monitor.Enter(locker) låser objektet, så kun én tråd kan køre.
- Monitor.Exit(locker) slipper låsen, når tråden er færdig.
- finally sikrer, at låsen altid bliver frigivet, selv hvis en exception opstår.

---

**2️****⃣ Brug af Monitor.Wait() og Monitor.Pulse() (Tikker-Takker ur)**

Dette eksempel demonstrerer, hvordan **Monitor.Wait()** og **Monitor.Pulse()** bruges til at få tråde til at vente på hinanden.

using System;

using System.Threading;

class TickTock {

    public void Tick(bool running) {

        lock (this) {

            if (!running) {

                Monitor.Pulse(this);

                return;

            }

            Console.Write("Tick ");

            Monitor.Pulse(this); // Signal til tock()

            Monitor.Wait(this);  // Vent på tock()

        }

    }

    public void Tock(bool running) {

        lock (this) {

            if (!running) {

                Monitor.Pulse(this);

                return;

            }

            Console.WriteLine("Tock");

            Monitor.Pulse(this); // Signal til tick()

            Monitor.Wait(this);  // Vent på tick()

        }

    }

}

class MyThread {

    public Thread thrd;

    TickTock ttOb;

    public MyThread(string name, TickTock tt) {

        thrd = new Thread(this.run);

        ttOb = tt;

        thrd.Name = name;

        thrd.Start();

    }

    void run() {

        if (thrd.Name == "Tick") {

            for (int i = 0; i < 5; i++) ttOb.Tick(true);

            ttOb.Tick(false);

        } else {

            for (int i = 0; i < 5; i++) ttOb.Tock(true);

            ttOb.Tock(false);

        }

    }

}

class TickingClock {

    public static void Main() {

        TickTock tt = new TickTock();

        MyThread mt1 = new MyThread("Tick", tt);

        MyThread mt2 = new MyThread("Tock", tt);

        mt1.thrd.Join();

        mt2.thrd.Join();

        Console.WriteLine("Clock Stopped");

    }

}

🔹 **Hvordan fungerer det?**

- Monitor.Wait(this) får en tråd til at vente, indtil den får et signal fra en anden tråd.
- Monitor.Pulse(this) signalerer til den ventende tråd, at den må fortsætte.
- **"Tick" og "Tock" skiftes til at køre**, hvilket skaber et synkroniseret ur.

---

**3️****⃣ Monitor Pool: Trådgenbrug**

En **Thread Pool** genbruger tråde, så man undgår omkostningen ved at oprette og destruere tråde hele tiden.

using System;

using System.Threading;

class Program {

    static object locker = new object();

    static void Worker() {

        while (true) {

            lock (locker) {

                Monitor.Wait(locker);

            }

            Console.WriteLine("{0} arbejder...", Thread.CurrentThread.ManagedThreadId);

            Thread.Sleep(500);

        }

    }

    static void Main() {

        Thread[] threads = new Thread[3];

        for (int i = 0; i < 3; i++) {

            threads[i] = new Thread(Worker);

            threads[i].IsBackground = true;

            threads[i].Start();

        }

        for (int i = 0; i < 10; i++) {

            Thread.Sleep(1000);

            lock (locker) {

                Monitor.Pulse(locker);

            }

        }

        Console.ReadLine();

    }

}

🔹 **Hvad sker der her?**

- **Tre tråde genbruges**, i stedet for at oprette nye hver gang.
- Monitor.Wait(locker) får en tråd til at vente, indtil den får et signal fra Monitor.Pulse(locker).

---

**🔹 Konklusion**

**Fordele ved Monitor:**  
Kraftig synkroniseringsmekanisme.  
Giver mere kontrol end lock.  
Kan styre ventende tråde med Wait() og Pulse().

**Ulemper:**  
Kan føre til deadlocks, hvis tråde låser objekter i forkert rækkefølge.  
Kræver omhyggelig brug af Monitor.Enter() og Monitor.Exit().

Monitor er et kraftfuldt værktøj til trådsynkronisering i C#, men kræver omhyggelig brug for at undgå fejl!

## Semaphore i C#

**Semaphore** er en synkroniseringsmekanisme i C#, der begrænser antallet af tråde, der kan få adgang til en delt ressource samtidigt.

**🔹 Grundlæggende koncept**

- En **Semaphore** har et **maksimalt antal slots**, som bestemmer, hvor mange tråde der kan få adgang til ressourcen på samme tid.
- Når en tråd vil have adgang, kalder den **WaitOne()**, som reserverer et slot.
- Når tråden er færdig, kalder den **Release()** for at frigive slottet til andre tråde.
- Hvis alle slots er optaget, blokeres nye tråde, indtil et slot bliver ledigt.

**🔹 Konstruktorer til oprettelse af en Semaphore**

|**Konstruktor**|**Beskrivelse**|
|---|---|
|Semaphore(Int32, Int32)|Opretter en semaphore med et angivet maksimalt antal tilladte samtidige tråde.|
|Semaphore(Int32, Int32, String)|Opretter en navngiven system-semaphore.|
|Semaphore(Int32, Int32, String, Boolean)|Giver mulighed for at verificere, om en ny system-semaphore blev oprettet.|
|Semaphore(Int32, Int32, String, Boolean, SemaphoreSecurity)|Giver sikkerhedsindstillinger for adgangskontrol.|

**🔹 Eksempel på brug af Semaphore**

Koden nedenfor opretter en semaphore, der tillader maksimalt 3 tråde ad gangen:

using System;

using System.Threading;

class Program

{

    static Semaphore sem = new Semaphore(3, 3); // Maks 3 samtidige tråde

    static void AccessResource()

    {

        Console.WriteLine("{0} venter...", Thread.CurrentThread.Name);

        sem.WaitOne(); // Forsøger at få adgang

        Console.WriteLine("{0} har fået adgang!", Thread.CurrentThread.Name);

        Thread.Sleep(300); // Simulerer arbejde

        Console.WriteLine("{0} frigiver ressourcen.", Thread.CurrentThread.Name);

        sem.Release(); // Frigiver adgang

    }

    static void Main()

    {

        for (int i = 0; i < 10; i++)

        {

            Thread thread = new Thread(AccessResource);

            thread.Name = "Tråd_" + i;

            thread.Start();

        }

        Console.Read();

    }

}

  
Tråde forsøger at få adgang én ad gangen, men kun tre kan køre samtidigt.

**🔹 Vigtige fakta om Semaphore**

- **Ikke garanteret rækkefølge**: Tråde får ikke nødvendigvis adgang i FIFO- eller LIFO-orden.
- **Programmeringsansvar**: Release() skal kaldes korrekt, ellers kan SemaphoreFullException opstå.
- **Typer af Semaphores**:

- **Lokal semaphore**: Eksisterer kun inden for en enkelt proces.
- **Navngiven system-semaphore**: Kan bruges på tværs af processer og styres af operativsystemet.

Semaphores bruges typisk i **serverapplikationer**, **ressourcestyring** og andre scenarier, hvor begrænsning af samtidige adgangspunkter er nødvendig.

## Interlocked i C# – Trådsikkerhed uden låse

System.Threading.Interlocked er en klasse i C#, der tilbyder atomiske operationer på delte variabler. Den bruges til **trådsikker manipulation af variabler**, hvilket undgår race conditions **uden brug af locks** (lock, Monitor, Semaphore, osv.).

---

**🔹 Hvorfor bruge Interlocked?**

- **Hurtigere** end lock og Monitor, da den udføres som en enkelt CPU-instruktion.
- **Ingen risiko for deadlocks**, da den ikke låser tråde.
- **Perfekt til enkle tællere, flags og delte variabler** i multitrådede applikationer.

---

**🔹 Interlocked Metoder**

|**Metode**|**Beskrivelse**|
|---|---|
|Interlocked.Increment(ref int location)|Øger en variabel med 1 atomisk.|
|Interlocked.Decrement(ref int location)|Sænker en variabel med 1 atomisk.|
|Interlocked.Add(ref int location, int value)|Lægger value til en variabel atomisk.|
|Interlocked.Exchange(ref int location, int value)|Erstatter location med value atomisk.|
|Interlocked.CompareExchange(ref int location, int newValue, int comparand)|Erstatter location med newValue, hvis location er lig med comparand (bruges ofte til lock-free programmering).|

---

**🔹 Eksempler**

**Atomisk tæller uden lock**

using System;

using System.Threading;

class Program

{

    static int counter = 0; // Delt ressource

    static void IncrementCounter()

    {

        for (int i = 0; i < 10000; i++)

        {

            Interlocked.Increment(ref counter); // Øger tælleren trådsikkert

        }

    }

    static void Main()

    {

        Thread t1 = new Thread(IncrementCounter);

        Thread t2 = new Thread(IncrementCounter);

        t1.Start();

        t2.Start();

        t1.Join();

        t2.Join();

        Console.WriteLine($"Counter: {counter}"); // Skal være præcist 20000

    }

}

**Fordel**: Interlocked.Increment() sikrer, at tælleren altid er korrekt uden at bruge lock.

---

**Sikring af korrekt værdi med CompareExchange()**

using System;

using System.Threading;

class Program

{

    static int sharedValue = 0;

    static void SafeUpdate()

    {

        int oldValue, newValue;

        do

        {

            oldValue = sharedValue;

            newValue = oldValue + 5;

        }

        while (Interlocked.CompareExchange(ref sharedValue, newValue, oldValue) != oldValue);

    }

    static void Main()

    {

        Thread t1 = new Thread(SafeUpdate);

        Thread t2 = new Thread(SafeUpdate);

        t1.Start();

        t2.Start();

        t1.Join();

        t2.Join();

        Console.WriteLine($"Shared Value: {sharedValue}"); // Skal være 10

    }

}

**Fordel**: CompareExchange() sikrer, at vi kun opdaterer variablen, hvis den ikke er ændret af en anden tråd i mellemtiden.

---

**🔹 Hvornår skal du bruge Interlocked?**

**Ja, brug Interlocked hvis...**

- Du **kun** skal lave simple operationer som ++, --, +=, eller sammenligning.
- Du vil **forbedre ydeevnen** uden risiko for deadlocks.
- Du arbejder med **enkle delte variabler** (fx tællere, flags).

 **Nej, brug lock eller Monitor hvis...**

- Du arbejder med **komplekse data** (fx lister, arrays, objekter).
- Du har **flere operationer**, der skal være trådsikre som en enhed.

---

**🔹 Konklusion**

🔹 **Interlocked er ideel til simple, trådsikre variable-opdateringer uden brug af locks**  
🔹 **For mere komplekse scenarier (fx data i en liste) bør lock eller Monitor bruges**  
🔹 **Brug CompareExchange() til mere avanceret, lock-free programmering**

## Dijkstra’s Bounded Buffer Problem (Producer-Consumer Problem)

Dijkstra’s bounded buffer problem (også kendt som **Producer-Consumer-problemet**) handler om at sikre synkronisering mellem **producenter**, der producerer varer (data) og **forbrugere**, der forbruger dem.

For at styre adgangen til den **begrænsede buffer**, bruger vi **semaforer** til at sikre, at:

1. **Producenter ikke overskriver en fuld buffer**
2. **Forbrugere ikke læser fra en tom buffer**

---

**🔹 Brug af semaforer**

Dijkstra foreslog at bruge **tre semaforer**:

- **empty**: Antal ledige pladser i bufferen (starter på bufferstørrelsen).
- **full**: Antal fyldte pladser i bufferen (starter på 0).
- **mutex**: En binær semafor (ligesom en lock), der sikrer, at kun én tråd ad gangen tilgår bufferen.

Disse semaforer sikrer, at producenter ikke fylder en allerede fuld buffer, og at forbrugere ikke forsøger at læse fra en tom buffer.

## Hvad er Channels i C#?

Channels i C# er en funktion i System.Threading.Channels namespace, som gør det muligt for tråde at kommunikere sikkert med hinanden ved at sende og modtage data i et trådsikkert miljø. Channels er en god løsning til opgaver som producer-forbruger-problemet, hvor du har en buffer (en kanal) til at opbevare data midlertidigt.

**Producer-forbruger problemet med Channels**

I denne løsning har vi en **producer** (producent), der producerer data og skriver det til kanalen (bufferen), og en **consumer** (forbruger), der læser data fra kanalen.

**Hvordan virker det?**

1. **Producer** skriver data til kanalen.
2. **Consumer** læser data fra kanalen.
3. **Channel** tager sig af synkroniseringen, så vi behøver ikke bruge låse (locks) eller semaforer manuelt.

**Vigtige funktioner ved Channels:**

- Trådsikker: Channels håndterer automatisk synkronisering mellem producer- og forbrugstråde. Du behøver ikke at bruge låse eller semaforer manuelt.
- Blokering: Channels understøtter blokering. Producenten blokkerer, når kanalen er fuld, og forbrugeren blokkerer, når kanalen er tom.
- Asynkron: Operationsmetoderne for Channels er asynkrone, hvilket gør dem velegnede til højtydende og skalerbare applikationer.

**Fordele ved at bruge Channels:**

- **Forenkler samtidighed**: Channels gør det lettere at håndtere trådsikker kommunikation og synkronisering mellem tråde.
- **Bedre end låse**: Channels abstrakterer den underliggende låsemekanisme, hvilket gør koden renere og mindre fejlbehæftet.
- **Skalerbar**: Channels er ideelle i situationer, hvor du har brug for at skalere og håndtere høj gennemstrømning på tværs af flere tråde uden at bekymre dig om manuel låsning eller semaforer.

Dette er en effektiv og simpel løsning på producer-forbruger-problemet i C# ved hjælp af Channels, der sikrer korrekt synkronisering og kommunikation mellem tråde.

## Interlocking

I C# refererer **interlocking** til brugen af atomare operationer for at håndtere delt data sikkert i multitrådede miljøer. Klassen **Interlocked** i System.Threading tilbyder metoder, der udfører atomare operationer på variabler, hvilket forhindrer race conditions.

---

**Hvorfor bruge Interlocked?**

- Sikrer, at opdateringer udføres atomisk (uden afbrydelser fra andre tråde).
- Forhindrer race conditions, når flere tråde ændrer en delt variabel.
- Mere effektivt end lock, når der kun skal ændres én variabel.

---

**De vigtigste Interlocked metoder**

1. **Interlocked.Increment(ref int location)**

- Øger en integer atomisk.

3. using System;
4. using System.Threading;

5. class Program
6. {
7.     static int tæller = 0;

8.     static void Øg()
9.     {
10.         for (int i = 0; i < 1000; i++)
11.         {
12.             Interlocked.Increment(ref tæller);
13.         }
14.     }

15.     static void Main()
16.     {
17.         Thread t1 = new Thread(Øg);
18.         Thread t2 = new Thread(Øg);

19.         t1.Start();
20.         t2.Start();
21.         t1.Join();
22.         t2.Join();

23.         Console.WriteLine($"Endelig værdi: {tæller}");  // Forventet: 2000
24.     }
25. }
26. **Interlocked.Decrement(ref int location)**

- Formindsker en integer atomisk.

33. Interlocked.Decrement(ref tæller);
34. **Interlocked.Add(ref int location, int value)**

- Lægger et tal til atomisk.

36. Interlocked.Add(ref tæller, 10);
37. **Interlocked.Exchange(ref int location, int value)**

- Erstatter en værdi atomisk.

39. int gammelVærdi = Interlocked.Exchange(ref tæller, 100);
40. **Interlocked.CompareExchange(ref int location, int newValue, int comparand)**

- Opdaterer en værdi, hvis den nuværende værdi matcher en forventet værdi.

42. int forventet = 0;
43. int nyVærdi = 100;
44. int resultat = Interlocked.CompareExchange(ref tæller, nyVærdi, forventet);

---

**Hvornår skal man bruge Interlocked vs Lock?**

|**Scenario**|**Brug Interlocked**|**Brug Lock**|
|---|---|---|
|Simple numeriske opdateringer|✅ Ja|❌ Nej|
|Kompleks logik|❌ Nej|✅ Ja|
|Performance-kritiske opgaver|✅ Ja|❌ Nej|
|Flere variabler skal synkroniseres|❌ Nej|✅ Ja|

Hvis du kun skal ændre én variabel atomisk, er Interlocked hurtigere end lock.

## Thread Apartments

C# refererer **Thread Apartments** til en model i **COM (Component Object Model)**, der styrer, hvordan tråde interagerer med COM-objekter. Dette er især relevant, når .NET-applikationer kommunikerer med COM-baserede biblioteker, f.eks. Microsoft Office-interoperabilitet.

Windows COM bruger en **Apartment Threading Model** til at administrere tråde og sikre, at COM-objekter tilgås på en trådsikker måde. Der er to primære modeller:

1. **STA (Single-Threaded Apartment)**

- Hver tråd har sit eget **"apartment"**, hvor den kan oprette og bruge COM-objekter.
- Andre tråde kan ikke tilgå objekter direkte – de skal bruge marshaling.
- Bruges ofte i **GUI-applikationer** (Windows Forms, WPF), da mange UI-komponenter ikke er trådsikre.

3. **MTA (Multi-Threaded Apartment)**

- Flere tråde kan dele adgang til COM-objekter uden marshaling.
- Bruges ofte i **baggrundsopgaver og parallelle operationer**.

### **Hvordan indstiller man Thread Apartments i C#?**

Du kan sætte en tråds **ApartmentState** med Thread.SetApartmentState() eller [STAThread]-attributten.

**Eksempel: STA i en GUI-applikation**

Windows Forms kræver STA, fordi UI-komponenter ikke er trådsikre:

[STAThread]

static void Main()

{

    Application.Run(new MainForm());

}

Hvis du ikke har [STAThread], kan du få en fejl ved adgang til f.eks. **Clipboard** eller **Drag & Drop**.

**Eksempel: Indstilling af ApartmentState manuelt**

csharp

CopyEdit

Thread thread = new Thread(() =>

{

    // Kald til COM-objekter her

});

thread.SetApartmentState(ApartmentState.STA);

thread.Start();

**Eksempel: Brug af MTA i en baggrundstråd**

csharp

CopyEdit

Thread thread = new Thread(() =>

{

    // Kør tunge beregninger eller adgang til COM-objekter i MTA

});

thread.SetApartmentState(ApartmentState.MTA);

thread.Start();

**Hvornår bruger man hvad?**

- **STA**: Når du arbejder med GUI (WPF, WinForms) eller bruger COM-objekter, der kræver STA (f.eks. **Clipboard**, **Shell**-integration).
- **MTA**: Når du arbejder med parallelle operationer eller COM-objekter, der understøtter multi-threading.

I WPF (Windows Presentation Foundation) er **Dispatcher** en mekanisme, der styrer tråde og sikrer, at UI-elementer kun opdateres fra den tråd, de blev oprettet på – typisk hovedtråden (UI-tråden).

**Hvad er Dispatcher?**

- **Dispatcher** håndterer udførelsen af opgaver i den rigtige tråd (UI-tråden).
- WPF har en **single-threaded UI-model**, hvilket betyder, at UI-elementer kun kan ændres fra den tråd, de blev oprettet på.
- Hvis en baggrundstråd skal opdatere UI, skal den **dispatches** via **Dispatcher**.

**Hvordan bruger man Dispatcher?**

**1. Kald fra en baggrundstråd til UI-tråden:**

Application.Current.Dispatcher.Invoke(() =>

{

    myLabel.Content = "Opdateret fra en baggrundstråd!";

});

- **Invoke()** udfører koden **synkront** på UI-tråden.

**2. Kør koden asynkront:**

Application.Current.Dispatcher.BeginInvoke(() =>

{

    myLabel.Content = "Opdateret asynkront!";

});

- **BeginInvoke()** kører koden **asynkront**, så tråden ikke blokeres.

**3. Brug af DispatcherPriority:**

Application.Current.Dispatcher.Invoke(() =>

{

    myLabel.Content = "Opdateret med prioritet!";

}, System.Windows.Threading.DispatcherPriority.Background);

- Her angives en prioritet for, hvornår koden skal køres.

**Hvornår bruger man Dispatcher?**

- Når man arbejder med baggrundstråde via **Task.Run()** eller **Thread**.
- Når man vil opdatere UI fra en anden tråd.

**Eksempel med Task.Run():**

Task.Run(() =>

{

    // Simulerer baggrundsarbejde

    Thread.Sleep(2000);

    // Opdater UI via Dispatcher

    Application.Current.Dispatcher.Invoke(() =>

    {

        myLabel.Content = "Opdateret efter baggrundsarbejde!";

    });

});

Dispatcher er essentiel i WPF for at sikre, at UI-opdateringer sker korrekt uden at bryde trådbegrænsningerne.