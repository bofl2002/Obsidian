[[Distruberede Systemer]]

Et **socket** er et kommunikationsendepunkt, der gør det muligt for programmer at kommunikere med hinanden over et netværk (eller på samme maskine).

Socket-programmering er en teknik, der bruges til at etablere kommunikation mellem to applikationer over et netværk. Det indebærer at oprette en socket, som grundlæggende er et software-endepunkt, der kan sende og modtage data over netværket. De to applikationer kommunikerer ved at sende data gennem deres respektive sockets, som er forbundet via et netværk.

**Grundlæggende om C# socket-programmering:**  
Før man dykker ned i detaljerne omkring C# socket-programmering, er det vigtigt at forstå nogle grundlæggende koncepter ved socket-programmering generelt. En socket er et software-endepunkt, der repræsenterer den ene ende af en tovejskommunikationskanal mellem to netværksbaserede programmer. En socket defineres af en IP-adresse og et portnummer, og disse to værdier identificerer entydigt socket’en.

I C# giver klassen Socket mulighed for at oprette og arbejde med sockets. Klassen Socket er en del af navnerummet System.Net.Sockets og indeholder metoder og egenskaber, der gør det muligt at oprette, konfigurere, forbinde, sende og modtage data over et netværk.

## Nøglekarakteristika ved et socket:

**Et socket identificeres ved:**

- **IP-adresse** - hvor programmet kører
- **Portnummer** - hvilken specifik applikation/service
- **Protokol** - typisk TCP eller UDP

## Hvordan fungerer sockets?

Sockets bruges til at etablere tovejskommunikation mellem to programmer:

1. **Oprette forbindelse** - etablere en kommunikationskanal
2. **Sende data** - transmittere information
3. **Modtage data** - lytte efter og modtage information
4. **Lukke forbindelse** - afslutte kommunikationen

## Typer af sockets:

- **Stream Sockets (TCP)** - pålidelig, forbindelsesorienteret kommunikation
- **Datagram Sockets (UDP)** - hurtigere, men ikke garanteret levering

**

**Eksempel på at oprette en socket:

For at bruge sockets i C# skal du først importere **System.Net.Sockets-navnerummet**. Klassen Socket bruges derefter til at oprette og håndtere sockets.

Socket socket = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);

AddressFamily angiver adressetypen, SocketType angiver typen af socket, og ProtocolType angiver protokollen.

**For at oprette forbindelse bruges Connect():**

IPAddress ipAddress = IPAddress.Parse("192.168.1.1");

IPEndPoint remoteEndPoint = new IPEndPoint(ipAddress, 80);

socket.Connect(remoteEndPoint);

  
**For at sende data bruges Send():**

byte[] data = Encoding.ASCII.GetBytes("Hello World");

socket.Send(data);

  
**For at modtage data bruges Receive():**

byte[] data = new byte[1024];

int receivedBytes = socket.Receive(data);

string receivedData = Encoding.ASCII.GetString(data, 0, receivedBytes);


**For at lukke forbindelsen bruges Close():**

socket.Close();

**Eksempel med server og klient:**  
Serveren lytter på port 1234, klienten forbinder til samme port. Klienten sender en besked, serveren modtager den og sender et svar tilbage. Til sidst lukkes begge sockets.

1. **Server code**  
2. Socket serverSocket = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);  
3. serverSocket.Bind(new IPEndPoint(IPAddress.Any, 1234));  
4. serverSocket.Listen(10);  
5. Socket clientSocket = serverSocket.Accept();  
6. byte[] data = new byte[1024];  
7. int receivedBytes = clientSocket.Receive(data);  
8. string receivedMessage = Encoding.ASCII.GetString(data, 0, receivedBytes);  
9. Console.WriteLine("Received message: " + receivedMessage);  
10. clientSocket.Send(Encoding.ASCII.GetBytes("Hello from server!"));  
11. clientSocket.Close();  
12. serverSocket.Close();  

13. **Client code**  
14. Socket clientSocket = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);  
15. clientSocket.Connect(new IPEndPoint(IPAddress.Loopback, 1234));  
16. clientSocket.Send(Encoding.ASCII.GetBytes("Hello from client!"));  
17. byte[] data = new byte[1024];  
18. int receivedBytes = clientSocket.Receive(data);  
19. string receivedMessage = Encoding.ASCII.GetString(data, 0, receivedBytes);  
20. Console.WriteLine("Received message: " + receivedMessage);  
21. clientSocket.Close();
**

**Server**
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

