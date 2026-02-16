# Memória az AI ügynökök számára  
[![Agent Memory](../../../translated_images/hu/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Az AI ügynökök egyedi előnyeinek megvitatásakor elsősorban két dolog kerül szóba: az eszközök hívásának képessége a feladatok elvégzéséhez és az idővel való fejlődés képessége. A memória az önfejlesztő ügynök létrehozásának alapja, amely jobb élményeket képes nyújtani a felhasználók számára.

Ebben a leckében megnézzük, mi a memória az AI ügynökök számára, hogyan kezelhetjük azt, és hogyan használhatjuk az alkalmazásaink javára.

## Bevezetés

Ez a lecke ezekkel foglalkozik:

• **AI ügynök memória megértése**: Mi a memória és miért elengedhetetlen az ügynökök számára.

• **A memória megvalósítása és tárolása**: Gyakorlati módszerek az AI ügynökök memóriaképességeinek hozzáadására, különös tekintettel a rövid- és hosszútávú memóriára.

• **Az AI ügynökök önfejlesztővé tétele**: Hogyan teszi lehetővé a memória az ügynökök számára, hogy megtanuljanak a múltbeli interakciókból és idővel fejlődjenek.

## Elérhető megvalósítások

Ez a lecke két átfogó jegyzetfüzet-tutorialt tartalmaz:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Mem0 és Azure AI Search használatával, Semantic Kernel keretrendszerrel megvalósított memória

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Strukturált memóriát valósít meg Cognee segítségével, amely automatikusan építi a beágyazásokkal támogatott tudásgráfot, vizualizálja a gráfot, és intelligens lekérdezést biztosít

## Tanulási célok

A lecke elvégzése után tudni fogja, hogyan:

• **Megkülönböztesse az AI ügynök memória különféle típusait**, beleértve a munkamemóriát, rövid- és hosszútávú memóriát, valamint speciális formákat, mint a személyiség- és epizodikus memória.

• **Megvalósítsa és kezelje a rövid- és hosszútávú memóriát az AI ügynökök számára** a Semantic Kernel keretrendszer használatával, kihasználva olyan eszközöket, mint a Mem0, Cognee, Whiteboard memória, és integrálva az Azure AI Search-t.

• **Megértse az önfejlesztő AI ügynökök mögötti elveket** és azt, hogyan járulnak hozzá a robusztus memóriakezelési rendszerek a folyamatos tanuláshoz és alkalmazkodáshoz.

## Az AI ügynök memória megértése

Alapvetően az **AI ügynökök memóriája azokat a mechanizmusokat jelenti, amelyek lehetővé teszik számukra az információk megtartását és előhívását**. Ezek az információk lehetnek beszélgetési részletek, felhasználói preferenciák, korábbi lépések vagy akár tanult mintázatok.

Memória nélkül az AI alkalmazások gyakran állapot nélküli alkalmazások, azaz minden interakció újrakezdődik a nulláról. Ez ismétlődő és bosszantó felhasználói élményhez vezet, ahol az ügynök „elfelejti” a korábbi kontextust vagy preferenciákat.

### Miért fontos a memória?

Az ügynök intelligenciája szorosan összefügg a múltbéli információk előhívásának és felhasználásának képességével. A memória lehetővé teszi, hogy az ügynökök legyenek:

• **Reflektívak**: tanuljanak a múltbéli cselekvésekből és eredményekből.

• **Interaktívak**: fenntartsák a kontextust egy folyamatban lévő beszélgetés során.

• **Proaktívak és reaktívak**: előre lássák a szükségleteket vagy megfelelően reagáljanak a történelmi adatok alapján.

• **Autonómok**: önállóbban működjenek a tárolt tudás felhasználásával.

A memória megvalósításának célja, hogy az ügynökök megbízhatóbbak és hatékonyabbak legyenek.

### A memória típusai

#### Munkamemória

Gondoljunk rá úgy, mint egy vázlatlapra, amelyet egy ügynök használ egy folyamatban lévő feladat vagy gondolatmenet során. Ez azonnali információt tartalmaz, amely a következő lépés kiszámításához szükséges.

Az AI ügynökök esetében a munkamemória általában a beszélgetés legfontosabb információit rögzíti, még akkor is, ha a teljes beszélgetési előzmény hosszú vagy csonkított. Arra összpontosít, hogy kiemelje a fő elemeket, mint a követelmények, javaslatok, döntések és lépések.

**Munkamemória példa**

Egy utazásszervező ügynöknél a munkamemória rögzítheti a felhasználó aktuális kérését, például: „Szeretnék egy utat foglalni Párizsba”. Ez a konkrét igény az ügynök közvetlen kontextusában marad az azonnali interakció irányítására.

#### Rövidtávú memória

Ez a memória típus megtartja az információt egyetlen beszélgetés vagy munkamenet idejére. Ez a jelenlegi csevegés kontextusa, amely lehetővé teszi az ügynök számára, hogy visszautaljon a párbeszéd korábbi fordulóira.

**Rövidtávú memória példa**

Ha a felhasználó megkérdezi: „Mennyibe kerülne egy repülőút Párizsba?” majd utána: „És a szállás ott?”, a rövidtávú memória biztosítja, hogy az ügynök tudja, hogy az „ott” kifejezés ebben a beszélgetésben Párizsra utal.

#### Hosszútávú memória

Ez az információ több beszélgetés vagy munkamenet során is fennmarad. Lehetővé teszi az ügynökök számára, hogy megjegyezzék a felhasználói preferenciákat, történelmi interakciókat vagy általános tudást hosszabb időn keresztül. Ez fontos a személyre szabás szempontjából.

**Hosszútávú memória példa**

A hosszútávú memória tárolhatja azt, hogy „Ben szeret síelni és a szabadtéri tevékenységeket, kávét szeret inni hegyi kilátással, és szeretné elkerülni a nehéz sípályákat egy korábbi sérülés miatt”. Ez az előző interakciókból tanult információ befolyásolja a jövőbeni utazástervezési ajánlásokat, amelyek így nagyon személyre szabottak lesznek.

#### Személyiség memória

Ez a speciális memória típus segít az ügynöknek következetes „személyiséget” vagy „arculatot” kialakítani. Lehetővé teszi az ügynök számára, hogy megjegyezze saját magáról vagy tervezett szerepéről szóló részleteket, így a kommunikáció gördülékenyebb és fókuszáltabb lesz.

**Személyiség memória példa**  
Ha az utazási ügynököt „szakelőtervezőként” alakították ki, a személyiség memória megerősítheti ezt a szerepet, befolyásolva a válaszokat, hogy azok megfeleljenek egy szakértő hangnemének és tudásának.

#### Munkafolyamat/Epizodikus memória

Ez a memória tárolja a lépések sorrendjét, amelyeket az ügynök egy összetett feladat során tesz meg, beleértve a sikereket és kudarcokat is. Olyan, mint amikor az ügynök megjegyzi a korábbi „epizódokat” vagy élményeket, hogy tanuljon belőlük.

**Epizodikus memória példa**

Ha az ügynök megpróbált lefoglalni egy adott járatot, de az nem volt elérhető, az epizodikus memória rögzítheti ezt a kudarcot, lehetővé téve, hogy az ügynök alternatív járatokat próbáljon vagy tájékoztassa a felhasználót erről a problémáról egy későbbi próbálkozás során.

#### Entitás memória

Ez magában foglalja az olyan konkrét entitások (például személyek, helyek vagy tárgyak) és események kinyerését és megjegyzését a beszélgetésekből. Lehetővé teszi az ügynök számára, hogy felépítsen egy strukturált megértést a kulcselemekről.

**Entitás memória példa**

Egy korábbi utazásról szóló beszélgetésből az ügynök kinyerheti a „Párizs”, „Eiffel-torony” és „vacsora a Le Chat Noir étteremben” entitásokat. Egy jövőbeli interakcióban az ügynök felidézheti a „Le Chat Noir”-t és felajánlhatja egy új foglalás lehetőségét.

#### Strukturált RAG (Retrieval Augmented Generation)

Bár a RAG egy szélesebb körű technika, a „Strukturált RAG” kiemeltként jelenik meg, mint egy erőteljes memória-technológia. Ez az eszköz sűrű, strukturált információkat nyer ki különféle forrásokból (beszélgetések, e-mailek, képek) és felhasználja azokat a válaszok pontosságának, előhívásának és gyorsaságának növelésére. A klasszikus RAG bal kizárólag a szemantikai hasonlóságra támaszkodik, míg a Strukturált RAG az információ belső struktúrájával dolgozik.

**Strukturált RAG példa**

A kulcsszavak egyezése helyett a Strukturált RAG képes kinyerni a repülőjárat adatait (úti cél, dátum, idő, légitársaság) egy e-mailből, és strukturált módon tárolni azokat. Ez lehetővé teszi a precíz lekérdezéseket, például: „Milyen repülőt foglaltam Párizsba kedden?”

## A memória megvalósítása és tárolása

A memória megvalósítása az AI ügynökök számára egy rendszerezett folyamatot jelent, azaz a **memóriakezelést**, amely magában foglalja az információ létrehozását, tárolását, előhívását, integrálását, frissítését, sőt elfelejtését (vagy törlését). Az előhívás különösen fontos elem.

### Speciális memóriaeszközök

#### Mem0

Az ügynök memória tárolására és kezelésére egy mód a speciális eszközök, például a Mem0 használata. A Mem0 egy tartós memória rétegként működik, amely lehetővé teszi, hogy az ügynökök előhívják a releváns interakciókat, tárolják a felhasználói preferenciákat és tényadatokat, valamint tanuljanak a sikerekből és kudarcokból az idő múlásával. Az ötlet az, hogy az állapot nélküli ügynökök állapottal rendelkezővé váljanak.

Ez egy **kétfázisú memóriafolyamatot** használ: kinyerés és frissítés. Először az ügynök szálába érkező üzeneteket a Mem0 szolgáltatásnak továbbítják, amely egy Nagy Nyelvi Modell (LLM) segítségével összefoglalja a beszélgetés történetét és kinyeri az új emlékeket. Ezután egy LLM által vezérelt frissítési fázis dönti el, hogy az emlékeket hozzáadják, módosítsák vagy töröljék, és ezek egy hibrid adattárolóban kerülnek eltárolásra, amely lehet vektor-, gráf- vagy kulcs-érték adatbázis. Ez a rendszer több memóriatípust is támogat, és gráfmemóriát is beépíthet az entitások közötti kapcsolatok kezelésére.

#### Cognee

Egy másik erőteljes megközelítés a **Cognee** használata, amely egy nyílt forráskódú szemantikus memória az AI ügynökök számára, amely az strukturált és strukturálatlan adatokat lekérdezhető tudásgráfokká alakítja, beágyazások segítségével támogatva. A Cognee egy **kettős tároló architektúrát** kínál, amely vektoros hasonlóságkeresést kombinál gráf kapcsolatkezeléssel, lehetővé téve az ügynökök számára, hogy megértsék nem csak a hasonló információkat, hanem azt is, hogy a fogalmak hogyan kapcsolódnak egymáshoz.

Kiemelkedő a **hibrid előhívásban**, amely ötvözi a vektoros hasonlóságot, a gráfszerkezetet és az LLM-alapú érvelést — a nyers töredékek keresésétől a gráf-tudatos kérdés-válaszolásig. A rendszer fenntart egy **élő memóriát**, amely fejlődik és nő ugyanakkor lekérdezhető marad egy egybefüggő gráfként, támogatva mind a rövid távú munkamenet kontextust, mind a hosszú távú tartós memóriát.

A Cognee jegyzetfüzet bemutató ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) szemlélteti ezt az egységes memória réteget gyakorlati példákkal, amelyekben különféle adatforrások bevitele, a tudásgráf vizualizálása és különböző keresési stratégiák alkalmazása történik az egyedi ügynöki igényekhez igazítva.

### Memória tárolása RAG-gal

A speciális memóriaeszközök, mint a Mem0 mellett, kihasználhatjuk az olyan robusztus keresési szolgáltatásokat, mint az **Azure AI Search**, mint háttérrendszert az emlékek tárolásához és előhívásához, különösen strukturált RAG esetén.

Ez lehetővé teszi, hogy az ügynök válaszait saját adatain alapozzuk meg, biztosítva relevánsabb és pontosabb válaszokat. Az Azure AI Search tárolhat felhasználói utazási emlékeket, termékkatalógusokat vagy bármilyen más domain-specifikus tudást.

Az Azure AI Search támogatja a **Strukturált RAG** képességet, amely kitűnően alkalmas nagy adathalmazokból (beszélgetések, e-mailek vagy akár képek) sűrű, strukturált információk kinyerésére és előhívására. Ez „emberfeletti pontosságot és előhívást” biztosít a hagyományos szövegtöredék- és beágyazás alapú megközelítésekhez képest.

## Az AI ügynökök önfejlesztővé tétele

Az önfejlesztő ügynökök gyakori mintája a **„tudásügynök”** bevezetése. Ez a külön ügynök figyeli a felhasználó és az elsődleges ügynök közötti fő beszélgetést. Feladatai:

1. **Értékes információk azonosítása**: Megállapítani, hogy a beszélgetés bármely része érdemes-e mentésre általános tudásként vagy felhasználói preferenciaként.

2. **Kinyerés és összefoglalás**: A beszélgetés lényeges tanulságának vagy preferenciájának kivonatolása.

3. **Tudásbázisban történő tárolás**: Az így kinyert információt gyakran vektorbázisú adatbázisba menti el későbbi előhívásra.

4. **Jövőbeli lekérdezések kiegészítése**: Ha a felhasználó új lekérdezést indít, a tudásügynök előhívja a releváns információkat és hozzáfűzi a felhasználó kérdéséhez, ezáltal fontos kontextust biztosítva az elsődleges ügynöknek (hasonlóan a RAG-hoz).

### Memória optimalizációk

• **Késleltetés kezelése**: A felhasználói interakciók lassítása elkerülése érdekében olcsóbb, gyorsabb modellt lehet használni előzetesen annak ellenőrzésére, hogy egy információ érdemes-e tárolásra vagy előhívásra, és csak szükség esetén hívni meg a bonyolultabb kinyerési/előhívási folyamatot.

• **Tudásbázis karbantartása**: A növekvő tudásbázis esetén a ritkábban használt információkat „hideg tárolóba” lehet helyezni a költségek kezelése érdekében.

## Több kérdése van az ügynök memória kapcsán?

Csatlakozzon az [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) közösséghez, hogy találkozzon más tanulókkal, részt vegyen hivatalos órákon, és választ kapjon AI ügynökökkel kapcsolatos kérdéseire.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Jogi Nyilatkozat**:
Ez a dokumentum az AI fordító szolgáltatás, a [Co-op Translator](https://github.com/Azure/co-op-translator) használatával készült. Bár a pontosságra törekszünk, kérjük, vegye figyelembe, hogy az automatikus fordítások tartalmazhatnak hibákat vagy pontatlanságokat. Az eredeti dokumentum az anyanyelvén tekintendő hivatalos forrásnak. Kritikus információk esetén javasolt professzionális, emberi fordítást használni. Nem vállalunk felelősséget a fordítás használatából eredő félreértésekért vagy téves értelmezésekért.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->