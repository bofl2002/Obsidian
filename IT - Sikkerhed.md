[[Teknologi]]


**

## Hashing

Hashing er en algoritme der tager data af vilkårlig størrelse og omdanner det til en fast længde af data (kaldet en "hash" eller "hash-værdi"). Det er som et digitalt fingeraftryk af dine data.

## Praktisk eksempel (DNA-scenariet)

Eksemplet illustrerer tydeligt fordelen:

- Uden hashing: Sammenlign 2,2 MB DNA-data med hver prøve i databasen → langsomt
    
- Med hashing: Beregn først en 128-bit hash af DNA'et, søg derefter kun efter denne korte værdi → meget hurtigere
    

## Vigtig forskel: Hashing vs. Kryptering

Kryptering kan reverseres (dekrypteres) tilbage til originalen.  
Hashing kan IKKE reverseres - det er en envejsfunktion.

## Egenskaber ved kryptografiske hash-funktioner

En god hash-funktion skal være:

1. Let at beregne - hurtigt at lave en hash
    
2. Envejs - umuligt at gå fra hash tilbage til beskeden
    
3. Deterministisk - samme input giver altid samme hash
    
4. Følsom - selv små ændringer i input giver en helt anden hash
    

  

## Sikkerhedsmodstand

En kryptografisk hash skal modstå:

- Kollisioner: At to forskellige beskeder giver samme hash
    
- Pre-image resistance: At finde en besked der matcher en given hash
    
- Second pre-image resistance: At finde en alternativ besked med samme hash som en kendt besked
    

## Anvendelser

Hashing bruges til bl.a.:

- Password-beskyttelse (gemmer hash af password, ikke passwordet selv)
    
- Data-integritet (tjekke om filer er ændret)
    
- Hurtig data-søgning (som i eksemplet)
    
- Digital signatur
    

Eksempler på hash-funktioner: SHA-256, SHA-3, BLAKE2 (MD5 nævnt i teksten er forældet og usikker).

### Forklaring af Moderne Hashing Algoritmer

Dette afsnit gennemgår de mest kendte hash-algoritmer og deres sikkerhedsstatus.

## MD-5 (Message Digest 5)

Status: Kryptografisk usikker, men stadig meget brugt

Problemer:

- Kollisionssårbar - man kan finde to forskellige beskeder med samme hash
    
- Første angreb blev offentliggjort i 1996 (mod kompressionsmetoden)
    
- I 2004 kom teoretiske angreb mod pre-image resistance, men de er for langsomme til praktisk brug
    

Konklusion: Må IKKE bruges til sikkerhedskritiske formål som certifikater eller signaturer, men kan stadig bruges til simpel data-integritet hvor sikkerhed ikke er kritisk.

## SHA-familien (Secure Hash Algorithm)

Udviklet af NIST (National Institute of Standards and Technology) som officiel amerikansk standard.

### SHA-1

- Hashstørrelse: 160 bit
    
- Designer: NSA (National Security Agency)
    
- Formål: Oprindeligt til Digital Signature Algorithm
    
- Status: Kryptografisk svag - ikke godkendt efter 2010 til de fleste sikkerhedsformål
    
- Vigtig pointe: Selvom SHA-1 er "brudt", er den stadig okay til password hashing hvis korrekt implementeret
    

### SHA-2 (nuværende standard)

En familie af sikre hash-funktioner:

- SHA-256: Bruger 32-bit ord, outputter 256 bit
    
- SHA-512: Bruger 64-bit ord, outputter 512 bit
    
- SHA-224: Afkortet version af SHA-256
    
- SHA-384: Afkortet version af SHA-512
    

Designer: Også NSA  
Status: Anses for sikker og bruges bredt i dag

### SHA-3

- Baseret på: Keccak-algoritmen
    
- Status ved tekstens skrivning: Under finalisering af NIST
    
- Keccak er en konfigurerbar funktion, og NIST arbejdede på at justere parametrene
    

Bemærk: Teksten er lidt forældet - SHA-3 blev færdiggjort og standardiseret i 2015.

## Vigtig praktisk pointe

Selvom SHA-1 er "kryptografisk brudt" betyder det ikke, at alle systemer der bruger den skal skiftes med det samme:

- Til password hashing: Stadig acceptabel hvis korrekt implementeret
    
- Til digitale signaturer/certifikater: Bør ikke bruges
    
- Kontekst og anvendelse afgør om det er et reelt sikkerhedsproblem
    

## Anbefaling i dag (2025)

- Brug SHA-2 (især SHA-256 eller SHA-512) til de fleste formål
    
- SHA-3 er også tilgængelig som moderne alternativ
    
- Undgå MD-5 og SHA-1 til sikkerhedskritiske opgaver
    

### Forklaring af Stærke Passwords

Dette afsnit forklarer hvorfor passwordlængde er kritisk for sikkerhed, og hvordan angribere forsøger at knække hashede passwords.

