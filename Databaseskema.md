[[Systemudvikling Dokumentation]]

Database skemaet bruges til at definere tabeller i database med Primary Key, Foreign Keys osv..

Et **database skema** er en **strukturplan** over en database. Det beskriver:

- **Hvilke tabeller** databasen indeholder
    
- **Hvilke felter/attributter** hver tabel har
    
- **Datatyper** for hvert felt (f.eks. tekst, tal, dato)
    
- **Relationer** mellem tabeller (f.eks. fremmednøgler / foreign keys)
    

Man kan sige, det er databasedelens "arkitekttegning".

---

##### Hvad indeholder et typisk relationsskema?

Her er de vigtigste elementer i et relationsskema:

|Element|Forklaring|
|---|---|
|**Tabelnavn**|Navnet på en tabel i databasen (fx `Kunde`)|
|**Primærnøgle (PK)**|Et felt, der entydigt identificerer en række i tabellen (fx `KundeID`)|
|**Attributter**|Felterne i tabellen (fx `Navn`, `Adresse`, `Telefon`)|
|**Fremmednøgle (FK)**|En reference til en primærnøgle i en anden tabel (for at forbinde tabeller)|

---

##### Eksempel på database skema

Forestil dig et system til en webshop:

###### Tabel: **Kunde**

|Feltnavn|Datatype|Noter|
|---|---|---|
|KundeID|INT (PK)|Primærnøgle|
|Navn|VARCHAR||
|Email|VARCHAR||

---

###### Tabel: **Ordre**

|Feltnavn|Datatype|Noter|
|---|---|---|
|OrdreID|INT (PK)||
|KundeID|INT (FK)|Fremmednøgle → Kunde|
|OrdreDato|DATE||

---

###### Tabel: **Produkt**

|Feltnavn|Datatype|Noter|
|---|---|---|
|ProduktID|INT (PK)||
|Navn|VARCHAR||
|Pris|DECIMAL||

---

###### Tabel: **OrdreLinje**

|Feltnavn|Datatype|Noter|
|---|---|---|
|OrdreID|INT (FK)|Fremmednøgle → Ordre|
|ProduktID|INT (FK)|Fremmednøgle → Produkt|
|Antal|INT|Hvor mange af produktet|

> **NB:** Her er der en **mange-til-mange** relation mellem Ordrer og Produkter, løst via en mellemtabel: **OrdreLinje**.

---

###### Hvorfor er et database skema vigtigt?

- Det hjælper med at **strukturere data korrekt og effektivt**
    
- Det danner grundlag for selve opbygningen af databasen (SQL)
    
- Det gør det lettere at forstå, hvordan data hænger sammen
    
- Det er afgørende for at kunne lave forespørgsler, integration og vedligeholdelse
    
