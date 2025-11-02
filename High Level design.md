
[[Fokusområder]]


**

## High Level Design (HLD)

Det store billede: Softwareudvikling kan ses som en proces, hvor man deler systemet op i mindre og mindre dele, indtil delene er små nok til at implementere. High-level design er det første skridt i denne opdeling.

High Level Design (HLD) er en fase i systemudviklingsprocessen, hvor man udarbejder en overordnet arkitektur og struktur for systemet. Det er et vigtigt trin mellem kravspecifikationen og den mere detaljerede Low Level Design (LLD).

High Level Design beskriver hvordan systemet skal fungere på et overordnet niveau – uden at gå i detaljer med implementering eller kode. Det handler om at definere systemets hovedkomponenter og deres indbyrdes relationer.  
  
Elementer i HLD

1. Systemarkitektur:
    

- Valg af arkitekturtype (f.eks. klient-server, microservices, lagdelt arkitektur).
    
- Hvordan komponenter taler sammen (API’er, databaser, netværk).  
      
    

3. Modulopdeling:
    

- Overordnet opdeling af systemet i moduler eller komponenter.
    
- F.eks. frontend, backend, database, autentificering, mm.  
      
    

5. Databaseskemaer:
    

- Beskrivelser af hvilke databaser der bruges, og hvordan data struktureres på et højt niveau.  
      
    

7. Teknologivalg:
    

- Hvilke programmeringssprog, frameworks og platforme systemet bygger på.  
      
    

9. Grænseflader (Interfaces):
    

- Hvilke interfaces de forskellige moduler bruger til at kommunikere (REST, GraphQL, SOAP, osv.)  
      
    

11. Overordnede datastrømme og kommunikationsveje:
    

- Hvordan data flyder igennem systemet fra input til output.
    

### Formål med High Level Design

- At give udviklingsteamet, arkitekter og interessenter et fælles billede af systemets struktur.
    
- At gøre det nemmere at planlægge, estimere og fordele arbejdet.
    
- At sikre, at designet opfylder kravene til funktionalitet, skalerbarhed, sikkerhed og vedligeholdelse.
    

En High Level Design-dokumentation kan typisk indeholde:

- Diagrammer (f.eks. komponentdiagrammer, arkitekturdiagrammer)
    
- Beskrivelser af hver komponent
    
- Tabel over teknologier og ansvar  
    Kommunikationsdiagrammer (hvordan services snakker sammen)
    

### Hvad skal man have med i High level design

Sikkerhed er en kritisk del af HLD, og som teksten rigtigt påpeger, starter sikkerheden langt før login-skærmen. I High Level Design handler det om at:

1. Identificere potentielle trusler og svagheder
    
2. Skitsere sikkerhedstiltag på et overordnet niveau
    
3. Beskytte systemets aktiver tidligt i udviklingen
    
4. Forberede systemet på både utilsigtede fejl og forsætlige angreb
    

5. Typer af trusler at overveje

  

|   |   |
|---|---|
|Type af trussel|Emner|
|Externe|Hackere, bots, brute-force login, SQL injection, DDoS osv.|
|Interne|Utilfredse medarbejdere, “snoopere” fra andre teams, sabotage|
|Utilsigtede hændelser|Mistede enheder (f.eks. bærbare med kode eller data)<br><br>Forkert konfiguration, fejl i kode eller adgangsrettigheder|
|Fysiske|Tyveri af hardware, adgang til serverrum, backup-disks m.m.|

2. Forholdsregler du kan skitsere i HLD  
  

|   |   |
|---|---|
|Forholdsregel|Action|
|Autentificering og autorisation|Hvordan håndteres login?  <br>Hvem har adgang til hvad (RBAC – Role-Based Access Control)?|
|Databeskyttelse|Kryptering af data i hvile og i transit  <br>Beskyttelse af følsomme oplysninger|
|Sikkerhedskopiering og recovery|Backup af kode, data, dokumentation<br><br>Regelmæssige snapshots/versionering|
|Adgangskontrol og audit logs|Hvem tilgår hvad – og hvornår?  <br>Logging af følsomme handlinger|
|Sikring af udviklingsmiljøet|Versionskontrol (f.eks. Git) med adgang restriktioner  <br>Begræns adgang til CI/CD-pipelines, testmiljøer, databaser|
|Beskyttelse mod interne trusle|Begrænset adgang til nøgledata  <br>Automatiske alert-systemer for uautoriserede handlinger|
|Enhedssikkerhed|Kryptering af laptops, VPN til fjernadgang  <br>Politik for håndtering af mistede enheder|

