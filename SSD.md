[[Systemudvikling Dokumentation]]


Et **System Sekvens Diagram** (på engelsk _System Sequence Diagram_, SSD) viser **hvordan systemet interagerer med aktører (brugere eller eksterne systemer)** i forbindelse med én bestemt **funktion eller use case**.

SSD'et viser **hvordan systemet reagerer på input fra aktøren**, og **hvilke systemoperationer** der bliver kaldt – **set udefra**.

Det bruges især i analysefasen til at:

- Analysere og forstå **interaktion mellem bruger og system**.
    
- Beskrive **rækkefølgen af hændelser** (sekvens).
    
- Forberede operationskontrakter og design.
    

---

Hvad indeholder et System Sekvens Diagram?

Et SSD fokuserer **kun på aktøren og systemet som én “sort boks”**. Det indeholder:

|Element|Forklaring|
|---|---|
|**Aktør**|En bruger eller et andet system, der interagerer med systemet|
|**System**|Selve systemet (vises som én kasse – intern logik vises ikke)|
|**Beskeder**|Hvad aktøren sender til systemet (f.eks. input eller handlinger)|
|**Svar** _(valgfrit)_|Hvad systemet returnerer (f.eks. kvittering, data)|
|**Sekvens**|Rækkefølgen af beskeder og svar – vises med pile|

---

Eksempel: SSD for "Gennemfør køb" i en webshop

```
Aktør: Kunde                   System: Webshop
   |                                |
   |------> vælgVare(vareID, antal) |
   |                                |
   |------> opretBetaling(kortinfo)|
   |                                |
   |<----- kvittering               |
```

Forklaring:

- Kunden vælger en vare og sender info til systemet.
    
- Kunden opretter en betaling.
    
- Systemet sender en kvittering tilbage.
    

---

##### Sådan bruges SSD i en rapport eller opgave

Du kan fx skrive:

> **System Sekvens Diagram – "opret bestilling"**  
> Diagrammet viser interaktionen mellem brugeren og systemet i forbindelse med oprettelse af en bestilling.  
> Brugeren vælger varer, sender bestillingen og modtager bekræftelse.  
> Diagrammet hjælper med at forstå systemets forventede opførsel og er grundlag for operationskontrakter.

---

##### Eksempel på tekst til rapporten

> Vi har udarbejdet et System Sekvens Diagram for use casen **”Gennemfør køb”**.  
> Aktøren (kunden) sender tre beskeder til systemet:  
> `vælgVare(vareID, antal)`, `opretBetaling(kortoplysninger)` og `bekræftOrdre()`.  
> Systemet returnerer en kvittering.  
> Diagrammet viser sekvensen af interaktioner og danner grundlag for design og test.



Fordele ved SSD

- Giver **hurtigt overblik** over aktør-system-interaktion.
    
- Understøtter kravspecifikation og design.
    
- Brugbar til at **identificere systemoperationer** og udvikle operationskontrakter.
    
- Simpel og nem at forstå – også for ikke-tekniske interessenter.
    

---

Brug i skole- eller eksamensprojekt

SSD'er er især nyttige i rapporter, hvor du skal dokumentere:

- Hvordan systemet **skal reagere på brugerinput**.
    
- Hvilke **systemoperationer der skal implementeres**.
    
- Hvilke **data** der bliver sendt frem og tilbage.
    
