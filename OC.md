[[Systemudvikling Dokumentation]]


En **operationskontrakt** (eller **operation contract**) er en **beskrivelse af, hvad en bestemt operation (funktion/metode) gør** i et system, **hvilke betingelser der gælder før og efter**, og **hvordan systemets tilstand ændres**.

Den bruges typisk i **objektorienteret analyse og design**, til at beskrive **interaktionen med objekter og deres tilstand** – uden at gå i detaljer med kode.

---

##### Hvad indeholder en operationskontrakt?

En operationskontrakt beskriver normalt følgende:

|Element|Forklaring|
|---|---|
|**Navn**|Navnet på operationen (f.eks. `opretBruger`)|
|**Beskrivelse**|Kort tekst om, hvad operationen gør|
|**Parametre**|Hvilke input data operationen får (f.eks. navn, e-mail)|
|**Forudsætninger (preconditions)**|Hvad skal være opfyldt, før operationen kan udføres?|
|**Eftertilstand (postconditions)**|Hvad skal gælde, **efter** operationen er udført? (hvilke objekter oprettes, ændres osv.)|
|_(Evt. Undtagelser)_|Hvad sker der, hvis noget går galt? (valgfrit)|

---

##### Eksempel på en operationskontrakt

**Operation:** `opretBruger`

|Felt|Indhold|
|---|---|
|**Beskrivelse**|Opretter en ny bruger i systemet.|
|**Parametre**|navn: String, email: String, adgangskode: String|
|**Forudsætninger**|Der må ikke allerede findes en bruger med samme email.|
|**Eftertilstand**|En ny instans af `Bruger` er oprettet med de angivne data. Brugeren er tilføjet til brugerliste.|

---

##### Hvad bruges operationskontrakter til?

- **Analyserer og beskriver systemets funktioner præcist.**
    
- Hjælper med at forstå **hvad der sker "bag kulissen"** ved en operation.
    
- Skaber klar kommunikation mellem **analytikere, designere og udviklere**.
    
- Understøtter **objektorienteret design** og **use cases**.
    

---

##### Hvor i processen bruges de?

- I **analysefasen**: Til at beskrive adfærd for systemfunktioner ud fra krav og use cases.
    
- I **designfasen**: Som grundlag for metodeimplementering i klasser/objekter.
    

---

##### Eksempel på brug i en rapport

> **Operationskontrakt – `tilføjVareTilKurv()`**  
> Denne operation tilføjer en valgt vare til en brugers indkøbskurv.  
> **Parametre:** vareID: int, antal: int  
> **Precondition:** Brugeren har en aktiv kurv. Varen findes på lager.  
> **Postcondition:** Varen er tilføjet til brugerens kurv med angivet antal. Lagerbeholdningen reduceres tilsvarende.

---

##### Fordele ved operationskontrakter

- Tydeliggør systemets **forretningslogik**.
    
- Hjælper med at undgå **misforståelser** i implementeringen.
    
- Fungerer som en slags **"kontrakt"** mellem hvad systemet **skal gøre** og **hvordan det gøres korrekt**.
    
- Giver et klart grundlag for **test** og **validering**.
    
