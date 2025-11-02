Adaptive Software Development

[[Typer af Systemudv. metoder]]

## **Hvad er Adaptive Software Development?**


**Adaptive Software Development (ASD)** er en agil systemudviklingsmetode skabt af **Jim Highsmith** i 1990'erne. Den fokuserer på **kontinuerlig tilpasning** til ændringer og kompleksitet i stedet for at følge en fast, lineær plan.

**Filosofi:** "Forandring er konstant - omfavn det i stedet for at bekæmpe det"

---

## **Kerneprincipper**

### **1. Adaptation over Optimization**

- Tilpasning vigtigere end at følge en perfekt plan
- Forvent og velkommen ændringer
- Systemet skal kunne evolvere

### **2. Collaboration**

- Tæt samarbejde mellem alle parter
- Delt viden og ansvar
- Kontinuerlig kommunikation

### **3. Learning**

- Læring gennem hele processen
- Fejl er læringsmuligheder
- Kontinuerlig forbedring

### **4. Emergence**

- Løsninger "emerger" gennem iterationer
- Ikke alt kan planlægges på forhånd
- Kompleksitet håndteres gennem tilpasning

---

## **De 3 Faser i ASD**

### **1. Speculate (Spekuler)**

**Hvad:**

- Planlægningsfase - men med forventning om ændringer
- Definér projektets mission og mål
- Identificér features og funktionalitet
- Planlæg iterations (cycles)

**Aktiviteter:**

- Projekt initiering
- Adaptive cycle planning
- Identificér komponenter
- Prioritér features
- Estimér tid og ressourcer

**Output:**

- Project mission statement
- Release plan
- Iteration plan (typisk 4-8 uger pr. iteration)

**Mindset:**

- "Vi spekulerer på hvad der skal bygges"
- "Vi forventer at planen ændrer sig"
- Ikke "Vi ved præcis hvad vi skal bygge"

---

### **2. Collaborate (Samarbejd)**

**Hvad:**

- Udviklingsfasen hvor teamet samarbejder intensivt
- Bygger funktionalitet gennem iterationer
- Kontinuerlig kommunikation og koordinering

**Aktiviteter:**

- Parallel development af komponenter
- Daglige møder (standup)
- Collaborative work sessions
- Teknisk review
- Knowledge sharing

**Nøgleelementer:**

- **Joint Application Development (JAD)** - Brugere og udviklere arbejder sammen
- **Peer reviews** - Kontinuerlig kvalitetssikring
- **Pair programming** - To udviklere, én computer
- **Cross-functional teams** - Alle kompetencer repræsenteret

**Output:**

- Funktionel software i hver iteration
- Updated documentation
- Lessons learned

---

### **3. Learn (Lær)**

**Hvad:**

- Evaluerings- og læringsfase
- Review af hvad der virker/ikke virker
- Justér tilgang og planer

**Aktiviteter:**

- **Quality reviews** - Teknisk kvalitet
- **Customer focus groups** - Brugerfeedback
- **Project retrospectives** - Hvad kan forbedres?
- **Software inspections** - Code review

**3 typer reviews:**

**a) Customer Focus Groups**

- Brugere tester software
- Feedback på funktionalitet og usability
- Validerer om vi bygger det rigtige

**b) Technical Reviews**

- Teknisk kvalitet af koden
- Arkitektur og design review
- Performance og sikkerhed

**c) Project Retrospectives**

- Team reflekterer over processen
- Hvad gik godt?
- Hvad kan forbedres?
- Actionable improvements

**Output:**

- Feedback til næste iteration
- Process improvements
- Adjusted plans
- Lessons learned database

---

## **ASD Lifecycle - Iterativ Cyklus**

