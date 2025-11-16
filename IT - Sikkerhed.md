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
**

## Cross-Site Scripting (XSS)

Cross-Site Scripting (XSS) er en type angreb, hvor en hacker indsætter ondsindet kode (typisk JavaScript) i en webside eller webapplikation. Når en bruger besøger den side, bliver koden kørt i deres browser.

Angrebet udnytter sider, der viser brugerinput uden at rense det først — for eksempel kommentarer, beskeder eller forumindlæg.

Formålet er ofte at stjæle data (som cookies eller loginoplysninger) eller manipulere, hvad brugeren ser på siden.

### Risks of XSS Vulnerabilities

XSS-sårbarheder kan give angribere mulighed for at køre skadelig JavaScript i brugernes browsere. Det kan føre til datatyveri, ændring af webindhold eller omdirigering til skadelige sider — og kompromitterer både brugernes og websidens sikkerhed.

### Why Can XSS be Dangerous

XSS-sårbarheder opfattes ofte som mindre farlige end f.eks. SQL-injektion angreb. Ved første øjekast virker muligheden for at køre JavaScript på en webside måske ikke alvorlig, fordi browsere kører JavaScript i et kontrolleret miljø med begrænset adgang til brugerens styresystem og filer. Men JavaScript kan stadig være farligt, hvis det bruges ondsindet:

- Ondsindet JavaScript har adgang til de samme objekter som resten af websiden — herunder cookies, som ofte indeholder sessionstokens. Hvis en angriber får fat i en brugers session-cookie, kan de udgive sig for brugeren og få adgang til følsomme data.  
      
    
- JavaScript kan læse og ændre DOM’en (websidens struktur og indhold).  
      
    
- Det kan sende HTTP-forespørgsler (via XMLHttpRequest) til vilkårlige destinationer.  
      
    
- Moderne browsere tillader også adgang til HTML5-API’er, som kan give adgang til brugerens placering, kamera, mikrofon og visse filer — ofte med brugerens tilladelse, men angriberen kan narre brugeren til at give adgang (social engineering).  
      
    

I kombination med social engineering kan XSS bruges til avancerede angreb som cookie-tyveri, trojanere, keylogging, phishing og identitetstyveri. XSS kan også bruges sammen med andre angreb, f.eks. Cross-Site Request Forgery (CSRF).

### What Are the Three Types of Cross Site Scripting (XSS) Attacks

Reflekteret XSS: payload sendes via URL og reflekteres i svar; ikke gemt på serveren; kræver ofte, at offeret klikker på et link.  
Gemt/persistent XSS: payload gemmes på serveren (fx i en database) og påvirker alle, der besøger den kompromitterede side.  
DOM-baseret XSS: sker udelukkende i browseren ved DOM-manipulation; payload når ikke serveren og er sværere at opdage.

### Hvordan fungerer XSS

 Der er to trin i et typisk XSS-angreb:

1. For at få ondsindet JavaScript til at køre i en offers browser, skal en angriber først finde en måde at injicere ondsindet kode (payload) ind i en webside, som offeret besøger.
    
2. Derefter skal offeret besøge den webside, der indeholder den ondsindede kode. Hvis angrebet er målrettet mod bestemte ofre, kan angriberen bruge social engineering eller phishing til at sende et ondsindet link til offeret.  
      
    

For at trin et kan lade sig gøre, skal den sårbare hjemmeside inkludere brugerinput direkte i sine sider. Angriberen kan så indsætte en ondsindet streng, som bliver brugt i websiden og fortolket som kildekode af offerets browser. Der findes også varianter, hvor angriberen lokker brugeren til at besøge en URL via social engineering, og payload’en er en del af det link, brugeren klikker på.

### Hvordan opdager og tester man for XSS-sårbarheder

 Cross-site Scripting-sårbarheder er blandt de mest almindelige sårbarheder i webapplikationer. OWASP (Open Web Application Security Project) placerer XSS i deres OWASP Top 10 2017-dokument som det næsthyppigste problem.

Heldigvis er det let at teste, om dit website eller din webapplikation er sårbar over for XSS og andre sårbarheder ved at køre en automatiseret webscanning med en sårbarhedsscanner — for eksempel Acunetix, som indeholder en specialiseret XSS-scannermodul. Prøv en demo og læs mere om at køre XSS-scanninger mod dit website eller din webapplikation. Et eksempel på, hvordan man kan opdage såkaldte blind XSS-sårbarheder med Acunetix

### Hvordan man forhindrer XSS-angreb

