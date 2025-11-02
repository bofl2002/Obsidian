
[[Databaseskema]]


Normalisering er processen, hvor man **organiserer tabeller og relationer i en database** for at:

- Reducere **redundans** (gentagelse af data)
    
- Forbedre **dataintegritet**
    
- Gøre databasen lettere at **vedligeholde og udvide**
    

Man arbejder med **normalformer**, som er regler eller niveauer, man følger. Jo højere normalform, jo mere struktureret (og kompleks) bliver databasen.

---

##### De tre vigtigste normalformer

######  1. Normalform (1NF) – _"Én værdi per celle"_

**Krav:**

- Hver celle i tabellen skal kun indeholde én enkelt værdi (atomær).
    
- Ingen gentagne grupper eller lister i samme kolonne.
    

**Eksempel: Ikke 1NF:**

|KundeID|Navn|Telefonnummer|
|---|---|---|
|1|Mette|12345678, 87654321|

**✔️ Korrekt i 1NF:**

|KundeID|Navn|Telefonnummer|
|---|---|---|
|1|Mette|12345678|
|1|Mette|87654321|

---

###### 2. Normalform (2NF) – _"Fjern delvis afhængighed"_

**Krav:**

- Skal være i 1NF.
    
- Alle **ikke-nøglefelter** skal være fuldt afhængige af **hele primærnøglen** (gælder især når primærnøglen består af flere felter).
    

**Problem i 2NF:**

|OrdreID|ProduktID|ProduktNavn|Antal|
|---|---|---|---|
|101|1|Mus|2|
|101|2|Tastatur|1|

Her afhænger `ProduktNavn` kun af `ProduktID`, **ikke af hele nøglen (OrdreID, ProduktID)** → det skal ud i en separat tabel.

**Løsning:**

- Lav én tabel for ordrer (OrdreID + ProduktID + Antal)
    
- Én tabel for produkter (ProduktID + ProduktNavn)
    

---

###### 3. Normalform (3NF) – _"Fjern transitive afhængigheder"_

**Krav:**

- Skal være i 2NF.
    
- Ikke-nøglefelter må ikke afhænge af andre ikke-nøglefelter.
    

**Problem i 3NF:**

|KundeID|Navn|Postnummer|By|
|---|---|---|---|
|1|Jens|8000|Aarhus|
|2|Maria|2300|København S|

Her afhænger `By` af `Postnummer`, ikke direkte af `KundeID` → det er en **transitiv afhængighed**.

**Løsning:**

- Flyt `Postnummer` og `By` til en separat tabel.
    

---

##### Opsummering

|Normalform|Fokusområde|Hvad den løser|
|---|---|---|
|**1NF**|Atomære (uopdelte) værdier|Fjerner lister og gentagelser|
|**2NF**|Fuld funktionel afhængighed|Fjerner delvise afhængigheder|
|**3NF**|Transitive afhængigheder|Fjerner afhængigheder mellem ikke-nøgler|

---

###### Ekstra: Højere normalformer

Der findes også:

- **BCNF (Boyce-Codd Normal Form)** – en strengere version af 3NF
    
- **4NF** og **5NF** – sjældent brugt i praksis, men håndterer mere komplekse afhængigheder (fx multi-værdi og joint afhængigheder)
    