Hardware

Tidligere var hardwarevalget begrænset, og det bestemte ofte hvilket styresystem og programmeringssprog, man brugte. I dag findes der mange typer enheder: mainframes, computere, tablets, telefoner, wearables (som smartwatches og AR-briller) samt IoT-enheder (f.eks. køleskabe, alarmer, låse).

Når du udvikler en applikation, skal du angive, hvilken hardware den skal køre på. Det kan også inkludere tilbehør som printere, netværksudstyr, servere, specialinstrumenter, lyd/video-udstyr og IoT-apparater.

User Interfaces

I high-level design kan du skitsere brugergrænsefladen, men kun overordnet – vent med detaljerne til senere.

- Du kan beskrive, hvordan brugeren navigerer i applikationen (f.eks. med knapper, menuer eller swipe-bevægelser), men ikke det præcise layout af skærmbilleder.
    
- Traditionelle desktop-applikationer bruger ofte flere åbne vinduer og menuer.
    
- Moderne tablet-/mobilapps har som regel ét vindue ad gangen og navigerer med knapper (f.eks. "Tilbage" og "Næste").
    

Du skal sørge for, at dine skitserede vinduer dækker alle funktioner i user stories og use cases.

High-level design kan også inkludere:

- Specielle funktioner som klikbare kort, vigtige tabeller og indstillinger (f.eks. skydeknapper og tekstfelter)
    
- Overordnede designvalg som farvetema, firmalogo og layout/”skin”
    

Internal Interfaces - Interne grænseflader

Når du opdeler et program i forskellige dele (moduler eller komponenter), skal du tydeligt definere, hvordan de skal kommunikere med hinanden.

- Det gør det muligt for flere teams at arbejde uafhængigt, uden konstant at skulle koordinere.
    
- En klart defineret intern grænseflade forhindrer misforståelser og sparer tid.
    

- Hvis to teams er uenige om, hvordan de skal interagere, spildes der tid på diskussioner og ændringer.
    
- Problemet vokser, hvis flere teams bruger den samme grænseflade.  
      
    

### Udsatte grænseflader

Nogle gange er det ikke muligt at definere en præcis grænseflade mellem to teams i starten af et projekt, fordi:

- Ingen af dem har skrevet kode endnu.  
      
    
- Det er uklart, hvilken data de skal udveksle.
    

External Interfaces - Eksterne grænseflader

Mange applikationer skal kommunikere med eksterne systemer – f.eks. databaser, salgsprogrammer eller tredjepartssoftware.

Eksterne grænseflader kan faktisk være nemmere at specificere end interne, fordi:

- Hvis du interagerer med et eksisterende system, skal du bare følge dets grænsefladekrav.
    
- Hvis andre systemer senere skal interagere med dit, kan du selv definere grænsefladen.
    

## Arkitektur

Applikationsarkitektur beskriver, hvordan programmets dele hænger sammen på et overordnet niveau.

- Udviklere bruger ofte standardarkitekturer, som er tilpasset bestemte typer problemer.
    
- Valget af arkitektur afhænger af, hvad systemet skal løse, og hvordan det bedst kan opdeles.
    

### Eksempler på arkitekturer:

- Regelbaserede systemer:
    

- Bruges til at håndtere komplekse situationer via et sæt regler.
    
- Eksempel: Et fejlfindingssystem, hvor supporten stiller spørgsmål baseret på dine svar (f.eks. internetproblemer).  
      
    

- Komponentbaseret arkitektur:
    

- Forsøger at gøre hver del af systemet så uafhængig som muligt.
    
- Gør det nemmere for flere teams at arbejde parallelt, uden at forstyrre hinanden.
    

### Monolitisk arkitektur

I en monolitisk arkitektur er hele applikationen samlet i ét enkelt program, som håndterer alt – f.eks.:

- Brugergrænseflade
    
- Databehandling
    
- Udskrivning
    
- Kommunikation
    
- Forretningslogik m.m.
    

  
  

### Monolitiske operativsystemer

De fleste operativsystemer er bygget som monolitiske systemer – dvs. ét stort program (eller tæt integreret programgruppe), der håndterer:

- Login
    
- Skrivebordsmiljø
    
