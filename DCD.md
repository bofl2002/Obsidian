[[Systemudvikling Dokumentation]]


Et **Design Class Diagram (DCD)** er en type **UML-diagram**, der viser de **klasser**, der skal implementeres i softwaren, og hvordan de hænger sammen. Det bruges til at **designe den indre struktur** af et objektorienteret system, ofte baseret på krav og use cases.

Det er en videreudvikling af **domæneklasser** (fra domænemodellen), men nu med **mere tekniske detaljer** såsom typer, metoder og relationer, der kan implementeres direkte i kode.

---

##### Hvad indeholder et DCD?

Hver **klasse** i diagrammet viser typisk:

###### 1. **Navn på klassen**

- Skrivs i toppen af boksen (fx `Ordre`, `Bruger`, `Produkt`)
    

###### 2. **Attributter (felter/variabler)**

- Viser, hvilke data klassen indeholder
    
- Inkluderer navn og datatype (fx `navn: String`, `pris: double`)
    
- Kan have synlighed:
    
    - `+` (public)
        
    - `-` (private)
        
    - `#` (protected)
        

###### 3. **Metoder (operationer/funktioner)**

- Viser, hvad klassen kan gøre (funktionalitet)
    
- Inkluderer navne, parametre og returtype (fx `beregnPris(): double`)
    
- Synlighed angives ligesom attributter
    

---

###### 🔹 Eksempel på en klasse

```
---------------------
|     Produkt        |
---------------------
| - navn: String     |
| - pris: double     |
---------------------
| + getPris(): double|
| + setPris(p: double): void |
---------------------
```

---

###### 🔹 Relationer mellem klasser

DCD’er viser også **forholdet mellem klasser**, fx:

|Forhold|Symbol/notation|Forklaring|
|---|---|---|
|**Association**|Linje|En klasse "bruger" en anden|
|**Aggregation**|Hvid diamant|En "del af" relation, hvor delene kan eksistere selv|
|**Kompodition**|Sort diamant|En stærkere "del af"-relation (del = ejet af helhed)|
|**Arv (Generalisering)**|Pil med trekant|En klasse nedarver fra en overklasse|
|**Afhængighed**|Stiplet pil|Midlertidig brug, fx i en metode|

---

##### Eksempel: Webshop

###### Klasser:

- **Kunde**
    
- **Ordre**
    
- **Produkt**
    
- **OrdreLinje**
    

###### Relationer:

- En kunde **har** flere ordrer (1:m)
    
- En ordre **har** flere ordrelinjer (1:m)
    
- En ordrelinje **refererer** til ét produkt (m:1)
    

---

###### Forskellen på DCD og Domænemodel

|Domænemodel|Design Class Diagram|
|---|---|
|Fokus på begreber og forretning|Fokus på implementerbare klasser|
|Ingen datatyper/metoder|Har datatyper og metoder|
|Bruges til at forstå problemet|Bruges til at designe løsningen|

---

##### Hvornår bruges et DCD?

- I **designfasen** af udviklingsprocessen
    
- Når man skal **forberede programmering**
    
- Når man ønsker at **analysere og optimere struktur**
    
- Som **dokumentation** af systemets arkitektur
    

---

###### Ekstra tip

Når du laver DCD:

- Start med **domænemodellen**, og tilføj detaljer.
    
- Tænk i **ansvar** (hvem gør hvad?).
    
- Brug **navngivning og synlighed** korrekt.
    
- Tegn **relationer tydeligt** og hold diagrammet overskueligt.
    