For at beskytte dig mod XSS skal du rense (sanitisere) alt input. Din applikationskode må aldrig sende data, der kommer fra brugere, direkte videre til browseren uden først at tjekke for ondsindet kode.

For mere information kan du læse artiklerne Preventing XSS Attacks og How to Prevent DOM-based Cross-site Scripting. Du kan også finde nyttige retningslinjer i XSS Prevention Cheat Sheet fra OWASP-organisationen.

### Sådan forhindres Cross-site Scripting (XSS) – Bedste praksis

Det er ikke let at forhindre XSS. De konkrete teknikker afhænger af XSS-typen, hvordan brugerinput bruges, og hvilket programmeringsframework der anvendes. Der er dog nogle generelle strategier, som bør følges for at sikre din webapplikation:

1. **Træn og hold opmærksomhed ved lige**  
Alle, der bygger webapplikationen, skal være opmærksomme på risiciene ved XSS. Sørg for sikkerhedstræning til udviklere, QA, DevOps og systemadministratorer.

2. **Stol ikke på noget brugerinput**  
Alt brugerinput skal behandles som ubrugt og potentielt farligt. Risikoen for XSS er til stede, uanset om input kommer fra autentificerede brugere, interne brugere eller offentligheden.

3. **Brug escaping/encoding**  
Brug korrekt escaping afhængigt af konteksten: HTML-escape, JavaScript-escape, CSS-escape, URL-escape osv. Brug eksisterende biblioteker fremfor at skrive egne escaping-funktioner.

4. **Rens HTML**  
Hvis input skal indeholde HTML, kan du ikke escape det uden at ødelægge tags. Brug i stedet et pålideligt bibliotek til at parse og rense HTML, fx HtmlSanitizer til .NET eller SanitizeHelper til Ruby on Rails.

5. **Sæt HttpOnly-flag på cookies**  
Sæt HttpOnly-flag på cookies for at forhindre, at de kan tilgås via klient-side JavaScript, hvilket begrænser konsekvenserne af XSS.

6. **Brug Content Security Policy (CSP)**  
CSP er en HTTP-header, der specificerer, hvilke dynamiske ressourcer der må loades. Det hjælper med at begrænse effekten af eventuelle XSS-angreb.

7. **Scan regelmæssigt (fx med Acunetix)**  
XSS kan introduceres af udviklere eller tredjepartsbiblioteker. Scan jævnligt dine webapplikationer med en sårbarhedsscanner. Bruges Jenkins, kan Acunetix-pluginet automatisere scanning ved hver build.

**
### Typer af XSS: XSS-typer, eksempler og angreb

Cross-site Scripting-angreb (XSS) kan bruges af angribere til at kompromittere applikationssikkerhed på mange måder. Mest almindeligt bruges XSS til at stjæle session-cookies, hvilket giver angriberen mulighed for at udgive sig for offeret.
### Stored XSS (Persistent XSS)

- Beskrivelse: Den mest skadelige XSS-type. Angriberen injicerer ondsindet indhold (payload), typisk JavaScript, i webapplikationen. Hvis der ikke er inputvalidering, gemmes koden permanent i applikationen, fx i en database.  

- Eksempel: En angriber indsætter et skadeligt script i en blogkommentar eller et forumindlæg.  

- Hvordan det virker: Når en bruger åbner den kompromitterede side, bliver scriptet serveret som en del af HTML-koden og eksekveres i browseren.  

### Reflected XSS (Non-persistent XSS)

- Beskrivelse: Den mest almindelige type XSS. Payload’en sendes som en del af brugerens HTTP-request og reflekteres tilbage i HTTP-responsen.  

- Hvordan det virker: Angribere bruger ondsindede links, phishing-e-mails eller andre social engineering-metoder for at få offeret til at besøge linket. Scriptet kører derefter i brugerens browser.  

- Bemærkning: Reflected XSS er ikke vedvarende, så payload’en skal leveres til hvert offer individuelt.  

### DOM-baseret XSS

- Beskrivelse: Avanceret XSS-angreb, hvor klient-side scripts skriver brugerdata til Document Object Model (DOM). Hvis data håndteres forkert, kan angriberen injicere payload, som gemmes i DOM’en og eksekveres, når data læses tilbage.  

- Bemærkning: Dette angreb sker kun på klient-siden, og payload’en sendes aldrig til serveren. Det gør det svært at opdage for WAFs og sikkerhedsingeniører.  

- Ofte manipulerede DOM-objekter: document.URL, location.hash, document.referrer.


**
**

### XSS-filtrering:

