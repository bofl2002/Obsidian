[[Programmering]]

SignalR er et open-source bibliotek fra Microsoft, der gør det muligt at lave real-time kommunikation mellem server og klient i webapplikationer. Det betyder, at serveren kan sende data til klienterne, så snart noget ændrer sig, uden at klienterne behøver at sende nye forespørgsler.

## Hvordan fungerer det?

SignalR håndterer valg af kommunikationsmetode automatisk. Det bruger den bedst mulige teknologi, som klienten understøtter, fx:

- WebSockets
- Server-Sent Event
- Long polling

Du behøver ikke selv at kode mod de forskellige protokoller.

## Hubs

SignalR bruger “hubs” som kommunikationspunkt. En hub tillader:

- At klienten kan kalde metoder på serveren
- At serveren kan kalde metoder på klienterne

Eksempel på serverkald til klienter:  
`Clients.All.SendAsync("ReceiveMessage", message)`

## Versioner

Der er to hovedversioner af SignalR:

- ASP.NET SignalR (ældre)
- ASP.NET Core SignalR (moderne og anbefalet)

Den nye version er hurtigere, lettere og mere skalerbar.

## Hvorfor bruge SignalR?

- Gør real-time funktionalitet enkel at implementere
- Undgår komplekst WebSocket-kode
- God integration med .NET og Azure
- Understøtter både små og store applikationer

SignalR er en afgørende del af Blazor Server og en værdifuld tilføjelse til Blazor WebAssembly, når realtidskommunikation er nødvendig. Kombinationen muliggør C#-baserede løsninger med interaktivitet på niveau med traditionelle JavaScript-rammer.

En **SignalR Hub** er en central komponent i Microsofts SignalR-bibliotek, der forenkler **real-tidskommunikation** mellem server og klienter (f.eks. webbrowsere eller apps). Hubs fungerer som en mellemmand, der gør det nemt at sende og modtage beskeder, kalde metoder og håndtere forbindelser.

### Hvad gør en Hub?

1. **Abstraherer kompleksitet**:  
    Hubs anvender; **RPC (Remote Procedure Calls)**, således at du kan kalde metoder direkte på klienter fra serveren (og omvendt) uden at håndtere low-level kommunikation som WebSocket eller HTTP-direkte.
    
2. **Håndterer forbindelser**:  
    Automatisk sporing af tilsluttede klienter, grupper og livscyklus-hændelser (f.eks. når en klient forbinder/fra-kobler).
    
3. **Broadcast og grupper**:  
    Send beskeder til alle klienter, specifikke klienter eller grupper (f.eks. et chatrum).



### **Nøglefunktioner**

- Metodekald mellem server og klient:
    
    - Serveren kan kalde Clients.All.SendAsync("ModtagBesked", besked) for at sende til alle klienter.
        
    - Klienter kan kalde en metode på serveren (f.eks. hubConnection.invoke("SendMessage", "Hej")).
        



**Gruppedaministration**

// Tilføj en klient til en gruppe
await Groups.AddToGroupAsync(Context.ConnectionId, "GruppeA");
// Send besked til gruppen
await Clients.Group("GruppeA").SendAsync("ModtagBesked", "Hej GruppeA!");


**Livscyklus-metoder**

Overwrite **OnConnectedAsync()** og **OnDisconnectedAsync()** for at håndtere logik, når klienter forbinder/fra-kobler.


### **Eksempel: En simpel ChatHub**

public class ChatHub : Hub 
{
    public async Task SendMessage(string bruger, string besked)
    {
        // Send besked til alle klienter
        await Clients.All.SendAsync("ModtagBesked", bruger, besked);
    }
}


**Klientkode**

using Microsoft.AspNetCore.SignalR.Client;

// Opret forbindelse
var connection = new HubConnectionBuilder()
    .WithUrl("https://din-server-url/chatHub")  // Tilføj fuld URL
    .Build();

// Lyt til "ModtagBesked"-metoden
connection.On<string, string>("ModtagBesked", (bruger, besked) => 
{
    Console.WriteLine($"{bruger}: {besked}");
});

try
{
    // Start forbindelsen
    await connection.StartAsync();
    
    // Send besked
    await connection.InvokeAsync("SendMessage", "Alice", "Hej verden!");
}
catch (Exception ex)
{
    Console.WriteLine($"Fejl: {ex.Message}");
}


**Brugere**

I SignalR kan brugere identificeres og håndteres på flere måder:

**Connection ID**

- Hver bruger får automatisk tildelt et unikt Connection ID, når de opretter forbindelse
    
- Dette ID kan bruges til at sende beskeder til specifikke brugere
    
- Connection ID'et ændres dog, hvis brugeren genopretter forbindelsen
    

**User Identity**

- Du kan knytte autentificerede brugere til deres [ASP.NET(opens in a new tab)](http://asp.net/) Identity
    
- Dette giver mulighed for at spore brugere på tværs af forbindelser
    
- Brug Context.User.Identity.Name for at få brugernavnet
    

**Persistente forbindelser**

- SignalR tilbyder mulighed for at gemme brugerinformation
    
- Dette kan bruges til at genoptage sessioner ved genoprettelse af forbindelser
    

**Eksempel på brugerhåndtering**:

public class ChatHub : Hub
{
    public override async Task OnConnectedAsync()
    {
        // Få brugerens navn fra Authentication
        var userName = Context.User.Identity.Name;
        
        // Tilføj brugeren til en gruppe baseret på deres rolle
        if (Context.User.IsInRole("Admin"))
        {
            await Groups.AddToGroupAsync(Context.ConnectionId, "Administrators");
        }
        
        await Clients.All.SendAsync("UserConnected", userName);
        await base.OnConnectedAsync();
    }
}