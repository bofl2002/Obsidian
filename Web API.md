[[Programmering]]


- Et **Web API** er en serverapplikation, der **eksponerer data og funktioner via HTTP**.
    
- Klienter (fx webapps, mobilapps) kan kalde API’en for at hente, oprette, opdatere eller slette data.
    
- API’et sender ofte data i **JSON-format**.
    

---

##### Eksempel: Minimal Web API i ASP.NET Core

---

###### 1. Opret nyt projekt (i terminalen)

```bash
dotnet new webapi -o MinWebApi
cd MinWebApi
dotnet run
```

Dette opretter og kører en minimal Web API med ASP.NET Core.

---

###### 2. Simpelt Controller-eksempel

I `Controllers`-mappen, opret en fil `PostController.cs`:

```csharp
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;

namespace MinWebApi.Controllers
{
    [ApiController]
    [Route("api/[controller]")]
    public class PostController : ControllerBase
    {
        // Dummy data
        private static List<Post> posts = new List<Post>
        {
            new Post { Id = 1, Title = "Hej verden", Content = "Dette er et indlæg." }
        };

        // GET api/post
        [HttpGet]
        public IEnumerable<Post> Get()
        {
            return posts;
        }

        // GET api/post/1
        [HttpGet("{id}")]
        public ActionResult<Post> Get(int id)
        {
            var post = posts.Find(p => p.Id == id);
            if (post == null) return NotFound();
            return post;
        }

        // POST api/post
        [HttpPost]
        public ActionResult<Post> Post(Post nytPost)
        {
            posts.Add(nytPost);
            return CreatedAtAction(nameof(Get), new { id = nytPost.Id }, nytPost);
        }
    }

    public class Post
    {
        public int Id { get; set; }
        public string Title { get; set; }
        public string Content { get; set; }
    }
}
```

---

###### 3. Kør og test API’en

- Start API’en med `dotnet run`
    
- Åbn fx:
    
    - `GET http://localhost:5000/api/post` — hent alle posts
        
    - `GET http://localhost:5000/api/post/1` — hent post med id 1
        
    - `POST http://localhost:5000/api/post` — opret en ny post (fx via Postman eller curl)
        

---

##### Hvordan virker det?

- `[ApiController]` gør det til en API-controller (ikke MVC view)
    
- `[Route("api/[controller]")]` sætter URL-ruten (fx `/api/post`)
    
- HTTP-metoderne styres af `[HttpGet]`, `[HttpPost]` osv.
    
- Returneringer er JSON-serialiserede objekter
    

---

##### Fordele ved ASP.NET Core Web API

- Hurtigt at komme i gang med minimal opsætning
    
- Understøtter RESTful services
    
- Bygger på moderne .NET platform
    
- God integration med frontend frameworks (React, Angular, Vue)
    


## Eksempel på WebAPI

#### ASP.NET Core MVC med Web API Controller – Eksempel

---

###### 1. Opret et nyt ASP.NET Core MVC-projekt

I terminalen:

```bash
dotnet new mvc -o MinMvcWebApi
cd MinMvcWebApi
dotnet run
```

Dette starter et klassisk MVC-projekt, som også kan indeholde API-controllere.

---

###### 2. Tilføj en Web API Controller

Opret en ny controller i `Controllers`-mappen, fx `ProductsApiController.cs`:

```csharp
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;

namespace MinMvcWebApi.Controllers
{
    [ApiController]
    [Route("api/[controller]")]
    public class ProductsApiController : ControllerBase
    {
        // Dummy data - liste af produkter
        private static List<Product> products = new List<Product>
        {
            new Product { Id = 1, Name = "T-shirt", Price = 149 },
            new Product { Id = 2, Name = "Jeans", Price = 399 }
        };

        // GET: api/productsapi
        [HttpGet]
        public IEnumerable<Product> Get()
        {
            return products;
        }

        // GET: api/productsapi/1
        [HttpGet("{id}")]
        public ActionResult<Product> Get(int id)
        {
            var product = products.Find(p => p.Id == id);
            if (product == null) return NotFound();
            return product;
        }

        // POST: api/productsapi
        [HttpPost]
        public ActionResult<Product> Post(Product newProduct)
        {
            products.Add(newProduct);
            return CreatedAtAction(nameof(Get), new { id = newProduct.Id }, newProduct);
        }

        // PUT: api/productsapi/1
        [HttpPut("{id}")]
        public IActionResult Put(int id, Product updatedProduct)
        {
            var product = products.Find(p => p.Id == id);
            if (product == null) return NotFound();

            product.Name = updatedProduct.Name;
            product.Price = updatedProduct.Price;
            return NoContent();
        }

        // DELETE: api/productsapi/1
        [HttpDelete("{id}")]
        public IActionResult Delete(int id)
        {
            var product = products.Find(p => p.Id == id);
            if (product == null) return NotFound();

            products.Remove(product);
            return NoContent();
        }
    }

    // Model-klasse
    public class Product
    {
        public int Id { get; set; }
        public string Name { get; set; }
        public decimal Price { get; set; }
    }
}
```

