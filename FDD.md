
FDD - Feature Driven Development

[[Typer af Systemudv. metoder]]

Feature Driven Development (FDD) er en agil udviklingsmetodologi, der fokuserer på at levere funktionalitet gennem korte, iterative cyklusser centreret omkring konkrete features eller funktioner.

Kerneprincipper i FDD

## Værktøjer og teknikker

Code Ownership tildeler hver klasse til en specifik udvikler, som er ansvarlig for dens vedligeholdelse og kvalitet. Dette reducerer konflikter og sikrer ansvarlighed.

Regular Builds gennemføres dagligt eller oftere for at sikre systemintegration og opdage problemer tidligt.

Configuration Management sporer alle ændringer i kode, dokumentation og andre projektartefakter gennem hele udviklingsprocessen.

Progress Reporting bruger detaljerede metrics til at spore fremskridt på feature-niveau, hvilket giver præcis synlighed i projektets tilstand.

## Modellerings- og designværktøjer

FDD anvender UML-modellering extensivt, særligt klassediagrammer for domænemodellen og sekvensdiagrammer for feature-design. Værktøjer som Enterprise Architect, Rational Rose eller moderne alternativer som PlantUML understøtter denne tilgang.

Inspection processes sikrer kvalitet gennem formelle gennemgange af design og kode, typisk med checklister og dokumenterede resultater.

## Praktiske værktøjer

Versionskontrol (Git, SVN), projektplanlægning (MS Project, Jira), og integration tools er centrale. FDD lægger vægt på værktøjer der understøtter feature tracking og rapportering af fremskridt på granulært niveau.

FDD's styrke ligger i den strukturerede tilgang til store projekter, klar ejerskab og synlighed, samt fokus på leverance af konkrete forretningsværdier gennem veldefinerede features.

FDD bygger på fem grundlæggende processer:

0. Indsamling af information

1. Udvikl en overordnet model Teamet skaber en bred forståelse af systemets omfang og sammenhæng gennem domænemodellering og arkitekturplanlægning.

2. Byg en feature-liste Alle systemkrav opdeles i små, klient-værdifulde funktioner. Hver feature formuleres typisk som "action result object" (f.eks. "Beregn den samlede værdi af en ordre").

3. Plan efter feature Features prioriteres og organiseres i udviklingssekventser, ofte grupperet i feature-sæt, der kan leveres sammen.

4. Design efter feature For hver feature laves detaljeret design, hvor arkitektur og implementeringsdetaljer fastlægges.

5. Byg efter feature Selve implementeringen, test og integration af featuren foregår i denne fase.

Karakteristiske træk

Feature-centreret tilgang: Alt arbejde organiseres omkring leverbare features frem for tekniske komponenter eller abstrakte faser.

Korte iterationer: Typisk 1-2 ugers cyklusser for individuelle features, hvilket giver hyppig feedback og synlig fremgang.

Klare roller: FDD definerer specifikke roller som Chief Architect, Development Manager, Chief Programmer og Class Owner.

Objektorienteret: Metoden er særligt velegnet til objektorienterede projekter og lægger vægt på domænemodellering.

Måling og rapportering: Fremgang måles konkret gennem antal færdiggjorte features, hvilket giver god synlighed for ledelse og interessenter.

FDD kombinerer strategisk planlægning med taktisk fleksibilitet og er særligt effektiv i større projekter, hvor der er behov for både struktur og agil leverance.