- Filhåndtering
    
- Opgavestyring
    
- Adgangskontrol
    
- Programstyring og -prioriteter
    

## Client/Server

I en klient/server-arkitektur adskilles systemets dele i:

- Klienter: De dele, som bruger funktioner (typisk brugergrænsefladen).
    
- Servere: De dele, som leverer funktionerne (f.eks. databasen).
    

Fordele:

- Adskillelse af klient og server gør det muligt for udviklere at arbejde på dem uafhængigt.
    
- Flere brugere kan få adgang til og dele samme data.
    
- Kommunikation sker over et netværk (LAN, WAN eller Internettet).
    

### To-lags arkitektur (two-tier):

- Gør det nemmere at have flere klienter, som bruger samme server.  
      
    
- Udfordring: Klienter og servere er stadig tæt koblede.
    

- Klienterne skal kende serverens dataformat.
    
- Ændrer serveren dataformat, skal klienterne også opdateres.
    

- Dette kan medføre ekstra arbejde, især i starten af projekter, hvor krav ikke er helt klare.
    

### Tre-lags arkitektur (three-tier):

- For at øge adskillelsen kan man tilføje et ekstra lag mellem klient og server.
    
- Dette hjælper med at mindske koblingen mellem klienter og servere, hvilket øger fleksibiliteten.
    

### Tre-lags arkitektur

- Mellemlaget (middle tier) fungerer som en buffer eller isolator mellem klienten og serveren.
    
- Det oversætter data mellem serverens format og det format, klienten forventer.
    
- Hvis serverens dataformat ændres, skal kun mellemlaget opdateres — klienten kan fortsætte uden ændringer.
    
- Hvis klienten har brug for data i et nyt format, kan mellemlaget også omforme dataene til klientens behov.
    
- Ved større ændringer, fx hvis serveren mangler data, kan mellemlaget indsætte midlertidige (falske) data, så udviklingen kan fortsætte på begge sider, indtil serveren er opdateret.
    
- Denne adskillelse gør det muligt for forskellige udviklingsteams at arbejde uafhængigt på klient og server uden for meget konflikt.
    

### funktioner i mellemlaget:

- Kan forarbejde data for klientens behov.  
      
    

- Fx kan serveren gemme rådata om salg, mens mellemlaget aggregerer (opsummerer) salgsdata, før det sendes til klienten.
    
- Eksempel: Vise antal solgte klokker pr. medarbejder pr. kvartal, uden at klienten selv skal beregne det.
    

### Multilagsarkitektur (N-tier arkitektur)

- Du kan definere flere lag end bare tre — altså N-lags arkitektur, hvis det giver mening for dit system.
    
- Eksempel på en 4-lags arkitektur:
    

1. Datalag: Lagrer rådata.
    
2. Beregningslag: Udfører aggregeringer og andre beregninger på data.
    
3. Intelligenslag: Bruger kunstig intelligens til at lave anbefalinger baseret på beregningerne.
    
4. Præsentationslag: Viser resultaterne til brugerne.
    

### Component-Based Arkitektur

- I component-based software engineering (CBSE) opfatter man systemet som en samling af løst koblede komponenter, som leverer tjenester til hinanden.
    
- Eksempel: Et system til at planlægge medarbejderes arbejdstider.
    

- Brugergrænsefladen kan hente data direkte fra databasen via en komponent.
    
- Andre komponenter kan stå for specifikke funktioner som tidsplanlægning, brugerstyring eller rapportering.
    

### Service-Orienteret Arkitektur (SOA)

- SOA minder om komponent-baseret arkitektur, men her er systemets dele implementeret som selvstændige tjenester (services).
    
- En service er et selvstændigt program, der kører for sig selv og leverer en bestemt funktion til klienter.
    
- Mange services er implementeret som webservices, som opfylder standarder, så de nemt kan kaldes over internettet.
    
- To almindelige metoder til dataudveksling over nettet er SOAP og REST.
    

  
  

### SOAP

- SOAP er en protokol, der gør det muligt at kalde funktioner på fjerncomputere, også selvom de kører forskellige operativsystemer.
    
- SOAP bruger XML til at pakke forespørgsler, hvor elementer beskriver den funktion, der skal udføres, samt nødvendige parametre.
    

### REST (Representational State Transfer)

- REST er en arkitekturstil, designet til at beskrive, hvordan store systemer som internettet skal fungere.
    
