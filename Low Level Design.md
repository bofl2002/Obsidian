
[[Fokusområder]]

**

## Low level Design (LLD)

Overordnet design fokuserer på hvad. Detaljeret design begynder at fokusere på hvordan.

Denne sætning beskriver forskellen mellem de to niveauer af systemdesign:

- Overordnet design (High-level design) handler om at definere hvad systemet skal gøre - altså systemets overordnede funktioner, komponenter og arkitektur.
    
- Detaljeret design (Low-level design) handler om at specificere hvordan systemet skal implementeres - altså de konkrete tekniske løsninger, algoritmer og implementeringsdetaljer.
    

Low-Level Design er en afgørende fase i softwareudvikling, der fungerer som en detaljeret køreplan mellem arkitekturbeslutninger og den faktiske implementering. Her er de vigtigste aspekter:

### Definition og formål

LLD transformerer abstrakte koncepter på højt niveau til detaljerede, handlingsegnede komponenter, som udviklere kan bruge til at bygge systemet. [What is Low Level Design or LLD? - GeeksforGeeks](https://www.geeksforgeeks.org/system-design/what-is-low-level-design-or-lld-learn-system-design/) Det fungerer som en detaljeret tegning, der forbinder arkitektur på højt niveau med faktiske implementeringsklare moduler. [Low-Level Design(LLD) Interview Questions - System Design - GeeksforGeeks](https://www.geeksforgeeks.org/system-design/top-low-level-system-designlld-interview-questions-2024/)

### Hvad LLD indeholder

LLD involverer specifikation af individuelle moduler, datastrukturer [Different types of Low Level Design in System Design - GeeksforGeeks](https://www.geeksforgeeks.org/system-design/different-types-of-low-level-design-in-system-design/) og omfatter typisk:

- Klassedesign: Detaljerede klassediagrammer med metoder, attributter og relationer
    
- Databasedesign: Tabeller, indekser, relationer og forespørgelser
    
- Interface-specifikationer: API'er og kommunikation mellem komponenter
    
- Algoritmer og datastrukturer: Konkrete implementeringsdetaljer
    
- Error handling: Fejlhåndtering og exception management
    

### Forskellen på HLD og LLD

Mens High-Level Design (HLD) fokuserer på systemarkitekturen og komponenternes overordnede samspil, går LLD ned i de tekniske detaljer og svarer på spørgsmålet "hvordan" snarere end "hvad".

### Praktisk anvendelse

I moderne softwareudvikling er objektorienteret design og databasedesign to af de vigtigste dele af LLD. Dette inkluderer:

- Design patterns og SOLID-principper
    
- UML-diagrammer til visualisering
    
- Detaljeret datamodellering
    
- Performance-optimering på kode-niveau
    

  

### Design-to-Schedule (Design efter tidsplan)

Design-to-Schedule er en designtilgang i softwareudvikling, hvor projektets design og funktionalitet tilpasses den tilgængelige tidsramme, snarere end at lade designkravene diktere tidsplanen.

#### Kerneprincipper

I Design-to-Schedule tilgangen:

1. Tidsrammen er fast: Projektets deadline er ikke til forhandling
    
2. Flexibel funktionalitet: Features og kompleksitet justeres for at passe inden for tidsrammen
    
3. Prioriteret levering: De vigtigste funktioner implementeres først
    

LLD er særligt vigtigt, fordi det giver udviklere den nødvendige detaljegrad til at kunne implementere systemet effektivt og vedligeholdeligt.

### Hvornår anvendes det

Design-to-Schedule er særligt relevant ved:

- Projekter med hårde deadlines (f.eks. markedsføring eller juridiske krav)
    
- Startup MVP-udvikling
    
- Prototyping og proof-of-concept projekter
    
- Situationer hvor time-to-market er kritisk
    

### Fordele og ulemper

Fordele:

- Sikrer rettidig levering
    
- Tvinger til prioritering af kernefeatures
    
- Reducerer "feature creep"
    
- Bedre forudsigelige projekter
    

Ulemper:

- Kan kompromittere funktionalitet
    
- Risk for teknisk gæld
    
- Mindre optimal arkitektur
    
- Potentielt lavere kvalitet
    

## Design-to-Tools (Design efter værktøjer)

Design-to-Tools er en designtilgang i softwareudvikling, hvor projektets arkitektur og implementering tilpasses de tilgængelige udviklings- og implementeringsværktøjer, snarere end at vælge værktøjer baseret på ideelle designkrav.

  

### Kerneprincipper

I Design-to-Tools tilgangen:

1. Værktøjerne er begrænsende faktorer: Eksisterende teknologi og værktøjer definerer mulighedsrammen
    
2. Pragmatisk tilgang: Design tilpasses til hvad der faktisk kan implementeres effektivt
    
3. Udnyt værktøjernes styrker: Maksimer brugen af indbyggede funktioner og capabilities
    

#### Eksempler på værktøjsdrevet design

- Database-first design: Lad databasens struktur og capabilities drive applikationslogikken
    
- Framework-centreret arkitektur: Byg løsningen omkring et specifikt framework (f.eks. Django, Spring Boot)
    
- Cloud-native design: Tilpas arkitekturen til specifikke cloud-tjenester (AWS Lambda, Azure Functions)
    
- Low-code/No-code platforms: Design inden for platformens templates og komponenter
    

### Fordele og ulemper

Fordele:

- Hurtigere udvikling ved at udnytte eksisterende værktøjer
    
- Lavere læringskurve for teamet
    
- Ofte mere stabile og velafprøvede løsninger
    
- Reducerede udviklings- og vedligeholdelsesomkostninger
    

Ulemper:

- Kan begrænse kreativitet og optimal problemløsning
    
- Risiko for "golden hammer" syndrom (alt ser ud som søm)
    
- Potentielt suboptimal performance eller skalerbarhed
    
- Vendor lock-in og afhængighed af tredjepartsværktøjer
    

### Hvornår anvendes det

Design-to-Tools er særligt relevant når:

- Teamet har dybe kompetencer inden for specifikke teknologier
    
- Budgettet eller tiden er begrænset
    
- Der er krav om at bruge organisationens standardværktøjer
    
- Vedligeholdelse og support prioriteres højt
    
- Projektet ikke kræver cutting-edge teknologi
    

Denne tilgang kræver et godt kendskab til værktøjernes kapaciteter og begrænsninger for at kunne træffe informerede designbeslutninger.

  

## Process-Oriented Design (Procesorienteret design)

Process-Oriented Design er en designtilgang der fokuserer på systemets processer og arbejdsgange som det primære organiseringsprincip.

### Princip

Systemet designes omkring de forretningsprocesser eller workflows, det skal understøtte. Strukturen følger trinene i processen fra start til slut.

### Karakteristika

- Sekventiel flow: Design følger processens naturlige rækkefølge
    
- Funktionel opdeling: Hver komponent håndterer et specifikt procestrin
    
- Input-output fokus: Klar definition af hvad der går ind og ud af hvert trin
    

### Eksempler

- E-handel: Produktvisning → Kurv → Betaling → Ordrebekræftelse → Forsendelse
    
- Lønkørsel: Tidsregistrering → Beregning → Godkendelse → Udbetaling
    
- Kundesupport: Oprettelse → Kategorisering → Tildeling → Behandling → Lukning
    

### Fordele

- Intuitivt for forretningsbrugere
    
- Klar procesflow og ansvarsfordeling
    
- Nem at forstå og vedligeholde
    
- Understøtter workflow automation
    

### Ulemper

- Kan blive rigidt og infleksibelt
    
- Svært at håndtere parallelle processer
    
- Udfordring ved procesomlægninger
    
- Mindre genbrugelige komponenter
    

### Hvornår bruges det

Velegnet til systemer med veldefinerede, lineære forretningsprocesser hvor workflow-understøttelse er kritisk.

## Hybrid Approaches (Hybride tilgange)

Hybrid Approaches kombinerer forskellige designtilgange for at udnytte fordelene ved hver metode og minimere deres individuelle begrænsninger.

### Princip

I stedet for at vælge én enkelt designtilgang, blandes flere metoder strategisk baseret på projektets forskellige behov og komponenter.

### Almindelige kombinationer

- Design-to-Schedule + Design-to-Tools: Fast deadline med begrænsede værktøjer
    
- Object-Oriented + Process-Oriented: OOP for datastrukturer, procesorienteret for workflows
    
- High-Level Architecture + Tool-Driven Implementation: Strategisk arkitektur med pragmatisk implementering
    

### Eksempler

- E-commerce platform:
    

- Process-oriented for checkout-flow
    
- Object-oriented for produktkatalog
    
- Tool-driven for betalingsintegration
    

- Enterprise system:
    

- Service-oriented architecture overordnet
    
- Database-first for rapportering
    
- Schedule-driven for kritiske moduler
    

### Fordele

- Fleksibilitet: Tilpas tilgangen til specifikke områder
    
- Optimeret løsning: Bedste metode til hver komponent
    
- Balancerede trade-offs: Minimer svaghederne ved enkelte tilgange
    
- Realistisk: Matcher komplekse projekters virkelige behov
    

### Ulemper

- Kompleksitet: Sværere at administrere forskellige tilgange
    
- Konsistensudfordringer: Risk for inkonsekvente designbeslutninger
    
- Kræver erfaring: Teamet skal mestre flere metoder
    

### Best Practices

- Definér klart hvor hver tilgang anvendes
    
- Dokumentér begrundelser for tilgangsskift
    
- Sikr sammenhæng på tværs af forskellige designområder
    
- Evaluér regelmæssigt om kombinationen fungerer optimalt
    

Hybrid approaches anerkender at moderne software sjældent passer perfekt ind i én designkategori.

## Data-Oriented Design (Dataorienteret design)

Data-Oriented Design er en designtilgang der prioriterer datastrukturer og datahåndtering som det fundamentale organiseringsprincip i systemarkitekturen.

### Princip

Systemet designes primært omkring dataens struktur, flow og transformation. Funktionalitet og processer tilpasses datamodellen snarere end omvendt.

### Kerneelementer

- Data først: Datastrukturer defineres før funktionalitet
    
- Transformation-fokus: Systemet ses som datapipelines
    
- Cache-venlig: Optimeret for moderne CPU-arkitektur
    
- Locality of reference: Data organiseres for effektiv hukommelsesadgang
    

### Karakteristika

- Strukturer over objekter: Arrays og structs frem for komplekse objekthierarkier
    
- Hot/cold data separation: Adskillelse af ofte/sjældent brugte data
    
- Batch processing: Behandling af data i grupper for bedre performance
    
- Minimal indirection: Færre pointere og reference-kæder
    

### Eksempler

- Game engines: Entity Component Systems (ECS)
    
- Databaser: Column-store designs
    
- High-frequency trading: Latency-optimerede datastrukturer
    
- Scientific computing: Numeriske arrays og vectorisering
    

### Fordele

- Høj performance: Optimeret for moderne hardware
    
- Forudsigelig adfærd: Klar dataflow gør systemet lettere at analysere
    
- Skalerbarhed: Parallel processing og cache-effektivitet
    
- Mindre memory footprint: Kompakte datarepræsentationer
    

### Ulemper

- Kompleks design: Kræver dyb forståelse af hardware
    
- Mindre intuitivt: Ikke altid naturligt for forretningslogik
    
- Refactoring-udfordringer: Ændringer i datastrukturer påvirker hele systemet
    
- Begrænsede abstraktioner: Kan være sværere at modularisere
    

### Hvornår bruges det

Særligt værdifuldt i performance-kritiske systemer, real-time applikationer, spil, og systemer der behandler store datamængder.

## Object-Oriented Design (Objektorienteret design)

Object-Oriented Design er en designtilgang der organiserer software omkring objekter - datastrukturer der kombinerer data (attributter) og funktionalitet (metoder) i sammenhængende enheder.

### Kerneprincipper

- Encapsulation (Indkapsling): Data og metoder samles i objekter med kontrolleret adgang
    
- Inheritance (Arv): Klasser kan arve egenskaber fra andre klasser
    
- Polymorphism (Polymorfi): Samme interface kan have forskellige implementeringer
    
- Abstraction (Abstraktion): Skjuler kompleksitet bag simple interfaces
    

### Grundkoncepter

- Klasser: Blueprints der definerer objekters struktur og adfærd
    
- Objekter: Konkrete instanser af klasser
    
- Metoder: Funktioner tilknyttet objekter
    
- Attributter: Data der tilhører objektet
    

### Design Patterns

- Creational: Factory, Singleton, Builder
    
- Structural: Adapter, Decorator, Facade
    
- Behavioral: Observer, Strategy, Command
    

### Eksempler

Klasse: Bil

Attributter: mærke, model, hastighed

Metoder: start(), stop(), accelerer()

Klasse: ElBil (arver fra Bil)

Ekstra attributter: batteriNiveau

Ekstra metoder: oplad()

  

### Fordele

- Genbrug: Kode kan genbruges gennem arv og komposition
    
- Modularity: Klar opdeling i sammenhængende komponenter
    
- Vedligeholdelse: Ændringer isoleres til specifikke objekter
    
- Naturlig modellering: Matcher virkelige domæner godt
    

### Ulemper

- Kompleksitet: Kan skabe komplekse hierarkier
    
- Performance overhead: Indirection og virtual calls
    
- Over-engineering: Tendens til unødvendig abstraktion
    
- Tight coupling: Objekter kan blive for afhængige af hinanden
    

### Objektsammensætning (Object Composition)

Objektsammensætning er en programmeringsteknik, hvor du bygger komplekse klasser ved at kombinere eksisterende klasser som komponenter, i stedet for at bruge nedarvning.

### Grundlæggende koncept

I stedet for at sige "X er en type af Y" (nedarvning), siger objektsammensætning "X har en Y" eller "X består af Y". Du opretter nye funktionaliteter ved at samle objekter fra forskellige klasser.

Praktisk eksempel

Person klasse: Fornavn, Efternavn, Telefon, Adresse

Virksomhed klasse: Navn, CVR-nummer, Kontaktperson (af type Person)

Her "har" Virksomhed en Person, i stedet for at "være" en Person.

Fordele ved objektsammensætning

- Større fleksibilitet: Du kan nemt ændre komponenter runtime
    
- Bedre genbrugsmuligheder: Samme klasse kan bruges i mange forskellige sammenhænge
    
- Undgår hierarkiproblemer: Ingen dybe, komplicerede nedarvningskæder
    
- Naturlig modellering: Afspejler ofte den virkelige verden bedre
    
- Lettere at teste: Komponenter kan testes uafhængigt
    

Hvornår skal du bruge sammensætning?

- Når forholdet er "har en" snarere end "er en"
    
- Når du vil kombinere funktionalitet fra flere kilder
    
- Når du har brug for runtime fleksibilitet
    
- Når nedarvning bliver for kompleks eller ulogisk
    

  
**