- XSS kommer fra brugerinput: Alt ondsindet kode stammer fra klient-side input, fx formularer, JSON, XML-webservices eller cookies. Al ekstern data skal betragtes som ikke-pålidelig.  
      
    
- Filtrering som første forsvar: En simpel metode er at sende al ekstern data gennem et filter, der fjerner farlige tags og attributter, fx `<script>`, JavaScript-kommandoer, CSS-styles eller HTML med event-handlers.  

- Egne filtre vs. biblioteker: Mange udviklere skriver egne server-side filtre med fx PHP eller ASP, ofte med regular expressions. Dette kan fungere, men hackere kan ofte omgå simple filtre med teknikker som hex- eller Unicode-kodning, linjeskift og null-tegn.  

- Anbefalet metode: Brug velafprøvede biblioteker, som vedligeholdes løbende. Eksempler:  

- Java: OWASP Java Encoder Project  

- PHP: HTML Purifier  

- Begrænsning: Strenge filtre kan fjerne legitim tekst, fx kodeeksempler med `<script>` eller alert('…'). Hvis du vil bevare formatering, bør du kombinere filtrering med HTML-, Script- og CSS-escaping.  

Essensen:  
Brug altid pålidelige filtre eller biblioteker til at rense brugerinput, men kombiner dem med escaping-teknikker for at bevare legitim data og samtidig forhindre XSS. Filtre skal opdateres jævnligt, da XSS-teknikker hele tiden udvikler sig.

**

**

### XSS-escaping:

- Hvad er escaping?  
    Escaping fortæller browseren, at brugerdata skal behandles som ren tekst og ikke som kode. Selv hvis en angriber indsætter et ondsindet script, vil det ikke blive eksekveret, hvis escape-teknikkerne er korrekt anvendt. I HTML kan man f.eks. bruge HTML-entities som &#…; til at erstatte farlige tegn.  

- Udvidet escaping:  
    For fuld sikkerhed skal du også escape:  

- JavaScript  

- CSS (Cascading Style Sheets)  

- Nogle gange XML  

- Biblioteker hjælper:  
    Det kan være svært selv at escape korrekt i alle kontekster, derfor anbefales brug af etablerede biblioteker:  

- ESAPI (OWASP): Kan bruges med Java, .NET, PHP, Classic ASP, ColdFusion, Python og Haskell.  

- AntiXSS (Microsoft): Designet til Microsoft-teknologier, ideelt i Windows-miljøer.  

- Fordel:  
    Begge biblioteker opdateres løbende for at beskytte mod nye XSS-teknikker og holdes vedlige af eksperter med indsigt i aktuelle sikkerhedstrusler.  

Essens:  
Escaping er den vigtigste metode til at forhindre XSS. Brug pålidelige biblioteker fremfor egen kode for at sikre korrekt og opdateret beskyttelse.

**

## DOM-based XSS

Hvad det er:  
DOM-baseret XSS er en type cross-site scripting, hvor sårbarheden opstår fuldstændig på klient-siden i browserens DOM (Document Object Model). I modsætning til reflekteret eller gemt XSS findes payload’en ikke i serverens HTML-respons, men kun i DOM’en under runtime, hvilket gør den svær at opdage med almindelige server-side filtre eller WAFs.  
  

Hvordan det opstår:  
DOM-XSS opstår, når bruger-kontrollerede inputdata (kaldet source) sendes til et farligt eksekveringspunkt (sink). Almindelige sinks inkluderer document.write, innerHTML, eval, setTimeout, execScript, mens typiske sources kan være document.URL, location.hash, document.referrer, window.name osv.  
  

