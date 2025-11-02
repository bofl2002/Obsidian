[[Programmering]]

**HTML** står for **HyperText Markup Language**, og det er sproget, man bruger til at **strukturere indholdet** på en webside.

HTML beskriver, hvad der er **på siden** – fx tekst, billeder, overskrifter, links, lister osv.  
Det fortæller **browseren**, hvordan indholdet skal vises, men ikke hvordan det skal **se ud** – det klarer **CSS**.

---

##### Eksempel på et simpelt HTML-dokument

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Min første side</title>
  </head>
  <body>
    <h1>Hej verden!</h1>
    <p>Dette er min første webside.</p>
    <a href="https://example.com">Klik her</a>
  </body>
</html>
```

---

##### Grundlæggende HTML-elementer

|Element|Hvad det gør|Eksempel|
|---|---|---|
|`<h1>` til `<h6>`|Overskrifter (h1 = største)|`<h1>Titel</h1>`|
|`<p>`|Afsnit (paragraph)|`<p>Dette er tekst</p>`|
|`<a>`|Link|`<a href="https://...">Link</a>`|
|`<img>`|Billede|`<img src="billede.jpg">`|
|`<ul>`, `<li>`|Uordnet liste|`<ul><li>Én</li></ul>`|
|`<table>`|Tabel|`<table><tr><td>Data</td></tr></table>`|
|`<div>`|"Box" til layout|`<div>Indhold</div>`|
|`<input>`|Formularfelt|`<input type="text">`|

---

##### HTML-struktur (anatomien af et dokument)

- `<!DOCTYPE html>`: Fortæller browseren, at det er HTML5
    
- `<html>`: Rødderne på hele HTML-siden
    
- `<head>`: Info om siden (metadata, titel, links til CSS osv.)
    
- `<body>`: Alt det brugeren ser (tekst, billeder, knapper osv.)
    

---

##### HTML-attributter

HTML-elementer kan have **attributter**, som giver ekstra information:

```html
<img src="kat.jpg" alt="En sød kat" width="200">
```

Her er `src`, `alt` og `width` attributter til `<img>`-elementet.

---

##### HTML er ikke et programmeringssprog

HTML er et **markup-sprog** – det **beskriver indhold**, men kan **ikke udføre logik** som beregninger, betingelser eller funktioner.  
Til det bruges JavaScript.

---

##### Opsummering

|Punkt|Beskrivelse|
|---|---|
|Hvad er HTML?|Markup-sprog til strukturering af webindhold|
|Bruges til|At definere tekst, links, billeder, lister mm.|
|Hvor kører det?|I browseren (client-side)|
|Samarbejder med|CSS (design) og JavaScript (interaktion)|

---

###### Vil du lære mere?

- Formularer og inputfelter (`<form>`, `<input>`, `<select>`)
    
- Semantiske tags (`<header>`, `<main>`, `<footer>`)
    
- HTML5 features (video, lyd, canvas)
    
- Tilgængelighed og god HTML-struktur
    
