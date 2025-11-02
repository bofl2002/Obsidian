[[Teknologi]]

**

# Virtual Maskine

En virtuel maskine (VM) er en softwarebaseret computer, som kører inde i en fysisk computer ved hjælp af en hypervisor. Den opfører sig som en rigtig computer, med sit eget operativsystem, programmer og ressourcer – men alt foregår virtuelt.

En virtuel maskine opererer ved hjælp af hardwarevirtualisering:

1. Hypervisoren (enten type 1 eller type 2) styrer og fordeler adgang til den fysiske hardware.  
      
    
2. Når du opretter en VM, tildeles den:
    

- Virtuel CPU (vCPU)
    
- Virtuel RAM
    
- Virtuel harddisk (ofte en fil på den fysiske disk)
    
- Virtuelt netværkskort osv.  
      
    

4. På den virtuelle maskine installerer du et operativsystem (f.eks. Windows, Linux), som tror, det kører på rigtig hardware.
    
5. Brugeren eller applikationer interagerer med VM’en, som om det var en almindelig fysisk computer.
    

### Fordele ved virtuelle maskiner:

- Isolering: Hver VM er adskilt fra andre – en fejl i én påvirker ikke de andre.
    
- Fleksibilitet: Du kan hurtigt oprette, ændre, kopiere eller slette VM’er.
    
- Effektiv udnyttelse af ressourcer: Flere VM’er kan dele én fysisk server.
    
- Sikkerhed: VM’er kan nemt "sandboxes", hvilket beskytter systemet.
    

En hypervisor er et stykke software, der gør det muligt at oprette og køre virtuelle maskiner (VM’er) på en fysisk computer (typisk en server). Hypervisoren fungerer som et mellemled mellem den fysiske hardware og de virtuelle maskiner, og den sørger for, at hver VM får tildelt en passende del af systemets ressourcer: CPU, RAM, disk og netværk.

Hypervisoren har følgende hovedfunktioner:

1. Virtualiserer hardware: Den skaber virtuelle versioner af fysisk hardware (f.eks. CPU, RAM, netkort).
    
2. Allokerer ressourcer: Den fordeler systemressourcer til hver virtuel maskine.
    
3. Isolerer VM’er: Den sikrer, at VM’erne er adskilte fra hinanden – hvis én fejler, påvirker det ikke de andre.
    
4. Styrer og overvåger VM’er: Den giver mulighed for at starte, stoppe, pause og flytte VM’er.
    

### Typer af hypervisorer:

|   |   |   |
|---|---|---|
|Type|Beskrivelse|Eksempel|
|Type 1 (bare-metal)|Kører direkte på den fysiske hardware uden et underliggende operativsystem. Mere effektiv og bruges typisk i datacentre.|VMware ESXi, Microsoft Hyper-V, Xen|
|Type 2 (hosted)|Installeres som et program oven på et eksisterende operativsystem. Bruges ofte på desktops og til testformål.|VMware Workstation, Oracle VirtualBox, Parallels|

**

# Cloud vs Multicloud

## **Cloud (Single Cloud)**

**Hvad er det?**

- Brug af **én enkelt cloud-udbyder** til alle eller de fleste cloud-services
- Eksempler: Kun AWS, kun Azure, eller kun Google Cloud Platform

**Fordele:**

- **Enklere administration** - ét interface, ét sæt værktøjer
- **Lavere kompleksitet** - færre systemer at integrere
- **Bedre integration** - services fungerer problemfrit sammen
- **Nemmere at lære** - kun ét ecosystem at mestre
- **Ofte billigere** - volumenrabatter hos én udbyder
- **Centraliseret sikkerhed** - ét sæt policies og governance

**Ulemper:**

- **Vendor lock-in** - svært/dyrt at skifte udbyder
- **Single point of failure** - hvis udbyderen går ned, går alt ned
- **Begrænset valgfrihed** - kun de services udbyderen tilbyder
- **Forhandlingsposition** - mindre leverage ved prisforhandlinger

---

## **Multicloud**

**Hvad er det?**

- Brug af **flere cloud-udbydere samtidigt**
- Eksempel: AWS til compute, Azure til AI/ML, Google Cloud til data analytics

**Fordele:**

- **Undgår vendor lock-in** - ikke afhængig af én udbyder
- **Best-of-breed** - vælg de bedste services fra hver udbyder
- **Højere redundans** - hvis én cloud går ned, fortsætter andre
- **Bedre forhandlingsposition** - kan presse priser
- **Geografisk fleksibilitet** - brug lokale datacentre hvor det giver mening
- **Compliance** - lettere at opfylde forskellige regionale krav

**Ulemper:**

- **Høj kompleksitet** - flere platforme at administrere
- **Dyrere** - ekstra omkostninger til integration og management
- **Kræver flere kompetencer** - personale skal kende flere platforme
- **Data transfer costs** - dyrt at flytte data mellem clouds
- **Sikkerhedsudfordringer** - flere systemer at sikre og monitere
- **Integrationsudfordringer** - services snakker ikke naturligt sammen

---

## **Sammenligning**

|**Aspekt**|**Single Cloud**|**Multicloud**|
|---|---|---|
|**Kompleksitet**|Lav|Høj|
|**Omkostninger**|Lavere (typisk)|Højere|
|**Vendor lock-in**|Høj risiko|Lav risiko|
|**Fleksibilitet**|Begrænset|Høj|
|**Management**|Simpelt|Komplekst|
|**Redundans**|Lavere|Højere|
|**Integration**|Nem|Svær|

---

## **Hvornår bruge hvad?**

### Vælg **Single Cloud** hvis:

- Du er et mindre firma eller startup
- Du vil holde kompleksiteten lav
- Budget er begrænset
- Dit team har begrænset cloud-erfaring
- Du ikke har kritiske uptime-krav

### Vælg **Multicloud** hvis:

- Du er en stor enterprise-virksomhed
- Uptime er kritisk (finance, healthcare)
- Du vil undgå vendor lock-in
- Du har ressourcer til kompleks management
- Du har specifikke compliance-krav på tværs af regioner
- Du ønsker best-of-breed services

---

## **Hybrid Cloud (bonus)**

En tredje variant er **hybrid cloud** - kombination af on-premise infrastruktur og cloud. Dette er forskelligt fra multicloud, som kun handler om flere cloud-udbydere.