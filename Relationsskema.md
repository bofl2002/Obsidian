[[Systemudvikling Dokumentation]]

Et **relationsskema** er en **formel beskrivelse af en relation (tabel) i en relationsdatabase**. Det viser, hvordan data er organiseret i tabeller, og hvilke kolonner (attributter) der indgår.

Relationsskemaet bruges til at beskrive tabellernes struktur, deres kolonner, primærnøgler og eventuelle fremmednøgler.

---

##### Hvad indeholder et relationsskema?

For hver tabel i databasen beskriver relationsskemaet:

- **Navnet på tabellen** (relationen)
    
- **Attributter (kolonner)** i tabellen
    
- **Primærnøgle (PK)** — den eller de attributter, som entydigt identificerer en række
    
- **Fremmednøgle (FK)** — attributter, som refererer til primærnøgler i andre tabeller (for at lave relationer mellem tabeller)
    

---

##### Eksempel: Relationsskema for et bibliotekssystem

|Tabel: LÅNER (Låner)|
|---|
|LånerID (PK)|
|Navn|
|Email|

|Tabel: BOG|
|---|
|BogID (PK)|
|Titel|
|Forfatter|

|Tabel: LÅN|
|---|
|LånID (PK)|
|LånerID (FK)|
|BogID (FK)|
|Lånedato|
|ReturneretDato|

Forklaring:

- `LÅNER` har primærnøglen `LånerID`.
    
- `LÅN` forbinder `LÅNER` og `BOG` via fremmednøgler `LånerID` og `BogID`.
    

---

##### Hvordan skriver man et relationsskema?

Typisk skrives det sådan:

```
LÅNER(LånerID, Navn, Email)
BOG(BogID, Titel, Forfatter)
LÅN(LånID, LånerID, BogID, Lånedato, ReturneretDato)
```

Og man angiver nøgler, fx:

```
LÅNER(LånerID [PK], Navn, Email)
LÅN(LånID [PK], LånerID [FK], BogID [FK], Lånedato, ReturneretDato)
```

---

##### Hvorfor er relationsskema vigtigt?

- Det **formaliserer databasens struktur**.
    
- Hjælper med at designe databasen korrekt med klare relationer.
    
- Understøtter implementering i et databasesystem (SQL).
    
- Gør det lettere at forstå, hvordan data hænger sammen.
    

---

##### Brug i skoleprojekt eller rapport

Du kan skrive:

> **Relationsskema:**  
> Vi har designet følgende relationsskema for databasen:  
> `LÅNER(LånerID [PK], Navn, Email)`  
> `BOG(BogID [PK], Titel, Forfatter)`  
> `LÅN(LånID [PK], LånerID [FK], BogID [FK], Lånedato, ReturneretDato)`  
> Dette sikrer, at hver låner og bog kan knyttes til specifikke lån, og relationerne understøtter databasedrift.
