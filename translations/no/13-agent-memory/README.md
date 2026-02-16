# Minne for AI-agenter  
[![Agent Memory](../../../translated_images/no/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Når man diskuterer de unike fordelene med å lage AI-agenter, er det to ting som ofte nevnes: muligheten til å bruke verktøy for å fullføre oppgaver og evnen til å forbedre seg over tid. Minne er grunnlaget for å skape selvforbedrende agenter som kan skape bedre opplevelser for våre brukere.

I denne leksjonen skal vi se på hva minne er for AI-agenter og hvordan vi kan administrere det og bruke det til fordel for applikasjonene våre.

## Introduksjon

Denne leksjonen vil dekke:

• **Forstå AI-agenters minne**: Hva minne er og hvorfor det er viktig for agenter.

• **Implementering og lagring av minne**: Praktiske metoder for å legge til minnefunksjoner i AI-agentene dine, med fokus på korttids- og langtidsminne.

• **Gjør AI-agenter selvforbedrende**: Hvordan minne gjør det mulig for agenter å lære fra tidligere interaksjoner og bli bedre over tid.

## Tilgjengelige implementasjoner

Denne leksjonen inkluderer to omfattende notebook-tutorials:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementerer minne ved bruk av Mem0 og Azure AI Search med Semantic Kernel-rammeverket

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementerer strukturert minne ved hjelp av Cognee, som automatisk bygger kunnskapsgraf støttet av embeddings, visualiserer grafen og utfører intelligent oppslag

## Læringsmål

Etter å ha fullført denne leksjonen vil du kunne:

• **Skille mellom ulike typer AI-agentminne**, inkludert arbeidsminne, korttidsminne og langtidsminne, samt spesialiserte former som persona- og episodisk minne.

• **Implementere og administrere korttids- og langtidsminne for AI-agenter** ved bruk av Semantic Kernel-rammeverket, med verktøy som Mem0, Cognee, Whiteboard-minne og integrasjon med Azure AI Search.

• **Forstå prinsippene bak selvforbedrende AI-agenter** og hvordan robuste minneadministrasjonssystemer bidrar til kontinuerlig læring og tilpasning.

## Forstå AI-agenters minne

I sin kjerne refererer **minne for AI-agenter til mekanismene som gjør det mulig for dem å beholde og hente informasjon**. Denne informasjonen kan være spesifikke detaljer om en samtale, brukerpreferanser, tidligere handlinger eller til og med lærte mønstre.

Uten minne er AI-applikasjoner ofte stateless, noe som betyr at hver interaksjon starter på nytt. Dette fører til en gjentakende og frustrerende brukeropplevelse der agenten "glemmer" tidligere kontekst eller preferanser.

### Hvorfor er minne viktig?

En agents intelligens er dypt knyttet til dens evne til å hente og bruke tidligere informasjon. Minne gjør at agenter kan være:

• **Reflekterende**: Lære av tidligere handlinger og resultat.

• **Interaktive**: Opprettholde kontekst over en pågående samtale.

• **Proaktive og reaktive**: Forutse behov eller svare hensiktsmessig basert på historiske data.

• **Autonome**: Operere mer selvstendig ved å trekke på lagret kunnskap.

Målet med å implementere minne er å gjøre agenter mer **pålitelig og dyktige**.

### Typer minne

#### Arbeidsminne

Tenk på dette som et utkastark agenten bruker under en enkelt, pågående oppgave eller tankeprosess. Det holder umiddelbar informasjon som trengs for å utføre neste steg.

For AI-agenter fanger arbeidsminne ofte den mest relevante informasjonen fra en samtale, selv om hele chatthistorien er lang eller forkortet. Det fokuserer på å trekke ut nøkkelpunkter som krav, forslag, beslutninger og handlinger.

**Eksempel på arbeidsminne**

I en reisebestillingsagent kan arbeidsminnet fange opp brukerens nåværende forespørsel, som "Jeg vil bestille en tur til Paris". Dette spesifikke kravet holdes i agentens umiddelbare kontekst for å styre den pågående interaksjonen.

#### Korttidsminne

Denne typen minne beholder informasjon i løpet av en enkelt samtale eller økt. Det er konteksten for den nåværende chatten, som gjør at agenten kan referere tilbake til tidligere utvekslinger i dialogen.

**Eksempel på korttidsminne**

Hvis en bruker spør: "Hvor mye koster en flybillett til Paris?" og deretter følger opp med "Hva med overnatting der?", sikrer korttidsminnet at agenten vet at "der" refererer til "Paris" i samme samtale.

#### Langtidsminne

Dette er informasjon som vedvarer gjennom flere samtaler eller økter. Det gjør at agenter kan huske brukerpreferanser, historiske interaksjoner eller generell kunnskap over lengre tid. Dette er viktig for personalisering.

**Eksempel på langtidsminne**

Langtidsminnet kan lagre at "Ben liker ski og utendørsaktiviteter, foretrekker kaffe med fjellutsikt, og ønsker å unngå avanserte skibakker på grunn av en tidligere skade". Denne informasjonen, lært fra tidligere interaksjoner, påvirker anbefalinger i fremtidige reiseplanleggingsøkter, og gjør dem svært tilpasset.

#### Persona-minne

Denne spesialiserte minnetypen hjelper en agent å utvikle en konsistent "personlighet" eller "rolle". Det gjør at agenten kan huske detaljer om seg selv eller sin tiltenkte rolle, noe som gjør interaksjonene mer flytende og målrettet.

**Eksempel på persona-minne**  
Hvis reiseagenten er designet til å være en "ekspert på ski", kan persona-minnet styrke denne rollen, og påvirke svarene slik at de samsvarer med en eksperts tone og kunnskap.

#### Arbeidsflyt-/episodisk minne

Dette minnet lagrer sekvensen av steg en agent tar under en kompleks oppgave, inkludert suksesser og feil. Det er som å huske spesifikke "episoder" eller tidligere erfaringer for å lære av dem.

**Eksempel på episodisk minne**

Hvis agenten prøvde å booke en bestemt flyvning, men det feilet på grunn av utilgjengelighet, kan episodisk minne lagre denne feilen, slik at agenten kan prøve alternative flyvninger eller informere brukeren mer klokt om problemet ved et nytt forsøk.

#### Entitetsminne

Dette innebærer å trekke ut og huske spesifikke entiteter (som personer, steder eller ting) og hendelser fra samtaler. Det lar agenten bygge en strukturert forståelse av viktige elementer som diskuteres.

**Eksempel på entitetsminne**

Fra en samtale om en tidligere reise kan agenten trekke ut "Paris," "Eiffeltårnet," og "middag på restauranten Le Chat Noir" som entiteter. Ved en fremtidig interaksjon kan agenten huske "Le Chat Noir" og tilby å lage en ny reservasjon der.

#### Strukturert RAG (Retrieval Augmented Generation)

Mens RAG er en bredere teknikk, fremheves "Strukturert RAG" som en kraftfull minneteknologi. Den trekker ut tettpakket, strukturert informasjon fra ulike kilder (samtaler, e-poster, bilder) og bruker det for å forbedre presisjon, hukommelse og responshastighet. I motsetning til klassisk RAG, som bare baserer seg på semantisk likhet, arbeider Strukturert RAG med den iboende strukturen i informasjonen.

**Eksempel på strukturert RAG**

I stedet for bare å matche nøkkelord kan Strukturert RAG analysere flydetaljer (destinasjon, dato, tid, flyselskap) fra en e-post og lagre dem i en strukturert form. Dette tillater presise søk som "Hvilken flyvning bestilte jeg til Paris på tirsdag?"

## Implementering og lagring av minne

Å implementere minne for AI-agenter innebærer en systematisk prosess med **minneadministrasjon**, som inkluderer å generere, lagre, hente, integrere, oppdatere, og til og med "glemme" (eller slette) informasjon. Henting er et særlig viktig aspekt.

### Spesialiserte minneverktøy

#### Mem0

En måte å lagre og administrere agentminne på er ved bruk av spesialiserte verktøy som Mem0. Mem0 fungerer som et vedvarende minnelag, som gjør det mulig for agenter å hente relevante interaksjoner, lagre brukerpreferanser og faktuell kontekst, og lære av suksesser og feil over tid. Ideen er at stateless-agenter blir stateful.

Det fungerer gjennom en **to-fase minneprosess: utvinning og oppdatering**. Først sendes meldinger lagt til i en agents tråd til Mem0-tjenesten, som bruker en stor språkmodell (LLM) for å oppsummere samtalehistorikk og trekke ut nye minner. Etterpå avgjør en LLM-drevet oppdateringsfase om disse minnene skal legges til, endres eller slettes, og lagres i en hybrid databutikk som kan inkludere vektor-, graf- og nøkkel-verdi-databaser. Systemet støtter også ulike minnetyper og kan inkludere grafminne for å håndtere relasjoner mellom entiteter.

#### Cognee

En annen kraftfull tilnærming er å bruke **Cognee**, et åpen kildekode semantisk minne for AI-agenter som omdanner strukturert og ustrukturert data til søkbare kunnskapsgrafer støttet av embeddings. Cognee tilbyr en **dual-store-arkitektur** som kombinerer vektorsøking med grafrelasjoner, slik at agenter kan forstå ikke bare hva informasjon som ligner på hverandre, men også hvordan konsepter er relatert.

Det utmerker seg i **hybridinnhenting** som blander vektorsammenligning, grafstruktur og LLM-resonnement – fra rå oppslag av chunks til grafbevisst spørsmål-svar. Systemet opprettholder et **levende minne** som utvikler seg og vokser samtidig som det forblir søkbart som en sammenkoblet graf, og støtter både kortvarig sesjonskontekst og langtidsvarig permanent minne.

Notebook-tutorial for Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstrerer bygging av dette sammensatte minnelaget med praktiske eksempler på innlasting av ulike datakilder, visualisering av kunnskapsgrafen og oppslag med forskjellige søkestrategier tilpasset agentens behov.

### Lagring av minne med RAG

Utover spesialiserte minneverktøy som Mem0, kan du utnytte robuste søketjenester som **Azure AI Search som backend for lagring og oppslag av minner**, spesielt for strukturert RAG.

Dette gjør det mulig å forankre agentens svar i egne data, noe som sikrer mer relevante og korrekte svar. Azure AI Search kan brukes til å lagre brukerspesifikke reiseerfaringer, produktkataloger eller annen domenespesifikk kunnskap.

Azure AI Search støtter funksjoner som **Strukturert RAG**, som utmerker seg i å trekke ut og hente tettpakket, strukturert informasjon fra store datasett som samtalehistorikk, e-poster eller til og med bilder. Dette gir "overmenneskelig presisjon og gjenkalling" sammenlignet med tradisjonelle tekstbiterings- og embedding-tilnærminger.

## Gjør AI-agenter selvforbedrende

Et vanlig mønster for selvforbedrende agenter innebærer å introdusere en **"kunnskapsagent"**. Denne separate agenten observerer hovedsamtalen mellom brukeren og den primære agenten. Dens rolle er å:

1. **Identifisere verdifull informasjon**: Avgøre om deler av samtalen er verdt å lagre som generell kunnskap eller spesifikke brukerpreferanser.

2. **Trekk ut og oppsummer**: Destillere det essensielle læringspunktet eller preferansen fra samtalen.

3. **Lagre i en kunnskapsbase**: Vedvare denne informasjonen, ofte i en vektordatabse, slik at den kan hentes senere.

4. **Forbedre fremtidige søk**: Når brukeren starter en ny forespørsel, henter kunnskapsagenten relevant lagret informasjon og legger den til brukerens forespørsel, som gir viktig kontekst til hovedagenten (likt RAG).

### Optimaliseringer for minne

• **Latensstyring**: For å unngå forsinkelser i brukerinteraksjoner kan en billigere, raskere modell brukes i utgangspunktet for raskt å sjekke om informasjon er verdifull å lagre eller hente, og bare bruke den mer komplekse utvinning-/hentemekanismen når det trengs.

• **Vedlikehold av kunnskapsbase**: For en voksende kunnskapsbase kan mindre brukt informasjon flyttes til "kaldlagring" for å redusere kostnader.

## Har du flere spørsmål om agentminne?

Bli med i [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) for å møte andre lærende, delta på kontortimer og få svar på spørsmål om AI-agenter.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi streber etter nøyaktighet, vennligst vær oppmerksom på at automatiske oversettelser kan inneholde feil eller unøyaktigheter. Det originale dokumentet på dets opprinnelige språk skal betraktes som den autoritative kilden. For kritisk informasjon anbefales profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for eventuelle misforståelser eller feiltolkninger som oppstår ved bruk av denne oversettelsen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->