## Problemet med mennesker og passwords

Mennesker er dårlige til:

- At huske tilfældige tegn
    
- At generere ægte tilfældige sekvenser
    

  

Løsningen: Krav om passwords der indeholder:

- Tal
    
- Bogstaver (både store og små)
    
- Specialtegn
    
- Minimum 8 tegn
    

Dette gør det sværere at gætte/knække passwordet.

## Tre hovedangrebsmetoder mod hashede passwords

### 1. Dictionary Attack (Ordbogsangreb)

- Bruger lister af almindelige passwords, ord, navne, årstal osv.
    
- Hasher hvert ord og sammenligner med den stjålne hash-database
    
- Eksempler: "password123", "København", "2024"
    

### 2. Bruteforce (Rå-styrke angreb)

- Prøver alle mulige kombinationer af tegn
    
- Med 8 tegn fra ASCII (128 tegn): 128^8 mulige passwords
    

### 3. Rainbow Tables

- Pre-beregner alle hashes på forhånd i en database
    
- Slår derefter bare op i tabellen (meget hurtigere)
    
- Afværges med "salt" - mere om det senere sandsynligvis
    

##Passwordlængde er AFGØRENDE - Konkrete tal

Eksempel med moderne hardware (AMD Radeon 6990 GPU fra ~2011):

### 8 tegn password

- Muligheder: 128^8 ≈ 72 billiarder
    
- Enkelt GPU: ~10,3 milliarder MD-5 hashes/sekund → 80 dage
    
- 25-GPU cluster: 350 milliarder hashes/sekund → under 2 dage ⚠️
    

### 9 tegn password

- Muligheder: 128^9
    
- 25-GPU cluster: 305 dage ✓
    

### 10 tegn password

- Muligheder: 128^10
    
- 25-GPU cluster: 106 år ✓✓
    

  

## Vigtigste konklusion

Hvert ekstra tegn ganger mulighederne med 128!

Dette viser hvorfor:

- 8 tegn er MINIMUM (men egentlig for kort i dag)
    
- 12+ tegn anbefales i moderne systemer
    
- Passwordlængde er vigtigere end kompleksitet
    

## Moderne perspektiv (2025)

Hardware er blevet meget hurtigere siden teksten blev skrevet. Det betyder:

- 8-tegns passwords kan knækkes på timer/minutter i dag
    
- Anbefaling nu: minimum 12-16 tegn
    
- Eller brug password managers til at generere lange, tilfældige passwords
    

### Egenskaber ved Password Hashing

Nu kommer vi til de specifikke krav for password hashing - som er forskellige fra generel kryptografisk hashing!

## De tre kritiske egenskaber

### 1. Unikt Salt per Password

Hvad er salt?

- En tilfældig værdi der tilføjes til passwordet før hashing
    
- Eksempel: hash(password + salt) i stedet for bare hash(password)
    

Hvorfor er det kritisk?

- Forhindrer Rainbow Tables: Pre-beregnede hash-tabeller bliver ubrugelige
    
- Forhindrer identiske hashes: To brugere med samme password ("password123") får forskellige hashes
    
- Én kompromittering ≠ alle kompromitteret: Hvis angriberen knækker ét password, hjælper det ikke med de andre
    

Regel:

- Hvert password skal have sit eget, unikke salt
    
- Saltet må aldrig genbruges på tværs af hele databasen
    
- Saltet gemmes typisk sammen med hashen (det er ikke hemmeligt, bare unikt)
    

### 2. Hurtig på Software (enkelt kørsel)

Når en legitim bruger logger ind:

- Systemet skal kunne verificere passwordet hurtigt
    
- Én hash-beregning skal tage millisekunder, ikke sekunder
    
- Dårlig brugeroplevelse hvis login tager 10 sekunder!
    

### 3. Langsom på Hardware (parallel eksekvering)

Dette er det smarte trick:

For angribere der prøver millioner af passwords samtidig:

- Funktionen skal være svær at parallelisere
    
- Skal være ressourcekrævende (hukommelse/CPU)
    
- Dette gør bruteforce-angreb uforholdsmæssigt dyre
    

Hvordan?

- Brug algoritmer der kræver meget RAM (hukommelse)
    
- Moderne GPU'er er gode til simple beregninger, men dårlige til hukommelseskrævende opgaver
    
- Dette er hvorfor bcrypt, scrypt og Argon2 er designet til at være "memory-hard"
    

## Forskellen fra almindelig hashing (SHA-256 osv.)

|   |   |   |
|---|---|---|
|Egenskab|Almindelig Hash (SHA-256)|Password Hash (bcrypt/Argon2)|
|Hastighed|Så hurtig som muligt|Bevidst langsom|
|Salt|Ofte ikke nødvendigt|Absolut påkrævet|
|Hardware-modstand|Nem at parallelisere|Svær at parallelisere|
|Formål|Data-integritet|Beskytte passwords|

## Eksempel på hvorfor salt er kritisk

