[[Teknologi]]


**

## Docker

Docker er en containeriserings teknologi, der gør det muligt at pakke applikationer og deres afhængigheder ind i lette, portable "containere".

Tænk på det som en slags virtuel maskine, men meget mere effektiv. Hvor en virtuel maskine kører et helt operativsystem, deler Docker-containere kernelen med host operativsystemet, hvilket gør dem hurtigere og bruger færre ressourcer.

De vigtigste fordele ved Docker:

Konsistens: Din applikation kører ens på din computer, testservere og produktion. "Det virker på min maskine"-problemet forsvinder.

Portabilitet: En Docker-container kan køre på enhver maskine, der har Docker installeret - uanset om det er Windows, Mac eller Linux.

Isolation: Hver container er isoleret fra andre, så de ikke påvirker hinanden.

Skalerbarhed: Det er nemt at starte flere instanser af samme container for at håndtere øget trafik.

Et typisk workflow med Docker:

- Du skriver en "Dockerfile" der beskriver, hvordan din applikation skal bygges
    
- Du bygger et "image" baseret på denne fil
    
- Du kører containere baseret på dit image
    

Docker bruges meget i moderne softwareudvikling, især til microservices, CI/CD pipelines og cloud-deployment. Det har revolutioneret måden, vi udvikler og implementerer software på.

Udviklere bør gemme images i et registry, som fungerer som et bibliotek af images og er nødvendigt, når man skal deploye til produktions-orkestrationsværktøjer

  

## Node js

Node.js er en JavaScript runtime-miljø som gør det muligt at køre JavaScript-kode på serveren i stedet for kun i browseren

Event-driven og asynkron programmering: Node.js bruger en non-blocking, event-driven arkitektur som gør det særligt effektivt til at håndtere mange samtidige forbindelser uden at blokere for andre operationer.

Single-threaded men skalerbar: Selvom Node.js kører på en enkelt tråd, kan det håndtere tusindvis af samtidige forbindelser effektivt gennem event loops og callbacks.

NPM (Node Package Manager): Et massivt økosystem af open source-pakker og biblioteker som gør udvikling hurtigere og mere effektiv.

Node.js er populært til at bygge web-servere, REST APIs, real-time applikationer (som chat-systemer), mikroservices og værktøjer til webudvikling. Det er særligt velegnet til I/O-intensive applikationer.

## Dockerfile

En Dockerfile er en tekstfil, der indeholder en række instruktioner til at bygge et Docker-image. Det er grundlæggende en opskrift, der fortæller Docker, hvordan det skal oprette et containerimage trin for trin.

## Hvad bruges den til?

En Dockerfile gør det muligt at:

- Automatisere oprettelsen af Docker-images
    
- Definere hvilket miljø din applikation skal køre i
    
- Sikre, at applikationen kører ens på alle maskiner
    
- Versionsstyre din infrastruktur sammen med din kode
    

## Grundlæggende struktur

En typisk Dockerfile indeholder instruktioner som:

- FROM - Definerer basis-image (f.eks. FROM ubuntu:20.04)
    
- RUN - Kører kommandoer under build-processen (f.eks. installere pakker)
    
- COPY/ADD - Kopierer filer fra din computer ind i image't
    
- WORKDIR - Sætter arbejdsmappen inde i containeren
    
- EXPOSE - Dokumenterer hvilke porte applikationen bruger
    
- CMD/ENTRYPOINT - Angiver hvilken kommando der skal køres, når containeren starter
    

Eksempel:

FROM node:18

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["node", "[server.js](http://server.js)"]

Key Dockerfile instructions.

- FROM: Sets the base image (e.g., FROM ubuntu:20.04)
    
- RUN: Executes shell commands during build time
    
- CMD: Provides default command to run at container start
    
- ENTRYPOINT: Defines a fixed command, often combined with CMD for args
    
- COPY/ADD: Copies files into the image (ADD supports URLs and archives)
    
- ENV: Sets environment variables
    
- EXPOSE: Documents which ports the container will listen on
    
- WORKDIR: Sets the working directory for following instructions
    
- VOLUME: Declares mount points for persistent or shared data
    
- ARG: Defines build-time variables, usable during RUN
    

## Docker image layer

  

Docker images er bygget op af layers (lag) - tænk på dem som gennemsigtige ark stablet ovenpå hinanden.

Hvert layer er resultatet af en instruktion i din Dockerfile. Når du bygger et image, opretter Docker et nyt read-only layer for hver instruktion som FROM, RUN, COPY, osv.

### Hvorfor er layers vigtige

1. Caching:

- Docker genbruger layers der ikke er ændret
    
- Hvis kun app.py ændres, genbruges layers 1-3
    
- Kun layer 4 (COPY) bygges igen
    

2. Deling mellem images:

- Flere images kan dele de samme base layers
    
- Sparer disk plads og download tid
    

3. Effektiv distribution:

- Kun ændrede layers uploades/downloades
    
- Første docker pull er langsom, men updates er hurtige
    

# Se alle layers docker history bofl2002/catnip - username/imagenavn  
# Mere detaljeret info docker inspect bofl2002/catnip

  

## Eksponering af porte i Docker:

- Formål: Docker bruges ofte til at køre netværkstjenester som webservere. For at gøre disse tjenester tilgængelige, giver Docker dig mulighed for at eksponere porte.
    
- Forbindelse mellem containere: Du kan oprette private netværk, hvor containere kan kommunikere med hinanden, men forbliver isolerede fra andre containere.
    
- Eksponering af porte: For at gøre en containers tjeneste tilgængelig udefra, eksponerer du en port. Det betyder, at du angiver hvilken intern port containeren lytter på, og hvilken ekstern port den skal bruge.
    
- Eksempel: Forestil dig, at du har en server inde i en container, der lytter på port 45678. Ved at eksponere denne port gør du den tilgængelig udefra på samme port (45678).
    
- Dynamiske porte: Hvis du ikke angiver en ekstern port, kan Docker vælge en for dig blandt de tilgængelige porte.
    

**