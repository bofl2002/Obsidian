Extreme Programming

[[Typer af Systemudv. metoder]]


XP-Extreme programming

Extreme Programming (XP) er en agil udviklingsmetodologi skabt af Kent Beck i slutningen af 1990'erne. XP er et agilt softwareudviklingsframework, der sigter mod at producere højere kvalitetssoftware og højere livskvalitet for teamet. [What is Extreme Programming (XP)? | Agile Alliance](https://agilealliance.org/glossary/xp/)

Tenikker

## Kerneteknikker

Pair Programming er en grundpille i XP, hvor to udviklere arbejder sammen ved samme computer - den ene skriver kode, mens den anden gennemgår og foreslår forbedringer. Dette øger kodekvaliteten og deler viden mellem teammedlemmer.

Test-Driven Development (TDD) følger cyklussen rød-grøn-refactor: Skriv først en test der fejler, implementer derefter minimal kode for at få den til at lykkes, og refaktorer til sidst koden. Dette sikrer høj testdækning og bedre design.

Continuous Integration betyder at kode integreres og testes automatisk flere gange dagligt. Alle ændringer committes til et fælles repository, og automatiserede tests køres for at fange konflikter tidligt.

Refactoring er kontinuerlig forbedring af kodestruktur uden at ændre funktionalitet. Dette holder kodebasen ren og vedligeholdelig over tid.

## Planlægning og kommunikation

Planning Game involverer både kunder og udviklere i at prioritere og estimere user stories. Kunder bestemmer prioritet og omfang, mens udviklere estimerer indsats og risici.

Small Releases betyder hyppige leverancer af fungerende software - typisk hver 1-4 uge. Dette giver hurtig feedback og reducerer risiko.

On-Site Customer sikrer at en kunde eller produktrepræsentant er tilgængelig for at besvare spørgsmål og give feedback løbende.

## Designprincipper

Simple Design følger princippet om at implementere den enklest mulige løsning der opfylder kravene nu, frem for at bygge for fremtidige behov.

Collective Code Ownership betyder at alle teammedlemmer kan og skal ændre enhver del af kodebasen. Dette fremmer videndeling og reducerer flaskehalse.

Coding Standards etablerer fælles konventioner for kodestil, navngivning og struktur, så al kode ser ensartet ud uanset hvem der har skrevet den.

  

## Værktøjer

De mest anvendte værktøjer inkluderer versionskontrolsystemer som Git, automatiserede build-værktøjer som Maven eller Gradle, testing frameworks som JUnit, og continuous integration platforme som Jenkins eller GitHub Actions.

XP's styrke ligger i kombinationen af disse praktikker - de forstærker hinanden og skaber en robust udviklingsproces med høj kvalitet og fleksibilitet.

  

## Fem kerneværdier

XP bygger på fem fundamentale værdier:

Kommunikation er afgørende for teamets succes. XP lægger vægt på konstant dialog mellem teammedlemmer og med kunder gennem face-to-face samtaler og tæt samarbejde.

Enkelhed handler om at gøre det enklest mulige, der virker. Dette betyder at fokusere på nuværende behov frem for at bygge for fremtidige, usikre krav.

Feedback opnås gennem korte iterationer, hyppige releases og kontinuerlig testing. Dette sikrer hurtig validering af antagelser og mulighed for rettelser.

Mod involverer at træffe svære beslutninger, som at kassere kode der ikke virker, eller at ændre arkitektur når det er nødvendigt.

Respekt for teammedlemmer, kunder og koden selv. Dette skaber et miljø hvor alle kan bidrage optimalt.

## De 12 kernepraksis

XP definerer tolv specifikke praksis organiseret i fire kategorier:

Planlægningspraksis:

- Planning Game: Kunder og udviklere samarbejder om at prioritere features baseret på forretningsværdi og teknisk risiko
    
- Small Releases: Hyppige, små leverancer af funktionel software
    
- Customer på stedet: En kunderepræsentant er tilgængelig for at besvare spørgsmål og give feedback
    

Designpraksis:

- Simple Design: Design kun til nuværende krav, ikke fremtidige muligheder
    
- Refactoring: Kontinuerlig forbedring af kodestruktur uden at ændre funktionalitet
    
- System Metaphor: En fælles forståelse af systemet gennem metaforer og navngivning
    

Kodning Praksis:

- Pair Programming: To udviklere arbejder sammen ved samme computer
    
- Collective Code Ownership: Alle i teamet kan ændre enhver del af koden
    
- Coding Standards: Ensartede kodestandarder for hele teamet
    

Testpraksis:

- Test-Driven Development (TDD): Skriv tests før koden
    
- Continuous Integration: Hyppig integration af kode i hovedgrenen.
    
- Acceptance Testing: Automatiserede tests baseret på kundekrav
    

## Styrker og udfordringer

XP's styrker inkluderer høj kodekvalitet gennem pair programming og TDD, hurtig feedback, fleksibilitet over for ændringer og stærkt teamsamarbejde. Metodologien er særligt effektiv for små til mellemstore teams og projekter med skiftende krav.

Udfordringerne omfatter kravet om dedikerede, erfarne udviklere, behovet for en engageret kunde på stedet, og potentielle vanskeligheder med skalering til større teams. XP er bygget til at lade små til mellemstore teams producere højkvalitetssoftware og tilpasse sig udviklende og skiftende krav. [What Is Extreme Programming (XP)? - Values, Principles, And Practices](https://www.nimblework.com/agile/extreme-programming-xp/)

XP adskiller sig fra andre agile metoder ved sit stærke fokus på de tekniske aspekter af softwareudvikling og sine specifikke programmeringspraksis.

Validering

Valider foretages for at sikre at det er det rigtige der skal udvikles til kunden. Fjerne det ikke nødvendige. Forventningsafstemning med kunden. (Teorien)

Verificering

Foretages for at sikre at det er udviklet på den rigtige måde (Praktikken)