class SocketServer
{
    static void Main(string[] args)
    {
        // Definer host og port
	        string host = "127.0.0.1";
	        int port = 12345;
        
        // Opret et TCP/IP socket
        Socket serverSocket = new Socket(AddressFamily.InterNetwork, 
                                        SocketType.Stream, 
                                        ProtocolType.Tcp);
        
        // Bind socket til en specifik adresse og port
        IPEndPoint endPoint = new IPEndPoint(IPAddress.Parse(host), port);
        serverSocket.Bind(endPoint);
        
        // Lyt efter indkommende forbindelser (max 5 i kø)
        serverSocket.Listen(5);
        Console.WriteLine($"Server lytter på {host}:{port}");
        
        while (true)
        {
            // Accepter en forbindelse
            Socket clientSocket = serverSocket.Accept();
            Console.WriteLine($"Forbindelse etableret fra {clientSocket.RemoteEndPoint}");
            
            // Modtag data fra klienten
            byte[] buffer = new byte[1024];
            int bytesReceived = clientSocket.Receive(buffer);
            string data = Encoding.UTF8.GetString(buffer, 0, bytesReceived);
            Console.WriteLine($"Modtaget besked: {data}");
            
            // Send svar tilbage til klienten
            string response = $"Server modtog: {data}";
            byte[] responseBytes = Encoding.UTF8.GetBytes(response);
            clientSocket.Send(responseBytes);
            
            // Luk forbindelsen til denne klient
            clientSocket.Shutdown(SocketShutdown.Both);
            clientSocket.Close();
            Console.WriteLine("Forbindelse lukket");
            
            // Break efter én forbindelse (fjern denne linje for at køre kontinuerligt)
            break;
        }
        
        // Luk server socket
        serverSocket.Close();
    }
}

**Client**

using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

class SocketClient
{
    static void Main(string[] args)
    {
        // Definer server host og port (skal matche serveren)
        string host = "127.0.0.1";
        int port = 12345;
        
        // Opret et TCP/IP socket
        Socket clientSocket = new Socket(AddressFamily.InterNetwork, 
                                        SocketType.Stream, 
                                        ProtocolType.Tcp);
        
        // Forbind til serveren
        IPEndPoint endPoint = new IPEndPoint(IPAddress.Parse(host), port);
        clientSocket.Connect(endPoint);
        Console.WriteLine($"Forbundet til server på {host}:{port}");
        
        // Send en besked til serveren
        string message = "Hej fra klienten!";
        byte[] messageBytes = Encoding.UTF8.GetBytes(message);
        clientSocket.Send(messageBytes);
        Console.WriteLine($"Sendt besked: {message}");
        
        // Modtag svar fra serveren
        byte[] buffer = new byte[1024];
        int bytesReceived = clientSocket.Receive(buffer);
        string response = Encoding.UTF8.GetString(buffer, 0, bytesReceived);
        Console.WriteLine($"Modtaget svar: {response}");
        
        // Luk forbindelsen
        clientSocket.Shutdown(SocketShutdown.Both);
        clientSocket.Close();
        Console.WriteLine("Forbindelse lukket");
    }
}

**Multiple Clients Server**
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;
using System.Threading;

class MultiClientServer
{
    private static int clientCount = 0;
    
    static void Main(string[] args)
    {
        // Definer host og port
        string host = "127.0.0.1";
        int port = 12345;
        
        // Opret et TCP/IP socket
        Socket serverSocket = new Socket(AddressFamily.InterNetwork, 
                                        SocketType.Stream, 
                                        ProtocolType.Tcp);
        
        // Bind socket til en specifik adresse og port
        IPEndPoint endPoint = new IPEndPoint(IPAddress.Parse(host), port);
        serverSocket.Bind(endPoint);
        
        // Lyt efter indkommende forbindelser
        serverSocket.Listen(10);
        Console.WriteLine($"Server lytter på {host}:{port}");
        Console.WriteLine("Venter på klienter...\n");
        
        while (true)
        {
            try
            {
                // Accepter en forbindelse
                Socket clientSocket = serverSocket.Accept();
                clientCount++;
                
                Console.WriteLine($"Klient #{clientCount} forbundet fra {clientSocket.RemoteEndPoint}");
                
                // Opret en ny tråd til at håndtere denne klient
                Thread clientThread = new Thread(() => HandleClient(clientSocket, clientCount));
                clientThread.Start();
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Fejl ved accept: {ex.Message}");
            }
        }
    }
    
    static void HandleClient(Socket clientSocket, int clientId)
    {
        try
        {
            while (true)
            {
                // Modtag data fra klienten
                byte[] buffer = new byte[1024];
                int bytesReceived = clientSocket.Receive(buffer);
                
                // Hvis der ikke modtages data, er forbindelsen lukket
                if (bytesReceived == 0)
                {
                    break;
                }
                
                string data = Encoding.UTF8.GetString(buffer, 0, bytesReceived);
                Console.WriteLine($"[Klient #{clientId}] Modtaget: {data}");
                
                // Send svar tilbage til klienten
                string response = $"Server (til klient #{clientId}): Modtog '{data}'";
                byte[] responseBytes = Encoding.UTF8.GetBytes(response);
                clientSocket.Send(responseBytes);
                
                // Hvis klienten sender "exit", luk forbindelsen
                if (data.Trim().ToLower() == "exit")
                {
                    break;
                }
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"[Klient #{clientId}] Fejl: {ex.Message}");
        }
        finally
        {
            // Luk forbindelsen til denne klient
            clientSocket.Shutdown(SocketShutdown.Both);
            clientSocket.Close();
            Console.WriteLine($"[Klient #{clientId}] Forbindelse lukket\n");
        }
    }
}