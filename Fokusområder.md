Fokusområde er en guide/vejledning til Systemudviklingsmetoder

Følgende emner er en del af fokusområder:

Projektstyring
Kravindsamling
High Level Design
Low Level Design
Implementering/programmering
Test
Deployment
Maintenance

|Fase|Spørgsmål den besvarer|Output|
|---|---|---|
|Projektstyring|Hvordan styrer vi processen?|Plan, tidslinje, roller|
|Kravsindsamling|Hvad skal systemet kunne?|Kravspecifikation|
|High Level Design|Hvordan hænger det sammen?|Arkitekturdiagrammer|
|Low Level Design|Hvordan bygges det konkret?|Klassediagrammer, databaseplan|
|Programmering|Hvordan virker det i praksis?|Kode|
|Test|Virker det som forventet?|Testresultater|
|Udrulning|Hvordan får brugerne adgang?|Driftssat system|


## Projektstyring – Kvalitetskriterier

**Målet:** Projektet styres effektivt og leverer det aftalte resultat til tiden og inden for rammerne.

**Kvalitetskriterier:**

- Der findes en klar plan med mål, leverancer, deadlines og ansvar.
- Projektet overholder tidsplan og budget (eller afvigelser håndteres dokumenteret).
- Kommunikation mellem interessenter er tydelig og regelmæssig.
- Risici er identificeret og håndteret løbende.
- Ændringer i krav eller prioriteringer håndteres via en kontrolleret change management-proces.

## Kravsindsamling og dokumentation – Kvalitetskriterier

**Målet:** Kravene beskriver præcist, hvad systemet skal kunne, uden misforståelser.

**Kvalitetskriterier:**

- Kravene er entydige, målbare og verificerbare.
- Kravene er prioriterede (must-have vs. nice-to-have).
- Kravene er valideret med brugere og forretningen.
- Kravdokumentet er opdateret, når der sker ændringer.
- Der er sporbarhed fra krav til design, kode og test.

## High Level Design – Kvalitetskriterier

**Målet:** Systemets overordnede arkitektur er gennemtænkt, robust og skalerbar.

**Kvalitetskriterier:**

- Designet opfylder kravene og understøtter alle hovedfunktioner.
- Arkitekturen er modulær og fleksibel.
- Teknologivalg er begrundede.
- Designet understøtter performance, sikkerhed og vedligeholdelse.
- Dokumentationen er klar, opdateret og forståelig.
 
## Low Level Design – Kvalitetskriterier

**Målet:** Der findes et detaljeret teknisk grundlag, som gør kodningen effektiv og entydig.

**Kvalitetskriterier:**

- Alle komponenter, klasser og metoder er klart definerede.
- Designet følger best practices og kodestandarder.   
- Der er ingen duplikation eller overlappende ansvar mellem moduler.
- Databasedesign er normaliseret og effektivt.   
- Designet er gennemgået (reviewet) inden implementering.
-
## Programmering – Kvalitetskriterier

**Målet:** Koden er korrekt, læsbar, testbar og effektiv.

**Kvalitetskriterier:**

- Koden opfylder krav og design.    
- Der bruges kodekonventioner (navngivning, struktur, kommentarer).    
- Koden er modulær og genanvendelig.    
- Der findes enhedstests for vigtige funktioner.    
- Koden er reviewet af kollegaer.    
- Systemet kompilerer og kører uden fejl.
## Test – Kvalitetskriterier

**Målet:** Systemet virker som forventet, uden kritiske fejl.

**Kvalitetskriterier:**

- Der findes en testplan med klare testcases og forventede resultater.
- Alle krav er testet og dækket.    
- Fejl rapporteres og rettes systematisk.    
- Automatiserede tests bruges, hvor det er relevant.    
- Systemet består accepttesten uden alvorlige afvigelser.    
- Testresultater er dokumenterede og sporbare.
## 7. Udrulning – Kvalitetskriterier

**Målet:** Systemet implementeres sikkert, stabilt og uden at forstyrre brugerne unødigt.

**Kvalitetskriterier:**

- Der findes en udrulningsplan (hvem, hvornår, hvordan, rollback-plan).    
- Miljøet er korrekt opsat og testet.    
- Backup og rollback-muligheder er på plads.    
- Brugere og driftsteam er informeret og forberedte.    
- Efter udrulning fungerer systemet fejlfrit og stabilt.    
- Der følges op med monitorering og support.    


### Fokusområdernes påvirkning på hinanden

