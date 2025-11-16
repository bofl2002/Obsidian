[[Fokusområder]]

**

## Programmør Tools

Hardware

Hovedpointe: Programmører skal have kraftig hardware for at arbejde effektivt.

Hvorfor:

- Langsomme computere spild programmørens tid
    
- Lange ventetider (f.eks. på kompilering) bryder koncentrationen
    
- Bruddet i tankeprocessen øger risikoen for fejl, fordi programmøren mister overblikket over koden
    
- Det er dumt at spare få hundrede dollars på hardware, hvis det koster hundredvis af programmeurtimer om året
    

To problemer ved at give programmører alt:

1. Overforbrug - Nogle køber unødvendige "legetøj" (USB-raketaffyrere, osv.). Løsning: Check indkøbsrekvistioner.
    
2. Glemmer slutbrugernes hardware - Programmer kan køre hurtigt på kraftige udviklermaskiner, men være ubrugelige på brugernes svagere computere. Løsning: Test altid på hardware svarende til slutbrugernes.
    

Konklusion: Invester i god hardware til udviklere, men kontroller indkøb og test på realistisk brugerudstyr.

### Network

Hovedpointe: Programmører bør have fri adgang til internettet.

Hvorfor:

- En hurtig søgning kan løse et programmeringsproblem på minutter, som ellers ville tage timer
    
- Adgang til vigtige ressourcer og tidligere løsninger sparer enormt meget tid
    

Nyttige ressourcer nævnt:

