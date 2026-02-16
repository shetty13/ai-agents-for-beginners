# Paměť pro AI agenty 
[![Agent Memory](../../../translated_images/cs/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Při diskusi o jedinečných výhodách tvorby AI agentů se zejména mluví o dvou věcech: schopnosti volat nástroje k dokončení úkolů a schopnosti se časem zlepšovat. Paměť je základem pro vytvoření samo-zlepšujícího se agenta, který může vytvářet lepší zkušenosti pro naše uživatele.

V této lekci se podíváme na to, co je paměť pro AI agenty a jak ji můžeme spravovat a využívat k prospěchu našich aplikací.

## Úvod

Tato lekce pokrývá:

• **Porozumění paměti AI agentů**: Co je paměť a proč je pro agenty zásadní.

• **Implementace a uložení paměti**: Praktické způsoby, jak přidat paměťové schopnosti AI agentům, zaměřené na krátkodobou a dlouhodobou paměť.

• **Učinění AI agentů samo-zlepšujícími se**: Jak paměť umožňuje agentům učit se z minulých interakcí a zlepšovat se v čase.

## Dostupné implementace

Tato lekce obsahuje dva komplexní tutoriály v noteboocích:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementuje paměť pomocí Mem0 a Azure AI Search s frameworkem Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementuje strukturovanou paměť pomocí Cognee, která automaticky buduje znalostní graf podložený embeddingy, vizualizuje graf a inteligentně vyhledává

## Cíle učení

Po dokončení této lekce budete umět:

• **Rozlišovat mezi různými typy paměti AI agentů**, včetně pracovní, krátkodobé a dlouhodobé paměti, stejně jako specializovaných forem jako je paměť persona a episodiční paměť.

• **Implementovat a spravovat krátkodobou a dlouhodobou paměť pro AI agenty** pomocí frameworku Semantic Kernel, využívat nástroje jako Mem0, Cognee, Whiteboard paměť a integrovat s Azure AI Search.

• **Porozumět principům samo-zlepšujících se AI agentů** a jak robustní systémy správy paměti přispívají k nepřetržitému učení a adaptaci.

## Porozumění paměti AI agentů

V jádru **paměť pro AI agenty označuje mechanismy, které jim umožňují uchovávat a vybavovat si informace**. Tyto informace mohou být specifické detaily o konverzaci, preference uživatele, minulé akce nebo dokonce naučené vzory.

Bez paměti jsou AI aplikace často bezstavové, což znamená, že každá interakce začíná od nuly. To vede k opakujícímu se a frustrujícímu uživatelskému zážitku, kdy agent „zapomíná“ předchozí kontext nebo preference.

### Proč je paměť důležitá?

Inteligence agenta je úzce spojena s jeho schopností vybavovat si a využívat minulé informace. Paměť umožňuje agentům být:

• **Reflektivní**: Učit se z minulých akcí a výsledků.

• **Interaktivní**: Udržovat kontext během probíhající konverzace.

• **Proaktivní a reaktivní**: Předvídat potřeby nebo odpovídat vhodně na základě historických dat.

• **Autonomní**: Fungovat více nezávisle čerpáním ze uložených znalostí.

Cílem implementace paměti je učinit agenty více **spolehlivé a schopné**.

### Typy paměti

#### Pracovní paměť

Představte si to jako kus papíru, který agent používá během jediné, probíhající úlohy nebo myšlenkového procesu. Uchovává okamžité informace potřebné k výpočtu dalšího kroku.

Pro AI agenty pracovní paměť často zachycuje nejrelevantnější informace z konverzace, i když je celý chat dlouhý nebo zkrácený. Zaměřuje se na extrakci klíčových prvků jako požadavky, návrhy, rozhodnutí a akce.

**Příklad pracovní paměti**

U cestovního agenta pracovní paměť může zaznamenat aktuální požadavek uživatele, například „Chci si rezervovat cestu do Paříže“. Tento specifický požadavek je držen v bezprostředním kontextu agenta, aby řídit aktuální interakci.

#### Krátkodobá paměť

Tento typ paměti uchovává informace po dobu jedné konverzace nebo relace. Je to kontext aktuálního chatu, který umožňuje agentovi odkazovat zpět na předchozí kroky v dialogu.

**Příklad krátkodobé paměti**

Pokud uživatel položí otázku „Kolik by stál let do Paříže?“ a poté naváže otázkou „A co ubytování tam?“, krátkodobá paměť zajistí, že agent ví, že „tam“ odkazuje na „Paříž“ v rámci téže konverzace.

#### Dlouhodobá paměť

Jedná se o informace, které přetrvávají přes více konverzací nebo relací. Umožňuje agentům pamatovat si preference uživatele, historické interakce nebo obecné znalosti po delší období. To je důležité pro personalizaci.

**Příklad dlouhodobé paměti**

Dlouhodobá paměť může uložit, že „Ben má rád lyžování a outdoorové aktivity, miluje kávu s výhledem na hory a chce se vyhýbat pokročilým sjezdovkám kvůli minulému zranění“. Tyto informace, získané z předchozích interakcí, ovlivňují doporučení při plánování budoucích cest a činí je vysoce personalizovanými.

#### Paměť persona

Tento specializovaný typ paměti pomáhá agentovi rozvíjet konzistentní „osobnost“ nebo „persona“. Umožňuje agentovi pamatovat si detaily o sobě samém nebo o své zamýšlené roli, což činí interakce plynulejšími a zaměřenějšími.

**Příklad paměti persona**  
Pokud je cestovní agent navržen jako „expert na plánování lyžařských zájezdů“, paměť persona může tuto roli posilovat a ovlivňovat jeho odpovědi tak, aby odpovídaly tónu a znalostem experta.

#### Paměť workflow/episodická paměť

Tato paměť zaznamenává sled kroků, které agent podnikne během složitého úkolu, včetně úspěchů a neúspěchů. Je to jako zapamatování si konkrétních „epizod“ nebo minulých zkušeností, ze kterých se učí.

**Příklad episodiční paměti**

Pokud se agent pokusil rezervovat konkrétní let, ale selhalo to kvůli nedostupnosti, episodiční paměť může zaznamenat tento neúspěch a umožnit agentovi zkusit alternativní lety nebo informovat uživatele o problému informovaněji při dalším pokusu.

#### Paměť entit

Týká se extrahování a zapamatování si specifických entit (jako lidé, místa nebo věci) a událostí z konverzací. Umožňuje agentovi vybudovat strukturované porozumění klíčovým prvkům, o kterých se diskutuje.

**Příklad paměti entit**

Z konverzace o minulém výletu může agent vytáhnout entity jako „Paříž“, „Eiffelova věž“ a „večeře v restauraci Le Chat Noir“. Při budoucí interakci může agent vzpomenout „Le Chat Noir“ a nabídnout novou rezervaci právě tam.

#### Strukturovaný RAG (Retrieval Augmented Generation)

Zatímco RAG je širší technika, „Strukturovaný RAG“ je zdůrazněn jako výkonná paměťová technologie. Extrahuje husté, strukturované informace z různých zdrojů (konverzace, e-maily, obrázky) a využívá je k vylepšení přesnosti, výtěžnosti a rychlosti odpovědí. Na rozdíl od klasického RAG, který spoléhá pouze na sémantickou podobnost, Strukturovaný RAG pracuje s vnitřní strukturou informací.

**Příklad strukturovaného RAG**

Místo pouhého shodování klíčových slov může Strukturovaný RAG rozebrat detaily letu (destinace, datum, čas, letecká společnost) z e-mailu a uložit je strukturovaným způsobem. To umožňuje přesné dotazy jako „Jaký let jsem si zarezervoval do Paříže v úterý?“

## Implementace a ukládání paměti

Implementace paměti pro AI agenty zahrnuje systematický proces **správy paměti**, který zahrnuje generování, ukládání, vyhledávání, integraci, aktualizaci a dokonce „zapomínání“ (nebo mazání) informací. Vyhledávání je obzvlášť klíčový aspekt.

### Specializované nástroje pro paměť

#### Mem0

Jedním ze způsobů ukládání a správy agentní paměti je použití specializovaných nástrojů jako Mem0. Mem0 funguje jako perzistentní paměťová vrstva, která agentům umožňuje vybavovat si relevantní interakce, ukládat uživatelské preference a faktický kontext a učit se z úspěchů a neúspěchů v čase. Myšlenka je, že bezstavoví agenti se promění ve stavové.

Pracuje prostřednictvím **dvojfázového paměťového procesu: extrakce a aktualizace**. Nejprve se zprávy přidané do vlákna agenta posílají do služby Mem0, která využívá velký jazykový model (LLM) k shrnutí historii konverzace a extrakci nových vzpomínek. Následná aktualizační fáze řízená LLM pak rozhoduje, zda přidat, upravit nebo smazat tyto paměti, které jsou uloženy v hybridním datovém skladu zahrnujícím vektorové, grafové a klíč-hodnota databáze. Tento systém také podporuje různé typy paměti a může začlenit grafovou paměť pro správu vztahů mezi entitami.

#### Cognee

Dalším silným přístupem je použití **Cognee**, open-source sémantické paměti pro AI agenty, která transformuje strukturovaná i nestrukturovaná data do dotazovatelných znalostních grafů podložených embeddingy. Cognee poskytuje **dvojúložištní architekturu** kombinující vektorové vyhledávání podobnosti s grafovými vztahy, což umožňuje agentům rozumět nejen tomu, co je podobné, ale i jak jsou koncepty propojené.

Vyniká v **hybridním vyhledávání**, které kombinuje vektorovou podobnost, grafovou strukturu a uvažování LLM – od prostého vyhledávání po znalosti až po dotazování s uvědoměním grafu. Systém udržuje **živou paměť**, která se vyvíjí a roste a přitom zůstává dotazovatelná jako jeden propojený graf, podporující jak krátkodobý kontext relace, tak dlouhodobě perzistentní paměť.

Tutoriál notebooku Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) ukazuje budování této sjednocené paměťové vrstvy s praktickými příklady vstupu různorodých datových zdrojů, vizualizace znalostního grafu a dotazování s různými vyhledávacími strategiemi přizpůsobenými specifickým potřebám agentů.

### Ukládání paměti pomocí RAG

Kromě specializovaných nástrojů paměti jako Mem0 můžete využít robustní vyhledávací služby jako **Azure AI Search jako backend pro ukládání a vyhledávání pamětí**, zejména pro strukturovaný RAG.

Toto umožňuje zakotvit odpovědi agenta ve vašich vlastních datech, což zajišťuje relevantnější a přesnější odpovědi. Azure AI Search může být použito k ukládání uživatelsky specifických cestovních vzpomínek, katalogů produktů nebo jakýchkoli jiných doménově specifických znalostí.

Azure AI Search podporuje schopnosti jako **Strukturovaný RAG**, který exceluje ve vyvádění a vyhledávání hustých, strukturovaných informací z velkých datových sad jako jsou historie konverzací, e-maily nebo dokonce obrázky. To poskytuje „nadlidskou přesnost a výtěžnost“ ve srovnání s tradičními metodami segmentace textu a embeddingu.

## Učinění AI agentů samo-zlepšujícími se

Běžný vzorec pro samo-zlepšující se agenty zahrnuje zavedení **„agenta znalostí“**. Tento samostatný agent pozoruje hlavní konverzaci mezi uživatelem a primárním agentem. Jeho rolí je:

1. **Identifikovat cenné informace**: Určit, zda je jakákoliv část konverzace hodná uložení jako obecné znalosti nebo specifické uživatelské preference.

2. **Extrahovat a shrnout**: Destilovat podstatné učení nebo preferenci z konverzace.

3. **Uložit do znalostní báze**: Perzistentně uložit tyto vyextrahované informace, často ve vektorové databázi, aby bylo možné je později dohledat.

4. **Rozšířit budoucí dotazy**: Když uživatel zahájí nový dotaz, agent znalostí vyhledá relevantní uložené informace a připojí je k uživatelovu promptu, poskytujíc zásadní kontext primárnímu agentovi (podobně jako RAG).

### Optimalizace pro paměť

• **Řízení latence**: Aby se zabránilo zpomalení uživatelských interakcí, lze nejprve použít levnější a rychlejší model k rychlé kontrole, zda je informace hodná uložení nebo vyhledání, a složitější extrakční/vyhledávací proces spustit jen v případě potřeby.

• **Údržba znalostní báze**: Pro rostoucí znalostní bázi lze méně často používané informace přesouvat do „chladného úložiště“ pro řízení nákladů.

## Máte další otázky ohledně paměti agentů?

Připojte se k [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord), kde se můžete setkat s dalšími studenty, účastnit se konzultací a získat odpovědi na své otázky o AI agentech.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vyloučení odpovědnosti**:  
Tento dokument byl přeložen pomocí AI překladatelské služby [Co-op Translator](https://github.com/Azure/co-op-translator). I když usilujeme o přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho mateřském jazyce by měl být považován za závazný zdroj. U zásadních informací se doporučuje profesionální lidský překlad. Nejsme odpovědni za jakékoliv nedorozumění nebo chybné interpretace vyplývající z použití tohoto překladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->