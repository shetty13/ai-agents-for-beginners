# Pamäť pre AI agentov 
[![Agent Memory](../../../translated_images/sk/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Keď sa diskutuje o jedinečných výhodách tvorby AI agentov, hlavne sa hovoria dve veci: schopnosť volať nástroje na dokončenie úloh a schopnosť zlepšovať sa v priebehu času. Pamäť je základom tvorby samo-zlepšujúceho sa agenta, ktorý dokáže vytvárať lepšie skúsenosti pre našich používateľov.

V tejto lekcii si ukážeme, čo je pamäť pre AI agentov a ako ju môžeme spravovať a využívať v prospech našich aplikácií.

## Úvod

Táto lekcia zahŕňa:

• **Porozumenie pamäti AI agenta**: Čo je pamäť a prečo je pre agentov nevyhnutná.

• **Implementácia a ukladanie pamäti**: Praktické metódy pridania pamäťových schopností vašim AI agentom, so zameraním na krátkodobú a dlhodobú pamäť.

• **Umožnenie samo-zlepšenia AI agentov**: Ako pamäť umožňuje agentom učiť sa z minulých interakcií a zlepšovať sa v čase.

## Dostupné implementácie

Táto lekcia obsahuje dva komplexné učebné poznámkové bloky:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementuje pamäť pomocou Mem0 a Azure AI Search s frameworkom Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementuje štruktúrovanú pamäť pomocou Cognee, automaticky buduje znalostný graf založený na embeddingoch, vizualizuje graf a inteligentné vyhľadávanie

## Ciele učenia

Po dokončení tejto lekcie budete vedieť:

• **Rozlíšiť medzi rôznymi typmi pamäti AI agentov**, vrátane pracovnej, krátkodobej a dlhodobej pamäti, ako aj špecializovaných typov ako persona a epizodická pamäť.

• **Implementovať a spravovať krátkodobú a dlhodobú pamäť pre AI agentov** pomocou frameworku Semantic Kernel s využitím nástrojov ako Mem0, Cognee, Whiteboard pamäť a integrácie s Azure AI Search.

• **Pochopiť princípy samo-zlepšujúcich sa AI agentov** a ako robustné systémy správy pamäti prispievajú k neustálemu učeniu a adaptácii.

## Porozumenie pamäti AI agenta

V jadre, **pamäť pre AI agentov označuje mechanizmy, ktoré im umožňujú uchovávať a vyvolávať informácie**. Tieto informácie môžu byť konkrétne detaily o konverzácii, preferencie používateľa, minulé akcie alebo dokonca naučené vzorce.

Bez pamäti sú AI aplikácie často bezstavové, t.j. každá interakcia začína od nuly. To vedie k opakujúcemu sa a frustrujúcemu používateľskému zážitku, kde agent „zabudne“ predchádzajúci kontext alebo preferencie.

### Prečo je pamäť dôležitá?

inteligencia agenta je hlboko spätá s jeho schopnosťou vyvolať a využiť minulé informácie. Pamäť umožňuje agentom byť:

• **Reflexívni**: Učiť sa z minulých akcií a výsledkov.

• **Interaktívni**: Udržiavať kontext počas prebiehajúcej konverzácie.

• **Proaktívni a reaktívni**: Predvídať potreby alebo primerane reagovať na základe historických dát.

• **Autonómni**: Fungovať viac nezávisle využitím uložených znalostí.

Cieľom implementácie pamäti je spraviť agentov viac **spoľahlivými a schopnými**.

### Typy pamäte

#### Pracovná pamäť

Predstavte si ju ako kus škrtacieho papiera, ktorý agent používa počas jednej prebiehajúcej úlohy alebo procesu myslenia. Uchováva okamžité informácie potrebné na výpočet ďalšieho kroku.

Pre AI agentov pracovná pamäť často zachytáva najrelevantnejšie informácie z rozhovoru, aj keď je celá chatová história dlhá alebo skrátená. Zameriava sa na vyťaženie kľúčových prvkov ako požiadavky, návrhy, rozhodnutia a akcie.

**Príklad pracovnej pamäti**

V cestovnej bookingovej agentúre môže pracovná pamäť zachytiť aktuálnu požiadavku používateľa, napríklad „Chcem si zarezervovať výlet do Paríža“. Táto špecifická požiadavka je uložená v bezprostrednom kontexte agenta, aby riadila aktuálnu interakciu.

#### Krátkodobá pamäť

Tento typ pamäti uchováva informácie počas celej jednej konverzácie alebo relácie. Je to kontext aktuálneho chatu, ktorý agentovi umožňuje odkazovať na predchádzajúce kolá dialógu.

**Príklad krátkodobej pamäti**

Ak sa používateľ opýta: „Koľko by stál let do Paríža?“ a potom dodatočne „Čo ubytovanie tam?“, krátkodobá pamäť zaručí, že agent vie, že „tam“ sa vzťahuje na „Paríž“ v rámci tej istej konverzácie.

#### Dlhodobá pamäť

Ide o informácie, ktoré pretrvávajú naprieč viacerými konverzáciami alebo reláciami. Umožňuje agentom pamätať si používateľské preferencie, historické interakcie alebo všeobecné znalosti počas dlhých období. Toto je dôležité pre personalizáciu.

**Príklad dlhodobej pamäti**

Dlhodobá pamäť môže uložiť, že „Ben má rád lyžovanie a vonkajšie aktivity, má rád kávu s výhľadom na hory a chce sa vyhnúť pokročilým lyžiarskym svahom kvôli minulému zraneniu“. Táto informácia, získaná z predchádzajúcich interakcií, ovplyvňuje odporúčania pri plánovaní budúcich ciest, čím ich robí vysoko personalizovanými.

#### Persona pamäť

Tento špecializovaný typ pamäti pomáha agentovi rozvíjať konzistentnú „osobnosť“ alebo „perzonu“. Umožňuje agentovi pamätať si detaily o sebe alebo svojej zamýšľanej úlohe, čím robí interakcie plynulejšími a cielenejšími.

**Príklad persona pamäti**

Ak je cestovný agent navrhnutý ako „expert na plánovanie lyžovania,“ persona pamäť môže túto rolu posilniť a ovplyvniť jeho odpovede tak, aby korešpondovali s tónom a znalosťami experta.

#### Workflow/Epizodická pamäť

Táto pamäť uchováva sekvenciu krokov, ktoré agent vykoná počas komplexnej úlohy, vrátane úspechov a neúspechov. Je to ako zapamätať si konkrétne „epizódy“ alebo minulé skúsenosti, aby sa z nich agent mohol poučiť.

**Príklad epizodickej pamäti**

Ak sa agent pokúsil rezervovať konkrétny let, ale zlyhalo to kvôli nedostupnosti, epizodická pamäť môže zaznamenať tento neúspech, čo agentovi umožní skúsiť alternatívne lety alebo informovať používateľa o probléme počas ďalšieho pokusu.

#### Entity Memory (Pamäť entít)

Týka sa extrahovania a zapamätania si konkrétnych entít (ako ľudia, miesta alebo veci) a udalostí z konverzácií. Umožňuje agentovi vytvoriť štruktúrované porozumenie kľúčových prvkov, o ktorých sa hovorilo.

**Príklad entity pamäti**

Z konverzácie o minulej ceste by agent mohol vyextrahovať „Paríž,“ „Eiffelova veža“ a „večera v reštaurácii Le Chat Noir“ ako entity. Pri budúcej interakcii by si agent mohol spomenúť na „Le Chat Noir“ a navrhnúť novú rezerváciu tam.

#### Štruktúrovaný RAG (Retrieval Augmented Generation)

Hoci RAG je širšia technika, „Štruktúrovaný RAG“ je vyzdvihovaný ako silná pamäťová technológia. Extrahuje husté, štruktúrované informácie z rôznych zdrojov (konverzácie, emaily, obrázky) a používa ich na zvýšenie presnosti, vyhľadávania a rýchlosti odpovedí. Na rozdiel od klasického RAG, ktorý sa spolieha iba na sémantickú podobnosť, Štruktúrovaný RAG pracuje s inherentnou štruktúrou informácií.

**Príklad štruktúrovaného RAG**

Namiesto len zhodovania kľúčových slov, Štruktúrovaný RAG môže z emailu vyparsovať detaily letu (cieľ, dátum, čas, letecká spoločnosť) a uložiť ich štruktúrovane. To umožňuje presné dotazy ako „Aký let som si rezervoval do Paríža v utorok?“

## Implementácia a ukladanie pamäti

Implementácia pamäti pre AI agentov zahŕňa systematický proces **správy pamäti**, ktorý obsahuje generovanie, ukladanie, vyhľadávanie, integráciu, aktualizáciu a dokonca aj „zabúdanie“ (alebo mazanie) informácií. Vyhľadávanie je obzvlášť kľúčovým aspektom.

### Špecializované pamäťové nástroje

#### Mem0

Jedným zo spôsobov, ako ukladať a spravovať pamäť agenta, je použitie špecializovaných nástrojov ako Mem0. Mem0 funguje ako perzistentná pamäťová vrstva, ktorá agentom umožňuje vyvolávať relevantné interakcie, ukladať používateľské preferencie a faktický kontext a učiť sa z úspechov a zlyhaní v priebehu času. Myšlienka je, že bezstavoví agenti sa zmenia na stavových.

Funguje prostredníctvom **dvojfázového pamäťového pipeline: extrakcia a aktualizácia**. Najprv sú správy pridané do vlákna agenta odoslané do služby Mem0, ktorá využíva veľký jazykový model (LLM) na zhrnutie histórie konverzácie a extrahovanie nových spomienok. Následne fáza aktualizácie riadená LLM rozhodne, či tieto spomienky pridať, upraviť alebo vymazať, a ukladá ich do hybridného dátového úložiska, ktoré môže obsahovať vektorové, grafové a kľúčovo-hodnotové databázy. Tento systém tiež podporuje rôzne typy pamäte a môže začleniť grafovú pamäť na správu vzťahov medzi entitami.

#### Cognee

Ďalším silným prístupom je použitie **Cognee**, open-source sémantickej pamäti pre AI agentov, ktorá premieňa štruktúrované a neštruktúrované dáta na dotazovateľné znalostné grafy založené na embeddingoch. Cognee poskytuje **dvojitú architektúru úložísk** kombinujúcu vektorové vyhľadávanie podobnosti s grafovými vzťahmi, čo umožňuje agentom pochopiť nielen to, ktoré informácie sú podobné, ale aj ako sú pojmy navzájom prepojené.

Vyniká v **hybridnom vyhľadávaní**, ktoré spája vektorovú podobnosť, štruktúru grafu a uvažovanie LLM - od vyhľadávania surových segmentov po odpovedanie na otázky vedomé grafu. Systém udržiava **živú pamäť**, ktorá sa vyvíja a rastie, pričom zostáva dotazovateľná ako jeden prepojený graf, podporujúci krátkodobý kontext relácie aj dlhodobú perzistentnú pamäť.

Návod v Cognee poznámkovom bloku ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonštruje budovanie tejto zjednotenej pamäťovej vrstvy s praktickými príkladmi ingestovania rôznych zdrojov dát, vizualizácie znalostného grafu a vyhľadávania s rôznymi stratégiami prispôsobenými špecifickým potrebám agenta.

### Ukladanie pamäti s RAG

Navyše k špecializovaným pamäťovým nástrojom ako Mem0 môžete využiť robustné vyhľadávacie služby ako **Azure AI Search ako backend na ukladanie a vyhľadávanie spomienok**, najmä pre štruktúrovaný RAG.

To umožňuje zakotviť odpovede vášho agenta vo vašich vlastných dátach, čo zabezpečuje relevantnejšie a presnejšie odpovede. Azure AI Search môže byť použité na ukladanie používateľských cestovných spomienok, katalógov produktov alebo akýchkoľvek iných doménovo špecifických znalostí.

Azure AI Search podporuje funkcie ako **Štruktúrovaný RAG**, ktorý vyniká v extrahovaní a vyhľadávaní hustých, štruktúrovaných informácií z veľkých dátových súborov ako histórie konverzácií, emailov či dokonca obrázkov. Toto poskytuje „nadľudskú presnosť a pamäť“ v porovnaní s tradičnými prístupmi založenými na textovom rozkúskovaní a embeedingoch.

## Umožnenie samo-zlepšenia AI agentov

Bežný vzor samo-zlepšujúcich sa agentov zahŕňa zavedenie **„poznatkovóho agenta“**. Tento samostatný agent pozoruje hlavnú konverzáciu medzi používateľom a primárnym agentom. Jeho úlohou je:

1. **Identifikovať cenné informácie**: Zistiť, či niektorá časť konverzácie stojí za uloženie ako všeobecné vedomosti alebo konkrétna používateľská preferencia.

2. **Extrahovať a zhrnúť**: Destilovať podstatné učenie alebo preferenciu z konverzácie.

3. **Uložiť do znalostnej bázy**: Udržať tieto extrahované informácie, často vo vektorovej databáze, aby sa dali neskôr vyhľadať.

4. **Rozšíriť budúce dotazy**: Keď používateľ iniciuje nový dotaz, poznatkovo agent vyhľadá relevantné uložené informácie a prikladá ich k používateľovej výzve, poskytujúc kľúčový kontext primárnemu agentovi (podobne ako RAG).

### Optimalizácie pre pamäť

• **Manažment latencie**: Aby sa predišlo spomaleniu používateľských interakcií, môže sa najprv použiť lacnejší, rýchlejší model, ktorý rýchlo skontroluje, či sú informácie hodné uloženia alebo vyhľadávania, a zložitejší proces extrakcie/vyhľadávania spustiť iba v prípade potreby.

• **Údržba znalostnej bázy**: Pre rastúcu znalostnú bázu môže byť menej často používaná informácia presunutá do „studeného úložiska“ na reguláciu nákladov.

## Máte ďalšie otázky o pamäti agentov?

Pridajte sa na [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord), kde sa môžete stretnúť s inými študentmi, zúčastniť sa konzultácií a dostať odpovede na svoje otázky o AI agentoch.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Zrieknutie sa zodpovednosti**:  
Tento dokument bol preložený pomocou prekladateľskej služby AI [Co-op Translator](https://github.com/Azure/co-op-translator). Aj keď sa snažíme o presnosť, berte prosím na vedomie, že automatické preklady môžu obsahovať chyby alebo nepresnosti. Pôvodný dokument v jeho rodnom jazyku by mal byť považovaný za autoritatívny zdroj. Pre kritické informácie sa odporúča profesionálny preklad vykonaný človekom. Nie sme zodpovední za akékoľvek nedorozumenia alebo nesprávne interpretácie vyplývajúce z použitia tohto prekladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->