Uden salt:

Bruger A: "password123" → hash: abc123...

Bruger B: "password123" → hash: abc123... (identisk!)

Bruger C: "password123" → hash: abc123... (identisk!)

  

→ Angriberen ser med det samme at mange har samme password!

Med unikt salt:

Bruger A: "password123" + salt_a → hash: xyz789...

Bruger B: "password123" + salt_b → hash: def456...

Bruger C: "password123" + salt_c → hash: mno012...

  

→ Alle hashes er unikke, selvom passwordet er det samme!

## Konklusion

Password hashing handler om at gøre det økonomisk urentabelt for angribere at bruteforce passwords, selv når de har stjålet hele databasen. Det er en balance mellem brugervenlig hastighed og angriber-fjendtlig langsomhed.

### Salt og Pepper - Forklaring

Dette afsnit går i dybden med salt og introducerer konceptet pepper.

## Salt - Detaljeret forklaring

### Hvad er salt?

- En ikke-hemmelig, unik værdi per password
    
- Tilføjes til passwordet før hashing: hash(password + salt)
    
- Gemmes åbent i databasen sammen med hashen
    

### Vigtige egenskaber ved salt

1. Skal være unikt i databasen

- Hver bruger skal have sit eget salt
    
- Behøver ikke være kryptografisk tilfældigt - bare unikt
    
- Selv simple tællere (1, 2, 3...) ville fungere rent teknisk (men tilfældigt er bedre praksis)
    

2. Må ALDRIG være bruger-leveret information ❌ Forkert: Brug email, brugernavn eller ID som salt

Hvorfor ikke?

Database A: hash(password + "john@example.com")

Database B: hash(password + "john@example.com")

→ Samme hash hvis samme password bruges!

  

To forskellige applikationer ville give samme hash for samme bruger → angribere kan genbruge arbejde på tværs af databaser.

### Salt's effekt på bruteforce-angreb

Uden salt (fra tidligere eksempel):

- 25-GPU cluster knækker hele databasen på 2 dage
    
- Alle passwords knækkes i én kørsel
    

Med unikt salt per password:

- Samme cluster skal køre 2 dage PER password
    
- 1000 brugere = 2000 dage (~5,5 år) samlet tid
    
- I praksis ~1 dag per password (statistisk set finder man det før alle kombinationer er prøvet)
    

### Salt forhindrer Rainbow Tables

Rainbow Table: Gigantisk pre-beregnet database

"password" → hash_1

"123456"   → hash_2

"qwerty"   → hash_3

... milliarder af entries

  

Med salt: Angriberen skal lave en ny Rainbow Table for hvert salt = uoverkommeligt!

## Pepper - Den hemmelige krydderi

### Hvad er pepper?

En hemmelig nøgle der:

- Gemmes adskilt fra databasen (f.eks. i konfigurationsfil, hardware security module)
    
- Omdanner hash-funktionen til en MAC (Message Authentication Code)
    
- Ofte implementeret som HMAC (Hash-based Message Authentication Code)
    

### Forskellen på salt og pepper

|   |   |   |
|---|---|---|
|Egenskab|Salt|Pepper|
|Hemmelighed|Nej (public)|Ja (secret key)|
|Placering|I databasen|Separat/sikker lokation|
|Unikt per password|Ja|Nej (samme for alle)|
|Formål|Forhindre Rainbow Tables|Ekstra lag hvis DB kompromitteres|

### HMAC vs almindelig hash

Almindelig hash: hash(password + salt)

HMAC/Pepper:     HMAC(key, password + salt)

  

Uden nøglen kan angriberen ikke reproducere hashen, selv hvis de kender algoritmen, passwordet og saltet!

### Problem med pepper - begrænset beskyttelse

Teoretisk fordel:

- Hvis angriber kun får database-dump → kan ikke knække passwords uden pepper-nøglen
    

Praktisk problem:

1. Harddisk-adgang: Hvis angriber har database, har de ofte også filsystemet (hvor nøglen ligger)
    
2. Hukommelse: I avancerede angreb kan de få fat i nøglen fra RAM
    
3. Kompromitteret applikation: Hvis hele serveren er overtaget, hjælper pepper ikke
    

Konklusion om pepper:

- Kan tilføje et ekstra lag, men må ikke erstatte ordentlig password-hashing (bcrypt/Argon2)
    
- Kun værdifuld hvis nøglen faktisk kan holdes adskilt (HSM, separat server)
    
- Salt er kritisk, pepper er "nice to have"
    

## Vigtigste pointer

1. Salt er obligatorisk - intet moderne system bør være uden
    
2. Salt skal være unikt - aldrig genbruges
    
3. Salt er ikke hemmeligt - gemmes åbent i databasen
    
4. Pepper er valgfrit - kun nyttigt hvis rigtigt implementeret
    
5. Salt gør bruteforce lineært dyrere - fra "alle på én gang" til "én ad gangen"
    