```
┌──────────────────────────────────────────────┐
│         PROJEKT START                        │
│  - Mission statement                         │
│  - Initial requirements                      │
└──────────────┬───────────────────────────────┘
               │
               ▼
┌──────────────────────────────────────────────┐
│  1. SPECULATE (Planlæg iteration)            │
│     - Plan cycle (4-8 uger)                  │
│     - Prioritér features                     │
│     - Fordel opgaver                         │
└──────────────┬───────────────────────────────┘
               │
               ▼
┌──────────────────────────────────────────────┐
│  2. COLLABORATE (Udvikl)                     │
│     - Concurrent development                 │
│     - Daily collaboration                    │
│     - Continuous integration                 │
└──────────────┬───────────────────────────────┘
               │
               ▼
┌──────────────────────────────────────────────┐
│  3. LEARN (Review & Tilpas)                  │
│     - Customer review                        │
│     - Technical review                       │
│     - Retrospective                          │
└──────────────┬───────────────────────────────┘
               │
               ▼
         <Mere at bygge?> ──Ja──> [Tilbage til SPECULATE]
               │
              Nej
               │
               ▼
         [PROJEKT SLUT]
```

---

## **Karakteristika ved ASD**

### **Iterationer (Cycles)**

- Korte cycles (4-8 uger)
- Hver cycle leverer brugbar software
- Parallel udvikling af komponenter
- Overlappende cycles muligt

### **Timeboxing**

- Fast tidsramme for hver iteration
- Features prioriteres inden for tiden
- Acceptér at ikke alt bliver færdigt

### **Feature-Based Development**

- Fokus på business features
- Hver feature leverer værdi
- Prioritering baseret på business value

### **Risk-Driven**

- Adressér højrisiko områder først
- Kontinuerlig risiko-vurdering
- Eksperimenter for at reducere usikkerhed

---

## **ASD vs. Traditionelle Metoder**

|**Aspekt**|**ASD**|**Vandfaldsmodel**|
|---|---|---|
|**Planlægning**|Spekulativ, fleksibel|Detaljeret, fast|
|**Ændringer**|Omfavnes|Minimeres|
|**Udvikling**|Iterativ, parallel|Sekventiel|
|**Feedback**|Kontinuerlig|Ved projektets slut|
|**Læring**|I hver iteration|Post-project|
|**Risiko**|Håndteres løbende|Identificeres tidligt|
|**Leverancer**|Hyppige, inkrementelle|Én stor leverance|

---

## **Roller i ASD**

### **Project Leader (ikke manager)**

- Faciliterer snarere end kontrollerer
- Fjerner barrierer
- Støtter teamet

### **Development Team**

- Self-organizing
- Cross-functional
- Collaborative

### **Customer Representative**

- Aktiv deltager
- Giver kontinuerlig feedback
- Prioriterer features

### **Stakeholders**

- Involveret i reviews
- Giver input til retning
- Validerer deliverables

---

## **Collaborative Techniques i ASD**

### **1. JAD Sessions (Joint Application Development)**

- Strukturerede workshops
- Brugere + udviklere sammen
- Hurtig requirements gathering

### **2. Pair Programming**

- To udviklere, én computer
- Kontinuerlig code review
- Knowledge sharing

### **3. Daily Stand-ups**

- Hvad gjorde jeg i går?
- Hvad gør jeg i dag?
- Hvilke blokeringer har jeg?

### **4. Collaborative Design**

- Whiteboard sessions
- Prototyping sammen
- Shared ownership

---

## **Learning Techniques**

### **Focus Groups**

```
Formål: Få brugerfeedback
Deltagere: 5-10 repræsentative brugere
Aktiviteter:
- Demo af ny funktionalitet
- Hands-on testing
- Feedback session
- Prioritering af ændringer
```

### **Technical Reviews**

```
Formål: Teknisk kvalitetssikring
Deltagere: Development team
Aktiviteter:
- Code review
- Architecture assessment
- Performance analysis
- Security review
```

### **Retrospectives**

```
Formål: Process improvement
Deltagere: Hele team
Format:
- What went well? (Continue)
- What didn't? (Stop)
- What should we try? (Start)
```

---

## **Fordele ved ASD**

✅ **Fleksibilitet** - Håndterer ændringer godt  
✅ **Hurtigere time-to-market** - Tidlige releases  
✅ **Bedre kvalitet** - Kontinuerlig review og test  
✅ **Højere kundetilfredshed** - Involvering gennem hele processen  
✅ **Risikoreduktion** - Problemer opdages tidligt  
✅ **Team læring** - Kontinuerlig forbedring  
✅ **Realistiske forventninger** - Spekulativ planlægning

