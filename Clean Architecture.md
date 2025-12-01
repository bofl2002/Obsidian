[[Programmering]]

# Clean Architecture 

**Clean Architecture** er en arkitekturstil til software, der har som mål at gøre systemer lette at teste, vedligeholde og udvide. Modellen blev kendt gennem Robert C. Martin (Uncle Bob).

Grundideen er at placere forretningslogikken i centrum og sørge for, at tekniske detaljer som databaser, webframeworks og brugergrænseflader aldrig påvirker kernekoden.

---

## Grundprincip

Systemet organiseres i lag, som ligger i koncentriske cirkler. Afhængigheder må kun gå _indad_ mod de mest stabile lag. De inderste lag må aldrig kende til de ydre lag.

---

## Lagene i Clean Architecture

### 1. Domain (Entities)

Dette er det inderste lag og repræsenterer systemets kerneforretningsregler.  
Det indeholder:

- Forretningsobjekter (fx Order, Product, Customer)
    
- Regler og valideringer, der gælder uanset teknologi
    
- Logik, der ikke må afhænge af databaser, UI eller eksterne systemer
    

Dette lag ændrer sig sjældent og skal være fuldstændig teknologineutralt.

### 2. Application / Use Cases

Dette lag beskriver, hvad systemet _skal gøre_, men ikke hvordan det teknisk udføres.

Det indeholder:

- Use cases (fx CreateOrder, UpdateCustomer)
    
- Interfaces (porte), der definerer, hvilken data der skal ind og ud
    
- Orkestrering af domænelogikken
    

Use cases bruger domænet til at udføre handlinger, men kender ikke til database- eller GUI-detaljer.

### 3. Interface Adapters

Dette lag adapterer data mellem use cases og den ydre verden.

Det indeholder:

- Controllers (fra web/API)
    
- Repository-implementeringer (forbindelsen til databasen)
    
- Mappere/DTO’er
    
- Præsentationsmodeller
    

Lagets opgave er at sørge for, at de indre lag modtager og returnerer data i det format, de forventer.

### 4. Frameworks & Drivers

Det yderste lag, som består af konkrete teknologier.

Eksempler:

- Databaser (PostgreSQL, SQL Server, MongoDB)
    
- Webframeworks (ASP.NET, Django, Express)
    
- UI-lag (React, Angular)
    
- Eksterne API’er
    

Dette lag indeholder “detaljerne”, som kan udskiftes uden at påvirke de indre lag.

---

## Afhængighedsreglen

Hovedreglen i Clean Architecture er:

**Ingen ydre lag må påvirke indre lag. Afhængigheder må kun pege indad.**

Det betyder:

- Domain og Use Cases må ikke kende til databaser eller frameworks
    
- Interface Adapters kender use cases, men ikke omvendt
    
- Frameworks kender adaptere, men ikke omvendt
    

På den måde kan du skifte database, UI eller framework uden at ændre på forretningslogikken.

---

## Fordele

- Systemet bliver lettere at teste, især domain- og use-case-laget.
    
- Kernekoden er stabil, selv når teknologi skiftes.
    
- Arkitekturen bliver mere fleksibel og holdbar på lang sigt.
    
- Det bliver tydeligt, hvor logik hører hjemme.
    

---

## Ulemper

- Der er mere kode at skrive, især interfaces og struktur.
    
- Kan virke tung eller unødvendigt kompleks til små projekter.
    
- Teamet skal være enige om principperne for at få fuldt udbytte.
    
