**Tactical Domain-Driven Design (DDD)**

[[Typer af Systemudv. metoder]]

**Tactical DDD** er de konkrete, tekniske mønstre og byggeklodser, der bruges til at implementere domænelogik i kode. Det handler om **hvordan** du organiserer og strukturerer din kode inden for en Bounded Context.

Dette er i modsætning til **Strategic DDD**, som fokuserer på high-level arkitektur, Bounded Contexts, og hvordan forskellige dele af systemet kommunikerer.

**De vigtigste byggeklodser (Building Blocks)**

1. Entities (Entiteter)

**Hvad er det?**

- Objekter med en **unik identitet** der forbliver konstant gennem hele dets livscyklus
- To entities er forskellige, selvom alle deres attributter er identiske

**Karakteristika:**

- Har en unik ID (f.eks. CustomerID, OrderID)
- Identitet er vigtigere end attributter
- Kan ændre tilstand over tid

2. Value Objects

**Hvad er det?**

- Objekter uden identitet - defineres **kun** af deres attributter
- Immutable (uforanderlige)
- To value objects er ens hvis alle attributter er ens

**Karakteristika:**

- Ingen ID
- Beskriver karakteristika eller målinger
- Kan genbruges frit
- Immutable - skal oprettes ny ved ændring

3. Aggregates (Aggregater)

**Hvad er det?**

- En klynge af entities og value objects, der behandles som **én konsistent enhed**
- Har en **Aggregate Root** (rodentitet) som er indgangspunkten

**Karakteristika:**

- Definerer en konsistensgrænse
- Kun Aggregate Root kan tilgås udefra
- Interne objekter kun tilgængelige via roden
- Transaktionsgrænse - ændringer gemmes atomart

4. Repositories

**Hvad er det?**

- Abstraktion der giver adgang til aggregates som om de var i memory
- Skjuler persistence-detaljer

**Karakteristika:**

- Ét repository pr. Aggregate Root
- Leverer illusion af en collection
- Håndterer lagring og hentning

5. Domain Services

**Hvad er det?**

- Operationer der **ikke naturligt hører hjemme** i en entity eller value object
- Stateless operationer

**Hvornår bruge?**

- Logik involverer flere aggregates
- Operationer der ikke er ansvar for én specifik entity
- Koordinering af aktiviteter

6. Domain Events

**Hvad er det?**

- Noget vigtigt der er **sket** i domænet
- Immutable fakta om fortiden

**Karakteristika:**

- Navngivet i datid (OrderPlaced, PaymentReceived)
- Indeholder data om hvad der skete
- Kan udløse reaktioner i andre dele af systemet

7. Factories

**Hvad er det?**

- Ansvarlig for at skabe komplekse objekter eller aggregates
- Indkapsler kompleks konstruktionslogik

Design-principper

1. Ubiquitous Language

Brug samme termer i kode som domæneeksperter bruger
Klassenavne, metoder, og variabler skal matche forretningssprog

2. Bounded Context

Tactical patterns anvendes inden for én Bounded Context
Samme koncept kan have forskellige modeller i forskellige contexts

3. Aggregate Design Guidelines

**Gode praksisser:**

- Hold aggregates små
- Referér til andre aggregates via ID (ikke objektreference)
- Opdatér kun ét aggregate pr. transaktion
- Brug eventual consistency mellem aggregates
- Design omkring use cases og invariants

**Undgå:**

- Store, komplekse aggregates
- At modificere flere aggregates i samme transaktion
- At navigere dybt ind i aggregate-strukturer udefra

Entity vs Value Object - Beslutningsguide

|**Spørgsmål**|**Entity**|**Value Object**|
|---|---|---|
|Har det en unik identitet?|Ja|Nej|
|Ændrer det sig over tid?|Ja|Nej (immutable)|
|Er identitet vigtig?|Ja|Nej|
|**Eksempler**|Customer, Order, Account|Money, Address, DateRange|

---

Fordele ved Tactical DDD

**Bedre domæneforståelse** - Koden afspejler forretningslogikken  
**Stærkere konsistens** - Aggregates sikrer dataintegritet  
**Lettere vedligeholdelse** - Klare grænser og ansvar  
**Testbarhed** - Domænelogik isoleret fra infrastruktur  
**Fleksibilitet** - Nemmere at ændre persistence-strategi

---

Hvornår bruge Tactical DDD?

**Brug det når:**

- Kompleks forretningslogik og -regler
- Domænet er kerneforretningen (Core Domain)
- Langsigtet projekt med vedligeholdelse
- Tæt samarbejde med domæneeksperter muligt

**Undgå det når:**

- Simple CRUD-operationer
- Ingen kompleks forretningslogik
- Kortsigtet projekt eller prototype
- Generic/Supporting subdomains

---

## **Konklusion**

Tactical DDD giver et robust framework til at modellere kompleks domænelogik på en måde, der er både teknisk solid og forretningsvenlig. Nøglen er at forstå **hvornår** og **hvor** i dit system disse patterns giver værdi.