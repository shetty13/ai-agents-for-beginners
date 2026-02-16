# Geheugen voor AI-agents  
[![Agent Memory](../../../translated_images/nl/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Bij het bespreken van de unieke voordelen van het creëren van AI-agents worden vooral twee zaken besproken: het vermogen om tools aan te roepen om taken te voltooien en het vermogen om in de loop van de tijd te verbeteren. Geheugen vormt de basis voor het creëren van een zelfverbeterende agent die betere ervaringen kan bieden aan onze gebruikers.

In deze les bekijken we wat geheugen betekent voor AI-agents en hoe we dit kunnen beheren en gebruiken ten voordele van onze applicaties.

## Introductie

Deze les behandelt:

• **Begrip van AI-agentgeheugen**: Wat geheugen is en waarom het essentieel is voor agents.

• **Implementeren en opslaan van geheugen**: Praktische methoden om geheugencapaciteiten aan je AI-agents toe te voegen, met focus op kortetermijn- en langetermijngeheugen.

• **AI-agents zelfverbeterend maken**: Hoe geheugen agents in staat stelt te leren van vorige interacties en in de loop van de tijd te verbeteren.

## Beschikbare implementaties

Deze les bevat twee uitgebreide notebook-tutorials:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementeert geheugen met Mem0 en Azure AI Search met het Semantic Kernel-framework

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementeert gestructureerd geheugen met Cognee, bouwt automatisch een kennisgrafiek ondersteund door embeddings, visualiseert de grafiek en intelligente retrieval

## Leerdoelen

Na het voltooien van deze les weet je hoe je:

• **Verschillende typen AI-agentgeheugen kunt onderscheiden**, waaronder werkgeheugen, kortetermijngeheugen en langetermijngeheugen, evenals gespecialiseerde vormen zoals persona- en episodisch geheugen.

• **Kortetermijn- en langetermijngeheugen voor AI-agents kunt implementeren en beheren** met behulp van het Semantic Kernel-framework, gebruikmakend van tools zoals Mem0, Cognee, Whiteboardgeheugen, en integratie met Azure AI Search.

• **De principes begrijpt achter zelfverbeterende AI-agents** en hoe robuuste geheugensystemen bijdragen aan continu leren en aanpassing.

## Begrip van AI-agentgeheugen

In wezen verwijst **geheugen voor AI-agents naar de mechanismen die hen in staat stellen informatie te bewaren en terug te halen**. Deze informatie kan specifieke details zijn over een gesprek, gebruikersvoorkeuren, eerdere acties of zelfs aangeleerde patronen.

Zonder geheugen zijn AI-toepassingen vaak stateless, wat betekent dat elke interactie vanaf nul begint. Dit leidt tot een repetitieve en frustrerende gebruikerservaring waarbij de agent eerdere context of voorkeuren "vergeet".

### Waarom is geheugen belangrijk?

De intelligentie van een agent is nauw verbonden met zijn vermogen om eerder verkregen informatie te herinneren en te gebruiken. Geheugen stelt agents in staat om:

• **Reflectief te zijn**: Leren van eerdere acties en uitkomsten.

• **Interactief te zijn**: Context te behouden tijdens een lopend gesprek.

• **Proactief en reactief te zijn**: Behoeften te anticiperen of passend te reageren op basis van historische data.

• **Autonoom te zijn**: Onafhankelijker opereren door gebruik te maken van opgeslagen kennis.

Het doel van het implementeren van geheugen is agents **betrouwbaarder en capabeler** te maken.

### Typen geheugen

#### Werkgeheugen

Zie dit als een stuk kladpapier dat een agent gebruikt tijdens een enkele, lopende taak of denkproces. Het bevat directe informatie die nodig is om de volgende stap te berekenen.

Voor AI-agents vangt werkgeheugen vaak de belangrijkste informatie uit een gesprek op, zelfs als de volledige chatgeschiedenis lang is of afgekapt. Het richt zich op het extraheren van kernonderdelen zoals vereisten, voorstellen, beslissingen en acties.

**Voorbeeld van werkgeheugen**

In een reisboekingsagent kan werkgeheugen de huidige aanvraag van de gebruiker vastleggen, zoals "Ik wil een reis naar Parijs boeken". Deze specifieke vereiste wordt gehouden in de directe context van de agent om de huidige interactie te sturen.

#### Kortetermijngeheugen

Dit type geheugen behoudt informatie gedurende een enkele conversatie of sessie. Het is de context van de huidige chat, waardoor de agent kan terugverwijzen naar eerdere gesprekken in de dialoog.

**Voorbeeld van kortetermijngeheugen**

Als een gebruiker vraagt "Hoeveel kost een vlucht naar Parijs?" en vervolgens vervolgt met "Hoe zit het met accommodatie daar?", zorgt het kortetermijngeheugen ervoor dat de agent weet dat "daar" binnen hetzelfde gesprek naar "Parijs" verwijst.

#### Langetermijngeheugen

Dit is informatie die bewaart blijft over meerdere gesprekken of sessies heen. Het stelt agents in staat om gebruikersvoorkeuren, historische interacties of algemene kennis over langere periodes te onthouden. Dit is belangrijk voor personalisatie.

**Voorbeeld van langetermijngeheugen**

Langetermijngeheugen kan opslaan dat "Ben van skiën en buitenactiviteiten houdt, koffie drinkt met uitzicht op de bergen en geavanceerde skipistes wil vermijden vanwege een eerdere blessure". Deze informatie, geleerd uit eerdere interacties, beïnvloedt aanbevelingen in toekomstige reisplanningssessies en maakt ze zeer gepersonaliseerd.

#### Persona-geheugen

Dit gespecialiseerde geheugentype helpt een agent een consistente "persoonlijkheid" of "persona" te ontwikkelen. Het laat de agent details over zichzelf of zijn beoogde rol onthouden, waardoor interacties vloeiender en gerichter worden.

**Voorbeeld van persona-geheugen**  
Als de reisagent ontworpen is als een "expert ski-planner", kan persona-geheugen deze rol versterken en de reacties beïnvloeden om overeen te komen met de toon en kennis van een expert.

#### Workflow-/episodisch geheugen

Dit geheugen slaat de opeenvolging van stappen op die een agent neemt tijdens een complexe taak, inclusief successen en mislukkingen. Het is als het onthouden van specifieke "episodes" of ervaringen om ervan te leren.

**Voorbeeld van episodisch geheugen**

Als de agent geprobeerd heeft een specifieke vlucht te boeken maar dit mislukte vanwege onbeschikbaarheid, kan het episodisch geheugen deze mislukking registreren, waardoor de agent alternatieve vluchten kan proberen of de gebruiker beter geïnformeerd kan melden bij een volgende poging.

#### Entiteitgeheugen

Dit houdt in dat specifieke entiteiten (zoals mensen, plaatsen of dingen) en gebeurtenissen uit gesprekken worden geëxtraheerd en onthouden. Het stelt de agent in staat een gestructureerd inzicht te krijgen in belangrijke besproken elementen.

**Voorbeeld van entiteitgeheugen**

Uit een gesprek over een eerdere reis kan de agent "Parijs," "Eiffeltoren," en "diner bij restaurant Le Chat Noir" als entiteiten extraheren. Bij een toekomstige interactie kan de agent "Le Chat Noir" herinneren en aanbieden daar een nieuwe reservering te maken.

#### Gestructureerde RAG (Retrieval Augmented Generation)

Hoewel RAG een bredere techniek is, wordt "Gestructureerde RAG" benadrukt als een krachtige geheugentechnologie. Het extraheert dichte, gestructureerde informatie uit diverse bronnen (gesprekken, e-mails, afbeeldingen) en gebruikt dit om precisie, recall en snelheid in antwoorden te verbeteren. In tegenstelling tot klassieke RAG, die alleen op semantische gelijkenis steunt, werkt Gestructureerde RAG met de inherente structuur van informatie.

**Voorbeeld van gestructureerde RAG**

In plaats van alleen trefwoorden te matchen, kan Gestructureerde RAG vluchtgegevens (bestemming, datum, tijd, luchtvaartmaatschappij) uit een e-mail ontleden en deze op een gestructureerde manier opslaan. Dit maakt precieze queries mogelijk zoals "Welke vlucht heb ik geboekt naar Parijs op dinsdag?"

## Implementeren en opslaan van geheugen

Geheugen implementeren voor AI-agents houdt een systematisch proces van **geheugenbeheer** in, waaronder het genereren, opslaan, ophalen, integreren, bijwerken en zelfs "vergeten" (of verwijderen) van informatie. Retrieval is een bijzonder cruciaal aspect.

### Gespecialiseerde geheugentools

#### Mem0

Een manier om agentgeheugen op te slaan en te beheren is het gebruik van gespecialiseerde tools zoals Mem0. Mem0 functioneert als een persistent geheugenlaag, waardoor agents relevante interacties kunnen terughalen, gebruikersvoorkeuren en feitelijke context kunnen opslaan, en leren van successen en mislukkingen in de loop van de tijd. Het idee is dat stateless agents veranderen in stateful agents.

Het werkt via een **tweepasig geheugentraject: extractie en update**. Eerst worden berichten die aan de thread van een agent worden toegevoegd, naar de Mem0-service gestuurd, die een Large Language Model (LLM) gebruikt om de gespreksgeschiedenis samen te vatten en nieuwe herinneringen te extraheren. Vervolgens bepaalt een LLM-gestuurde updatefase of deze herinneringen moeten worden toegevoegd, aangepast of verwijderd, en slaat ze op in een hybride databank die vector-, grafiek- en key-value databases kan omvatten. Dit systeem ondersteunt ook verschillende geheugentypes en kan grafiekgeheugen integreren voor het beheren van relaties tussen entiteiten.

#### Cognee

Een andere krachtige aanpak is het gebruik van **Cognee**, een open-source semantisch geheugen voor AI-agents dat gestructureerde en ongestructureerde data omzet in doorzoekbare kenniskringen ondersteund door embeddings. Cognee biedt een **dual-store architectuur** die vectorgebaseerd zoeken combineert met grafiekrelaties, waardoor agents niet alleen kunnen begrijpen welke informatie vergelijkbaar is, maar ook hoe concepten zich tot elkaar verhouden.

Het blinkt uit in **hybride retrieval**, dat vector gelijkenis, grafiekstructuur en LLM-redenering combineert - van ruwe chunk lookup tot grafiekbewuste vraagbeantwoording. Het systeem onderhoudt een **levend geheugen** dat evolueert en groeit en tegelijkertijd doorzoekbaar blijft als één verbonden grafiek, ter ondersteuning van zowel kortetermijnsessiecontext als langetermijn persistent geheugen.

De Cognee-notebook tutorial ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstreert het bouwen van deze uniforme geheugenlaag, met praktische voorbeelden van het opnemen van diverse databronnen, het visualiseren van de kenniskring en het doorzoeken met verschillende zoekstrategieën die zijn aangepast aan specifieke agentbehoeften.

### Opslaan van geheugen met RAG

Naast gespecialiseerde geheugentools zoals Mem0 kun je gebruikmaken van robuuste zoekdiensten zoals **Azure AI Search als backend voor het opslaan en ophalen van herinneringen**, vooral voor gestructureerde RAG.

Dit stelt je in staat om de reacties van je agent te funderen op je eigen data, wat zorgt voor relevantere en nauwkeurigere antwoorden. Azure AI Search kan worden gebruikt om gebruikersspecifieke reisherinneringen, productcatalogi of andere domeinspecifieke kennis op te slaan.

Azure AI Search ondersteunt functionaliteiten zoals **Gestructureerde RAG**, die uitblinkt in het extraheren en ophalen van dichte, gestructureerde informatie uit grote datasets zoals gespreksgeschiedenissen, e-mails of zelfs afbeeldingen. Dit levert "supermenselijke precisie en recall" in vergelijking met traditionele tekstchunking- en embedding-methoden.

## AI-agents zelfverbeterend maken

Een veelvoorkomend patroon voor zelfverbeterende agents is het introduceren van een **"kennisagent"**. Deze aparte agent observeert het hoofdgesprek tussen de gebruiker en de primaire agent. Zijn rol is om:

1. **Waardevolle informatie te identificeren**: Bepalen of een deel van het gesprek het waard is om op te slaan als algemene kennis of specifieke gebruiker voorkeur.

2. **Extractie en samenvatting**: De essentie van de leerervaring of voorkeur uit het gesprek distilleren.

3. **Opslaan in een kennisdatabase**: Deze geëxtraheerde informatie persistent opslaan, vaak in een vectordatabase, zodat het later kan worden opgehaald.

4. **Toekomstige queries verrijken**: Wanneer de gebruiker een nieuwe query start, haalt de kennisagent relevante opgeslagen informatie op en voegt deze toe aan de prompt van de gebruiker, waardoor cruciale context aan de primaire agent wordt gegeven (vergelijkbaar met RAG).

### Optimalisaties voor geheugen

• **Latencybeheer**: Om te voorkomen dat gebruikersinteracties vertragen, kan aanvankelijk een goedkopere, snellere model worden gebruikt om snel te controleren of informatie het waard is om op te slaan of terug te halen, waarna het complexere extractie-/ophaalproces alleen wordt ingezet indien nodig.

• **Onderhoud van de kennisdatabase**: Voor een groeiende kennisdatabase kan minder vaak gebruikte informatie naar "cold storage" worden verplaatst om kosten te beheren.

## Vragen over agentgeheugen?

Word lid van de [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) om andere leerlingen te ontmoeten, deel te nemen aan spreekuren en je vragen over AI-agents beantwoord te krijgen.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Dit document is vertaald met behulp van de AI-vertalingsdienst [Co-op Translator](https://github.com/Azure/co-op-translator). Hoewel we streven naar nauwkeurigheid, dient u er rekening mee te houden dat automatische vertalingen fouten of onnauwkeurigheden kunnen bevatten. Het origineel in de oorspronkelijke taal moet als de gezaghebbende bron worden beschouwd. Voor cruciale informatie wordt een professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor eventuele misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->