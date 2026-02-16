# Hukommelse til AI-agenter  
[![Agent Memory](../../../translated_images/da/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Når man diskuterer de unikke fordele ved at skabe AI-agenter, handler det hovedsageligt om to ting: evnen til at kalde værktøjer for at udføre opgaver og evnen til at forbedre sig over tid. Hukommelse er fundamentet for at skabe en selvforbedrende agent, der kan skabe bedre oplevelser for vores brugere.

I denne lektion vil vi se på, hvad hukommelse er for AI-agenter, og hvordan vi kan administrere den og bruge den til fordel for vores applikationer.

## Introduktion

Denne lektion vil dække:

• **Forståelse af AI-agenters hukommelse**: Hvad hukommelse er, og hvorfor det er essentielt for agenter.

• **Implementering og lagring af hukommelse**: Praktiske metoder til at tilføje hukommelsesfunktioner til dine AI-agenter med fokus på kort- og langtidshukommelse.

• **Gøre AI-agenter selvforbedrende**: Hvordan hukommelse gør det muligt for agenter at lære af tidligere interaktioner og blive bedre over tid.

## Tilgængelige implementeringer

Denne lektion indeholder to omfattende note-øvelser:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementerer hukommelse ved hjælp af Mem0 og Azure AI Search med Semantic Kernel-frameworket

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementerer struktureret hukommelse ved hjælp af Cognee, der automatisk bygger en vidensgraf understøttet af embeddings, visualiserer grafen og foretager intelligent opslag

## Læringsmål

Efter at have gennemført denne lektion vil du kunne:

• **Differentierer mellem forskellige typer af AI-agenthukommelse**, herunder arbejdshukommelse, korttidshukommelse og langtidshukommelse samt specialiserede former som persona- og episodisk hukommelse.

• **Implementere og administrere kort- og langtidshukommelse for AI-agenter** ved hjælp af Semantic Kernel-frameworket, og udnytte værktøjer som Mem0, Cognee, Whiteboard-hukommelse samt integration med Azure AI Search.

• **Forstå principperne bag selvforbedrende AI-agenter** og hvordan robuste hukommelsesadministrationssystemer bidrager til kontinuerlig læring og tilpasning.

## Forstå AI-agenthukommelse

Grundlæggende refererer **hukommelse for AI-agenter til de mekanismer, der tillader dem at bevare og genkalde information**. Denne information kan være specifikke detaljer om en samtale, brugerpræferencer, tidligere handlinger eller endda lærte mønstre.

Uden hukommelse er AI-applikationer ofte uden tilstand (stateless), hvilket betyder, at hver interaktion starter forfra. Dette fører til en gentagende og frustrerende brugeroplevelse, hvor agenten ”glemmer” tidligere kontekst eller præferencer.

### Hvorfor er hukommelse vigtigt?

En agents intelligens er dybt knyttet til dens evne til at genkalde og anvende tidligere information. Hukommelse gør det muligt for agenter at være:

• **Reflekterende**: Lære af tidligere handlinger og resultater.

• **Interaktive**: Opretholde kontekst gennem en igangværende samtale.

• **Proaktive og reaktive**: Forudse behov eller reagere passende baseret på historiske data.

• **Autonome**: Virke mere selvstændigt ved at trække på lagret viden.

Målet med at implementere hukommelse er at gøre agenter mere **pålidelige og kompetente**.

### Typer af hukommelse

#### Arbejdshukommelse

Tænk på dette som et stykke kladdepapir, som en agent bruger under en enkelt, igangværende opgave eller tankeproces. Den holder den umiddelbare information, der er nødvendig for at udføre næste skridt.

For AI-agenter fanger arbejdshukommelsen ofte den mest relevante information fra en samtale, selv hvis hele chat-historikken er lang eller afkortet. Den fokuserer på at udtrække nøgleelementer som krav, forslag, beslutninger og handlinger.

**Eksempel på arbejdshukommelse**

I en rejsebookingsagent kan arbejdshukommelsen fange brugerens aktuelle forespørgsel som "Jeg vil booke en tur til Paris". Dette specifikke krav holdes i agentens umiddelbare kontekst for at guide den aktuelle interaktion.

#### Korttidshukommelse

Denne type hukommelse bevarer information i løbet af en enkelt samtale eller session. Det er konteksten i den nuværende chat, så agenten kan referere tilbage til tidligere dialogtrin.

**Eksempel på korttidshukommelse**

Hvis en bruger spørger: "Hvor meget koster en flyrejse til Paris?" og efterfølgende spørger: "Hvad med overnatning der?", sikrer korttidshukommelsen, at agenten ved, at "der" refererer til "Paris" i samme samtale.

#### Langtidshukommelse

Dette er information, der bevares på tværs af flere samtaler eller sessioner. Det tillader agenter at huske brugerpræferencer, historiske interaktioner eller generel viden over længere perioder. Det er vigtigt for personalisering.

**Eksempel på langtidshukommelse**

En langtidshukommelse kan gemme, at "Ben nyder skiløb og udendørsaktiviteter, kan lide kaffe med bjergudsigt og ønsker at undgå avancerede pister på grund af en tidligere skade". Denne information, lært fra tidligere interaktioner, påvirker anbefalinger i fremtidige rejseplanlægningssessioner og gør dem meget personlige.

#### Persona-hukommelse

Denne specialiserede hukommelsestype hjælper en agent med at udvikle en konsistent "personlighed" eller "persona". Den tillader agenten at huske detaljer om sig selv eller sin tilsigtede rolle, hvilket gør interaktioner mere flydende og fokuserede.

**Eksempel på persona-hukommelse**  
Hvis rejseagenten er designet til at være en "ekspert i skiplanlægning", kan persona-hukommelsen forstærke denne rolle ved at påvirke svarene, så de stemmer overens med en eksperts tone og viden.

#### Workflow/Episodisk hukommelse

Denne hukommelse gemmer rækkefølgen af trin, en agent tager under en kompleks opgave, inklusiv succeser og fejl. Det svarer til at huske specifikke "episoder" eller tidligere oplevelser for at lære af dem.

**Eksempel på episodisk hukommelse**

Hvis agenten forsøgte at booke en bestemt flyvning, men det mislykkedes på grund af manglende tilgængelighed, kan episodisk hukommelse registrere denne fejl, så agenten kan prøve alternative fly eller informere brugeren om problemet mere oplyst i et efterfølgende forsøg.

#### Entitetshukommelse

Det indebærer at udtrække og huske specifikke enheder (som personer, steder eller ting) og begivenheder fra samtaler. Det tillader agenten at opbygge en struktureret forståelse af nøgleelementer, der diskuteres.

**Eksempel på entitetshukommelse**

Fra en samtale om en tidligere rejse kan agenten udtrække "Paris," "Eiffeltårnet," og "middag på restauranten Le Chat Noir" som enheder. I en fremtidig interaktion kan agenten huske "Le Chat Noir" og tilbyde at foretage en ny reservation der.

#### Struktureret RAG (Retrieval Augmented Generation)

Selvom RAG er en bredere teknik, fremhæves "Struktureret RAG" som en kraftfuld hukommelsesteknologi. Den udtrækker tæt, struktureret information fra forskellige kilder (samtaler, e-mails, billeder) og bruger det til at forbedre præcision, genkaldelse og hastighed i svarene. I modsætning til klassisk RAG, der udelukkende bygger på semantisk lighed, arbejder Struktureret RAG med den iboende struktur i informationen.

**Eksempel på struktureret RAG**

I stedet for kun at matche nøgleord kan Struktureret RAG udtrække flyoplysninger (destination, dato, tid, flyselskab) fra en e-mail og lagre dem struktureret. Det gør det muligt at foretage præcise forespørgsler som "Hvilket fly bookede jeg til Paris på tirsdag?"

## Implementering og lagring af hukommelse

Implementering af hukommelse for AI-agenter involverer en systematisk proces med **hukommelsesstyring**, som omfatter generering, lagring, hentning, integration, opdatering og endda "glemsel" (eller sletning) af information. Hentning er en særlig væsentlig del.

### Specialiserede hukommelsesværktøjer

#### Mem0

En måde at lagre og administrere agenthukommelse på er ved at anvende specialiserede værktøjer som Mem0. Mem0 fungerer som et vedvarende hukommelseslag, der tillader agenter at genkalde relevante interaktioner, lagre brugerpræferencer og faktuel kontekst samt lære af succeser og fejl over tid. Ideen er her, at statsløse agenter bliver til agent med tilstand.

Det fungerer gennem en **to-faset hukommelsespipeline: udtrækning og opdatering**. Først sendes meddelelser, der er tilføjet til en agents tråd, til Mem0-tjenesten, som bruger en stor sprogmodel (LLM) til at opsummere samtalehistorik og udtrække nye minder. Efterfølgende afgør en LLM-drevet opdateringsfase, om disse minder skal tilføjes, ændres eller slettes, hvorefter de lagres i et hybridt datalager, der kan indeholde vektor-, graf- og nøgle-værdi-databaser. Systemet understøtter også forskellige hukommelsestyper og kan inkorporere grafhukommelse til at håndtere relationer mellem enheder.

#### Cognee

En anden kraftfuld tilgang er at bruge **Cognee**, en open source semantisk hukommelse til AI-agenter, som omdanner strukturerede og ustrukturerede data til søgbare vidensgrafer understøttet af embeddings. Cognee tilbyder en **dual-store arkitektur**, der kombinerer vektorsøgningslighed med grafrelationer, hvilket gør det muligt for agenter ikke blot at forstå, hvad information er ens, men også hvordan begreber relaterer til hinanden.

Det excellerer i **hybrid hentning**, der blander vektorsimilartet, grafstruktur og LLM-reasoning – fra rå chunks opslag til grafbevidst spørgsmålssvar. Systemet opretholder **levende hukommelse**, der udvikler sig og vokser, mens det forbliver søgbart som én sammenhængende graf, som støtter både korttids-sessioners kontekst og langtidshukommelse.

Cognee-noteøvelsen ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstrerer opbygningen af dette forenede hukommelseslag med praktiske eksempler på indtagelse af diverse datakilder, visualisering af vidensgrafen og forespørgsel med forskellige søgestrategier tilpasset specifikke agentbehov.

### Lagre hukommelse med RAG

Udover specialiserede hukommelsesværktøjer som Mem0 kan du udnytte robuste søgetjenester som **Azure AI Search som backend til lagring og hentning af minder**, især for struktureret RAG.

Dette gør det muligt at fastholde agentens svar med dine egne data, hvilket sikrer mere relevante og præcise svar. Azure AI Search kan bruges til at lagre brugerspecifik rejsehukommelse, produktkataloger eller anden domænespecifik viden.

Azure AI Search understøtter funktioner som **Struktureret RAG**, som excellerer i at udtrække og hente tæt, struktureret information fra store datasæt som samtalehistorik, e-mails eller endda billeder. Det giver "supermenneskelig præcision og genkaldelse" sammenlignet med traditionelle tekstchunking- og embedding-metoder.

## Gøre AI-agenter selvforbedrende

Et almindeligt mønster for selvforbedrende agenter indebærer introduktion af en **”vidensagent”**. Denne separate agent observerer hovedsamtalen mellem brugeren og den primære agent. Dens rolle er at:

1. **Identificere værdifuld information**: Vurdere om dele af samtalen er værd at gemme som generel viden eller specifik brugerpræference.

2. **Udtrække og opsummere**: Destillere den essentielle læring eller præference fra samtalen.

3. **Lagre i en vidensbase**: Gemme denne udtrukne information, ofte i en vektordatabse, så den kan hentes senere.

4. **Berige fremtidige forespørgsler**: Når brugeren starter en ny forespørgsel, henter vidensagenten relevant gemt information og tilføjer den til brugerens prompt, hvilket giver vigtig kontekst til den primære agent (på samme måde som RAG).

### Optimeringer for hukommelse

• **Forsinkelsesstyring**: For at undgå at bremse brugerinteraktioner kan en billigere, hurtigere model bruges i starten til hurtigt at afgøre, om information er værd at gemme eller hente, og kun aktivere den mere komplekse udtræknings-/hentningsproces når nødvendigt.

• **Vedligeholdelse af vidensbase**: For en voksende vidensbase kan mindre hyppigt brugt information flyttes til ”kold lagring” for at holde omkostningerne nede.

## Har du flere spørgsmål om agenthukommelse?

Deltag i [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) for at møde andre lærende, deltage i office hours og få svar på dine spørgsmål om AI-agenter.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokument er blevet oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi bestræber os på nøjagtighed, skal du være opmærksom på, at automatiske oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på dets modersmål bør betragtes som den autoritative kilde. For kritisk information anbefales professionel menneskelig oversættelse. Vi påtager os intet ansvar for eventuelle misforståelser eller fejltolkninger, der opstår som følge af brugen af denne oversættelse.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->