[[Systemudvikling Dokumentation]]


Et **use case diagram** er en visuel model, der viser, hvordan brugere (eller "aktører") interagerer med et system for at opnå bestemte mål (use cases). Det bruges til at beskrive systemets funktionalitet og grænseflader fra brugerens perspektiv.

---

##### Hovedkomponenter i et Use Case Diagram

1. **Aktører (Actors):**
    
    - Repræsenterer brugere eller andre systemer, der interagerer med systemet.
        
    - Kan være mennesker, eksterne systemer eller hardware.
        
    - Symboliseres som en lille stregmand.
        
2. **Use Cases:**
    
    - Repræsenterer funktioner eller tjenester, som systemet tilbyder aktørerne.
        
    - Beskrives som ovaler med navne, fx "Log ind", "Opret ordre".
        
3. **Systemgrænse (System Boundary):**
    
    - En rektangel, der afgrænser systemet og dets use cases.
        
    - Alt indenfor er systemets funktionalitet.
        
4. **Relationer:**
    
    - **Association:** Linjer der forbinder aktører med use cases, viser interaktion.
        
    - **Include:** En use case inkluderer en anden (genbruger funktionalitet).
        
    - **Extend:** En use case udvider en anden med ekstra funktionalitet.
        
    - **Generalization:** Arv mellem aktører eller use cases (specialisering).
        

---

##### Use Case Diagram bruges til?

- At forstå systemets funktioner fra brugerens perspektiv.
    
- At kommunikere krav og funktionalitet mellem udviklere og interessenter.
    
- At danne grundlag for detaljeret kravspecifikation og design.
    

---

## Simpelt eksempel

Forestil dig et bibliotekssystem:

- Aktører: **Låner**, **Bibliotekar**
    
- Use Cases: **Søg bog**, **Lån bog**, **Returner bog**, **Registrer ny bog**
    

Diagrammet viser, hvilke aktører der kan udføre hvilke handlinger i systemet.