- En RESTful webservice sender en forespørgsel over internettet via en specielt formateret URL (URI).
    
- Svaret indeholder data, som kan være i forskellige formater, fx XML, HTML, JSON eller andre.
    
- REST fokuserer på enkelhed og bruger standard HTTP-metoder som GET, POST, PUT og DELETE til at manipulere data.
    

### Variationer af Service-Oriented Arkitektur

- Service Component Architecture (SCA): Et sæt standarder for SOA defineret af store leverandører som IBM og Oracle.
    
- Microservices: Små, selvstændige services, som kan sammensættes til at bygge dele eller hele applikationer. Fordele inkluderer:
    

- Mulighed for at arbejde på dem separat.
    
- Udskifte versioner uden at forstyrre resten af systemet.
    
- Bruge færdige, "off-the-shelf" microservices.
    

### As a Service (aaS)

- En bred betegnelse for tjenester, som leveres til kunden som en service. Det kan være alt fra software til infrastruktur.
    
- Når man ikke kender den præcise service, bruger man betegnelsen Anything as a Service (XaaS).
    
- Disse services kan leveres via biblioteker, API’er, webbaserede kontrolpaneler, eller via webservices som SOAP og REST.
    

### To vigtige aaS-typer for softwareudvikling

- Infrastructure as a Service (IaaS): Leverer infrastruktur som processorkraft, netværk, lagerplads, backup, sikkerhed, firewalls osv.
    
- Platform as a Service (PaaS): Tilbyder alt nødvendigt for softwareudvikling — fx regnekraft, kompilatorer, værktøjer, og mulighed for at udrulle applikationer i skyen. Ofte uden direkte kontrol over den underliggende infrastruktur.
    

### Data-Centric Arkitektur

I en data-centreret arkitektur er data kernen i systemet. Al software og alle processer er organiseret omkring håndtering, lagring og behandling af data. Arkitekturen fokuserer på at sikre, at data er tilgængelige, konsistente og nemme at dele mellem forskellige dele af systemet eller endda mellem forskellige systemer.

Kendetegn ved Data-Centric arkitektur:

- Central datalager: Der er et centralt sted, hvor data opbevares, typisk en stor database eller en dataplatform.
    
- Adgang til data: Alle applikationer og komponenter kommunikerer via dette datalager.
    
- Data som en service: Data kan ses som en service, der leverer den nødvendige information til de forskellige applikationer og processer.
    
- Fokus på dataintegritet og -kvalitet: Sikrer at data altid er opdaterede, korrekte og tilgængelige.
    
- Let integration: Da data er central, bliver det lettere at integrere forskellige systemer, der deler samme datakilde.
    

### Event-Driven Arkitektur (Hændelsesdrevet arkitektur)

I en hændelsesdrevet arkitektur reagerer forskellige dele af systemet på hændelser, når de opstår. Systemets komponenter lytter efter specifikke begivenheder og udfører handlinger, når de bliver "underrettet" om disse hændelser.

Eksempel:  
Forestil dig en ordreproces for robotdele:

- Når en ordre oprettes, registrerer et opfyldelsesmodul hændelsen og udskriver en pakkeliste og adresseetiket.
    
- Når ordren er afsendt, registrerer et faktureringsmodul hændelsen og udskriver en faktura.
    
- Hvis kunden ikke betaler inden 30 dage, reagerer et håndhævelsesmodul og sender fx en opfølgning.
    

Denne arkitektur gør det muligt for systemets forskellige moduler at arbejde selvstændigt og reagere fleksibelt på ændringer i systemets tilstand.

### Rule-Based Arkitektur (Regelbaseret arkitektur)

I en regelbaseret arkitektur bruger systemet en samling af regler til at bestemme, hvad der skal ske næste gang. Disse systemer kaldes også ofte ekspertsystemer eller vidensbaserede systemer.

Hvordan det virker:  
Systemet følger en række foruddefinerede regler for at løse et problem eller træffe beslutninger. For eksempel kan et fejlfinding system spørge brugeren om symptomer og bruge regler til at bestemme det næste spørgsmål eller en løsning.

Fordele:

- Velegnet, når reglerne for at løse et problem kan identificeres klart.
    
- Kan håndtere komplekse situationer, hvis reglerne er veldefinerede
    

Ulemper:

- Virker dårligt, hvis problemet ikke er klart defineret, og det er svært at fastlægge regler.
    
