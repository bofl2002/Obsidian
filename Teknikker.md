[[Systemudviklingsmetoder]]

Teknikker er generiske beskrivelser af, hvad vi gør, og hvad vi ønsker at opnå med det. F.eks. hvis man vil lave et diagram, der på et konceptuelt plan beskriver de informationer, som skal behandles i systemet.

En **teknik** er en **generisk beskrivelse** af:

- **Hvad** vi gør
- **Hvad** vi ønsker at opnå
- **Formålet** med aktiviteten

Teknikken er **abstrakt** og **værktøjs-uafhængig**.

### **Eksempel: Konceptuel Informationsmodellering**

**Teknikken:**

"Lave et diagram, der på et konceptuelt plan beskriver de informationer, som skal behandles i systemet"

**Hvad vi gør:**

Identificerer centrale koncepter i domænet
Finder relationer mellem koncepter
Definerer attributter for koncepter
Modellerer informationsstrukturen

**Hvad vi ønsker at opnå:**

Fælles forståelse af domænet
Dokumentation af informationsbehov
Grundlag for system design
Kommunikation med stakeholders

**Værktøjer til denne teknik:**

UML Class Diagram (objekt-orienteret perspektiv)
Entity-Relationship Diagram (database perspektiv)
Domænemodel notation (DDD perspektiv)
Konceptuel datamodel


### **Konceptuel Model af Bibliotekssystem**

**Teknikken anvendt:**

"Beskriv informationer der skal behandles i systemet på konceptuelt niveau"

**Koncepter identificeret:**

Bog
Låner
Udlån
Forfatter

**Relationer:**

En låner kan låne mange bøger
En bog kan have flere forfattere
Et udlån knytter låner til bog

**Attributter (information):**

Bog: titel, ISBN, udgivelsesår
Låner: navn, medlemsnummer, kontaktinfo
Udlån: udlånsdato, afleveringsdato

## **Eksempler på Teknikker**

### **1. Procesmodellering**

**Teknikken:** "Beskrive arbejdsgange og processer i systemet"

**Hvad vi gør:**

- Identificere aktiviteter
- Definere rækkefølge
- Finde beslutningspunkter
- Kortlægge flow

**Hvad vi ønsker at opnå:**

- Forståelse af arbejdsgange
- Identificere ineffektivitet
- Dokumentere "as-is" og "to-be"
- Automatiseringsmuligheder

**Værktøjer:**

- UML Activity Diagram
- BPMN
- Flowchart
- Data Flow Diagram
- Swimlane Diagram

---

### **2. Use Case Modellering**

**Teknikken:** "Identificere systemets funktionalitet fra brugerens perspektiv"

**Hvad vi gør:**

- Identificere aktører (brugere)
- Beskrive use cases (funktionalitet)
- Definere relationer mellem use cases
- Specificere systemgrænser

**Hvad vi ønsker at opnå:**

- Funktionelle krav
- Brugerhistorier
- Scope definition
- Fælles forståelse af systemet

**Værktøjer:**

- UML Use Case Diagram
- User Story Cards
- Feature List
- Use Case Specifications (tekst)

---

### **3. Interaktionsmodellering**

**Teknikken:** "Beskrive hvordan objekter/komponenter kommunikerer over tid"

**Hvad vi gør:**

- Identificere objekter/deltagere
- Beskrive message flow
- Definere rækkefølge af interaktioner
- Vise asynkron/synkron kommunikation

**Hvad vi ønsker at opnå:**

- Forståelse af systemdynamik
- Design af API'er
- Identificere performance bottlenecks
- Dokumentere protokoller

**Værktøjer:**

- UML Sequence Diagram
- UML Communication Diagram
- Message Sequence Charts
- Timing Diagrams

---

### **4. Tilstandsmodellering**

**Teknikken:** "Beskrive hvordan objekters tilstand ændrer sig over tid"

**Hvad vi gør:**

- Identificere mulige tilstande
- Definere transitions (overgange)
- Specificere events der trigger transitions
- Beskrive guards og actions

**Hvad vi ønsker at opnå:**

- Forståelse af objekters livscyklus
- Validering af forretningsregler
- Design af state machines
- Test scenarios

**Værktøjer:**

- UML State Machine Diagram
- State Transition Tables
- State Charts
- Petri Nets

---

### **5. Arkitekturmodellering**

**Teknikken:** "Beskrive systemets overordnede struktur og komponenter"

**Hvad vi gør:**

- Identificere hovedkomponenter
- Definere lag/layers
- Beskrive dependencies
- Vise deployment

**Hvad vi ønsker at opnå:**

- Systemoverblik
- Tekniske beslutninger
- Skalerbarhed og vedligeholdelse
- Kommunikation med stakeholders

**Værktøjer:**

- UML Component Diagram
- UML Deployment Diagram
- C4 Model
- Layered Architecture Diagram
- 4+1 View Model

---

### **6. Kravdokumentation**

**Teknikken:** "Dokumentere hvad systemet skal kunne"

**Hvad vi gør:**

- Indsamle krav fra stakeholders
- Kategorisere krav (funktionelle/ikke-funktionelle)
- Prioritere krav
- Validere krav

**Hvad vi ønsker at opnå:**

- Klare specifikationer
- Fælles forventninger
- Testgrundlag
- Kontrakt mellem kunde og leverandør

**Værktøjer:**

- User Stories
- Use Case Specifications
- Requirements Specification Document (IEEE 830)
- Feature Lists
- BDD Scenarios (Given-When-Then)

---

### **7. Test Design**

**Teknikken:** "Planlægge hvordan systemet skal testes"

**Hvad vi gør:**

- Identificere testscenarier
- Definere test cases
- Specificere test data
- Planlægge test execution

**Hvad vi ønsker at opnå:**

- Systematisk testning
- Kvalitetssikring
- Fejl-opdagelse
- Dokumenteret test coverage

**Værktøjer:**

- Test Case Templates
- Decision Tables
- Test Matrices
- BDD Frameworks (Cucumber)
- State Transition Testing

---

## **Struktur af en Teknik**

Hver teknik har typisk:

### **1. Input**

Hvad skal vi have for at kunne udføre teknikken?

**Eksempel (Konceptuel modellering):**

- Domænekendskab
- Stakeholder interviews
- Eksisterende dokumentation
- Forretningsprocesser

### **2. Aktiviteter**

Hvad gør vi konkret?

**Eksempel:**

- Identificer hovedkoncepter (substantiver i domænet)
- Find relationer mellem koncepter (verber)
- Definer attributter (egenskaber)
- Validér med stakeholders

### **3. Output**

Hvad producerer teknikken?

**Eksempel:**

- Konceptuel model
- Ordliste (glossary)
- Forretningsregler
- Valideret forståelse

### **4. Formål**

Hvorfor gør vi det?

**Eksempel:**

- Fælles forståelse
- Grundlag for design
- Kommunikation
- Krav-validering

## **Hvorfor er Distinktionen Vigtig?**

### **Teknik (Hvad/Hvorfor) ≠ Værktøj (Hvordan)**

**Fordele ved at skelne:**

1. **Fleksibilitet**
    - Samme teknik kan bruges med forskellige værktøjer
    - Kan skifte værktøj uden at ændre teknik
2. **Læring**
    - Forstå principperne bag (teknik)
    - Lær notation bagefter (værktøj)
3. **Kontekst-afhængighed**
    - Vælg værktøj baseret på målgruppe
    - Teknisk publikum: UML
    - Forretning: Simplere notationer
4. **Standardisering**
    - Teknikken er stabil over tid
    - Værktøjer kan ændre sig (UML 2.0 → 2.5)