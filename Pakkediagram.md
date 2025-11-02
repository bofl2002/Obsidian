[[Systemudvikling Dokumentation]]


Et **pakkediagram** er en type UML-diagram, der viser **struktur og organisering af et større system** ved at opdele det i **pakker/moduler**. Hver **pakke** kan repræsentere en samling af klasser, interfaces eller andre elementer, som hører logisk sammen.

Formålet er at få **overblik** over systemets arkitektur og afhængigheder mellem forskellige dele af systemet.

---

##### Hvad er en “pakke”?

- En **pakke** er en **logisk gruppering af elementer**, fx klasser, use cases eller underpakker.
    
- Forestil dig det som en **mappe** i et filsystem eller en **namespace** i programmering.
    

**Eksempler på pakker:**

- `Brugeradministration`
    
- `Ordresystem`
    
- `Betalingsmodul`
    
- `GUI`
    
- `Databaseadgang`
    

---

##### Hvad viser et pakkediagram?

- **Pakkerne** i systemet
    
- **Afhængigheder** mellem pakker (hvem bruger hvad)
    
- **Hierarkier og organisering** (pakker inde i pakker)
    

---

##### Symboler og notation

|Element|Forklaring|
|---|---|
|📦 **Pakke**|En firkantet boks med en fane i øverste hjørne. Indeholder klasser eller andre pakker.|
|🔁 **Afhængighed**|En stiplet pil, som viser at én pakke er afhængig af en anden.|

**Eksempel:**  
Hvis `GUI` er afhængig af `Brugeradministration`, tegnes en stiplet pil fra `GUI` → `Brugeradministration`.

---

##### Eksempel på et pakkediagram

Forestil dig et online butikssystem. Pakkediagrammet kan se sådan ud:

```
+-------------------+       +------------------------+
|   Brugerinterface |<----->| Brugeradministration  |
+-------------------+       +------------------------+
                                   |
                                   v
                         +------------------+
                         |   Databaselag    |
                         +------------------+
```

Her kan du se:

- `Brugerinterface` er afhængig af `Brugeradministration`
    
- `Brugeradministration` er afhængig af `Databaselag`
    

---

##### Hvorfor bruge pakkediagrammer?

- For at **strukturere og organisere** systemet tidligt i udviklingen.
    
- For at **afgrænse ansvar** og gøre systemet mere **modulært** og vedligeholdbart.
    
- For at se, hvor der er **tætte koblinger** mellem dele af systemet.
    

---

##### Opsummering

|Punkt|Forklaring|
|---|---|
|Formål|Vise systemets struktur og afhængigheder|
|Fokusområde|Organisation i pakker/moduler|
|Bruges til|Arkitektur, design og overblik|
|Diagramtype|UML (Unified Modeling Language)|