Dette er fundamentet for hvorfor moderne password-hashing-algoritmer altid inkluderer automatisk salt-håndtering!

  

### Hastighed - Hvorfor almindelige hash-funktioner er uegnede til passwords

Dette er en kritisk pointe som ofte misforstås!

## Hovedproblemet: For hurtige!

Alle disse algoritmer er designet til at være hurtige:

- MD-5
    
- SHA-1
    
- SHA-2 (SHA-256, SHA-512)
    
- SHA-3 (Keccak)
    

Hvorfor er det et problem?

- Hurtig for legitime brugere = hurtig for angribere
    
- En moderne GPU kan lave milliarder af SHA-256 hashes per sekund
    
- Perfekt til data-integritet, katastrofalt til passwords
    

## Den store misforståelse om MD-5

❌ Forkert tro: "MD-5 er dårlig til passwords pga. kollisioner"

✅ Sandheden: "MD-5 er dårlig til passwords fordi den er for hurtig"

Kollisioner er ikke relevant for passwords:

- En kollision betyder to forskellige inputs giver samme output
    
- For passwords er problemet at angriberen kan teste milliarder af gæt i sekundet
    
- Pre-image resistance (kan ikke gå fra hash til password) er stadig intakt
    

## Misforståelsen om SHA-3

Mange tænker: "SHA-3 er den nyeste → den må være bedst til passwords"

Virkeligheden:

- Keccak (SHA-3) blev designet til at være ekstremt hurtig
    
- Det var et designmål (for data-integritet)
    
- Dette gør den totalt uegnet til password-hashing
    
- Nyere ≠ bedre til passwords!
    

## Hardware-specifikke problemer

Forskellige hash-funktioner er optimeret til forskellig hardware:

### MD-5, SHA-1, SHA-256 (SHA-224)

- Bruger 32-bit operationer
    
- ⚡ Ekstremt hurtig på:
    

- x86 CPU'er (almindelige computere)
    
- ARM processorer (smartphones, tablets)
    
- GPU'er (det værste - perfekt til parallel bruteforce!)
    

### SHA-512 (SHA-384)

- Bruger 64-bit aritmetik
    
- 🐌 Lidt langsommere på:
    

- GPU'er (mindre optimeret)
    
- 32-bit ARM systemer
    

- Men stadig alt for hurtig til passwords
    

### SHA-3 (Keccak)

- Bruger kun boolean operationer (AND, OR, XOR, NOT)
    
- ⚡⚡ Ekstremt hurtig på:
    

- Alle platforme
    
- FPGA'er (Field-Programmable Gate Arrays) - ingen carry propagation
    

- Specialiseret hardware kan lave disse operationer sindssygt hurtigt
    

## Konsekvensen

Ingen af disse algoritmer bør bruges direkte til password-hashing!

Selv med salt bliver de knækket for hurtigt:

SHA-256 med salt: Stadig milliarder af forsøg/sekund

bcrypt med salt:  Tusinder af forsøg/sekund

→ Faktoren er millioner!

  

## Løsningen (preview)

Teksten nævner PBKDF2 som én mulig løsning:

- Password-Based Key Derivation Function 2
    
- Gentager hash-funktionen mange tusinde gange
    
- Gør selv hurtige funktioner langsommere
    

Men (som vi sikkert ser senere):

- Moderne alternativer som bcrypt, scrypt og Argon2 er bedre
    
- De er designet specifikt til password-hashing
    
- De har indbygget modstand mod hardware-acceleration
    

## Vigtigste læring

🎯 Ikke alle hash-funktioner er egnede til passwords!

- Hurtig hashing er godt for filer, checksums, integritet
    
- Hurtig hashing er katastrofalt for passwords
    
- Kollisionsresistens er irrelevant for passwords
    
- Hastighed (eller mangel på samme) er altafgørende
    

Husk: Når nogen siger "vi bruger SHA-256 til passwords", så ved du nu at det er en sikkerhedsrisiko - uanset hvor "moderne" det lyder!


**

### Kryptering

Kryptering er en metode til at beskytte information ved at omdanne den til en form, som kun kan læses af dem, der har den rette nøgle til at dekryptere den.

Kort fortalt:  
Kryptering = at gøre data ulæselige for uvedkommende.  
Dekryptering = at gøre data læselige igen for dem, der har nøglen.

  

### Caesar cipher

Caesar cipher er en enkel krypteringsmetode, hvor hvert bogstav i teksten flyttes et bestemt antal pladser frem i alfabetet.

🔹 Eksempel (skift = 3):  
HELLO → KHOOR

For at dekryptere flytter man bogstaverne 3 tilbage.  
Den er nem at forstå — men også nem at bryde, fordi der kun findes 25 mulige skift.

  

### Polyalphabetic cipher

En polyalphabetisk cipher er en krypteringsmetode, hvor man bruger flere forskellige alfabeter til at kryptere teksten — i stedet for kun ét, som i Caesar cipher.