Eksempel:  
Hvis en side bruger document.write til at vise indhold baseret på document.baseURI eller URL-hash, kan en angriber indsætte JavaScript i URL’en (#<script>alert(1)</script>), som så eksekveres i browseren, selvom kildeteksten på serveren ikke viser payload’en.  
  

Konsekvenser:  
DOM-XSS kan udnyttes til at:  
  

- Stjæle cookies og session-tokens  

- Kapre brugerens session  

- Ændre adfærd på websiden med ondsindet kode  

- Udføre phishing eller andre sociale ingeniør-angreb  


Hvorfor server-side filtre ikke virker:  
Data efter # i URL’en sendes aldrig til serveren, så server-side validering, WAFs eller framework-beskyttelser som ASP.NET Request Validation kan ikke forhindre DOM-XSS. Dette gør det til en unik og ofte overset trussel.  
  

Forebyggelse / løsning:  
  

- Undgå farlige sinks som innerHTML, document.write og eval med bruger-input.  

- Brug sikre metoder som textContent eller innerText til at indsætte data i DOM’en.  

- Sanitér og encode data, hvor det er nødvendigt, men undgå at stole på server-side filtre alene.  

- Vær særlig opmærksom på sources, som brugeren kan kontrollere, og sørg for, at de aldrig bruges direkte i farlige sinks.  

Vigtigheden:  
DOM-baseret XSS er en reel trussel, og op til 50 % af websites kan være sårbare. Selv store webvirksomheder har haft DOM-XSS problemer, hvilket understreger behovet for korrekt sikker programmering på klient-siden.

![](data:image/png;base64,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)

  
  
**
**

## Hvad betyder # i en URL?

# kaldes fragment identifier (eller hash). Alt efter # i en URL kaldes fragment‑delen eller hash‑delen. Eksempel:

https://example.com/page.html#section2

Her er section2 fragmentet. Fragmentet bruges normalt til at scrolle til en bestemt del af en side eller til klient‑side routing i single‑page apps.

  
  

### Vigtigt: fragmentet sendes ikke til serveren

Når browseren laver en HTTP‑request, inkluderes teksten efter # aldrig i requesten. Serveren modtager kun https://example.com/page.html — fragmentet håndteres udelukkende i browseren af klient‑side kode (JavaScript).

Det betyder:

- Server‑side validering eller logging ser ikke fragmentet.  
      
    
- Server‑side filtre og WAFs kan ikke beskytte imod angreb, der bruger data i fragmentet.
    

### Praktiske sikkerhedstips når du bruger #

- Antag altid at fragmentet er kontrolleret af en angriber.  
      
    
- Brug aldrig innerHTML, document.write, eval eller lignende med ubearbejdet location.hash.  
      
    
- Foretræk textContent eller opret en TextNode for at indsætte brugerdata i DOM.  
      
    
- Hvis du skal acceptere markup, brug et velrenommeret sanitiserings‑bibliotek (fx DOMPurify).  
      
    
- Overvej en whitelist af gyldige værdier for fragmentet (fx kun tillad section1, section2 osv.).  
      
    
- Implementér CSP (Content Security Policy) for at begrænse hvad scripts kan køre.
    

## SQL Injection

SQL Injection Based on 1=1 is Always True

Look at the example above again. The original purpose of the code was to create an SQL statement to select a user, with a given user id.

If there is nothing to prevent a user from entering "wrong" input, the user can enter some "smart" input like this:

UserId: 

Then, the SQL statement will look like this:

SELECT * FROM Users WHERE UserId = 105 OR 1=1;

## XSRF Cross Site Request Forgery

Cross-Site Request Forgery (CSRF) – også kendt som Sea Surf eller XSRF – er et angreb, hvor en angriber narre offeret til at udføre handlinger på deres vegne.  
Hvor alvorligt angrebet er, afhænger af de rettigheder, som offeret har på den pågældende hjemmeside.  
Angrebet udnytter, at et website fuldstændigt stoler på en bruger, når det først har bekræftet, at brugeren er den, de udgiver sig for at være.

CSRF betragtes som en “sovende kæmpe” inden for webapplikationssikkerhed.  
Det bliver ofte ikke taget alvorligt nok, selvom det kan være et skjult og meget effektivt angreb, hvis det udføres korrekt.  
Det er også et hyppigt forekommende angreb, hvilket er grunden til, at det gentagne gange har været med på OWASP Top 10-listen.

Dog anses Cross-Site Scripting (XSS) for at være en større risiko end CSRF, fordi CSRF har en vigtig begrænsning:  
CSRF kan kun ændre tilstande (f.eks. sende en formular, ændre data) – angriberen kan ikke se eller modtage indholdet af HTTP-svaret.

  

### Hvordan fungerer det?

1. Brugeren logger ind på en legitim side (for eksempel sin netbank).  
    Den side opretter en autentificerings-cookie i browseren.  
      
    
2. Uden at logge ud, besøger brugeren en ondsindet hjemmeside.  
      
    
3. Den ondsindede side sender en skjult HTTP-anmodning (for eksempel en POST- eller GET-request) til den rigtige side — fx for at:  
      
    

- Overføre penge
    
- Ændre adgangskode
    
- Poste et opslag
    
- Slette en konto  
      
    

5. Da browseren automatisk sender cookies med anmodningen, tror den rigtige side, at handlingen kommer fra brugeren selv.  
      
    

### Hvordan beskytter man sig mod CSRF?

1. CSRF-token (anti-forfalsknings-token)
    

- Serveren genererer et unikt token for hver bruger.
    
- Tokenet skal sendes med hver formular eller API-anmodning.
    
- Serveren tjekker, at tokenet stemmer — ellers afvises anmodningen.
    
-   
    
-   
      
    

3. SameSite-cookies
    

- Sæt cookies med SameSite=Lax eller Strict, så de ikke sendes ved tredjeparts-anmodninger.  
      
    

5. Brug sikre HTTP-metoder
    

- Farlige handlinger (som at ændre data) bør kun tillades via POST, PUT eller DELETE, ikke GET.  
      
    

7. Brug CAPTCHA eller ekstra bekræftelse
    

- Især ved følsomme handlinger, som pengeoverførsler.  
      
    

9. Undgå at bruge GET-links til vigtige handlinger
    

- Fx GET /sletBruger?id=123 bør ikke bruges.
    

  

### Træn og oprethold bevidsthed

Trin 1: Træn og oprethold bevidsthed

For at holde din webapplikation sikker skal alle involverede i udviklingen være opmærksomme på risikoen forbundet med CSRF-sårbarheder.  
Du bør give passende sikkerhedstræning til alle udviklere, QA-medarbejdere, DevOps og systemadministratorer.  
Du kan starte med at henvise dem til denne side.

### Vurder risikoen

Trin 2: Vurder risikoen

CSRF-sårbarheder gælder ikke for offentligt indhold – de er kun farlige, når der kræves autentifikation.  
Derfor kan du se bort fra denne risiko, hvis dit websted kun indeholder offentligt tilgængeligt indhold.  
Men hvis du har en webapplikation med brugerlogin, skal du være ekstra opmærksom.  
Behandl CSRF som en kritisk risiko, især hvis du driver en e-handelsapplikation.

### Brug anti-CSRF tokens

Trin 3: Brug anti-CSRF tokens

Anti-CSRF tokens anses for at være den mest effektive metode til at beskytte mod CSRF-angreb.  
Brug en gennemtestet implementering som f.eks. CSRFGuard til Java eller CSRFProtector til PHP.  
Udvikl kun din egen mekanisme, hvis der ikke findes en passende løsning til dit miljø.

### Brug SameSite-cookies

Trin 4: Brug SameSite-cookies

Sæt cookie-attributten SameSite til Strict.  
Hvis det får din applikation til at holde op med at fungere korrekt, kan du sætte den til Lax, men aldrig til None.  
Ikke alle browsere understøtter SameSite-cookies endnu, men de fleste gør.  
Brug denne indstilling som ekstra beskyttelse sammen med dine anti-CSRF tokens.

### Scan regelmæssigt (med Acunetix)

Trin 5: Scan regelmæssigt (med Acunetix)

CSRF-sårbarheder kan blive introduceret af udviklere eller via eksterne biblioteker/moduler/software.  
Du bør derfor regelmæssigt scanne dine webapplikationer med et værktøj til sårbarhedsscanning, f.eks. Acunetix.  
Hvis du bruger Jenkins, bør du installere Acunetix-plugin’et for automatisk at scanne hver build.

## Open redirect

En open redirect-sårbarhed opstår, når en applikation tillader, at brugeren selv kan bestemme, hvilken URL der omdirigeres til, uden at applikationen validerer brugerens input.

Hvis input ikke kontrolleres, kan en angriber indsætte en ondsindet URL, der får en intetanende bruger til at blive omdirigeret fra et legitimt domæne til et phishing-site.

Hvordan afhjælper man en Open Redirect-sårbarhed?

Der findes flere måder at forhindre open redirects på, så sårbarheden ikke længere kan udnyttes.

En tilgang er at validere inputtet i redirect-parameteren, så kun legitime (tilladte) destinationer accepteres.  
En anden mulighed er helt at fjerne redirect-parameteren, hvis den ikke er nødvendig.

### Mulige løsninger

1. Whitelist godkendte domæner eller stier  
    – Kun tillad redirects til kendte interne sider (fx /home, /dashboard).  
    – Afvis eller ignorer eksterne URL’er.
    
2. Brug relative i stedet for absolutte URL’er  
    – Tillad kun redirects inden for samme domæne (fx /profile i stedet for https://evil.com).
    
3. Valider og rens input  
    – Kontroller, at parameteren matcher et sikkert format, og fjern mistænkelige tegn (som http://, //, \ osv.).
    
4. Brug en fast redirect-løsning  
    – Hvis der er behov for at sende brugere til eksterne sider (fx partnere), så opret et statisk redirect-kort i stedet for at tage URL’en direkte fra brugerinput.
    
5. Fjern parameteren helt  
    – Hvis redirect-funktionaliteten ikke er nødvendig, bør den fjernes for at eliminere risikoen fuldstændigt.
    

**