## Projektstyring

**Projektstyring** fungerer som en ramme omkring alle de andre områder.

- **Påvirker alt:** God planlægning sikrer, at krav, design, kodning, test og udrulning sker i rette rækkefølge, til rette tid og med de rette ressourcer.    
- **Bliver påvirket af de andre:** Hvis krav ændres, eller test afslører store fejl, skal projektstyringen reagere ved at opdatere tidsplan, budget og prioritering.    

**Eksempel:**  
En forsinkelse i testfasen kræver, at projektlederen justerer tidsplanen for udrulning.

## Kravsindsamling/dokumentation

Kravene er **grundlaget** for hele projektet.

- **Påvirker design:** Designet bygges op omkring de krav, der er indsamlet. Uklare krav giver uklart design.    
- **Påvirker test:** Testcases udarbejdes ud fra kravene. Hvis kravene er for vage, kan systemet ikke testes korrekt.    
- **Bliver påvirket af implementering og test:** Hvis udviklere eller testere opdager, at et krav er upraktisk eller urealistisk, kan kravene blive ændret eller præciseret.

**Eksempel:**  
Hvis brugerne under test opdager, at en funktion ikke løser deres behov, må kravene justeres, og design/kode tilpasses.

## High Level Design (HLD)

High level design oversætter kravene til **systemets overordnede arkitektur**.

- **Påvirker low level design og programmering:** En god arkitektur gør det lettere at lave detaljerede moduler og ren kode.    
- **Bliver påvirket af krav:** Ændrede krav kan kræve ændringer i arkitekturen (fx nye integrationer eller teknologier).    

**Eksempel:**  
Hvis man senere skal kunne håndtere tusindvis af brugere i stedet for hundrede, må arkitekturen justeres (fx fra lokal database til cloud-løsning).

## Low Level Design (LLD)

Low level design beskriver **hvordan hver del konkret skal bygges**.

- **Påvirker programmering:** Detaljeret design gør kodningen hurtigere og mere ensartet.    
- **Bliver påvirket af high level design:** Hvis arkitekturen ændres, skal de tekniske detaljer justeres. 
- **Påvirker test:** Testdesign afhænger af, hvordan komponenter og interfaces er opbygget.

**Eksempel:**  
Hvis du ændrer et klassedesign, kan det påvirke både den kode, der skal skrives, og de testcases, der skal laves.

## Programmering

Programmering er **realiseringen** af designet.

- **Påvirker test:** Kvaliteten af koden afgør, hvor mange fejl testerne finder.    
- **Påvirker udrulning:** Stabil kode gør udrulningen mere problemfri.    
- **Bliver påvirket af design og krav:** Koden skal følge designet og opfylde kravene.    

**Eksempel:**  
Hvis udviklerne ikke følger designet, kan testene fejle, og systemet vil ikke leve op til kravene.

## Test

Test er **feedbackmekanismen** for hele udviklingsforløbet.
- **Påvirker programmering:** Testresultater fører ofte til fejlrettelser og forbedringer i koden.    
- **Påvirker krav og design:** Test kan afsløre, at krav eller design var ufuldstændige.    
- **Bliver påvirket af krav:** Testplanen laves ud fra, hvad systemet _skal_ kunne.    

**Eksempel:**  
En fejl i en test kan vise, at et krav er misforstået — så både design og kode skal ændres.

## Udrulning

Udrulning markerer overgangen fra udvikling til drift.

- **Påvirker projektstyring:** Projektlederen skal planlægge og koordinere udrulningen.    
- **Bliver påvirket af test:** Kun systemer, der består test, kan udrulles.    
- **Påvirker kravindsamling (på længere sigt):** Når brugerne tager systemet i brug, kommer ny feedback, som bliver nye krav i næste version.


**Eksempel:**  
Efter udrulning opdager brugerne et behov for nye funktioner – det bliver starten på en ny kravfase (og dermed en ny iteration).

## Sammenhæng – oversigt

|Område|Påvirker|Bliver påvirket af|
|---|---|---|
|Projektstyring|Alle andre områder|Ændringer og forsinkelser i de øvrige|
|Kravsindsamling|Design, test|Feedback fra test og brugere|
|High Level Design|LLD, programmering|Krav|
|Low Level Design|Programmering, test|High level design|
|Programmering|Test, udrulning|Design og krav|
|Test|Programmering, krav|Kode, krav|
|Udrulning|Projektstyring, fremtidige krav|Test og kode|

