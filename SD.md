[[Systemudvikling Dokumentation]]


Et sekvensdiagram er en **UML-diagramtype**, der viser **interaktionen mellem forskellige objekter eller komponenter over tid** i forbindelse med en bestemt proces eller funktion.

Det beskriver **hvordan objekter kommunikerer ved at sende beskeder til hinanden i en bestemt rækkefølge**.

---

##### Hvad indeholder et sekvensdiagram?

- **Objekter/aktører**: De deltagende elementer (f.eks. systemkomponenter, brugere), vist som bokse øverst.
    
- **Livslinje**: En stiplet lodret linje under hvert objekt, der viser objektets liv over tid.
    
- **Beskeder**: Pile mellem objekterne, der viser kommunikation (kald, svar, signaler).
    
- **Tidsforløb**: Går fra toppen og nedad – sekvensen af beskeder vises i kronologisk rækkefølge.
    

---

##### Eksempel på et simpelt sekvensdiagram: Købsproces

```
Kunde          Webshop         Betalingssystem
 |               |                  |
 |---vælgProdukt->|                  |
 |               |---bekræftOrdre-> |
 |               |                  |---godkendBetaling->|
 |               |                  |<--bekræftelse-------|
 |<--kvittering---|                  |
```

Forklaring:

- Kunden vælger et produkt.
    
- Webshoppen bekræfter ordren og sender betalingsoplysninger til betalingssystemet.
    
- Betalingssystemet godkender betalingen og sender bekræftelse.
    
- Webshoppen sender kvittering tilbage til kunden.
    

---

##### Hvornår bruges sekvensdiagrammer?

- Til at visualisere **interaktionen i en bestemt use case eller funktion**.
    
- Når man vil beskrive, **hvordan objekter eller komponenter samarbejder**.
    
- Under analyse og design for at specificere systemadfærd.
    

---

##### Sekvensdiagram i en rapport eller opgave

Du kan fx skrive:

> **Sekvensdiagram:**  
> Diagrammet viser, hvordan aktører og objekter interagerer i en ordreproces.  
> Kunden sender en ordre, webshoppen håndterer den, og betalingssystemet godkender betalingen.  
> Sekvensen af beskeder viser systemets dynamiske adfærd.

---

##### Fordele ved sekvensdiagrammer

- Giver klar indsigt i **dynamikken i systemet**.
    
- Hjælper med at finde **mulige fejl eller mangler** i processen.
    
- Brugbar til både teknikere og ikke-tekniske interessenter.
    
- Kan let omsættes til implementering.
    
