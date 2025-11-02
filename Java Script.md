[[Programmering]]


**JavaScript (JS)** er et **programmeringssprog**, som bruges til at gøre **hjemmesider interaktive**.

Sammen med **HTML** og **CSS** udgør JavaScript de tre grundpiller i webudvikling:

|Teknologi|Hvad gør det?|
|---|---|
|**HTML**|Strukturen (fx overskrifter, knapper, lister)|
|**CSS**|Udseendet (farver, layout, animation)|
|**JavaScript**|Funktionalitet og interaktion (fx klik, beregninger, dynamisk indhold)|

---

##### Hvad bruges JavaScript til?

- Håndtere klik og brugerinput
    
- Indlæse og opdatere data uden at genindlæse siden (AJAX)
    
- Lave dynamiske elementer (f.eks. datoer, nedtælling, sliders)
    
- Validere formularer før de sendes
    
- Bygge komplette apps (fx med React, Vue eller Angular)
    

---

##### Simpelt eksempel på JavaScript

###### HTML + JavaScript:

```html
<button onclick="sigHej()">Klik mig</button>

<script>
  function sigHej() {
    alert("Hej med dig!");
  }
</script>
```

Når du klikker på knappen, popper en besked op.  
Dette er et eksempel på **interaktivitet** via JavaScript.

---

##### Grundlæggende JavaScript-syntaks

|Koncept|Eksempel|Forklaring|
|---|---|---|
|Variabler|`let navn = "Sara";`|Gemmer data|
|Funktioner|`function hils() { ... }`|Gruppe af kode, der kan genbruges|
|Betingelser|`if (x > 10) { ... }`|Kører kode, hvis betingelse er opfyldt|
|Løkker|`for (let i = 0; i < 5; i++)`|Gentager kode|
|DOM-manipulation|`document.getElementById(...)`|Ændrer indholdet på websiden|

---

##### DOM – Document Object Model

JavaScript kan **læse og ændre HTML- og CSS-indhold** på en side via DOM.

Eksempel:

```javascript
document.getElementById("overskrift").innerText = "Ny tekst!";
```

---

##### JavaScript er **client-side**

Det betyder, at JavaScript **kører i brugerens browser** (modsat fx PHP, der kører på serveren).  
Det gør det hurtigt, men også afhængigt af brugerens computer og browser.

---

##### Eksempel: Interaktiv tæller

```html
<p id="tæller">0</p>
<button onclick="plusEn()">+1</button>

<script>
  let værdi = 0;

  function plusEn() {
    værdi++;
    document.getElementById("tæller").innerText = værdi;
  }
</script>
```

---

##### Opsummering

|Punkt|Forklaring|
|---|---|
|Hvad er det?|Et programmeringssprog til websider|
|Hvad gør det?|Gør hjemmesider interaktive og dynamiske|
|Hvor kører det?|I brugerens browser (client-side)|
|Eksempler|Klik-events, popups, datohåndtering, API-kald|

---

##### Videre emner du kan udforske

- Events (`click`, `submit`, `mouseover`...)
    
- Arrays og objekter
    
- Asynkron programmering (`async/await`, `fetch`)
    
- JavaScript frameworks: **React**, **Vue**, **Angular**
    
- JavaScript + API’er (REST, JSON)
    