Man bruger et nøgleord til at bestemme skiftene.  
Hvis nøgleordet er "KEY" og teksten er "HELLO", gentages nøgleordet over teksten:

Tekst:  H  E  L  L  O  
Nøgle:  K  E  Y  K  E

Hvert bogstav i nøgleordet bestemmer, hvor meget man flytter hvert bogstav i teksten.

Kort sagt: En polyalphabetisk cipher = flere skift → mere sikker end Caesar cipher.

### The one-time pad

En one-time pad (på dansk: engangsnøgle) er en krypteringsmetode, der er teoretisk umulig at bryde, hvis den bruges korrekt.

### Sådan virker den:

1. Du har en besked (klartekst).  
      
    
2. Du har en tilfældig nøgle, som er lige så lang som beskeden.  
      
    
3. Hvert bogstav (eller bit) i beskeden kombineres med det tilsvarende bogstav/bit i nøglen — typisk ved hjælp af XOR (en logisk operation).
    

For at dekryptere, bruger man den samme nøgle igen — og får originalteksten tilbage.

One-time pad er den sikreste form for kryptering — men også den mest besværlige at bruge.

  

### Perfect secrecy

Perfect secrecy (perfekt sikkerhed) er et begreb inden for kryptering, der betyder, at en krypteret besked giver ingen information om den originale besked, uanset hvor meget angriberen ved eller hvor mange ressourcer de har.

- Hvis et krypteringssystem har perfekt sikkerhed, kan ingen gætte klarteksten bedre end ved tilfældighed, selvom de har adgang til krypteret tekst.
    
- Det sikreste eksempel på perfekt sikkerhed er one-time pad (engangsnøgle).
    

Perfect secrecy = umuligt at bryde krypteringen, så længe reglerne overholdes.

### Pseudorandom number generators

Pseudorandom number generators (PRNGs) er algoritmer, der genererer tal, som ser tilfældige ud, men som i virkeligheden er deterministiske — altså kan gentages, hvis man kender startværdien (seed).

### Forklaring:

- PRNG’er bruges til at simulere tilfældige tal, når ægte tilfældighed er svær at få.  
      
    
- De starter med en seed (startværdi), og beregner derefter en sekvens af tal, der ser tilfældige ud.  
      
    
- Samme seed giver samme sekvens, så de ikke er “ægte” tilfældige tal.  
      
    

### Anvendelser:

- Kryptering (til nøglegenerering, initialisering af algoritmer)  
      
    
- Computerspil (til tilfældige hændelser)  
      
    
- Simulationer og statistik
    

PRNG’er er ikke sikre nok til perfekt sikker kryptering, medmindre de bruges sammen med andre sikkerhedsmekanismer. Til virkelig sikker kryptering bruger man truly random number generators (TRNGs) eller en one-time pad.

PRNG = algoritme, der laver “tilfældige” tal, som i virkeligheden kan reproduceres.

**

**

### XOR bitwise operation

  

XOR står for "Exclusive OR" (eksklusiv ELLER på dansk). Det er en matematisk operation, der arbejder på individuelle bits i binære tal.

#### Grundlæggende princip

XOR sammenligner to bits ad gangen og følger denne simple regel:

Hvis de to bits er forskellige, bliver resultatet 1. Hvis de er ens, bliver resultatet 0.

Det er altså "enten-eller" - enten den ene ELLER den anden skal være 1, men ikke begge samtidig.

#### Hvordan det fungerer i praksis

Lad os sige du har to tal: 5 og 3.

Først skal vi konvertere dem til binær form:

1. Kan vi bruge en 8'er? Nej, 8 er større end 5 → skriv **0**  
2. Kan vi bruge en 4'er? Ja, 4 passer ind i 5 → skriv **1** (vi har nu brugt 4, mangler 1)  
3. Kan vi bruge en 2'er? Nej, vi har kun 1 tilbage → skriv **0**  
4. Kan vi bruge en 1'er? Ja, præcis hvad vi mangler → skriv **1**

- 5 bliver til 0101
    
- 3 bliver til 0011
    

Nu sammenligner XOR hver bit-position fra højre mod venstre:

Første bit (længst til højre): 1 og 1 - de er ens, så resultatet er 0

Anden bit: 0 og 1 - de er forskellige, så resultatet er 1

Tredje bit: 1 og 0 - de er forskellige, så resultatet er 1

Fjerde bit: 0 og 0 - de er ens, så resultatet er 0

Det endelige resultat bliver derfor: 0110, som er 6 i decimal notation.

#### Hvorfor er XOR nyttigt?

XOR har nogle særlige egenskaber, der gør den utrolig anvendelig:

1. Reversibilitet: Hvis du XOR'er et tal A med et tal B for at få C, kan du få A tilbage ved at XOR'e C med B igen. Dette gør den perfekt til simpel kryptering.
    
