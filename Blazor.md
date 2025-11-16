[[Programmering]]

**Blazor** er et **web-udviklingsframework** fra **Microsoft**, som gør det muligt at bygge **interaktive webapplikationer** ved hjælp af **C#** i stedet for **JavaScript**. Det er en del af **.NET-platformen** og bruges ofte som et alternativ til frameworks som React, Angular eller Vue — men med .NET-teknologier i stedet for JavaScript-økosystemet.

Blazor lader udviklere skrive **frontend-logik i C#** og dele **kode, modeller og validering** mellem klient og server. Det betyder, at du kan have **samme programmeringssprog** på hele stakken — både backend og frontend.


## Hvad er en komponent i Blazor?

En **komponent** i Blazor er en **genanvendelig byggeblok** for brugergrænsefladen (UI).  
Man kan sammenligne det med en **React Component** eller **Angular Component** — bare skrevet i **C# og Razor-syntax**.

En komponent:

- Indeholder **markup (HTML)** og **C#-kode** i én fil (typisk `.razor`).
    
- Kan modtage **parametre**.
    
- Kan **udløse events** (til forældrekomponenter).
    
- Kan have **livscyklusmetoder** (som `OnInitialized`, `OnParametersSet`, osv.).
    
- Kan indeholde **børnekomponenter**.

### Typer af Blazor

Der findes flere måder at køre Blazor-applikationer på:

1. **Blazor Server**
    
    - Kører på **serveren**.
        
    - UI opdateres via en **SignalR-forbindelse** mellem browseren og serveren.
        
    - Fordel: Lille klient-side download, hurtig initial load.
        
    - Ulempe: Afhænger af konstant forbindelse til serveren (latency kan mærkes).
        
2. **Blazor WebAssembly (Blazor WASM)**
    
    - Kører **direkte i browseren** via **WebAssembly**.
        
    - Hele .NET-runtime og applikationen downloades til browseren.
        
    - Fordel: Kan køre offline, mere “SPA-lignende”.
        
    - Ulempe: Større initial download og lidt tungere performance.
        
3. **Blazor Hybrid**
    
    - Bruges i **desktop- eller mobilapps** (fx med .NET MAUI).
        
    - UI gengives som en webvisning (WebView), men med adgang til native API’er.
        
    - Fordel: Kombinerer web-UI med native funktionalitet.
        
4. **Blazor United** _(kommende/forsøgsvis feature i .NET 8+)_
    
    - Samler Server, WASM og prerendering i ét fleksibelt model.
        
    - Formålet er at få det bedste fra alle verdener.

### Typiske anvendelser

- **Interne virksomhedsapps** og dashboards.
    
- **Data-drevne webapps** (CRM, ERP, osv.).
    
- **Progressive Web Apps (PWA)** med WebAssembly.
    
- **Hybrid mobile apps** via .NET MAUI.

### Fordele

- Samme sprog (C#) på klient og server.
    
- Stærk integration med .NET-økosystemet (Entity Framework, ASP.NET, Identity, osv.).
    
- Komponent-baseret struktur (ligesom React).
    
- God understøttelse af dependency injection, routing og formvalidering.

### Ulemper

- Mindre økosystem end JavaScript-frameworks.
    
- Større initial load for WebAssembly-versionen.
    
- Mindre modent community (men vokser hurtigt).
    
- Færre tredjeparts UI-biblioteker end fx React/Vue.

**

## Atomic Design

Selvfølgelig — her er en dansk forklaring på Atomic Design, uden ikoner og med et klart, professionelt sprog:

### Atomic Design – en metode til opbygning af designsystemer

Atomic Design er en metode til at skabe konsistente og skalerbare brugergrænseflader. Metoden er udviklet af Brad Frost og bygger på idéen om at opdele et design i mindre, genanvendelige dele – ligesom naturen består af atomer, der danner molekyler og videre komplekse strukturer.

Atomic Design består af fem niveauer:

### 1. Atomer

Atomer er de mest grundlæggende byggeklodser i et design.  
Eksempler kan være:

- HTML-elementer som knapper, inputfelter eller labels  
      
    
- Farver, typografi og ikoner  
      
    

Atomer står sjældent alene, men danner grundlaget for mere komplekse komponenter.

### 2. Molekyler

Molekyler opstår, når flere atomer sættes sammen og fungerer som én samlet enhed.  
Eksempler:

- Et søgefelt bestående af et inputfelt, en label og en knap  
      
    
- Et formularfelt med input og fejlmeddelelse  
      
    

Molekyler har en tydelig funktion og kan genbruges mange steder i et design.

### 3. Organismer

Organismer består af flere molekyler (og evt. atomer) og udgør selvstændige sektioner i et interface.  
Eksempler:

- En navigationsmenu  
      
    
- Et produktkort med billede, titel og pris  
      
    
- En artikeloversigt  
      
    

Organismer er større, genanvendelige moduler, der kan bruges på tværs af forskellige sider.

### 4. Skabeloner (Templates)

Skabeloner definerer layoutet for en side ved at placere organismer i en struktur.  
De viser, hvordan komponenterne hænger sammen, men indeholder som regel ikke rigtigt indhold.

Eksempel:  
En produktside-skabelon med header, produktliste og footer – men uden konkrete produkter.

### 5. Sider (Pages)

Sider er konkrete versioner af skabelonerne med rigtigt indhold og data.  
De viser, hvordan designet fungerer i praksis, og bruges ofte til test og godkendelse af layout og indhold.

### Fordele ved Atomic Design

- Konsistens: Ensartet udseende på tværs af produkter og sider  
      
    
- Genanvendelighed: Komponenter kan bruges igen og igen  
      
    
- Skalerbarhed: Nemt at bygge videre og tilføje nye funktioner  
      
    
- Bedre samarbejde: Designere og udviklere arbejder ud fra de samme byggesten  
      
    

**