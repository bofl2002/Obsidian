[[Systemudviklingsmetoder]]

Værktøjer er en praktisk beskrivelse af, hvordan teknikken skal udføres, det kendes bl.a. fra UML. Et eksempel på to forskellige værktøjer til at udføre ovenstående teknik er enten Objekt Modellen eller Domænemodellen.

**Værktøj (Tool/Notation)**

- **Hvordan** teknikken udføres
- **Konkret notation** eller **standard**
- Praktisk implementation af teknikken


**Værktøjer i Systemudvikling**

Værktøjer er **konkrete notationer, standarder eller frameworks** der giver en praktisk beskrivelse af hvordan en teknik udføres.

---

**UML Værktøjer (14 diagramtyper)**

**Strukturelle Diagrammer**

1. Class Diagram (Klassediagram)

Viser klasser, attributter, metoder og relationer
Notation: Rektangler med 3 sektioner
Symboler: + (public), - (private), # (protected)
Relationer: Association, Aggregation (◇), Composition (◆), Inheritance (▷)

2. Object Diagram (Objektdiagram)

Viser konkrete objektinstanser
Notation: Som Class Diagram, men med understreget navn
Eksempel: kunde1: Kunde i stedet for Kunde

3. Component Diagram (Komponentdiagram)

Viser systemets komponenter og interfaces
Notation: Rektangler med «component» stereotype eller plugin-ikon
Viser dependencies mellem komponenter

4. Composite Structure Diagram

Viser intern struktur af en klasse
Notation: Parts, ports, connectors
Bruges til komplekse sammensatte strukturer

5. Package Diagram (Pakkediagram)

Viser organisering i packages
Notation: Mappe-ikoner med dependencies
Relationer: <<import>>, <<merge>>, <<access>>

6. Deployment Diagram (Implementeringsdiagram)

Viser fysisk deployment af artefakter
Notation: 3D-kasser for nodes, artefakter som dokumenter
Eksempel: Servere, databaser, netværk

7. Profile Diagram

Udvider UML med domæne-specifikke elementer
Notation: Stereotypes, tagged values, constraints
Bruges til at tilpasse UML

---

Adfærdsmæssige Diagrammer

8. Use Case Diagram

Viser systemets funktionalitet fra brugerens perspektiv
Notation:
    Actors: Stickfigures
    Use cases: Ovaler
    System boundary: Rektangel
    Relationer: <<include>>, <<extend>>

9. Activity Diagram (Aktivitetsdiagram)

Viser arbejdsgange og processer
Notation:
    Start: Fyldt cirkel (●)
    Activity: Rund rektangel
    Decision: Diamant (◇)
    Fork/Join: Tyk vandret streg
    End: Fyldt cirkel med kant (◉)

10. State Machine Diagram (Tilstandsdiagram)

Viser objekters tilstande og transitions
Notation:
    State: Rund rektangel
    Initial state: Fyldt cirkel
    Final state: Bull's eye
    Transition: Pile med events/guards/actions

11. Sequence Diagram (Sekvensdiagram)

Viser interaktion mellem objekter over tid
Notation:
    Lifeline: Vertikal stiplet linje
    Activation: Tynd rektangel på lifeline
    Messages: Horisontale pile
    Return: Stiplet pil
    Frames: loop, alt, opt, ref

12. Communication Diagram (Kommunikationsdiagram)

Viser objektinteraktion med fokus på struktur
Notation:
    Objekter: Rektangler
    Links: Linjer mellem objekter
    Messages: Nummererede pile (1, 1.1, 1.2, 2)

13. Timing Diagram

Viser timing constraints mellem objekter
Notation: Timeline med state changes
Bruges til real-time systemer

14. Interaction Overview Diagram

Kombinerer activity og interaction diagrammer
Notation: Activity diagram med interaction frames
High-level view af komplekse interaktioner

---

**Andre Modelleringsværktøjer**

BPMN (Business Process Model and Notation)

Procesmodellering
Notation:
    Events: Cirkler (start, intermediate, end)
    Activities: Runde rektangler
    Gateways: Diamanter (AND, OR, XOR)
    Sequence flow: Pile
    Message flow: Stiplede pile
    Pools/Lanes: Swim lanes

ERD (Entity-Relationship Diagram)

Chen Notation

Entities: Rektangler
Attributes: Ovaler
Relations: Diamanter
Cardinality: 1, N, M notation

Crow's Foot Notation