2. Nulstilling: Når du XOR'er et tal med sig selv, får du altid 0. Dette bruges til at finde unikke elementer i lister.
    
3. Identitet: Når du XOR'er et tal med 0, får du det originale tal tilbage uændret.
    
4. Bit-vending: Du kan bruge XOR til at skifte specifikke bits mellem 0 og 1.
    

#### Hverdagsmetafor

Tænk på XOR som et lys med to kontakter. Lyset tændes kun når præcis én af kontakterne er tændt. Hvis begge er tændt eller begge er slukket, er lyset slukket. Det er "eksklusivt" - kun den ene situation giver lys.

### AND operator

AND er en binær bitwise operation, der sammenligner to bits ad gangen og følger denne simple regel:

Resultatet bliver kun 1 hvis BEGGE bits er 1. Ellers bliver resultatet 0.

Først konverterer vi til binær:  
- 5 bliver til 0101  
- 3 bliver til 0011  
Nu sammenligner AND hver bit-position:  
5 AND 3  
  0101 (5 i binær)  
∧ 0011 (3 i binær)  
------  
  0001 (1 i decimal)

  

### OR operator

OR er en binær bitwise operation, der sammenligner to bits ad gangen og følger denne simple regel:

Resultatet bliver 1 hvis MINDST ÉN af de to bits er 1. Resultatet bliver kun 0 hvis begge bits er 0.

Først konverterer vi til binær: 

- 5 bliver til 0101  
- 3 bliver til 0011 

Nu sammenligner OR hver bit-position:  
5 OR 3  
  0101 (5 i binær)  
∨ 0011 (3 i binær)  
------ 

   0111 (7 i decimal)

  

### Derfor skal man bruge XOR.

AND har en 75% chance for at give 0 som output og en 25% chance for at give 1 som output. Mens OR har en 25% chance for at give 0 som output og 75% chance for at give 1 som output. XOR operationen har derimod 50% chance for at give enten 0 eller 1 som output.

**
**

## Public Key Cryptography (Offentlig Nøgle Kryptografi)

Public key cryptography, også kaldet asymmetrisk kryptografi, er et kryptografisk system der bruger to forskellige nøgler: en offentlig nøgle og en privat nøgle.

### Grundprincippet

I modsætning til traditionel kryptering (symmetrisk), hvor samme nøgle bruges til både at kryptere og dekryptere, fungerer public key cryptography sådan:

- Offentlig nøgle (public key): Kan deles frit med alle. Bruges til at kryptere beskeder.
    
- Privat nøgle (private key): Holdes hemmelig. Bruges til at dekryptere beskeder.
    

### Hvordan det virker - Simpel analogi

Forestil dig en postkasse:

- Offentlig nøgle = postkassen med en åbning i toppen. Alle kan putte breve i (kryptere beskeder).
    
- Privat nøgle = nøglen til postkassen. Kun ejeren kan åbne den og læse brevene (dekryptere beskeder).
    

### Praktisk eksempel

Alice vil sende en hemmelig besked til Bob:

1. Bob genererer et nøglepar: en offentlig og en privat nøgle
    
2. Bob deler sin offentlige nøgle med Alice (og hele verden om nødvendigt)
    
3. Alice krypterer sin besked med Bobs offentlige nøgle
    
4. Alice sender den krypterede besked til Bob
    
5. Bob bruger sin private nøgle til at dekryptere beskeden
    
6. Kun Bob kan læse beskeden, selv hvis andre fanger den
    

  

## The Discrete Logarithm (Den Diskrete Logaritme)

Den diskrete logaritme er et matematisk problem der danner grundlaget for mange public key kryptografi-systemer. Det er et "envejsproblem" - nemt at beregne i én retning, men ekstremt svært at vende tilbage.

## Almindelig logaritme (til sammenligning)

Først, hvad er en normal logaritme?

Hvis vi har: a^x = b

Så er: x = log_a(b)

Eksempel: 2^3 = 8, derfor er log_2(8) = 3

## Diskret logaritme - hvad er forskellen?

Den diskrete logaritme fungerer på samme måde, men indenfor modulo aritmetik (resten ved division).

Formlen er: g^x ≡ h (mod p)

Hvor:

- g = generator (et basistal)
    
- x = den hemmelige eksponent (det vi vil finde)
    
- h = resultatet
    
- p = et stort primtal (modulus)
    
- ≡ betyder "kongruent med" (har samme rest)
    

Lad os bruge små tal for at forstå konceptet:

g = 3, p = 17

Lad os beregne forskellige potenser af 3 modulo 17:

3^1 mod 17 = 3

3^2 mod 17 = 9

3^3 mod 17 = 27 mod 17 = 10

3^4 mod 17 = 81 mod 17 = 13

3^5 mod 17 = 243 mod 17 = 7

3^6 mod 17 = 729 mod 17 = 4

...

### Frem-retningen (let)

Hvis jeg beder dig om: "Hvad er 3^5 mod 17?"