- Har svært ved at håndtere uventede eller ukendte situationer.
    

  

### Distribueret Arkitektur

I en distribueret arkitektur kører forskellige dele af applikationen på forskellige processorer, og de kan køre samtidigt. Disse processorer kan være placeret på forskellige computere i et netværk eller på forskellige kerner i en enkelt computer (moderne computere har ofte flere kerner, som kan eksekvere kode parallelt).

- Service-orienterede og multitier arkitekturer er ofte distribuerede, hvor forskellige dele kører på forskellige computere.
    
- Komponent-orienterede arkitekturer kan også være distribuerede, hvor forskellige komponenter kører på forskellige kerner i samme computer.
    

### Output Typer

Næsten alle softwareprojekter, der er lidt mere komplekse, kan have gavn af at inkludere forskellige former for rapporter. Forretningsapplikationer bruger typisk rapporter til at vise information om:

- Kunder (hvem køber, hvem har ubetalte regninger, hvor kunderne bor)
    
- Produkter (lagerstatus, priser, hvad der sælger godt)
    
- Brugere (hvilke medarbejdere sælger mest, medarbejdernes arbejdsplaner)
    

Ud over almindelige rapporter bør du også overveje andre former for output, som applikationen kan generere, såsom:

- Udskrifter (både rapporter og andre dokumenter)
    
- Websider
    
- Datafiler
    
- Billedfiler
    
- Lyd (enten til højttalere eller til lydfiler)
    
- Video (vises på skærm eller gemmes som videofiler)
    
- Output til specielle enheder, fx elektroniske skilte, termostater eller andre IoT-enheder
    
- Email
    
- Tekstbeskeder (SMS), som kan sendes lige så let som en email til den rette adresse
    
- Beskeder til pagere (hvis man da kan finde nogen, der ikke er antikvariske!)
    

### Database

Database design er en vigtig del af de fleste applikationer. Det første skridt er at beslutte, hvilken type database programmet skal bruge. Du skal specificere, om applikationen skal gemme data i:

- Tekstfiler
    
- XML-filer
    
- En fuldgyldig relationsdatabase
    
- Noget mere specielt, som en temporal database eller in memory
    
- Eller en kombination af flere af disse
    

Definer hvilken database der skal bruges: Access, SQL Server, Oracle eller MySQL osv……

  
  

### Audit Trails (Revisions spor)

Et revisionsspor holder styr på hver bruger, der ændrer (og i nogle tilfælde også ser) en bestemt post i systemet. Ledelsen kan senere bruge disse spor til at se, hvem der f.eks. gav en kunde en usædvanlig rabat på 120%.

### Brugeradgang (User Access)

Mange applikationer har behov for at give forskellige brugere forskellige adgangsniveauer til data.

En måde at håndtere brugeradgang på er at oprette en tabel, som indeholder brugerne og de rettigheder, de skal have. Programmet kan så deaktivere eller fjerne knapper og menupunkter, som en bestemt bruger ikke må bruge.

### Databasevedligeholdelse (Database Maintenance)

Over tid bliver databasen uorganiseret og fyldt med rod som forkerte postnumre, udgåede telefonnumre, kunder der er flyttet væk for længe siden, og lignende "glemte" data. Derfor skal databasen af og til organiseres, så det er nemmere at finde og håndtere data effektivt.

At fjerne gamle data hjælper med at holde databasen hurtig, men hvis der sker mange ændringer i data, kan det gøre indeksene ineffektive og skade ydelsen. 

igtigt at designe en backup- og gendannelsesplan for databasen (som også er vigtigt af sikkerhedsmæssige årsager). For små systemer kan det være nok at kopiere datafilen til en DVD eller en USB-nøgle en gang imellem. For mere almindelige systemer kopieres databasen ofte automatisk hver nat og gemmes i en periode. 

For kritiske systemer kan man investere i specialiserede databaser, der i realtid kopierer (shadow) alle ændringer til flere maskiner, gerne placeret på forskellige geografiske steder, så man kan klare katastrofer som oversvømmelser eller jordskælv.

### NoSQL-databaser

Relationelle databaser (som SQL) er rygraden i mange applikationer, men der findes andre typer databaser

Typisk er en NoSQL-database én af fire typer:

- Dokumentdatabase: Designet til at lagre dokumenter, som fx data i XML- eller JSON-filer. Data er relativt ustruktureret, så forespørgsler kan være tunge, hvilket kræver hurtige computere og lagringssystemer.
    