---

###### 3. Test API’en

Kør projektet (`dotnet run`), og brug fx en browser eller Postman til at teste:

|HTTP-metode|URL|Handling|
|---|---|---|
|GET|`https://localhost:5001/api/productsapi`|Hent alle produkter|
|GET|`https://localhost:5001/api/productsapi/1`|Hent produkt med id=1|
|POST|`https://localhost:5001/api/productsapi`|Opret et nyt produkt|
|PUT|`https://localhost:5001/api/productsapi/1`|Opdater produkt med id=1|
|DELETE|`https://localhost:5001/api/productsapi/1`|Slet produkt med id=1|

---

###### 4. Forklaring

- Controller er arvet fra `ControllerBase` (ikke `Controller`), fordi den ikke skal returnere Views, kun data (JSON).
    
- `[ApiController]` og `[Route]` bestemmer API-ruten.
    
- Metoderne svarer til RESTful HTTP-anmodninger.
    
- Dummy-datastruktur bruges til at holde styr på produkter i hukommelsen.
    

---

###### 5. MVC + Web API sammen

I samme projekt kan du have:

- Almindelige MVC Controllers med Views (fx til frontend HTML-udsendelse)
    
- API Controllers som denne, der kun returnerer JSON til frontend apps, mobile apps eller andre services
    




#### Kombinér MVC Controller (C#) med Web API-kald (C#)

---

## Situation

Du har en Web API (fx `ProductsApiController`) og vil i din MVC-controller i C# hente data fra API’et (internt kald) og sende det videre til Razor View.

---

###### 1. MVC Controller, som kalder Web API via HttpClient

```csharp
using Microsoft.AspNetCore.Mvc;
using System.Net.Http;
using System.Text.Json;
using System.Threading.Tasks;
using System.Collections.Generic;

namespace MinMvcWebApi.Controllers
{
    public class HomeController : Controller
    {
        private readonly HttpClient _httpClient;

        public HomeController(HttpClient httpClient)
        {
            _httpClient = httpClient;
        }

        public async Task<IActionResult> Products()
        {
            var response = await _httpClient.GetAsync("https://localhost:5001/api/productsapi");
            if (!response.IsSuccessStatusCode)
            {
                // Håndter fejl, fx vis fejlbesked
                return View("Error");
            }

            var jsonString = await response.Content.ReadAsStringAsync();
            var products = JsonSerializer.Deserialize<List<Product>>(jsonString, new JsonSerializerOptions
            {
                PropertyNameCaseInsensitive = true
            });

            return View(products);
        }
    }

    // Samme Product-model som i API-controller
    public class Product
    {
        public int Id { get; set; }
        public string Name { get; set; }
        public decimal Price { get; set; }
    }
}
```

---

###### 2. Registrér HttpClient i `Program.cs`

I `Program.cs` (for .NET 6+ minimal hosting model), tilføj:

```csharp
var builder = WebApplication.CreateBuilder(args);

// Tilføj HttpClient som service
builder.Services.AddHttpClient<HomeController>();

builder.Services.AddControllersWithViews();

var app = builder.Build();

app.MapDefaultControllerRoute();

app.Run();
```

---

###### 3. Razor View til at vise produkterne

I `Views/Home/Products.cshtml`:

```csharp
@model List<MinMvcWebApi.Controllers.Product>

<h2>Produkter hentet via Web API (C#)</h2>

<table>
    <thead>
        <tr>
            <th>Navn</th>
            <th>Pris (kr.)</th>
        </tr>
    </thead>
    <tbody>
    @foreach (var product in Model)
    {
        <tr>
            <td>@product.Name</td>
            <td>@product.Price</td>
        </tr>
    }
    </tbody>
</table>
```

---

##### Sådan fungerer det

- MVC-controlleren bruger `HttpClient` til at lave et HTTP-kald til dit eget API-endpoint.
    
- JSON-data fra API’et deserialiseres til C#-objekter (`Product`).
    
- Data sendes videre til Razor View som model.
    
- Razor View render tabellen med produkter.
    

---

##### Bemærkning

- For at det virker skal din app køre på `https://localhost:5001` (eller rette URL til API’et).
    
- Du kan også lave API-kald til eksterne API’er på samme måde.
    
