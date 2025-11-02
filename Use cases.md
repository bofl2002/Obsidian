[[Systemudvikling Dokumentation]]

En **use case** beskriver en **funktion eller handling**, som et system skal kunne udføre, set fra en brugers (aktørs) perspektiv.

Den fortæller, **hvilket mål brugeren ønsker at opnå**, og hvordan systemet hjælper med at nå det.

---

##### Hvad indeholder en use case?

Typisk indeholder en use case:

- **Navn**: Kort og præcist, fx "Opret bruger".
    
- **Aktør**: Den person eller system, der interagerer med systemet (fx kunde, administrator).
    
- **Formål**: Hvad aktøren ønsker at opnå.
    
- **Beskrivelse/Flow**: Trinvis beskrivelse af, hvordan aktøren og systemet interagerer.
    
- **Forudsætninger**: Hvilke betingelser der skal være opfyldt før use casen kan udføres.
    
- **Resultat**: Hvad er sluttilstanden, når use casen er fuldført.
    
- **Alternative flows**: Eventuelle variationer eller fejlscenarier.
    

---

##### Eksempel på en use case: "Bestil vare"

|Felt|Indhold|
|---|---|
|**Navn**|Bestil vare|
|**Aktør**|Kunde|
|**Formål**|Kunden ønsker at bestille en vare|
|**Forudsætninger**|Kunden er logget ind|
|**Hovedflow**|1. Kunden vælger vare2. Kunden tilføjer vare til kurv3. Kunden betaler4. System bekræfter bestilling|
|**Resultat**|Varen er bestilt og betalingen er modtaget|
|**Alternative flows**|Hvis betalingsoplysninger er ugyldige, afvises betalingen|

---

##### Hvorfor bruger man use cases?

- For at forstå **kravene fra brugerens perspektiv**.
    
- Sikrer, at udviklingsteamet og interessenter har en fælles forståelse.
    
- Grundlag for design, test og dokumentation.
    
- Hjælper med at identificere funktioner i systemet.
    

---

##### Use cases i rapport eller opgave

Du kan skrive:

> **Use case: Opret bruger**  
> Denne use case beskriver, hvordan en ny bruger kan oprettes i systemet.  
> Aktøren er en potentiel bruger, som indtaster sine oplysninger og får oprettet en konto.  
> Use casen dækker både normale forløb og fejlscenarier, som fx manglende obligatoriske oplysninger.

---

##### Kort opsummering

|**Use Case**|**Beskrivelse**|
|---|---|
|Formål|At beskrive brugerens mål med systemet|
|Aktør|Den person/system, der bruger systemet|
|Flow|Trinvis beskrivelse af interaktionen|
|Anvendelse|Analyse, design, test, kommunikation|

##### De tre variationer af use cases

##### 1. **Brief Use Case**

- En superkort opsummering.
    
- Bare et par sætninger, der fortæller, hvad use casen handler om.
    
- God til hurtigt overblik.
    

**Eksempel:**  
_“Brugeren logger ind på systemet.”_

---

##### 2. **Casual Use Case**

- En lidt mere udførlig beskrivelse.
    
- En kort tekst, der forklarer hovedtrinnene, uden for mange detaljer.
    
- Let at læse for både teknikere og ikke-teknikere.
    

**Eksempel:**  
_“Brugeren indtaster brugernavn og kodeord, og systemet bekræfter, om login er korrekt.”_

---

##### 3. **Fully Dressed Use Case**

- Den mest detaljerede version.
    
- Inkluderer alt: navn, aktører, forudsætninger, hovedflow, alternative flows, og resultat.
    
- Bruges til grundig dokumentation og testgrundlag.
    

**Eksempel:**

|Felt|Indhold|
|---|---|
|**Navn**|Log ind|
|**Aktør**|Bruger|
|**Forudsætninger**|Bruger er registreret|
|**Hovedflow**|1. Bruger åbner login-side2. Indtaster brugernavn og kodeord3. System validerer og logger ind|
|**Alternative flows**|3a. Forkert kodeord → system viser fejlbesked|
|**Resultat**|Bruger er logget ind og kan bruge systemet|

##### Use Case test: BOSS Test, Elementary Business Process (EBP) og Size Test 

##### 1. BOSS Test (Business Operation Support System Test)

- **Definition:**  
    En **BOSS test** fokuserer på at teste en **hel forretningsproces** (use case) i sin fulde længde, som brugeren forventer at udføre den. Den tester systemets evne til at understøtte en komplet operationel arbejdsgang.
    
- **Formål:**  
    At sikre, at hele den primære forretningsproces (happy path) fungerer korrekt uden fejl. Det er en slags end-to-end test, der simulerer brugers interaktion med systemet.
    
- **Karakteristika:**
    
    - Tester hele sekvensen af trin, som brugeren følger.
        
    - Inkluderer interaktion mellem systemkomponenter og eventuelle eksterne systemer.
        
    - Sikrer at forretningens kerneoperationer understøttes.
        
- **Eksempel:**  
    En kunde gennemfører en fuld ordreproces i et ERP-system — fra oprettelse af ordre, lagercheck, betaling til ordrebekræftelse.
    

---

##### 2. Elementary Business Process (EBP)

- **Definition:**  
    En **Elementary Business Process** er den **mindste forretningsproces** med en selvstændig og meningsfuld forretningsværdi. Det er en afgrænset og sammenhængende operation, som udføres af systemet eller forretningen.
    
- **Formål:**  
    At nedbryde komplekse use cases i mindre, håndterbare enheder, som hver især kan udvikles og testes separat.
    
- **Karakteristika:**
    
    - Kan ikke opdeles yderligere uden at miste sin forretningsmæssige mening.
        
    - Hver EBP leverer en konkret værdi til en aktør (fx bruger eller kunde).
        
    - Gør det lettere at forstå, udvikle og teste forretningsprocesser.
        
- **Eksempel:**  
    I en ordreproces kan EBPer være: "Opret kundeprofil", "Indtast ordre", "Betal ordre", "Send kvittering".
    

---

##### 3. Size Test

- **Definition:**  
    En **Size test** undersøger, hvordan systemet håndterer forskellige størrelser af input, datamængder eller belastning. Det er en del af performance- og robusthedstestning.
    
- **Formål:**  
    At sikre, at systemet kan klare den forventede arbejdsbyrde og store datamængder uden fejl eller performanceproblemer.
    
- **Karakteristika:**
    
    - Test af små vs. store mængder data.
        
    - Kan inkludere stress- og belastningstest.
        
    - Hjælper med at finde systemets kapacitetsgrænser.
        
- **Eksempel:**  
    Test hvor man behandler en enkelt ordre versus tusindvis af samtidige ordrer for at måle svartid og stabilitet.
    

---

# Opsummeringstabel

|Test/Koncept|Beskrivelse|Formål|Eksempel|
|---|---|---|---|
|**BOSS Test**|Test af hele forretningsprocessen (use case) i normal flow|Sikre at hele processen fungerer korrekt|Fuldført ordreproces fra start til slut|
|**Elementary Business Process (EBP)**|Mindste forretningsproces med selvstændig værdi|Nedbryde og teste delprocesser separat|"Betal ordre" som en del af ordreprocessen|
|**Size Test**|Test af systemets håndtering af forskellige datamængder og belastning|Sikre systemets performance og stabilitet|1 ordre vs. 10.000 samtidige ordrer|