- Du beregner: 3^5 = 243
    
- Så finder du resten: 243 ÷ 17 = 14 rest 7
    
- Svar: 7
    

### Konkret eksempel med små tal

Offentlige værdier: p = 23, g = 5

Alice's hemmelighed: a = 6

- Alice beregner: A = 5^6 mod 23 = 15625 mod 23 = 8
    
- Alice sender 8 til Bob
    

Bob's hemmelighed: b = 15

- Bob beregner: B = 5^15 mod 23 = 30517578125 mod 23 = 19
    
- Bob sender 19 til Alice
    

Fælles nøgle:

- Alice beregner: K = 19^6 mod 23 = 47045881 mod 23 = 2
    
- Bob beregner: K = 8^15 mod 23 = 35184372088832 mod 23 = 2
    

Begge har K = 2 som fælles hemmelig nøgle!

En angriber ser kun: p=23, g=5, A=8, B=19

- Men kan ikke effektivt finde a eller b for at beregne K
    

## Diffie-hellman key exchange

## Setup

Offentlige værdier (alle kan se):

- p = 23 (primtal)
    
- g = 5 (generator)
    

---

## Alice's trin

1. Vælger hemmeligt tal: a = 6
    
2. Beregner: A = 5^6 mod 23 = 8
    
3. Sender 8 til Bob (offentligt)
    

---

## Bob's trin

1. Vælger hemmeligt tal: b = 15
    
2. Beregner: B = 5^15 mod 23 = 19
    
3. Sender 19 til Alice (offentligt)
    

---

## Fælles nøgle

Alice modtager 19:

- K = 19^6 mod 23 = 2
    

Bob modtager 8:

- K = 8^15 mod 23 = 2
    

✓ Begge har K = 2 som fælles hemmelighed!

---

## Hvad ser angriberen?

Eve kan se: p=23, g=5, 8, 19

Eve kan IKKE finde: a=6 eller b=15 (diskret logaritme - umuligt med store tal)

Eve kan IKKE beregne: K=2 (uden at kende a eller b)

  

## RSA encryption

RSA er den mest kendte public key krypterings-algoritme, opfundet i 1977 af Ron Rivest, Adi Shamir og Leonard Adleman.

### Grundprincippet

RSA bruger to forskellige nøgler:

- Offentlig nøgle (e, n): Bruges til at kryptere - kan deles med alle
    
- Privat nøgle (d, n): Bruges til at dekryptere - holdes hemmelig
    

Sikkerheden bygger på at det er ekstremt svært at faktorisere store tal (opdele dem i primfaktorer).

  

![](data:image/png;base64,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)

  

  

## Nøglegenering (Bob)

Vælg primtal:

- p = 61, q = 53
    

Beregn:

- n = 61 × 53 = 3233
    
- φ(n) = 60 × 52 = 3120
    
- e = 17 (offentlig eksponent)
    
- d = 2753 (privat eksponent, hvor 17 × 2753 mod 3120 = 1)
    

Nøgler:

- Offentlig nøgle: (17, 3233) - deler med alle
    
- Privat nøgle: (2753, 3233) - holder hemmelig
    

---

## Kryptering (Alice sender til Bob)

Besked: m = 65

Krypter med Bobs offentlige nøgle:

- c = 65^17 mod 3233 = 2790
    

Sender: 2790 til Bob

---

## Dekryptering (Bob)

Modtager: c = 2790

Dekrypter med sin private nøgle:

- m = 2790^2753 mod 3233 = 65
    

✓ Original besked genoprettet!

---

## Hvorfor er det sikkert?

Angriber ser:

- Offentlig nøgle: (17, 3233)
    
- Krypteret: 2790
    

For at dekryptere skal angriber:

- Finde d = 2753
    
- Det kræver faktorisering af 3233 = 61 × 53
    
- Med store tal (2048-bit) tager det millioner af år!
    

  

## Euler's Totient Function φ(n)

Euler's totient function, skrevet φ(n) (udtales "fi af n"), tæller hvor mange positive heltal der er mindre end eller lig med n, som er relativt primiske med n.

## Hvad betyder "relativt primisk"?

To tal er relativt primiske (coprime) hvis deres største fælles divisor er 1.

Eksempler:

- 8 og 15 er relativt primiske: GCD(8,15) = 1 ✓
    
- 8 og 12 er IKKE relativt primiske: GCD(8,12) = 4 ✗
    

---

## Simple eksempler

### φ(8) = ?

Tal mindre end 8: 1, 2, 3, 4, 5, 6, 7

Hvilke er relativt primiske med 8?

- 1: GCD(1,8) = 1 ✓
    
- 2: GCD(2,8) = 2 ✗
    
- 3: GCD(3,8) = 1 ✓
    
- 4: GCD(4,8) = 4 ✗
    
- 5: GCD(5,8) = 1 ✓
    
- 6: GCD(6,8) = 2 ✗
    
- 7: GCD(7,8) = 1 ✓
    

