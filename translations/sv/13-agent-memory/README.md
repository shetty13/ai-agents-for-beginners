# Minne för AI-agenter  
[![Agent Memory](../../../translated_images/sv/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

När man diskuterar de unika fördelarna med att skapa AI-agenter, är det främst två saker som tas upp: förmågan att anropa verktyg för att slutföra uppgifter och förmågan att förbättras över tid. Minne är grunden för att skapa självförbättrande agenter som kan skapa bättre upplevelser för våra användare.

I denna lektion kommer vi att titta på vad minne är för AI-agenter och hur vi kan hantera det och använda det till fördel för våra applikationer.

## Introduktion

Denna lektion kommer att täcka:

• **Att förstå AI-agenters minne**: Vad minne är och varför det är viktigt för agenter.

• **Implementera och lagra minne**: Praktiska metoder för att lägga till minneskapacitet till dina AI-agenter, med fokus på korttids- och långtidsminne.

• **Att göra AI-agenter självförbättrande**: Hur minne gör det möjligt för agenter att lära sig från tidigare interaktioner och förbättras över tid.

## Tillgängliga implementationer

Denna lektion inkluderar två omfattande anteckningsbokstutorials:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementerar minne med Mem0 och Azure AI Search med Semantic Kernel-ramverket

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementerar strukturerat minne med Cognee, som automatiskt bygger en kunskapsgraf baserad på embeddings, visualiserar grafen och intelligent hämtning

## Lärandemål

Efter att ha slutfört denna lektion kommer du att kunna:

• **Skilja mellan olika typer av AI-agentminne**, inklusive arbetsminne, korttidsminne och långtidsminne, samt specialiserade former som persona- och episodiskt minne.

• **Implementera och hantera korttids- och långtidsminne för AI-agenter** med Semantic Kernel-ramverket, genom att använda verktyg som Mem0, Cognee, Whiteboard-minne och integrera med Azure AI Search.

• **Förstå principerna bakom självförbättrande AI-agenter** och hur robusta minneshanteringssystem bidrar till kontinuerligt lärande och anpassning.

## Att förstå AI-agenters minne

I grunden refererar **minne för AI-agenter till de mekanismer som gör det möjligt för dem att behålla och återkalla information**. Denna information kan vara specifika detaljer om en konversation, användarpreferenser, tidigare handlingar eller till och med inlärda mönster.

Utan minne är AI-applikationer ofta statslösa, vilket innebär att varje interaktion börjar från början. Detta leder till en repetitiv och frustrerande användarupplevelse där agenten "glömmer" tidigare kontext eller preferenser.

### Varför är minne viktigt?

en agents intelligens är djupt kopplad till dess förmåga att återkalla och använda tidigare information. Minne gör att agenter kan vara:

• **Reflekterande**: Lära sig av tidigare handlingar och resultat.

• **Interaktiva**: Bibehålla kontexten under en pågående konversation.

• **Proaktiva och reaktiva**: Förutse behov eller reagera lämpligt baserat på historiska data.

• **Autonoma**: Arbeta mer självständigt genom att dra nytta av lagrad kunskap.

Målet med att implementera minne är att göra agenter mer **pålitliga och kapabla**.

### Typer av minne

#### Arbetsminne

Tänk på detta som en skisslapp som en agent använder under en enda pågående uppgift eller tankeprocess. Den håller omedelbar information som behövs för att beräkna nästa steg.

För AI-agenter fångar arbetsminnet ofta den mest relevanta informationen från en konversation, även om hela chathistoriken är lång eller trunkerad. Det fokuserar på att extrahera nyckelelement som krav, förslag, beslut och åtgärder.

**Exempel på arbetsminne**

I en resbokningsagent kan arbetsminnet innehålla användarens nuvarande förfrågan, som "Jag vill boka en resa till Paris". Detta specifika krav hålls i agentens omedelbara kontext för att vägleda den aktuella interaktionen.

#### Korttidsminne

Denna typ av minne behåller information under en enda konversation eller session. Det är kontexten för den aktuella chatten, vilket gör att agenten kan hänvisa tillbaka till tidigare turer i dialogen.

**Exempel på korttidsminne**

Om en användare frågar "Hur mycket skulle en flygresa till Paris kosta?" och sedan följer upp med "Hur är det med boende där?", säkerställer korttidsminnet att agenten vet att "där" syftar på "Paris" inom samma konversation.

#### Långtidsminne

Detta är information som kvarstår över flera konversationer eller sessioner. Det gör att agenter kan minnas användarpreferenser, historiska interaktioner eller allmän kunskap under längre perioder. Detta är viktigt för personalisering.

**Exempel på långtidsminne**

Ett långtidsminne kan lagra att "Ben gillar skidåkning och utomhusaktiviteter, föredrar kaffe med utsikt över bergen och vill undvika avancerade skidbackar på grund av en tidigare skada". Denna information, inhämtad från tidigare interaktioner, påverkar rekommendationer i framtida reseplaneringssessioner, vilket gör dem mycket personliga.

#### Persona-minne

Denna specialiserade minnestyp hjälper en agent att utveckla en konsekvent "personlighet" eller "persona". Det gör att agenten kan komma ihåg detaljer om sig själv eller sin avsedda roll, vilket gör interaktionerna mer flytande och fokuserade.

**Exempel på persona-minne**  
Om resagenten är designad för att vara en "expert på skidplanering" kan persona-minnet förstärka denna roll och påverka dess svar så att de överensstämmer med en experts ton och kunskap.

#### Workflow/Episodiskt minne

Detta minne lagrar sekvensen av steg som en agent tar under en komplex uppgift, inklusive framgångar och misslyckanden. Det är som att minnas specifika "episoder" eller tidigare erfarenheter för att lära sig av dem.

**Exempel på episodiskt minne**

Om agenten försökte boka ett specifikt flyg men misslyckades på grund av otillgänglighet, kan episodiskt minne registrera detta misslyckande och låta agenten prova alternativa flyg eller informera användaren om problemet på ett mer informerat sätt vid ett senare försök.

#### Enhetsminne

Detta involverar att extrahera och minnas specifika enheter (som personer, platser eller saker) och händelser från konversationer. Det gör att agenten kan bygga en strukturerad förståelse av viktiga element som diskuterats.

**Exempel på enhetsminne**

Från en konversation om en tidigare resa kan agenten extrahera "Paris", "Eiffeltornet" och "middag på restaurangen Le Chat Noir" som enheter. Vid en framtida interaktion kan agenten minnas "Le Chat Noir" och erbjuda att boka en ny reservation där.

#### Strukturerad RAG (Retrieval Augmented Generation)

Medan RAG är en bredare teknik, lyfts "Strukturerad RAG" fram som en kraftfull minnesteknologi. Den extraherar tät, strukturerad information från olika källor (konversationer, e-post, bilder) och använder den för att förbättra precision, återkallelse och svarshastighet. Till skillnad från klassisk RAG som bara förlitar sig på semantisk likhet, arbetar Strukturerad RAG med den inneboende strukturen i informationen.

**Exempel på strukturerad RAG**

Istället för att bara matcha nyckelord kan Strukturerad RAG tolka flygdetaljer (destination, datum, tid, flygbolag) från ett e-postmeddelande och lagra dem på ett strukturerat sätt. Detta möjliggör precisa frågor som "Vilket flyg bokade jag till Paris på tisdag?"

## Implementera och lagra minne

Att implementera minne för AI-agenter innebär en systematisk process för **minneshantering**, vilket inkluderar generering, lagring, hämtning, integration, uppdatering och till och med "glömmande" (eller borttagning) av information. Hämtning är en särskilt viktig aspekt.

### Specialiserade minnesverktyg

#### Mem0

Ett sätt att lagra och hantera agentminne är att använda specialiserade verktyg som Mem0. Mem0 fungerar som ett persistenslager för minne, vilket gör det möjligt för agenter att återkalla relevanta interaktioner, lagra användarpreferenser och faktuell kontext, samt lära sig från framgångar och misslyckanden över tid. Idén här är att statslösa agenter förvandlas till tillståndsbaserade.

Det fungerar genom en **tvåfasig minnespipeline: extraktion och uppdatering**. Först skickas meddelanden som läggs till en agents tråd till Mem0-tjänsten, som använder en stor språkmodell (LLM) för att summera konversationshistoriken och extrahera nya minnen. Därefter avgörs i en LLM-driven uppdateringsfas om minnena ska läggas till, ändras eller raderas, och de lagras i en hybriddatabas som kan inkludera vektor-, graf- och nyckel-värde-databaser. Systemet stöder också olika minnestyper och kan integrera grafminne för att hantera relationer mellan enheter.

#### Cognee

Ett annat kraftfullt tillvägagångssätt är att använda **Cognee**, ett öppen källkods semantiskt minne för AI-agenter som omvandlar strukturerad och ostrukturerad data till frågebara kunskapsgrafer baserade på embeddings. Cognee erbjuder en **dubbel-lagringsarkitektur** som kombinerar vektorsökning med grafrelationer, vilket möjliggör att agenter förstår inte bara vad som är likt informationmässigt, utan också hur begrepp relaterar till varandra.

Det utmärker sig vid **hybridhämtning** som blandar vektorsimilaritet, grafstruktur och LLM-resonemang – från rå fragmentuppslagning till grafmedveten frågeställning. Systemet underhåller ett **levande minne** som utvecklas och växer samtidigt som det förblir frågbart som en sammanhängande graf, och stödjer både korttidskontext i sessioner och långtidsbeständigt minne.

Cognee-anteckningsbokstutorialen ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) visar hur man bygger detta enhetliga minneslager med praktiska exempel på att ta in olika datakällor, visualisera kunskapsgrafen och göra sökningar med olika strategier anpassade till specifika agentbehov.

### Lagra minne med RAG

Utöver specialiserade minnesverktyg som Mem0 kan du använda robusta söktjänster som **Azure AI Search som backend för lagring och hämtning av minnen**, särskilt för strukturerad RAG.

Detta gör att du kan förankra din agents svar med din egen data och säkerställa mer relevanta och korrekta svar. Azure AI Search kan användas för att lagra användarspecifika reseminnen, produktkataloger eller annan domänspecifik kunskap.

Azure AI Search stödjer funktioner som **Strukturerad RAG**, vilket är mycket effektivt för att extrahera och hämta tät, strukturerad information från stora datamängder som konversationshistorik, e-post eller även bilder. Detta ger "övermänsklig precision och återkallelse" jämfört med traditionella metoder med textuppdelning och embedding.

## Att göra AI-agenter självförbättrande

Ett vanligt mönster för självförbättrande agenter involverar införandet av en **"kunskapsagent"**. Denna separata agent observerar huvudkonversationen mellan användaren och huvudsakliga agenten. Dess roll är att:

1. **Identifiera värdefull information**: Avgöra om någon del av konversationen är värd att spara som allmän kunskap eller en specifik användarpreferens.

2. **Extrahera och sammanfatta**: Destillera den väsentliga lärdomen eller preferensen från konversationen.

3. **Lagra i en kunskapsbas**: Spara denna extraherade information, ofta i en vektordatabas, så att den kan hämtas senare.

4. **Förstärka framtida förfrågningar**: När användaren initierar en ny fråga hämtar kunskapsagenten relevant sparad information och lägger till den i användarens prompt för att ge viktig kontext till huvudagenten (likt RAG).

### Optimeringar för minneshantering

• **Latenshantering**: För att undvika att sakta ner användarinteraktioner kan en billigare, snabbare modell användas initialt för att snabbt kontrollera om information är värdefull att lagra eller hämta, och endast vid behov använda den mer komplexa extraktions-/hämtningsprocessen.

• **Underhåll av kunskapsbasen**: För en växande kunskapsbas kan mindre frekvent använd information flyttas till "kall förvaring" för att hantera kostnader.

## Har du fler frågor om agentminne?

Gå med i [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) för att träffa andra studerande, delta i kontorstid och få svar på dina frågor om AI-agenter.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfriskrivning**:
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Vi strävar efter noggrannhet, men var vänlig och observera att automatiska översättningar kan innehålla fel eller felaktigheter. Det ursprungliga dokumentet på dess modersmål bör betraktas som den auktoritativa källan. För viktig information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för några missförstånd eller feltolkningar som uppstår från användningen av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->