Entities: Rektangler
Attributes: Inde i rektangler
Relations: Linjer med "crow's foot" symboler
Cardinality: │├ (one-to-many), ├┤ (many-to-many)

IDEF1X

Entities: Rektangler med runde hjørner
Relationships: Linjer med dots/diamonds
Bruges ofte i database design

Data Flow Diagram (DFD)

Processer: Cirkler eller runde rektangler
Data stores: Parallelle linjer eller åben rektangel
External entities: Rektangler
Data flows: Pile
Levels: Context (level 0), Level 1, Level 2, osv.

Flowchart

Start/End: Oval
Process: Rektangel
Decision: Diamant
Input/Output: Parallelogram
Connector: Cirkel
Flow: Pile

Wireframes

Low-fidelity: Håndtegnede eller simple boxes
High-fidelity: Detaljerede UI mockups
Værktøjer: Balsamiq, Figma, Adobe XD, Sketch

C4 Model

Level 1: System Context Diagram
Level 2: Container Diagram
Level 3: Component Diagram
Level 4: Code Diagram
Notation: Simple boxes og pile med forskellige farver

---

**Arkitektur-værktøjer**

ArchiMate

Enterprise architecture notation
Layers: Business, Application, Technology
Aspects: Active structure, Behavior, Passive structure
Farve-kodet: Gul (business), blå (application), grøn (technology)

4+1 View Model

Logical View: Class diagrams
Process View: Activity/Sequence diagrams
Development View: Component/Package diagrams
Physical View: Deployment diagrams
Scenarios: Use case diagrams

Layered Architecture Diagram

Horisontale lag som rektangler
Dependencies som pile
Typisk: Presentation → Business Logic → Data Access

---

**Agile/Lean Værktøjer**

User Story Mapping

Horisontale "backbone" activities
Vertikale "walking skeleton" features
Post-it notes arrangeret i grid
Releases markeret med horisontale linjer

Impact Mapping

Mindmap-struktur
Center: Goal
Level 1: Actors
Level 2: Impacts
Level 3: Deliverables

Kanban Board

Kolonner: Backlog → To Do → In Progress → Done
Cards: Work items
WIP limits: Maksimalt antal per kolonne
Swimlanes: For forskellige typer arbejde

Burndown Chart

X-akse: Tid (dage/sprints)
Y-akse: Work remaining (story points/timer)
Ideal linje vs. actual linje
Viser progress mod deadline

---

**Test-værktøjer (Notationer)**

Test Case Template

Test ID
Test Description
Preconditions
Test Steps
Expected Results
Actual Results
Status (Pass/Fail)

Decision Table

Conditions: Rækker øverst
Actions: Rækker nederst
Rules: Kolonner med Y/N/- værdier
Kombinationer af inputs → outputs

State Transition Table

Rows: Current states
Columns: Events/inputs
Cells: Next state + actions
Alternativ til State Machine Diagram

---

**Database Design Værktøjer**

Normalization Diagrams

1NF, 2NF, 3NF, BCNF representation
Functional dependencies med pile
Candidate keys understreget

Database Schema Diagram

Tables: Rektangler
Columns: Listet med datatyper
Primary keys: Understreget eller nøgle-ikon
Foreign keys: Pile til referenced table
Indexes: Markeret med special notation

---

**Software Værktøjer (til at tegne notationer)**

Desktop Applikationer

Visual Paradigm - Alle UML diagrammer
Enterprise Architect - Enterprise modeling
StarUML - Open source UML
Astah - Lightweight modeling
Microsoft Visio - Generelle diagrammer

Online Værktøjer

Lucidchart - Alle diagramtyper
Draw.io / diagrams.net - Gratis, open source
Miro - Collaboration whiteboard
Creately - Online diagramming
Cacoo - Team collaboration

Code-baserede

PlantUML - Text-to-UML
Mermaid - Markdown-integreret
Graphviz - Graph visualization
Structurizr - C4 model as code

Specialiserede

Balsamiq - Wireframes
Figma - UI/UX design
ARIS - Business process
Bizagi Modeler - BPMN
ERDPlus - ERD modeling

---

**Konklusion**

**Værktøjer giver:**

📐 Standardiseret notation - Fælles symboler og regler
📋 Praktisk guide - Hvordan teknikken udføres konkret
🌍 Internationalt anerkendt - Samme forståelse globalt
✅ Verificerbar - Kan tjekkes om korrekt anvendt
💬 Kommunikationsværktøj - Fælles sprog mellem interessenter