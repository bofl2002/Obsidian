[[Programmering]]

### Cross-Origin Resoure Sharing

**CORS** er en **mekanisme**, der gør det muligt at **tillade adgang på tværs af origins**, når det er sikkert og ønsket.

CORS gør det muligt for serveren at sige:

"Ja, denne anden origin må godt få adgang til min data."

Det **omgår SOP**, men **kun hvis serveren selv tillader det** via specifikke HTTP-headers.

---

##### Hvordan fungerer det?

Når en browser prøver at hente data fra en anden origin (fx med `fetch()`), sender den en **CORS-forespørgsel**:

1. **Browseren spørger serveren:**  
    "Må jeg hente denne ressource fra et andet domæne?"
    
2. **Serveren svarer (hvis tilladt):**  
    `Access-Control-Allow-Origin: https://din-klientside.dk`
    
3. Hvis svaret mangler – eller ikke tillader origin – **blokerer browseren** anmodningen.
    

---

##### Eksempel på en CORS-header:

`Access-Control-Allow-Origin: *`

Tillader alle domæner (ikke anbefalet til følsomme data)

Eller mere sikkert:

`Access-Control-Allow-Origin: https://minfrontend.dk`

---

#####  Hvorfor er det vigtigt?

- SOP forhindrer ondsindet adgang til brugerdata.
    
- CORS giver fleksibel og sikker adgang, fx mellem **frontend (React)** og **backend (API)** hostet på forskellige domæner eller porte.
    


### Same Origin Policy

**Same-Origin Policy** er en **sikkerhedsregel i webbrowsere**, som **begrænser scripts (fx JavaScript)** fra at få adgang til data på et andet domæne end det, hvor scriptet blev indlæst fra.

Det beskytter brugeren mod angreb som fx **Cross-Site Scripting (XSS)** og **data-tyveri**.

To URL’er har samme **origin** hvis de har:

|Del|Samme?|
|---|---|
|**Protokol**|(http vs. https)|
|**Domæne**|(eksempel.dk vs. test.dk)|
|**Port**|(80, 443, 3000, osv.)|

**Eksempel:**

|URL|Samme origin?|
|---|---|
|`https://eksempel.dk/data.json`|✅|
|`http://eksempel.dk/data.json`|❌ (protokol)|
|`https://api.eksempel.dk/data.json`|❌ (subdomæne)|
|`https://eksempel.dk:3000/data.json`|❌ (port)|

##### Kort opsummeret

|Funktion|Same-Origin Policy|CORS|
|---|---|---|
|Formål|Beskytte mod uautoriseret adgang|Tillade legitim adgang på tværs af domæner|
|Styres af|Browseren|Serveren (via headers)|
|Standard opførsel|Blokerer cross-origin requests|Giver mulighed for at tillade dem|

---

🔐 **SOP = Sikkerhedsbarriere**  
🌐 **CORS = Kontrolleret adgang på tværs af domæner**

