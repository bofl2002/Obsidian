[[Systemudvikling Dokumentation]]


En **domænemodel** er en **visuel repræsentation af de vigtigste begreber, objekter og relationer** i det **problemområde (domæne)**, som systemet skal understøtte.

  Domænemodellen beskriver **"virkeligheden" bag systemet** – altså hvad systemet handler om – **før man tænker på teknik og programmering**.

En domænemodel viser typisk:

- **Begreber** og **entiteter** i domænet (fx Kunde, Bestilling, Produkt).
    
- **Relationer** mellem begreberne (fx En Kunde laver en Bestilling).
    
- **Attributter** (fx en Kunde har navn, e-mail).
    
- **Ingen metoder** – det handler kun om struktur og betydning, ikke om funktionalitet.
    

Fokus er på **forretningsforståelse** – ikke kode.


## Domænemodel i rapport eller præsentation

Du kan fx skrive:

**Domænemodel:**  
Vi har udarbejdet en domænemodel for at skabe overblik over de vigtigste begreber og relationer i systemets anvendelsesområde.  
I vores model indgår begreber som `Bruger`, `Bestilling`, `Produkt` og `Betaling`, som afspejler forretningslogikken i en webshop.  
Modellen danner grundlag for vores videre design af systemet og hjælper med at sikre, at vi forstår domænet korrekt.

![[Pasted image 20251014121012.png]]## rug i praksis (skoleprojekt-eksempel)

> I et projekt om en madbestillings-app lavede vi en domænemodel, hvor:
> 
> - `Kunde` kan afgive en `Bestilling`.
>     
> - `Bestilling` indeholder flere `Menuvarer`.
>     
> - `Menuvare` har en `Pris` og hører til en `Kategori` (fx "Pizza" eller "Drikkevarer").

 Modellen hjalp os med at forstå, hvilke data vi skulle arbejde med, og hvordan de hang sammen.