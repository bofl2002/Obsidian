[[Programmering]]


**CSS (Cascading Style Sheets)** er et **stylesheet-sprog**, der bruges til at **styre udseendet og layoutet af HTML-elementer** på en webside.

Kort sagt: HTML strukturerer indholdet – **CSS bestemmer, hvordan det ser ud.**

---

##### Hvad kan CSS bruges til?

Med CSS kan du fx:

- Ændre **farver**, **fonte** og **tekststørrelser**
    
- Tilføje **margener**, **afstande**, **rammer** og **baggrunde**
    
- Lave **layouts** med grid, flexbox, positionering osv.
    
- Gøre siden **responsiv** (tilpasser sig forskellige skærmstørrelser)
    
- Tilføje **effekter** og **animationer**
    

---

##### Eksempel på HTML + CSS

###### HTML:

```html
<p class="intro">Velkommen til min hjemmeside!</p>
```

###### CSS:

```css
.intro {
  color: darkblue;
  font-size: 20px;
  margin: 20px;
}
```

Dette gør teksten mørkeblå, større og med afstand rundt om.

---

##### Hvordan tilføjes CSS?

Du kan tilføje CSS på tre måder:

|Metode|Eksempel|Bruges når...|
|---|---|---|
|**Inline**|`<p style="color: red;">Hej</p>`|Kun for hurtige tests|
|**Internal**|I `<style>` i `<head>`|Små sider eller demoer|
|**External**|I en `.css`-fil (fx `style.css`)|Store projekter – **mest almindelige**|

---

##### Eksempler på typiske CSS-egenskaber

|Egenskab|Beskrivelse|Eksempel|
|---|---|---|
|`color`|Tekstfarve|`color: red;`|
|`background`|Baggrundsfarve eller billede|`background: #eee;`|
|`font-size`|Størrelse på tekst|`font-size: 18px;`|
|`margin`|Afstand udenfor elementet|`margin: 10px;`|
|`padding`|Afstand inde i elementet|`padding: 15px;`|
|`border`|Kant omkring elementet|`border: 1px solid;`|
|`display`|Layout-opførsel (fx `block`, `flex`)|`display: flex;`|

---

##### Responsive design med CSS

Du kan gøre din side mobilvenlig med fx **media queries**:

```css
@media (max-width: 600px) {
  body {
    background-color: lightgray;
  }
}
```

Dette ændrer baggrunden, hvis skærmen er mindre end 600px bred.

---

###### CSS står for “Cascading”

Det betyder, at **regler "falder ned" og overskriver hinanden** ud fra:

1. **Specificitet** (hvor præcis selektoren er)
    
2. **Rækkefølge** (sidste regel vinder)
    
3. **Vægt** (fx `!important` overtrumfer alt)
    

---

##### CSS Frameworks (bonus)

Der findes færdige **CSS-rammeværk**, som hjælper dig i gang:

- **Bootstrap**
    
- **Tailwind CSS**
    
- **Bulma**
    
- **Foundation**
    

---

##### Opsummering

|Punkt|Beskrivelse|
|---|---|
|Hvad er CSS?|Sprog til at style HTML-elementer|
|Hvad gør det?|Ændrer udseende, layout og responsivitet|
|Hvor bruges det?|På alle moderne hjemmesider|
|Hvordan bruges det?|Via selectors og egenskaber (`selector { property: value; }`)|