---

## **Ulemper ved ASD**

❌ **Kræver erfarne teams** - Self-organization er svært  
❌ **Intensiv kommunikation** - Mange møder og reviews  
❌ **Svært at estimere** - Spekulativ natur gør budgettering svær  
❌ **Dokumentation** - Kan blive nedprioriteret  
❌ **Kræver aktiv kunde** - Hvis kunde ikke deltager, fejler det  
❌ **Scope creep** - Konstante ændringer kan udvide scope  
❌ **Stressende** - Højt tempo og konstant tilpasning

---

## **Hvornår bruge ASD?**

### ✅ **Brug ASD når:**

- Kravene er usikre eller ændrer sig ofte
- Komplekse, innovative projekter
- Tæt kunde-samarbejde muligt
- Erfarne, self-organizing teams
- Hurtig time-to-market vigtig
- Høj grad af usikkerhed/risiko

### ❌ **Undgå ASD når:**

- Faste, veldefinerede krav
- Kritiske systemer med strenge compliance-krav
- Kunde kan ikke deltage aktivt
- Uerfarne teams
- Meget store projekter (>100 personer)
- Fixed-price kontrakter med fast scope

---

## **ASD vs. Andre Agile Metoder**

|**Metode**|**Fokus**|**Iterations**|**Planlægning**|
|---|---|---|---|
|**ASD**|Tilpasning, læring|4-8 uger|Spekulativ|
|**Scrum**|Sprints, ceremonies|2-4 uger|Sprint planning|
|**XP**|Tekniske practices|1-2 uger|User stories|
|**Kanban**|Flow, WIP limits|Kontinuerlig|Just-in-time|

**ASD's særkende:**

- Stærkere fokus på **læring** og **tilpasning**
- Mindre rigid end Scrum
- Mere fokus på **collaboration** end XP

---

## **Praktisk Eksempel**

### **Projekt: E-commerce platform**

**Mission:** "Bygge en moderne e-commerce platform der kan håndtere 10,000 brugere og tilpasse sig hurtigt ændrede markedsbehov"

**Iteration 1 (6 uger):**

**SPECULATE:**

- Features: Produktkatalog, søgefunktion, indkøbskurv
- Risiko: Performance med mange produkter
- Team: 6 udviklere, 1 UX designer

**COLLABORATE:**

- Uge 1-2: Produktkatalog udvikles
- Uge 3-4: Søgefunktion og kurv parallelt
- Uge 5-6: Integration og test
- Daglige standups, pair programming på kritiske dele

**LEARN:**

- Customer focus group: "Søgningen er for langsom"
- Technical review: "Database indexering mangler"
- Retrospective: "Bedre task breakdown næste gang"
- **Tilpasning:** Prioritér search performance i iteration 2

**Iteration 2:**

- Justeret baseret på læring
- Performance optimering prioriteres
- Nye features tilføjes baseret på feedback

---

## **Værktøjer til ASD**

### **Collaboration:**

- **Slack/Teams** - Kommunikation
- **Miro/Mural** - Virtual whiteboard
- **Zoom/Meet** - Video møder

### **Project Management:**

- **Jira** - Issue tracking
- **Trello** - Kanban boards
- **Azure DevOps** - End-to-end

### **Development:**

- **Git** - Version control
- **CI/CD pipelines** - Continuous integration
- **Automated testing** - Quality assurance

### **Learning:**

- **Confluence** - Knowledge base
- **Retrospective tools** - FunRetro, TeamRetro
- **Survey tools** - Feedback fra brugere

---

## **Konklusion**

**Adaptive Software Development** er ideel til projekter hvor:

- 🔄 Forandring er konstant
- 📚 Læring er central
- 🤝 Samarbejde er intensivt
- 🎯 Tilpasning er vigtigere end at følge en plan

**Nøglen:** Omfavn kompleksitet og usikkerhed gennem **spekulativ planlægning**, **intens collaboration** og **kontinuerlig læring**.