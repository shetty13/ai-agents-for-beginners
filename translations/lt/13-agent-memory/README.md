# Atmintis dirbtinio intelekto agentams  
[![Agentų atmintis](../../../translated_images/lt/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Kalbant apie unikalius dirbtinio intelekto agentų kūrimo privalumus, dažniausiai aptariamos dvi savybės: gebėjimas kviesti įrankius užduotims atlikti ir gebėjimas tobulėti laikui bėgant. Atmintis yra savarankiškai tobulėjančio agento, galinčio kurti geresnes patirtis mūsų naudotojams, pagrindas.

Šioje pamokoje apžvelgsime, kas yra atmintis dirbtinio intelekto agentams, kaip ją galime valdyti ir naudoti savo programų naudai.

## Įvadas

Šioje pamokoje bus aptariama:

• **Dirbtinio intelekto agentų atminties supratimas**: kas yra atmintis ir kodėl ji svarbi agentams.

• **Atminties įgyvendinimas ir saugojimas**: praktiniai būdai pridėti atminties galimybes savo DI agentams, akcentuojant trumpalaikę ir ilgalaikę atmintį.

• **Kaip padaryti DI agentus savarankiškai tobulėjančius**: kaip atmintis leidžia agentams mokytis iš ankstesnių sąveikų ir laikui bėgant tobulėti.

## Turimi įgyvendinimai

Ši pamoka apima dvi išsamių bloknotų pamokas:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: atminties įgyvendinimas naudojant Mem0 ir Azure AI Search su Semantic Kernel karkasu

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: struktūruotos atminties įgyvendinimas naudojant Cognee, automatiškai kuriant žinių grafiką remiantis įdėjiniais, grafinį vizualizavimą ir intelektualių užklausų vykdymą

## Mokymosi tikslai

Baigę šią pamoką, sužinosite, kaip:

• **Atskirti skirtingus DI agentų atminties tipus**, įskaitant veiksmų atmintį, trumpalaikę ir ilgalaikę atmintį bei specializuotas formas kaip persona ir epizodinę atmintį.

• **Įgyvendinti ir valdyti trumpalaikę bei ilgalaikę atmintį DI agentams**, naudojant Semantic Kernel karkasą ir naudodami įrankius kaip Mem0, Cognee, Whiteboard atmintį bei integraciją su Azure AI Search.

• **Suprasti principus, kaip DI agentai savarankiškai tobulėja**, ir kaip tvirta atminties valdymo sistema prisideda prie nuolatinio mokymosi ir prisitaikymo.

## Dirbtinio intelekto agentų atminties supratimas

Iš esmės, **atmintis dirbtinio intelekto agentams reiškia mechanizmus, leidžiančius jiems išlaikyti ir prisiminti informaciją**. Ši informacija gali būti konkrečios detalės apie pokalbį, naudotojo pageidavimai, ankstesni veiksmai ar net išmoktos taisyklės.

Be atminties DI programos dažnai yra bevalstės, tai reiškia, kad kiekviena sąveika prasideda nuo nulio. Tai sukuria pasikartojančią ir dirginančią naudotojo patirtį, kai agentas „pamiršta“ ankstesnį kontekstą ar pageidavimus.

### Kodėl atmintis svarbi?

Agento intelektas glaudžiai susijęs su gebėjimu prisiminti ir panaudoti ankstesnę informaciją. Atmintis leidžia agentams būti:

• **Refleksyviais**: mokytis iš ankstesnių veiksmų ir rezultatų.

• **Interaktyviais**: palaikyti kontekstą vykstančiame pokalbyje.

• **Proaktyviais ir reaguojančiais**: numatyti poreikius arba tinkamai atsakyti remiantis istorine informacija.

• **Autonomiškais**: veikti savarankiškiau remiantis sukauptomis žiniomis.

Atminties įgyvendinimo tikslas yra padaryti agentus **patikimesnius ir pajėgesnius**.

### Atminties tipai

#### Veiklos atmintis

Galvokite apie tai kaip apie užrašų lapelį, kurį agentas naudoja vienos vienetinės užduoties ar minties proceso metu. Ji laiko būtiną informaciją kito žingsnio apskaičiavimui.

DI agentams veiklos atmintis dažnai sugeneruoja svarbiausią informaciją iš pokalbio, net jei visas pokalbių istorijos turinys yra ilgas ar sutrumpintas. Ji koncentruojasi į pagrindinių elementų ištrauką kaip reikalavimai, pasiūlymai, sprendimai ir veiksmai.

**Veiklos atminties pavyzdys**

Kelionės rezervavimo agentui veiklos atmintis gali fiksuoti dabartinį naudotojo užklausą, pavyzdžiui, „noriu užsakyti kelionę į Paryžių“. Šis konkretus reikalavimas laikomas agento tiesioginiame kontekste, kad nukreiptų einamą sąveiką.

#### Trumpalaikė atmintis

Šio tipo atmintis saugo informaciją vienos pokalbio ar sesijos metu. Ji yra dabartinio pokalbio kontekstas, leidžiantis agentui prisiminti ankstesnius dialogo žingsnius.

**Trumpalaikės atminties pavyzdys**

Jeigu naudotojas paklausia: „Kiek kainuotų skrydis į Paryžių?“ ir po to klausia „O kaip dėl nakvynės ten?“, trumpalaikė atmintis užtikrina, kad agentas supranta, jog „ten“ pokalbyje reiškia „Paryžių“.

#### Ilgalaikė atmintis

Tai informacija, kuri išlieka per kelis pokalbius ar sesijas. Tai leidžia agentams prisiminti naudotojo pageidavimus, istorines sąveikas ar bendras žinias ilgą laiką. Tai svarbu personalizavimui.

**Ilgalaikės atminties pavyzdys**

Ilgalaikė atmintis gali saugoti informaciją, kad „Benas mėgsta slidinėjimą ir lauko veiklas, patinka kava su kalnų vaizdu ir nori vengti sudėtingų slidinėjimo trasų dėl ankstesnės traumos“. Ši informacija, gauta iš ankstesnių sąveikų, daro įtaką rekomendacijoms būsimose kelionių planavimo sesijose, darant jas itin suasmenintomis.

#### Asmenybės atmintis

Šis specializuotas atminties tipas padeda agentui sukurti nuoseklią „asmenybę“ arba „personažą“. Tai leidžia agentui prisiminti detales apie save ar savo numatytą vaidmenį, darant sąveikas sklandesnes ir tikslingesnes.

**Asmenybės atminties pavyzdys**

Jei kelionių agentas suprojektuotas kaip „eksperto slidinėjimo planuotojas“, asmenybės atmintis gali stiprinti šį vaidmenį, veikiant atsakymus, kad atitiktų eksperto toną ir žinias.

#### Darbo eiga / Epizodinė atmintis

Ši atmintis saugo veiksmų seką, kurią agentas atlieka sudėtingos užduoties metu, įskaitant sėkmes ir nesėkmes. Tai kaip prisiminti konkrečius „epizodus“ ar ankstesnes patirtis, kad iš jų būtų galima pasimokyti.

**Epizodinės atminties pavyzdys**

Jei agentas bandė užsakyti konkretų skrydį, bet jis buvo neprieinamas, epizodinė atmintis galėtų užfiksuoti šią nesėkmę, leisdama agentui bandyti alternatyvius skrydžius arba informuoti naudotoją apie problemą įžvalgiau vėlesniu bandymu.

#### Objektų atmintis

Tai apima konkrečių objektų (kaip žmonių, vietų ar daiktų) ir įvykių iš pokalbių išgavimą ir įsimintinimą. Tai leidžia agentui sukurti struktūruotą supratimą apie aptartus pagrindinius elementus.

**Objektų atminties pavyzdys**

Iš pokalbio apie ankstesnę kelionę agentas gali išgauti „Paryžių“, „Eifelio bokštą“ ir „vakarienę restorane Le Chat Noir“ kaip objektus. Ateityje agentas gali prisiminti „Le Chat Noir“ ir pasiūlyti padaryti naują rezervaciją ten.

#### Struktūruotas RAG (Retrieval Augmented Generation)

Nors RAG yra platesnė technika, „Struktūruotas RAG“ yra išskiriamas kaip galinga atminties technologija. Ji ištraukia tankią, struktūruotą informaciją iš įvairių šaltinių (pokalbių, el. laiškų, vaizdų) ir naudoja ją padidinti tikslumą, užklausų atitikimą ir greitį atsakymuose. Skirtingai nei klasikinis RAG, kuris remiasi tik semantiniu panašumu, Struktūruotas RAG veikia su informacijos vidine struktūra.

**Struktūruoto RAG pavyzdys**

Užuot tiesiog atitikę raktažodžius, Struktūruotas RAG gali išskirti skrydžio duomenis (tikslą, datą, laiką, avialinijas) iš el. laiško ir juos saugoti struktūrizuotai. Tai leidžia tikslius užklausimus, pavyzdžiui: „Kokį skrydį į Paryžių užsakinėjau antradienį?“

## Atminties įgyvendinimas ir saugojimas

Atminties įgyvendinimas DI agentams apima sistemingą **atminties valdymo** procesą, kuris apima informacijos generavimą, saugojimą, išgavimą, integravimą, atnaujinimą ir netgi „pamiršimą“ (arba trynimą). Išgavimas yra ypač svarbus aspektas.

### Specializuoti atminties įrankiai

#### Mem0

Vienas iš būdų saugoti ir valdyti agento atmintį yra naudoti specializuotus įrankius kaip Mem0. Mem0 veikia kaip nuolatinio atminties sluoksnis, leidžiantis agentams prisiminti svarbias sąveikas, saugoti naudotojų pageidavimus ir faktinį kontekstą bei mokytis iš sėkmių ir nesėkmių laikui bėgant. Idėja yra, kad bevalstis agentas tampa valstingu.

Tai veikia per **dviejų etapų atminties srautą: išgavimą ir atnaujinimą**. Pirmiausia, pranešimai, įtraukti į agento pokalbių giją, siunčiami į Mem0 paslaugą, kuri naudoja didelį kalbos modelį (LLM), apibendrinti pokalbių istoriją ir išgauti naujas atmintis. Vėliau LLM valdomas atnaujinimo etapas nustato, ar pridėti, modifikuoti ar ištrinti šias atmintis, jas saugodamas hibridiniame duomenų saugykloje, kuri gali apimti vektorinę, grafinę ir raktas-reikšmė duomenų bazes. Sistema palaiko įvairius atminties tipus ir gali įtraukti grafinę atmintį santykiams tarp objektų valdyti.

#### Cognee

Kitas galingas būdas yra naudoti **Cognee** – atvirą semantinę atmintį DI agentams, kuri paverčia struktūruotus ir nestruktūruotus duomenis į užklausoms prieinamus žinių grafus remiantis įdėjiniais. Cognee siūlo **dvikryptę saugyklos architektūrą**, apjungiančią vektorinį panašumo paiešką su grafų ryšiais, leidžiančią agentams suprasti ne tik kokia informacija panaši, bet ir kaip sąvokos susijusios viena su kita.

Ji pasižymi puikiu **hibridiniu išgavimu**, jungiančiu vektorinį panašumą, grafinę struktūrą ir LLM samprotavimus – nuo žaliavinių fragmentų paieškos iki grafą suprantančių klausimų atsakymo. Sistema palaiko **gyvą atmintį**, kuri evoliucionuoja ir auga, išlikdama užklausų prieinama kaip vienas sujungtas grafas, palaikantis tiek trumpalaikį sesijos kontekstą, tiek ilgalaikę nuolatinę atmintį.

Cognee bloknotų pamoka ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstruoja šio vientiso atminties sluoksnio kūrimą su praktiniais pavyzdžiais, kaip įkelti įvairius duomenų šaltinius, vizualizuoti žinių grafiką ir užklausyti naudojant skirtingas paieškos strategijas, pritaikytas konkretiems agentų poreikiams.

### Atminties saugojimas su RAG

Be specializuotų įrankių kaip Mem0, galite panaudoti tvirtas paieškos paslaugas, tokias kaip **Azure AI Search** kaip pagrindą atminties saugojimui ir išgavimui, ypač struktūruotam RAG.

Tai leidžia pagrįsti agento atsakymus jūsų pačių duomenimis, užtikrinant tikslesnius ir aktualius atsakymus. Azure AI Search gali būti naudojamas saugoti naudotojo specifines kelionių atmintis, produktų katalogus ar bet kokias kitas domenu specifines žinias.

Azure AI Search palaiko funkcijas kaip **Struktūruotas RAG**, kuris puikiai ištraukia ir išgauna tankią, struktūruotą informaciją iš didelių duomenų rinkinių, kaip pokalbių istorijos, el. laiškai ar net vaizdai. Tai suteikia „žmogiškai pranokstančią tikslumą ir atitikimą“ lyginant su tradiciniu teksto fragmentavimo ir įdėjimo metodais.

## Kaip padaryti DI agentus savarankiškai tobulėjančius

Bendra savarankiškai tobulėjančių agentų praktika apima **„žinių agento“** įvedimą. Šis atskiras agentas stebi pagrindinį pokalbį tarp naudotojo ir pagrindinio agento. Jo vaidmuo yra:

1. **Nustatyti vertingą informaciją**: nuspręsti, ar kurioje nors pokalbio dalyje verta saugoti bendrą žinojimą ar konkrečius naudotojo pageidavimus.

2. **Išgauti ir apibendrinti**: išskirti svarbiausią mokymąsi ar pageidavimą iš pokalbio.

3. **Saugojimas žinių bazėje**: išsaugoti šią informaciją, dažnai vektorinėje duomenų bazėje, kad ją būtų galima ištraukti vėliau.

4. **Papildyti būsimus užklausimus**: kai naudotojas inicijuoja naują užklausą, žinių agentas prideda aktualią saugomą informaciją prie naudotojo užklausos, suteikdamas pagrindiniam agentui svarbų kontekstą (panašiai kaip RAG).

### Atminties optimizavimai

• **Vėlinimo valdymas**: kad nesulėtintų naudotojo sąveikų, pradžioje galima naudoti pigesnį ir greitesnį modelį, kuris greitai patikrina, ar verta saugoti ar išgauti informaciją, ir tik prireikus paleisti sudėtingesnį išgavimą / paiešką.

• **Žinių bazės priežiūra**: didėjant žinių bazei, rečiau naudojama informacija gali būti perkelta į „šaltą saugyklą“ siekiant sumažinti kaštus.

## Turite daugiau klausimų apie agentų atmintį?

Prisijunkite prie [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord), susitikite su kitais mokiniais, dalyvaukite konsultacijose ir gaukite atsakymus į savo klausimus apie DI agentus.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Atsakomybės apribojimas**:  
Šis dokumentas buvo išverstas naudojant dirbtinio intelekto vertimo paslaugą [Co-op Translator](https://github.com/Azure/co-op-translator). Nors siekiame tikslumo, prašome atkreipti dėmesį, kad automatiniai vertimai gali turėti klaidų arba netikslumų. Originalus dokumentas jo gimtąja kalba turėtų būti laikomas autoritetingu šaltiniu. Kritinei informacijai rekomenduojame naudotis profesionalaus žmogaus vertimu. Mes neatsakome už bet kokius nesusipratimus ar neteisingą interpretaciją, kilusią dėl šio vertimo naudojimo.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->