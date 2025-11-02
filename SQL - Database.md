[[Teknologi]]


**Database forbindelse**
"ConnectionStrings": {

    "MyDBConnection": "Server=localhost\\SQLEXPRESS;Database=SomeDatabase;Trusted_Connection=True;TrustServerCertificate=true;"

**I MVC (program.cs)**
builder.Services.AddDbContext<DiveDeepContext>(options =>
 {
     options.UseSqlServer(builder.Configuration.GetConnectionString("DiveDeepConnection"));
 });





**I Repositories (MVVM)**

IConfigurationRoot config = new ConfigurationBuilder()

            .AddJsonFile("appsettings.json")

            .Build();

        xxxx = new List<xxxx>();

        ConnectionString = config.GetConnectionString("MyDBConnection");


**

**Tabel:** en struktureret samling af data, organiseret i rækker og kolonner, hvor hver kolonne repræsenterer en bestemt type data, og hver række indeholder en enkelt post.

**Relation:** Multiplicitet mellem tabellerne

**Relationsskema:** Et relationsskema i SQL beskriver, hvordan tabellerne i en relationel database er organiseret og forbundet. Det viser tabellernes navne, deres kolonner og de relationer, der findes mellem dem via primærnøgler (PK) og fremmednøgler (FK).

**Database:** En database er en organiseret samling af data, der gør det muligt at lagre, hente og administrere information effektivt.

**Relationel database:** En relationel database (RDB – Relational Database) er en type database, der organiserer data i tabeller (relationer), hvor rækker repræsenterer individuelle poster, og kolonner definerer attributter. Tabellerne forbindes via nøgler (keys), hvilket gør det muligt at undgå redundans og sikre dataintegritet.

**Relationelt databaseskema:** Et relationelt databaseskema er en model, der viser strukturen i en relationel database. Det beskriver tabeller, deres kolonner og de relationer, der findes mellem dem via primærnøgler (PK) og fremmednøgler (FK).

**Primærnøgle:** En primærnøgle (PK) er en kolonne (eller en kombination af kolonner) i en tabel, der entydigt identificerer hver række.

**Fremmednøgle:** En fremmednøgle (FK) er en kolonne eller en kombination af kolonner, der refererer til primærnøglen i en anden tabel. Den bruges til at forbinde tabeller og sikre referentiel integritet i en relationel database.

**Sammensat nøgle:** En sammensat nøgle (Composite Key) er en primærnøgle, der består af flere kolonner i stedet for én enkelt kolonne. Den bruges, når ingen enkelt kolonne entydigt kan identificere en række, men en kombination af flere kolonner kan. 

**Kandidatnøgle:** En kandidatnøgle er en kolonne (eller en kombination af kolonner), der entydigt identificerer en række i en tabel og kan bruges som primærnøgle.

**En til mange (1:M):** En En-til-Mange (1:M) relation opstår, når en enkelt post i én tabel kan have mange relaterede poster i en anden tabel, men hver post i den anden tabel kun er relateret til én post i den første tabel.

**En til en (1:1):** En En-til-En (1:1) relation opstår, når en post i én tabel kun kan være relateret til én post i en anden tabel, og omvendt. Dette betyder, at hver række i den første tabel kun kan have én matchende række i den anden tabel.

**Mange til mange (M:M):** En Mange-til-Mange (M:N) relation opstår, når flere poster i én tabel kan være relateret til flere poster i en anden tabel. Dette kræver en mellem-tabel for at håndtere relationen mellem de to tabeller.

  

SQL - Structured Query Language

SQL-statement  
En SQL-statement (Structured Query Language statement) er en kommando, der bruges til at interagere med en database. SQL-statements kan udføre forskellige operationer som at hente data, indsætte nye data, opdatere eksisterende data og slette data.

Auto-Increment  
SQL bruges auto-increment til at generere en unik værdi automatisk, typisk for en primær nøgle (f.eks. Id-kolonnen). Det betyder, at du ikke behøver selv at angive værdien – databasen sørger for at tælle op for dig.

SQL-betingelse  
En SQL-betingelse bruges til at specificere kriterier, som data skal opfylde for at blive inkluderet i en forespørgsel. Betingelser bruges ofte i WHERE-klause og kan kombinere flere kriterier ved hjælp af logiske operatorer som AND, OR, og NOT. 

DML  
DML står for Data Manipulation Language og er en del af SQL, der bruges til at manipulere data i en database. SQL-kommandoer, som bruges til at indsætte, opdatere, slette og hente data i en database. DML fokuserer altså på at arbejde med selve indholdet i tabellerne.

SQL Connection  
betyder, at din applikation (f.eks. i C#) opretter forbindelse til en database for at kunne læse/skrive data.

SQL Command  
En SQL Command i C# bruges til at udføre SQL-forespørgsler mod en database, fx SELECT, INSERT, UPDATE, DELETE.

ExecuteReader  
ExecuteReader() er en metode i C# (ADO.NET), der bruges sammen med en SqlCommand til at læse data fra en database via en SELECT-forespørgsel. Den returnerer en SqlDataReader, som giver dig mulighed for at læse rækker én ad gangen

ExecuteNonQuery  
ExecuteNonQuery() er en metode i C# (ADO.NET), som bruges til at udføre SQL-kommandoer der ikke returnerer data – typisk INSERT, UPDATE, DELETE og DDL (f.eks. CREATE TABLE).

ExecuteScalar  
ExecuteScalar() i C# (ADO.NET) bruges til at udføre en SQL-forespørgsel, der returnerer én enkelt værdi – f.eks. en COUNT, SUM, MAX, eller en værdi fra den første række/første kolonne i et resultat.

SQL Command Parameters (Add, AddWithValue)  
Forebygger SQL Injection ved at adskille SQL-kode fra data. Håndterer korrekt datakonvertering (fx string, int, datetime), Gør koden mere læselig og vedligeholdelsesvenlig.

  

ConnectionString  
En Connection String er en tekststreng, som indeholder alle nødvendige oplysninger, for at din applikation kan oprette forbindelse til en database. Hvor databasen findes (servernavn, filsti),  Hvilken database der skal bruges, Hvordan du logger på (brugernavn/kodeord eller Windows Authentication), Andre opsætningsparametre (timeout, kryptering, m.m.)

  

Expression  
I SQL er et udtryk (expression) en kombination af en eller flere værdier, operatorer og SQL-funktioner, der evalueres til en værdi. Udtryk bruges i forskellige dele af SQL-forespørgsler, såsom i SELECT-klause, WHERE-klause og ORDER BY-klause.

Query  
En query (forespørgsel) i SQL er en kommando, der bruges til at hente data fra en database. Queries kan være meget enkle eller meget komplekse, afhængigt af hvilke data du har brug for og hvordan du vil filtrere eller sortere dem. Den mest almindelige type query er en SELECT-forespørgsel, som bruges til at hente data fra en eller flere tabeller.

SqlDataReader  
SqlDataReader er en hurtig, fremad-only, læsning-én-gang datastream fra SQL Server. Den bruges til at hente resultater fra en SQL-forespørgsel og læse rækkerne én efter én i din C#-kode

Nullable typer  
En nullable type er en datatype, der kan indeholde både en værdi og null. Det betyder, at en variabel kan være “tom” eller “uden værdi”.

DBNulls  
DBNull repræsenterer en database NULL-værdi i .NET.

Stored procedures  
En Stored Procedure er et sæt af prædefinerede SQL-kommandoer, som ligger gemt i databasen som en enkelt enhed

input parameter  
input parameter er en variabel, som du sender ind til en stored procedure, når du kalder den. Den bruges til at give procedure data, som den kan bruge i sine SQL-kommandoer.

output parameter  
output parameter er en variabel, som stored proceduren kan bruge til at sende data tilbage til den, der kalder den. Det er altså en måde at returnere værdier uden at bruge resultatsæt (SELECT).

  

Window  
I WPF (Windows Presentation Foundation) er et Window den grundlæggende enhed for et selvstændigt vindue i en applikation. Det svarer til en formular (Form) i WinForms og kan indeholde UI-elementer som knapper, tekstbokse og andre kontroller.

  

Page

I WPF (Windows Presentation Foundation) er en Page en UI-komponent, der fungerer som en selvstændig side inden for en applikation. Den bruges ofte i navigationsbaserede applikationer, hvor brugeren kan skifte mellem forskellige sider, ligesom i en browser.

  

UserControl  
UserControl er en brugerdefineret komponent i GUI-udvikling, der kombinerer flere kontroller (controls) i en enkelt genbrugelig enhed. Det bruges ofte i teknologier som WPF (Windows Presentation Foundation) og WinForms i C#

  

Mediator Pattern  
Mediator Pattern er et adfærdsmønster (behavioral design pattern), der bruges til at reducere koblingen (coupling) mellem objekter ved at introducere en central "mægler" (mediator), der styrer kommunikationen mellem dem. Dette forhindrer, at objekterne kommunikerer direkte med hinanden, hvilket forbedrer modularitet og vedligeholdelse af koden.

  
  
  

ContentControl  
ContentControl er en grundlæggende WPF-kontrol, der kan indeholde én enkelt visuel komponent (f.eks. en knap, et billede, en brugerdefineret kontrol eller endda en hel layout-container som en Grid eller StackPanel).

Den fungerer som en beholder for dynamisk indhold, hvilket gør den nyttig til scenarier, hvor indholdet ændrer sig under kørsel.

  

DataTemplate  
En DataTemplate i WPF bruges til at definere, hvordan data skal vises i en UI-kontrol. Når en kontrol som ListBox, ListView, ComboBox eller ContentControl binder til data, bestemmer DataTemplate, hvordan hvert element skal se ud.

  

ReadOnly  
I WPF kan ReadOnly anvendes på forskellige kontroller for at forhindre brugeren i at redigere indholdet, samtidig med at det stadig kan vises.

  

Passing Parameters 

Passing parameters betyder at sende værdier (argumenter) til en funktion, metode eller et program, når det bliver kaldt eller eksekveret. Dette gør det muligt for en funktion at arbejde med forskellig data uden at ændre sin definition.

  

Anonyme metoder  
En anonym metode er en metode uden et navn, som typisk bruges til kortvarige opgaver, især i forbindelse med delegerede eller funktionelle programmeringsmønstre. Anonyme metoder findes i flere programmeringssprog, hvor de ofte bruges til inline-funktioner eller callbacks.

  

Services  
En service i softwareudvikling er en komponent, der tilbyder funktionalitet, ofte som en del af en større applikation eller et distribueret system. Services bruges ofte i serviceorienteret arkitektur (SOA) eller microservices-arkitektur.

  

## IT Governance

IT Governance (IT-styring) refererer til de rammer, processer og strukturer, der sikrer, at en organisations IT understøtter forretningsmålene, samtidig med at risici håndteres og lovgivning overholdes. Det giver en struktureret tilgang til beslutningstagning, ansvar og præstationsmåling af IT-ressourcer.

## GDPR

I henhold til GDPR (General Data Protection Regulation), som er en lovgivning i EU, betragtes medarbejderes personoplysninger som følsomme data, og disse skal beskyttes korrekt. Medarbejderes personoplysninger, som inkluderer email, navn og telefonnummer, falder ind under beskyttelsen af privatlivets fred og skal håndteres i overensstemmelse med GDPR's krav. 

Enumerable

Enumerable en statisk klasse i navnerummet System.Linq. Den indeholder en række extension-metoder, der gør det muligt at arbejde med samlinger, der implementerer interfacet IEnumerable<T>. Klassen bruges ofte i LINQ (Language Integrated Query) til at udføre operationer på data.

  

Lambda udtryk

Lambda-udtryk er en kortfattet måde at skrive anonyme funktioner på i C#. De bruges ofte sammen med LINQ og delegerede (Func<T>, Action<T>, osv.).

  

LINQ

LINQ (Language Integrated Query) er en kraftfuld feature i C#, der gør det muligt at skrive forespørgsler direkte i koden for at manipulere data i arrays, lister, databaser, XML og meget mere.

LINQ giver en deklarativ måde at arbejde med data, hvilket gør koden kortere, mere læsbar og mindre fejlbehæftet.

LINQ Method Syntax

Method Syntax i LINQ (også kaldet Lambda Syntax) bruger metoder fra Enumerable-klassen til at manipulere data. Den er ofte mere kompakt og fleksibel end Query Syntax og bruges i moderne C#-udvikling.

  

Dataansvarlig

Den dataansvarlige er den, der bestemmer formålet med og midlerne til behandlingen af personoplysninger. Det betyder, at de beslutter hvorfor og hvordan personoplysninger behandles.

Den dataansvarlige har hovedansvaret for, at personoplysninger behandles lovligt og i overensstemmelse med GDPR.

  

Databehandler

En databehandler behandler personoplysninger på vegne af den dataansvarlige og efter dennes instruktioner. Databehandleren må ikke bruge oplysningerne til egne formål.

Databehandlere skal have en skriftlig databehandleraftale med den dataansvarlige, der fastsætter, hvordan personoplysningerne må behandles.

**