- Key-Value Store: Gemmer data som par af nøgle og værdi. For eksempel kan du hente alle oplysninger om en kunde ved at bruge kundens navn eller ID som nøgle.
    
- Kolonneorienteret database (eller wide-column database): Lagrer data i kolonner, ligesom relationelle databaser, men kolonnerne gemmes separat. Det gør det nemt at sprede data over mange steder i skyen, og du behøver kun hente de kolonner, du har brug for, ikke hele rækker.
    
- Grafdatabase: Gemmer objekter, der er relaterede på interessante måder. For eksempel i et socialt netværk, hvor personer er noder og forbindelser mellem dem er kanter. Det kan lagres i relationelle databaser, men grafdatabaser giver mere effektive værktøjer til netop denne slags data.
    

### Cloud-databaser

Cloud-databaser giver en ny mulighed for at håndtere dine databaseløsninger. Forskellige cloud-udbydere tilbyder forskellige niveauer af backup, pålidelighed og skalerbarhed efter behov, hvilket gør det nemmere at tilpasse kapaciteten efter hvor meget data eller trafik du har.

### Dataflows og Tilstande

Mange applikationer bruger data, som flyder mellem forskellige processer. 

Et datasæt, som fx en kundeordre, som bevæger sig gennem en række tilstande. Disse tilstande svarer ofte til processerne i dataflowet. I eksemplet kan en kundeordre have tilstandene: Created, Assembled, Shipped og Billed.

### Træning

Selvom det måske er for tidligt at begynde at skrive træningsmaterialer under den højniveau-designfase, er det vigtigt allerede nu at tænke over, hvordan træningen skal foregå. Systemet kan ændre sig meget fra design til færdig installation, men du kan planlægge træningsmetoder og -formater.

- Træningsformer:  
      
    

- Instruktørledede kurser (fysisk eller online)
    
- Trykte manualer
    
- Instruktionsvideoer
    
- Online dokumentation, som brugerne kan søge i  
      
    

- Forskellige læringsstile:  
    Folk lærer bedst på forskellige måder, så det kan være en god idé at tilbyde flere træningstyper og lade brugerne vælge det, der passer dem bedst.  
      
    
- Hands-on træning:  
    Supervised hands-on træning er ofte meget effektiv, fordi brugerne får øvelse i at bruge systemet i en kontrolleret situation, hvilket minder mest om faktisk brug.  
      
    
- Dokumentation under designfasen:  
    Selvom de fleste detaljer kommer senere, kan du allerede nu dokumentere, hvilke typer træning der bliver nødvendige. Trænere kan så begynde at udvikle materialer baseret på systemets overordnede formål.  
      
    

### Unified Modeling Language (UML)

UML 2.0 indeholder 14 diagramtyper opdelt i tre hovedkategorier:

#### 1. Strukturdiagrammer (Structure diagrams)

Viser systemets statiske struktur, fx klasser, komponenter og implementeringsmiljøet.

- Class diagram: Viser klasser og deres relationer.
    
- Component diagram: Viser komponenter og afhængigheder.
    
- Composite structure diagram: Viser intern struktur af klasser og komponenter.
    
- Deployment diagram: Viser hvordan software distribueres på hardware.
    
- Object diagram: Viser konkrete objekter og deres relationer på et bestemt tidspunkt.
    
- Package diagram: Organiserer klasser og komponenter i pakker.
    
- Profile diagram: Tilpasser UML til specifikke domæner.
    

#### 2. Adfærdsdiagrammer (Behavior diagrams)

Fokuserer på systemets dynamiske adfærd og workflow.

- Activity diagram: Viser flowet af aktiviteter.
    
- State machine diagram: Viser tilstande og tilstandsovergang.
    
- Use case diagram: Viser brugerscenarier og systemets funktioner.
    

#### 3. Interaktionsdiagrammer (Interaction diagrams)

Fokuserer på udveksling af beskeder mellem objekter.

- Communication diagram: Viser objekter og deres beskedudveksling.
    
- Interaction overview diagram: Kombinerer aktiviteter og sekvenser.
    
- Sequence diagram: Viser sekvensen af beskeder over tid.
    
- Timing diagram: Viser tidsrelaterede ændringer i objekter.
    

  
  
  
  
  
  
  
  
  
**