- Forfatterens egne websites ([www.csharphelper.com](http://www.csharphelper.com) og [www.vb-helper.com](http://www.vb-helper.com)) - Løsninger på tidligere problemer
    
- Wikipedia ([www.wikipedia.org](http://www.wikipedia.org)) - Generel viden og forklaringer
    
- Wolfram MathWorld ([https://mathworld.wolfram.com](https://mathworld.wolfram.com)) - Matematiske løsninger
    
- Søgemaskiner - Find løsninger andre steder på nettet
    

Begrænsninger: Nogle organisationer blokerer ekstern netværksadgang af sikkerhedshensyn (f.eks. hvis man udvikler ekstremt følsomt materiale), men dette bør undgås hvis muligt.

Balance: Tilskynd mildt medarbejdere til ikke at spilde hele dagen på spil eller chat, men giv dem en hurtig internetforbindelse og friheden til at bruge den professionelt.

Konklusion: Fordelene ved internetadgang langt opvejer risikoen for distraktioner - det er et essentielt værktøj for effektiv programmering.

  

### Development Environment

Absolut minimum: En compiler eller interpreter der oversætter kode til noget computeren kan køre.

IDE (Integrated Development Environment) kan inkludere meget mere:

- Debuggers - Find og ret fejl i koden
    
- Performance profilers - Analyser programmets ydeevne
    
- Class visualization tools - Visualiser klassers struktur og relationer
    
- Auto-completion - Automatisk færdiggørelse af kode under skrivning
    
- Context-sensitive help - Hjælp der tilpasser sig den aktuelle kode
    
- Team integration tools - Værktøjer til samarbejde i teamet
    
- Syntax highlighting - Farvekodning af kode for bedre læsbarhed
    

Eksempler på IDEer:

- Eclipse - Primært til Java, men med plug-ins til C++, Ruby osv.
    
- Visual Studio - Til Visual C#, Visual Basic, Visual C++, JavaScript, F#
    

Vigtig pointe: Du behøver ikke altid den dyreste version.

Eksempler:

- Visual Studio: Fra gratis Community edition (til individuelle brugere) til dyre Professional/Enterprise versioner (til store teams). Start med den gratis version - opgrader kun hvis nødvendigt.
    
- Eclipse: Findes i forskellige versioner med forskellige plug-ins til forskellige formål (f.eks. Eclipse for Testers).
    

Konklusion: Vælg et udviklingmiljø der passer til dit projekts størrelse og behov - brug ikke penge på features du ikke bruger.

### SourceCode control - Versionsstyring

Hovedpointe: Source code control er essentielt, hvis dit udviklingsmiljø ikke allerede inkluderer det.

Hvorfor det er vigtigt:

- Endnu vigtigere end dokumentstyring - Én fejl i koden kan ødelægge hele programmet
    
- Kode er ekstremt følsom - en enkelt forkert karakter kan gøre et fungerende program ubrugeligt
    

Hvad kan versionsstyring:

1. Spore historik:
    

- Se alle tidligere versioner af softwaren
    
- Se præcist hvilke ændringer der blev lavet og hvornår
    

3. Fejlfinding:
    

- Hvis programmet holder op med at virke, kan du hente gamle versioner
    
- Sammenlign fungerende og ikke-fungerende versioner
    
- Identificer præcist hvilke ændringer der forårsagede fejlen
    
- Ret fejlene
    

5. Samarbejde:
    

- Forhindrer at flere programmører ændrer samme kode samtidig og skaber konflikter
    

7. Sikkerhed:
    

- Beskytter mod ulykker - hvis nogen sletter hele projektet (forhåbentlig ved et uheld), kan det genskabes
    

Konklusion: Source code control er uundværligt for moderne softwareudvikling - det beskytter koden og gør samarbejde muligt.

### Profilers

Hvad er profilers: Værktøjer der viser hvilke dele af programmet bruger mest:

- Tid
    
- Hukommelse
    
- Filer
    
- Andre ressourcer
    

Fordele:

- Sparer enormt meget tid når man skal optimere et programs ydeevne
    
- Identificerer præcist hvor performance-problemerne er
    

Praktisk tilgang:

- Behøver ikke købe til alle programmører - typisk er det kun en lille del af koden der påvirker den samlede ydeevne
    
- Man behøver ikke analysere hver enkelt kodelinje detaljeret
    
- Vigtigt: Profilers skal være tilgængelige når de er nødvendige
    

Konklusion: Profilers er værdifulde til performance-optimering, men behøver ikke være standard-udstyr til alle udviklere - bare sørg for at de er tilgængelige når behovet opstår.

### Static Analysis Tools

Forskel mellem Profilers og Static Analysis Tools:

Profilers:

- Overvåger programmet mens det kører
    
- Ser hvordan det fungerer, hvor ofte kode kaldes, og hvor tidskrævende det er
    

Static Analysis Tools:

- Analyserer koden uden at køre den
    
- Fokuserer på kodens stil og struktur
    

  

Hvad Static Analysis Tools kan måle:

1. Kode-struktur:
    

- Hvor sammenkoblet forskellige kode dele er
    
- Hvor kompleks koden er
    

3. Kvalitets- og vedligeholdelses metrikker:
    

- Antal kommentarer per kodelinje
    
- Gennemsnitligt antal kodelinjer per metode
    
- Andre statistikker der indikerer kodekvalitet
    

Konklusion: Static analysis tools hjælper med at vurdere kodekvalitet og vedligeholdbarhed ved at analysere kodens struktur og stil - uden at skulle køre programmet.

### Testing Tools

Fordele ved testing tools:

- Gør testning meget hurtigere
    
- Gør testning nemmere
    
- Gør testning mere pålidelig
    
- Især automatiserede værktøjer er værdifulde
    

Vigtigt princip:

- Hvis testværktøjerne er nemme at bruge, er programmører mere tilbøjelige til faktisk at bruge dem
    

Tilgængelighed:

- Hver programmør skal udføre mindst en vis mængde testning
    
- Alle bør have adgang til testværktøjer
    

Note: Mere detaljeret information om testing tools findes i Kapitel 13 om testning.

Konklusion: Testing tools er essentielle for alle programmører - de skal være tilgængelige og nemme at bruge for at sikre at de faktisk bliver anvendt.

### Source Code Formatters

Hvorfor formatering er vigtig:

- Gør kode nemmere at læse og forstå
    
- Reducerer antal fejl i koden
    
- Gør det lettere at finde og rette fejl
    

Hvad nogle udviklingsmiljøer kan:

- Automatisk indrykning - Viser hvordan kode er indlejret i if-statements og loops
    
- Farvekodning af keywords
    
- Match parenteser og krøllede parenteser
    
- Ekspander/kollaps koderegioner
    
- Andre formateringsfunktioner
    

Hvis dit miljø mangler formatering: En separat code formatter kan:

- Standardisere indrykning
    
- Justere og omformatere kommentarer
    
- Bryde kode så den passer på print
    
- Håndhæve kodestandarder
    

Balancegang:

- For meget standardisering = irriterende for udviklere
    
- For lidt standardisering = nogle programmører producerer kaotisk kode der ligner poesi mere end professionel software
    

Konklusion: Teamet skal finde den rette balance af kodeuniformitet - nok til at holde koden læsbar, men ikke så meget at det kvæler udviklerne.

### Refactoring Tools

Hvad er refactoring: Programmør-jargon for "omorganisere kode for at gøre den:

- Lettere at forstå
    
- Mere vedligeholdbar
    
- Generelt bedre"
    

Hvad refactoring tools kan:

- Definere nye klasser eller metoder nemt
    
- Udtrække et stykke kode til en ny metode
    
- Andre omstruktureringer af kode
    

Placering: Kan være bygget ind i IDE'et eller være separate værktøjer

Særligt nyttigt: Især værdifuldt når man arbejder med eksisterende kode (i modsætning til at skrive ny kode)

Konklusion: Refactoring tools hjælper med at forbedre og omstrukturere eksisterende kode effektivt, hvilket gør den mere vedligeholdbar.

### Training (Træning)

Hvorfor træning er vigtig:

- Gør programmører mere effektive
    
- Holder medarbejdere glade
    
- Forbedrer performance betydeligt
    
- Hjælper med at fastholde personale
    

Ledelsesproblem: Nogle ledere sparer på træning (penny-wise and pound-foolish) - sparer småpenge men taber store penge på lang sigt.

Investering: Få tusinde dollars brugt på træning kan give stor gevinst i produktivitet og fastholdelse.

Træningsformer:

In-person træning:

- Ofte mere effektiv
    
- Dyrere
    
- Kræver fast tidspunkt
    

Online videokurser og bøger:

- Mindre effektiv
    
- Meget billigere
    
- Fleksibel - studer når du har tid
    
- Selv én nyttig tip fra en bog til $50 gør den værd at købe
    

Konklusion: Træning er en god investering - selv billige ressourcer som bøger kan give stor værdi, hvis de giver bare ét brugbart tip.

### Collaboration Tools (Samarbejdsværktøjer)

Hvorfor det er vigtigt: Større projekter kræver samarbejde - medmindre projektet er så lille at én person kan bygge det.

Før og nu:

- Før: Programmører sad sammen i kontorlandskaber - let at samarbejde over frokost eller ved kaffemaskinen
    
- Nu (efter COVID-19): Fjernarbejde er blevet normen - programmører er særligt velegnede til fjernarbejde
    

Nødvendige samarbejdsværktøjer:

1. Grundlæggende kommunikation:
    

- SMS, telefon, VoIP-opkald
    
- Diskutere problemer og forhandle interfaces
    

3. Videokonferencer:
    

- Særligt når ledelsen er involveret
    
- Tip: "Business mullet" - pænt tøj foroven, joggingbukser forneden
    

5. Skærmdeling:
    

- Dele design-diagrammer
    
- Vise nye features
    
- Demonstrere fejl
    

7. Fælles dokumentredigering:
    

- Flere personer arbejder på samme dokument samtidigt
    

  

Møder:

- Statusmøder og planlægningssessioner er nødvendige
    
- Hyppigheden afhænger af udviklingsmodellen
    

Vigtige principper:

GØR:

- Vælg værktøjer sammen med teamet
    
- Sørg for at værktøjerne er nemme at bruge
    
- Hold statusmøder indimellem så folk er vant til processen
    

UNDGÅ:

- Overbruge værktøjerne bare fordi de er nemme at bruge
    
- Konstant overvågning (kameraer altid tændt)
    
- Dystopisk arbejdsmiljø hvor alle altid er forbundet
    

Vigtigt at huske:

- Udvikling er en kreativ, tankefuld proces
    
- Konstant overvågning er demotiverende og ikke produktivt
    
- Folk har brug for ro til at tænke kreativt
    

Konklusion: Vælg gode samarbejdsværktøjer der gør fjernarbejde muligt, men brug dem med måde - respekter at programmering kræver koncentration og kreativitet.

  

### Algoritmer

Der findes allerede mange effektive algoritmer til opgaver som sortering, søgning i databaser, netværksoptimering, kryptering, investeringsstrategier og meget mere. 

### Sortering og organisering af data

Dette handler om at arrangere data (f.eks. tal eller navne) i en bestemt rækkefølge – fx stigende eller alfabetisk. Gode sorteringsalgoritmer som QuickSort, MergeSort eller HeapSort kan gøre det hurtigt og effektivt, især når der er mange data.

### 🔹 Hurtigt at finde ting i databaser

Når man arbejder med store mængder data, er det vigtigt at kunne finde bestemte elementer hurtigt. Algoritmer som binær søgning, hashing eller træstrukturer (som f.eks. B-træer) bruges til dette. Det gør databaser i stand til at levere svar på forespørgsler lynhurtigt.

### 🔹 At finde optimale ruter i netværk (veje, elnet, kommunikation m.m.)

Her bruges algoritmer til at finde den hurtigste eller billigste vej mellem to punkter i et netværk – som f.eks. GPS-ruteplanlægning. Kendte algoritmer er Dijkstra’s algoritme, A* eller Bellman-Ford.

### 🔹 At designe netværk med kapacitet og sikkerhed

Når man bygger et netværk (f.eks. internettet, elnet, eller transportsystemer), vil man sikre, at det både har kapacitet nok og er robust – altså at det ikke går ned, hvis én forbindelse fejler. Her bruges algoritmer fra grafteori og netværksdesign.

### 🔹 Kryptering og dekryptering af data

For at beskytte data (f.eks. ved onlinebank, e-mail, m.m.) bruges krypteringsalgoritmer som AES, RSA, eller ECC. De gør data ulæselige for uvedkommende – og dekrypteres kun af dem, der har den rette nøgle.

### 🔹 At vælge optimale investeringsstrategier

Algoritmer kan analysere risici, fordele og sandsynligheder for at finde den bedste måde at investere penge på. Dette er en del af finansiel optimering, og her bruges teknikker som dynamisk programmering, lineær programmering eller Monte Carlo-simulering.

### 🔹 At finde de billigste måder at bygge eller producere på

Dette handler om at minimere omkostninger ved f.eks. produktion eller byggeri. Algoritmer inden for operationsanalyse (fx transportproblemet, tildelingsproblemet) hjælper med at finde den mest effektive måde at bruge ressourcer på.

### 🔹 Og mange, mange flere

Der findes tusindvis af specialiserede algoritmer til alle tænkelige områder – fra billedgenkendelse og maskinlæring til spiludvikling og robotteknologi.

  

### TOP-DOWN DESIGN

Top-Down Design er en metode til at designe og planlægge programmer eller systemer ved at starte med det overordnede problem og gradvist nedbryde det i mindre og mere håndterbare dele (moduler eller funktioner).

## Trin i Top-Down Design

1. Definér hovedproblemet  
    → Hvad skal programmet gøre helt overordnet?  
      
    
2. Opdel i hovedkomponenter  
    → Hvilke store opgaver skal løses?  
      
    
3. Del hver komponent op i mindre dele  
    → Hvilke mindre funktioner eller klasser er nødvendige?  
      
    
4. Gentag processen indtil delene er små nok til at kode direkte
    

## PROGRAMMING TIPS AND TRICKS

### Be Alert

At skrive god kode er ikke let. For at gøre det rigtigt, skal du:

- Forstå hvad problemet er, og hvad koden skal gøre  
      
    
- Forstå hvad koden faktisk gør (inkl. bivirkninger og grænsetilfælde)  
      
    
- Overveje hvad der kan gå galt – fx:  
      
    

- En fil er låst og kan ikke åbnes
    
- En vigtig værdi mangler i en parameter-tabel
    
- Brugeren har glemt sin adgangskode  
      
    

## 🔹 Tænk i fejlhåndtering

Du skal kunne forestille dig alle mulige situationer, koden kan blive kørt i – og hvordan de kan ødelægge dit program, hvis du ikke har tænkt dem igennem.

## 🔹 Skriv kun kode, når du er skarp

Det kræver stor mental klarhed at kode ordentligt. Derfor bør du kun skrive kode, når du er:

- Vågen
    
- Fokuseret
    
- Mentalt frisk  
      
    

## 🔹 Planlæg din tid efter din hjerne

Folk har forskellige tidspunkter, hvor de fungerer bedst mentalt:

|   |   |
|---|---|
|Type|Bedste kodetid|
|Morgenmenneske|Morgen/formiddag|
|Aftentype|Sen eftermiddag/aften|
|Natugle|Sent om natten|

Find ud af, hvornår du er mest mentalt effektiv, og planlæg at skrive kode der.

  

## 🔹 Brug lavenergitid på rutineopgaver

Når du ikke er så skarp (fx sidst på dagen), så lav:

- Tidsregistrering
    
- Fremskridtsrapporter
    
- Ryd op i filer eller dokumentation
    

### Write for People, Not the Computer

Din kode skal være let at forstå for mennesker – ikke for computeren.

Computeren er ligeglad med:

- Meningsfulde variabelnavne
    
- Pæn indrykning
    
- Kommentarer
    
- Stavning
    
- Hvor “smart” du er
    

### Computeren læser ikke din kode direkte

- Alt, hvad computeren ser, er nuller og ettaller (maskinkode).
    
- Din kode skal først oversættes (via compiler eller interpreter), så computeren forstår den.
    
- Du skriver i et højniveausprog (som Python, Java eller C#), fordi det er lettere for dig, ikke for computeren.
    

### Hvorfor det er vigtigt at skrive læsbar kode

- Når du debugger (retter fejl), er det langt sværere end at skrive koden første gang.
    
- Du har måske glemt, hvad din oprindelige idé var, eller hvordan funktionen præcis virker.
    
- Det bliver svært at se forskel på:
    

- Hvad koden burde gøre
    
- Hvad koden faktisk gør
    

### Debugging er farligere end ny kode

- Der er større risiko for at lave nye fejl, når du retter gamle bugs.
    
- Du kender ikke altid konteksten eller intentionen med koden.
    
- Derfor er det vigtigt at gøre koden så gennemsigtig og forståelig som muligt fra starten.  
      
    

### Tænk på fremtidens udvikler (måske dig selv!)

- Den person, der skal læse og rette din kode senere, vil sætte pris på:
    

- Gode navne
    
- Forklarende kommentarer
    
- Enkle og forståelige løsninger
    

Du ved aldrig, hvem der skal overtage din kode – og det kan meget vel være dig selv om 6 måneder.

### Comment First

Mange programmører undgår at skrive kommentarer, fordi det føles som spild af tid – men det er en stor fejl.

### To almindelige (og dårlige) strategier:

#### 1. Kommentér undervejs

- Du skriver kommentarer, mens du koder.
    
- Men hver gang du ændrer koden (fx en løkke), skal du også ændre kommentaren.
    
- Efter 10, 20 eller 37 ændringer:  
      
    

- Kommentaren passer ikke længere til koden
    
- Du opgiver at holde den opdateret
    
- Kommentaren bliver vildledende eller forkert  
      
    

#### 2. Kommentér til sidst

- Du skriver hele koden færdig uden kommentarer.
    
- Til sidst skriver du så få kommentarer som muligt – kun for ikke at få skældud af teamlederen.
    
- Problemet: Kommentarerne er overfladiske og hjælper ikke rigtig nogen.  
      
    

### Just Barely Good Enough

- En udbredt holdning blandt programmører:  
    "Bare det lige akkurat er godt nok – så behøver jeg ikke skrive flere kommentarer."
    
- Nogle siger:  
    "Gode kommentarer er spild af tid – skriv bare bedre kode i stedet."  
      
    

Men det overser, at:

- Kommentarer ikke bare handler om, hvad koden gør
    
- De handler om, hvorfor koden gør det – altså intentionen bag  
      
    

## Den egentlige fejl: Fokus på hvad koden gør, ikke hvad den burde gøre

Når du ændrer kode, ændrer du, hvad den gør → så skal kommentaren også ændres.

Men hvis kommentaren beskriver formålet, altså hvad koden bør gøre, behøver den sjældent at ændres – selv hvis du ændrer implementeringen.

  

## Skriv kommentarer først

En god strategi:

1. Skriv en kommentar, der forklarer hensigten med det, du vil kode  
    → Hvad skal funktionen, løkken, eller metoden opnå?
    
2. Skriv derefter selve koden til at opfylde hensigten  
      
    

Fordele:

- Du tænker først, før du koder
    
- Du beholder fokus på intention i stedet for implementering
    
- Du sparer tid, fordi du ikke skal rette kommentaren hele tiden
    
- Debugging bliver lettere: du kan sammenligne "hvad koden gør" med "hvad den skulle gøre"
    

Hvis intentionen ændrer sig 37 gange, så er det ikke kommentarens skyld – så har du et designproblem, ikke et dokumentationsproblem.

### Write Self-Documenting Code

Koden skal i sig selv være så klar og beskrivende, at den næsten ikke behøver kommentarer.

### Brug beskrivende navne

- Giv klasser, metoder, variabler og egenskaber navne, der fortæller hvad de er og hvad de gør  
      
    
- Eksempel:  
      
    

- Dårligt: temp, data, doStuff()
    
- Godt: userName, calculateInvoiceTotal(), isLoggedIn
    

### Undgå “magic numbers”

Magic numbers = tal, der bare står i koden uden forklaring

### Keep It Small

Lang kode er sværere at læse, forstå og vedligeholde. Del den op i mindre og mere overskuelige dele.

### Hvorfor er lang kode et problem?

- Du skal holde mange detaljer i hovedet på én gang.
    
- Du risikerer at miste overblikket, især når koden bliver kompleks.
    
- Hvis du har flere indlejrede loops eller blokke, er det svært at vide, hvilken der slutter hvor.
    
- Hvis du har mange linjer kode inde i hvert loop, kan det blive umuligt at gennemskue, hvad der hører til hvad.
    

  
  

### Hvor langt er "for langt"?

- Før i tiden sagde man: “Hvis det ikke kan printes på én side, er det for langt.”
    
- I dag siger man ofte: “Hvis du ikke kan se hele metoden på din skærm, er den for lang.”
    

En uofficiel tommelfingerregel: Hvis du ikke kan forstå hele metodens formål med ét overblik, så er den for kompleks og bør opdeles.

### Stay Focused

Hver klasse skal repræsentere ét klart og intuitivt begreb. Hvis du ikke kan forklare klassens formål i én sætning, gør den for meget og bør opdeles.

### Avoid Side Effects

Et side effect er en handling, en metode udfører, som ikke er tydelig eller forventet ud fra metodens navn eller formål.

Eks. en metode som tjekker, om brugernavn og kodeord er korrekte i databasen. Men metoden lader databasen forblive åben bagefter. Det at databasen forbliver åben er et side effect — det er ikke klart ud fra navnet, og det kan skabe problemer (fx ressource-lækage eller uforudsete fejl).

### Fjern side effect ved at afslutte handlingen inden retur

F.eks. at:

- Lukke databasen i ValidateLogin inden metoden returnerer.
    
- Problemet kan være nedsat ydeevne, hvis databasen skal åbnes og lukkes ofte.
    

  

|   |   |
|---|---|
|Problem|Løsning|
|Metode har skjulte side effects|Flyt side effect til separate metoder eller gør det eksplicit|
|Side effects skjuler kodeadfærd|Sørg for at metoder har enkelt formål og ikke overrasker|
|Vanskeligt at forstå metodekald|Skriv klare metodenavne og del op i flere metoder|

  

### Validate Results

Murphy’s lov siger:

"Alt, der kan gå galt, vil gå galt."

Det betyder, at du altid skal antage, at dine beregninger på et tidspunkt vil fejle — måske ikke altid, men før eller siden.

## Hvorfor kan beregninger fejle?

- Inputdata kan være forkerte, manglende eller i et forkert format.
    
- Beregnings Logikken kan indeholde fejl.
    
- Resultater kan være ukorrekte eller forkert formaterede.  
      
    

## Hvordan kan du opdage fejl tidligt?

### Valideringskode

- Tilføj valideringskode i dine metoder, der tjekker input og output for fejl.
    
- Valider undervejs i beregningerne for at sikre, at alt forløber som forventet.  
      
    

### Assertioner

- En assertion er et udtryk, der skal være sandt på et givent tidspunkt i programmet.
    
- Hvis assertionen fejler, kastes en fejl (exception), så du ved, at noget er galt.  
      
    

## Eksempler på brug af assertioner

- Før sortering af ordrer kan du tjekke, at listen indeholder mindst to ordrer.
    
- Sørg for, at hver ordre har en positiv totalpris.
    
- Efter sortering kan du kontrollere, at hver ordre er dyrere eller lig med den foregående.  
      
    

## Invariants — tilstande, der ikke må ændre sig

- En invariant er en tilstand, der altid skal være sand i et objekt.
    
- Eksempel: I en medarbejderklasse skal en medarbejder altid have mindst 40 arbejdstimer om ugen.
    
- Du kan tilføje assertioner i metoder og egenskaber for at kontrollere, at denne invariant overholdes.  
      
    

## Fordele ved validering og assertioner

- Hjælper dig med at finde fejl tidligt, når de er nemmest at rette.
    
- Forhindrer, at fejl spreder sig og bliver svære at opdage.  
      
    

## Udfordringer ved at skrive valideringskode

- Programmører tror ofte, at deres nyligt skrevne kode er perfekt.
    
- Det gør det svært at tage sig tid til at skrive valideringskode.
    
- Selvom det ikke føles nødvendigt, findes fejl altid, og validering fanger dem.  
      
    

## Tip til bedre valideringspraksis

- Skriv valideringskode før du skriver resten af metoden.
    
- Dette mindsker risikoen for at springe validering over.
    
- Når valideringen skrives først, har du ikke forudindtagede meninger om, hvordan koden virker, og kan bedre opdage fejl.  
      
    

### Practice Offensive Programming

## Defensive programming

- Idéen er at få koden til at køre uanset hvad — også hvis den får "skralde"-input.
    
- Koden skal aldrig crashe, men kan godt returnere mærkelige eller meningsløse resultater.
    

## Offensive programming

- Idéen er at gøre opmærksom på fejl med det samme, så de kan fanges og rettes.
    
- Hvis input er forkert, skal koden "tage et raserianfald" og stoppe.
    

### Use Exceptions

### Kaste en undtagelse (Throwing an Exception)

- Når metoden opdager et problem, afbryder den programmet og smider en undtagelse.
    
- Programmet skal håndtere denne undtagelse, ellers crasher programmet.
    
- Fordel: Det er umuligt at overse en fejl, fordi programmet tvinges til at tage stilling til det.
    
- Eksempel: Factorial kaster en undtagelse ved negativ input eller overflow.
    

### Returnere en fejlkode (Returning an Error Code)

- Når metoden opdager et problem, returnerer den et særligt tal, fx -1, for at indikere en fejl.
    
- Problemet: Den kaldende kode kan let ignorere fejlkoden.
    
- Hvis fejlkoden ignoreres, kan programmet bruge eller vise forkerte værdier uden at advare om fejlen.
    

### Write Exception Handlers First

Start med kommentarer eller en plan  
Indsæt dine design-noter øverst — hvad metoden skal gøre, hvilke input den forventer, og hvad den skal returnere.  
  

Tilføj inputvalidering  
Skriv kode, der tjekker, om input er gyldige. Hvis ikke, smid en undtagelse (throw exception) eller brug assert.  
  

Pak hovedkoden ind i try/catch blokke  
  

- Første catch-blok: Håndter forventede fejl, som du kan gøre noget ved (fx filen er låst).
    
- Anden catch-blok: Håndter fejl, du ikke kan rette, men kan give en brugervenlig besked om (fx taloverløb).  
      
    

Oversæt tekniske fejl til brugervenlige beskeder  
Erstat kryptiske fejlmeddelelser med klare og forståelige beskeder, som brugeren kan handle på.

### Don’t Repeat Code

Hvis du opdager, at du skriver den samme (eller næsten samme) kode flere gange, bør du overveje at flytte den til en separat metode, som du kan kalde fra flere steder. Det sparer dig ikke kun tid ved at undgå at skrive den samme kode igen og igen, men det gør det også lettere at fejlfinde og vedligeholde koden, fordi du kun skal ændre ét sted.

Hvis du senere skal rette eller opdatere noget i den kode, kan du gøre det ét sted — i stedet for at skulle huske at ændre det i alle kopier. Hvis du glemmer at opdatere én af kopierne, risikerer du, at forskellige versioner af koden kommer til at opføre sig forskelligt, og det kan føre til meget forvirrende fejl

### Defer Optimization

### Udskyd optimering

Først få det til at virke. Derefter gør det hurtigere, hvis det er nødvendigt.

Fokuser først på at få din kode til at virke korrekt. Optimer kun, hvis det er nødvendigt, fordi for tidlig optimering ofte gør koden mere kompleks og svær at vedligeholde. Brug et profileringsværktøj til at finde de steder, hvor programmet virkelig er langsomt, og optimer kun de dele. Ofte bruger programmet mest tid i en lille del af koden, så det er spild af tid at optimere resten.  
  
Typisk bruger programmet 80 % af tiden på 20 % af koden (eller 90 % af tiden på 10 % af koden). Det betyder, at hvis du bruger tid på at optimere de 80 % der allerede er hurtige nok, spilder du tid. Det kan endda gøre koden mere forvirrende og sværere at vedligeholde.

**