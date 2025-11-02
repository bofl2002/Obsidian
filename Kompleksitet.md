
[[Systemudviklingsmetoder]]

Kompleksitet påvirker valget af Systemudviklingsmetode


**Kompleksitet i systemudvikling** handler om, hvor vanskeligt det er at forstå, udvikle, vedligeholde og ændre et system. Jo flere dele, afhængigheder og interaktioner der er i et system, jo mere komplekst bliver det.

Kompleksitet kan føre til fejl, misforståelser, forsinkelser og højere omkostninger – og gør det generelt sværere at lykkes med projektet.

---

##### Typer af kompleksitet i systemudvikling

##### 1. **Teknisk kompleksitet**

- **Beskrivelse**: Systemets tekniske struktur, teknologi-stak, integrationer og arkitektur kan være komplekse.
    
- **Eksempler**:
    
    - Mange komponenter og mikrotjenester, der skal tale sammen.
        
    - Integration med gamle systemer (legacy).
        
    - Brug af avancerede teknologier som AI, realtidsdata, cloud-infrastruktur osv.
        

---

##### 2. **Domænekompleksitet**

- **Beskrivelse**: Kompleksitet i det forretningsområde (domæne), systemet skal støtte.
    
- **Eksempler**:
    
    - Et økonomisystem med komplicerede skatteregler.
        
    - Sundheds-it, hvor der er mange regler, brugerroller og følsomme data.
        
- **Konsekvens**: Kræver stor forståelse af brugernes behov og arbejdsgange.
    

---

##### 3. **Organisatorisk kompleksitet**

- **Beskrivelse**: Mange interessenter, teams, afdelinger eller eksterne samarbejdspartnere.
    
- **Eksempler**:
    
    - Projektet involverer flere virksomheder eller lande.
        
    - Der er modstridende krav eller politiske interesser internt i organisationen.
        

---

##### 4. **Kravkompleksitet**

- **Beskrivelse**: Mange eller modsatrettede krav, som kan være svære at forstå, prioritere og implementere.
    
- **Eksempler**:
    
    - Brugerne vil have fleksibilitet, men ledelsen ønsker stram kontrol.
        
    - Et system skal både være brugervenligt og opfylde strenge sikkerhedskrav.
        

---

##### 5. **Tidsmæssig kompleksitet**

- **Beskrivelse**: Ændringer over tid, som gør det svært at holde styr på systemets tilstand og funktionalitet.
    
- **Eksempler**:
    
    - Krav ændrer sig hurtigt.
        
    - Der udvikles mange versioner parallelt.
        

---

##### Hvorfor er kompleksitet et problem?

- Svært at overskue hele systemet → risiko for fejl.
    
- Høj indlæringskurve for nye udviklere.
    
- Øget vedligeholdelsesbyrde.
    
- Vanskeligt at forudsige konsekvenser af ændringer.
    
- Større risiko for bugs og sikkerhedsproblemer.
    

---

##### Hvordan håndterer man kompleksitet?

|Tiltag|Forklaring|
|---|---|
|**Modulær arkitektur**|Opdel systemet i mindre, uafhængige moduler/tjenester.|
|**Dokumentation**|Sørg for god og opdateret dokumentation af kode, krav og beslutninger.|
|**DevOps og automatisering**|Automatiser test, deployment og overvågning.|
|**Agil udvikling**|Arbejd iterativt og håndter kompleksitet i små bidder.|
|**Domæneeksperter**|Involver brugere og eksperter tæt i udviklingen.|
|**God kommunikation**|Skab fælles forståelse på tværs af udvikling, ledelse og brugere.|

---

#####  Eksempel: Kompleksitet i praksis

> Et hospitalssystem skal udvikles til at håndtere både patientjournaler, tidsbestilling, medicinhåndtering og rapportering.  
> Her er der:
> 
> - **Domænekompleksitet** (lovgivning, medicinske data)
>     
> - **Teknisk kompleksitet** (integration med gamle systemer)
>     
> - **Organisatorisk kompleksitet** (læger, sygeplejersker, it-afdeling, ledelse)
>     
> - **Kravkompleksitet** (brugervenlighed vs. datasikkerhed)
>     

---


