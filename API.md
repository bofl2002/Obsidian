[[Programmering]]


**API** står for **Application Programming Interface**.

Det er en **måde for programmer (eller systemer) at kommunikere med hinanden** på – uden at kende hinandens interne detaljer.

Kort sagt: En API er som en **restaurantmenu** – den fortæller dig, **hvad du kan bestille**, men ikke hvordan maden bliver lavet.

---

##### Hvad bruges en API til?

API’er bruges til at:

- Hente data fra databaser eller eksterne systemer
    
- Sende data fra en app til en server
    
- Styre funktioner i software uden at ændre kildekode
    
- Opdele systemer i **moduler** der kan **snakke sammen**
    

---

##### Typer af API’er (mest relevante)

|Type|Eksempel|Forklaring|
|---|---|---|
|**Web API**|REST API, GraphQL API|API’er til web og mobil via internettet|
|**Biblioteks-API**|JavaScript’s DOM API, jQuery|Indbygget i programmeringssprog|
|**Operativsystem API**|Windows API, Android API|For at styre hardware/software-funktioner|

---

##### Eksempel: Web API

En typisk API (fx REST API) fungerer over HTTP og bruger **URL’er, metoder og dataformater** som:

###### HTTP-metoder:

|Metode|Hvad den gør|Bruges til|
|---|---|---|
|`GET`|Henter data|Vis data (fx brugerprofil)|
|`POST`|Sender data|Opret (fx nyt opslag)|
|`PUT`|Opdaterer data|Redigér (fx brugernavn)|
|`DELETE`|Sletter data|Slet (fx en kommentar)|

###### JSON-format (typisk dataformat):

```json
{
  "navn": "Sara",
  "alder": 22
}
```

---

###### Eksempel: API-kald i JavaScript

```javascript
fetch('https://api.eksempel.dk/brugere/123')
  .then(response => response.json())
  .then(data => console.log(data));
```

Dette kalder en `GET`-API, henter brugerdata og udskriver det i konsollen.

---

##### API og sikkerhed

API’er kræver ofte **adgangskontrol**:

- API-nøgler
    
- Tokens (fx JWT)
    
- OAuth (til login med Google, Facebook osv.)
    

---

##### Fordele ved at bruge API’er

|Fordel|Forklaring|
|---|---|
|Genbrug|Du kan bruge funktioner uden at opfinde dem igen|
|Modularitet|Systemer bliver opdelt og nemmere at vedligeholde|
|Integration|Forbind nemt til databaser, apps, cloud osv.|
|Skalerbarhed|Frontend og backend kan udvikles uafhængigt|

---

##### Eksempler på kendte API’er

- **Google Maps API** – vis kort på din side
    
- **OpenWeather API** – vis vejrdata
    
- **Spotify API** – hent musik og playlister
    
- **REST Countries API** – info om lande
    
- **ChatGPT API** – brug OpenAI’s modeller i egne apps
    

---

## Bonus: API vs. Database

|API|Database|
|---|---|
|Kommunikationsinterface|Datakilde|
|Styrer adgang og funktion|Gemmer selve dataene|
|Kan ligge på en anden server|Ligger ofte bag API'en|

---

##### Kort opsummering

|Punkt|Forklaring|
|---|---|
|Hvad er en API?|Et sæt regler for kommunikation mellem systemer|
|Hvad bruges den til?|Dataudveksling, integration, automatisering|
|Hvordan bruges den?|Ofte via HTTP og JSON|
|Hvorfor bruge API?|For at skabe fleksible, moderne systemer|


#### Eksempel: Kald til en Web API i C#

Vi bruger her:

- `HttpClient` til at sende anmodningen
    
- `System.Text.Json` til at læse JSON-svaret
    
- Et simpelt eksempel på en **public REST API** (fx [https://jsonplaceholder.typicode.com](https://jsonplaceholder.typicode.com/))
    

---

##### 1. Installer nødvendige namespaces

I toppen af filen (typisk en `.cs`-fil):

```csharp
using System;
using System.Net.Http;
using System.Threading.Tasks;
using System.Text.Json;
```

---

##### 2. Definér en model (til at deserialisere JSON)

Fx hvis vi henter en "post" fra JSONPlaceholder API:

```csharp
public class Post
{
    public int UserId { get; set; }
    public int Id { get; set; }
    public string Title { get; set; }
    public string Body { get; set; }
}
```

---

##### 3. Lav et API-kald med HttpClient

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        HttpClient client = new HttpClient();

        try
        {
            // Kald til en offentlig API
            string url = "https://jsonplaceholder.typicode.com/posts/1";
            HttpResponseMessage response = await client.GetAsync(url);

            response.EnsureSuccessStatusCode(); // Smid fejl hvis ikke 200 OK

            string responseBody = await response.Content.ReadAsStringAsync();

            // Konverter JSON til C#-objekt
            Post post = JsonSerializer.Deserialize<Post>(responseBody);

            // Udskriv data
            Console.WriteLine($"Titel: {post.Title}");
            Console.WriteLine($"Bruger-ID: {post.UserId}");
            Console.WriteLine($"Indhold: {post.Body}");
        }
        catch (Exception e)
        {
            Console.WriteLine($"Noget gik galt: {e.Message}");
        }
    }
}
```

---

##### Output (eksempel)

Hvis det virker, får du fx:

```
Titel: sunt aut facere repellat provident occaecati
Bruger-ID: 1
Indhold: quia et suscipit
suscipit recusandae consequuntur expedita...
```

---

##### Hvad hvis API'en kræver en nøgle?

Så tilføjer du en header som dette:

```csharp
client.DefaultRequestHeaders.Add("Authorization", "Bearer DIN_TOKEN_HER");
```

---

##### ✅ Krav for at køre koden

- .NET 6+ eller .NET Core (koden bruger `async/await`)
    
- Hvis du bruger Visual Studio eller VS Code, skal du have en `Main` metode med `async Task`
    

---

##### Opsummering

Med `HttpClient` i C# kan du:

- Kalde REST API’er (`GET`, `POST`, `PUT`, `DELETE`)
    
- Læse JSON og konvertere til C#-objekter
    
- Håndtere fejl og validere svar
    
- Tilføje headers og tokens (fx ved sikre API’er)
    
