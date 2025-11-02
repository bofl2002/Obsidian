[[Fokusområder]]

**Implementering og Krav**
Programmering og krav hænger meget tæt sammen - de er faktisk uadskillelige i succesfuld softwareudvikling:

**Fra krav til kode** Krav beskriver _hvad_ systemet skal gøre, mens programmering er _hvordan_ det implementeres. Programmører skal forstå kravene dybt for at omsætte dem til fungerende kode. Hvis kravene er uklare eller misforstås, bliver programmeringen forkert.

**Kravvalidering gennem programmering** Under programmeringen opdager man ofte at krav er ufuldstændige, selvmodsigende eller teknisk umulige. Programmører giver vigtig feedback til kravarbejdet om, hvad der faktisk kan realiseres, og hvad der er komplekst eller dyrt at implementere.

**Funktionelle vs. ikke-funktionelle krav** Funktionelle krav (f.eks. "brugeren skal kunne logge ind") oversættes direkte til programmeringsfunktioner. Ikke-funktionelle krav (som performance, sikkerhed, brugervenlighed) påvirker hvordan koden struktureres og optimeres.

**Testbarhed** Gode krav skal være testbare. Programmører skriver ofte unit tests og integrationstests baseret direkte på kravene for at verificere at koden opfylder dem. Krav der ikke kan testes, kan heller ikke programmeres ordentligt.

**Iterativ forbedring** I moderne udvikling (Agile, Scrum) arbejder man iterativt: krav specificeres, programmeres, testes og forfines løbende. User stories og acceptance-kriterier fungerer som bro mellem kravene og programmeringen.

**Teknisk gæld** Når krav ændrer sig konstant eller er dårligt definerede, opstår teknisk gæld i koden - hurtige løsninger der senere skal omskrives. God kravhåndtering minimerer dette.


**Implementering og HLD, LLD**
Programmering hænger direkte sammen med HLD (High-Level Design) og LLD (Low-Level Design) som forskellige abstraktionsniveauer i softwareudviklingen:

**HLD - High-Level Design (Overordnet Design)** HLD beskriver systemets overordnede arkitektur uden at gå i detaljer med implementeringen:

- Systembygningsblokke og komponenter
- Hvordan komponenter kommunikerer (API'er, databaser, netværk)
- Teknologivalg (programmeringssprog, frameworks, databaser)
- Sikkerhed og skalerbarhed på systemniveau

HLD fungerer som "landkort" for programmøren - det viser hvordan systemet hænger sammen, men ikke hvordan hver del kodes.

**LLD - Low-Level Design (Detaljeret Design)** LLD går tæt på den faktiske programmering:

- Klassediagrammer og datastrukturer
- Funktioner/metoder med parametre og returværdier
- Algoritmer og logik
- Detaljerede database-skemaer
- Fejlhåndtering og edge cases

LLD er ofte så detaljeret at det næsten er "pseudokode" - programmeringen bliver en direkte oversættelse af LLD til faktisk kode.

**Sammenhængen:**

1. **Krav → HLD → LLD → Programmering** er den typiske flow
2. **HLD** sikrer at programmøren forstår helheden og ikke koder i isolation
3. **LLD** giver programmøren den konkrete plan for implementering
4. **Programmering** realiserer designet, men giver også feedback: "Denne del af LLD er for kompleks" eller "HLD mangler en komponent"

**Eksempel:**

- **HLD:** "Systemet har en webserver, en applikationsserver og en database. De kommunikerer via REST API"
- **LLD:** "UserController har en createUser() metode der tager email og password, validerer dem, hasher passwordet med bcrypt, og kalder UserRepository.save()"
- **Programmering:** Den faktiske Java/Python/C# kode der implementerer ovenstående

Uden HLD risikerer man at kode et system med dårlig arkitektur. Uden LLD risikerer man ineffektiv eller rod-kode. God programmering kræver begge niveauer.