φ(8) = 4 (tallene 1, 3, 5, 7)

---

### φ(10) = ?

Tal mindre end 10: 1, 2, 3, 4, 5, 6, 7, 8, 9

Relativt primiske med 10:

- 1: GCD(1,10) = 1 ✓
    
- 2: GCD(2,10) = 2 ✗
    
- 3: GCD(3,10) = 1 ✓
    
- 4: GCD(4,10) = 2 ✗
    
- 5: GCD(5,10) = 5 ✗
    
- 6: GCD(6,10) = 2 ✗
    
- 7: GCD(7,10) = 1 ✓
    
- 8: GCD(8,10) = 2 ✗
    
- 9: GCD(9,10) = 1 ✓
    

φ(10) = 4 (tallene 1, 3, 7, 9)

---

## Formler (lette genveje)

### Hvis n er et primtal

φ(p) = p - 1

Eksempler:

- φ(7) = 6 (alle tal 1-6 er relativt primiske med 7)
    
- φ(13) = 12
    
- φ(61) = 60
    

Hvorfor? Primtal deler kun 1 og sig selv, så alle andre tal er relativt primiske.

---

### Hvis n = p × q (to primtal)

φ(p × q) = (p-1) × (q-1)

Dette bruges i RSA!

Eksempel:

- n = 15 = 3 × 5
    
- φ(15) = (3-1) × (5-1) = 2 × 4 = 8
    

Verificering: Tal relativt primiske med 15: 1, 2, 4, 7, 8, 11, 13, 14 = 8 tal ✓

---

### Hvis n = p^k (potens af primtal)

φ(p^k) = p^k - p^(k-1)

Eksempel:

- φ(8) = φ(2³) = 2³ - 2² = 8 - 4 = 4 ✓
    
- φ(9) = φ(3²) = 3² - 3¹ = 9 - 3 = 6
    

---

## RSA eksempel (hvorfor det er vigtigt)

Bob genererer RSA nøgler:

1. Vælg primtal: p = 61, q = 53
    
2. Beregn: n = 61 × 53 = 3233
    
3. Beregn: φ(n) = (61-1) × (53-1) = 60 × 52 = 3120
    
4. Vælg e = 17
    
5. Find d hvor: 17 × d mod 3120 = 1 → d = 2753
    

Uden φ(n) kan man ikke finde d!

Angriberen kender n = 3233, men for at finde φ(n) skal de faktorisere n til 61 × 53 - hvilket er svært med store tal!

---

## Flere eksempler

|   |   |   |   |
|---|---|---|---|
|n|Faktorisering|φ(n)|Beregning|
|5|5 (prim)|4|5-1|
|12|2² × 3|4|φ(4) × φ(3) = 2 × 2|
|15|3 × 5|8|(3-1)(5-1) = 2×4|
|21|3 × 7|12|(3-1)(7-1) = 2×6|
|33|3 × 11|20|(3-1)(11-1) = 2×10|

---

## Vigtige egenskaber

1. Hvis p er primtal: φ(p) = p - 1  
      
    
2. Multiplikativ: Hvis GCD(m,n) = 1, så φ(m×n) = φ(m) × φ(n)  
      
    
3. Sum egenskab: Summen af φ(d) for alle divisorer d af n er lig med n  
      
    
4. Euler's teorem: Hvis GCD(a,n) = 1, så a^φ(n) ≡ 1 (mod n)  
      
    

---

## Praktisk anvendelse i RSA

Hvorfor φ(n) er kritisk:

Offentligt: n = 3233, e = 17

Hemmeligt: φ(n) = 3120, d = 2753

  

For at finde d skal man kende φ(n)

For at finde φ(n) skal man faktorisere n

Faktorisering af store n er praktisk umuligt!

  

Dette er hele sikkerheden i RSA!

  

---

## Opsummering

φ(n) i én sætning: Tæller hvor mange tal mindre end n der ikke deler nogen fælles faktorer med n.

Nøgleformler:

- φ(primtal p) = p - 1
    
- φ(p × q) = (p-1) × (q-1) ← bruges i RSA
    

I RSA: φ(n) er hemmeligheden der gør det muligt at finde den private nøgle - uden faktorisering af n er φ(n) umulig at finde!

  
  
  
  

|   |   |
|---|---|
|Alice|Bob|
|P1 = 53<br><br>P2 = 59<br><br>n = 53*59<br><br>n = 3127|m = 89 (Bobs valg)<br><br>e = 3<br><br>Mod 3127|
|FI(n) = 3016    (P1-1 * P2-1)<br><br>e = 3                (vælg lille eksponent)<br><br>d = 2011          (2*(3016) +1 / 3)|c = 89^3 mod 3127 = 1394|
|n & e = public key -> sendes til bob|c sendes til Alice|
|Alice dekryptere med <br><br>d = 2011<br><br>c^d = 1394^2011mod 3127 = 89||

  
**