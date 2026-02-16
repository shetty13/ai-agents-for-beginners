# Mälu AI agentidele 
[![Agent Memory](../../../translated_images/et/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Kui räägitakse AI agentide loomise unikaalsetest eelistest, siis käsitletakse peamiselt kahte asja: võimet kasutada tööriistu ülesannete täitmiseks ja võimet aja jooksul paremaks saada. Mälu on aluseks iseenda arendava agendi loomisel, kes suudab meie kasutajatele pakkuda paremaid kogemusi.

Selles õppetükis vaatleme, mis on mälu AI agentide jaoks ja kuidas saame seda hallata ning kasutada meie rakenduste huvides.

## Sissejuhatus

See õppetükk hõlmab:

• **AI agendi mälu mõistmine**: Mis on mälu ja miks see agentidele oluline on.

• **Mälu rakendamine ja salvestamine**: Praktilised meetodid mäluvõime lisamiseks oma AI agentidele, keskendudes lühiajalisele ja pikaajalisele mälule.

• **AI agentide iseenda parandamine**: Kuidas mälu võimaldab agentidel õppida varasematest interaktsioonidest ja aja jooksul paremaks saada.

## Saadaval olevad rakendused

See õppetükk sisaldab kahte põhjalikku märkmiku õpetust:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Rakendab mälu, kasutades Mem0 ja Azure AI Search Semantic Kernel raamistikuga

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Rakendab struktureeritud mälu, kasutades Cognee’d, mis ehitab automaatselt teadmiste graafi, toetatud sissekannete abil, visualiseerib graafi ja võimaldab intelligentset päringut

## Õpieesmärgid

Pärast selle õppetüki läbimist oskad:

• **Erinevaid AI agendi mälutüüpe eristada**, sealhulgas töömälu, lühiajalist ja pikaajalist mälu ning spetsialiseeritud vorme nagu persona ja episoodiline mälu.

• **Rakendada ja hallata lühiajalist ja pikaajalist mälu AI agentidele** Semantic Kernel raamistikuga, kasutades tööriistu nagu Mem0, Cognee, Whiteboard memory ning integreerides Azure AI Searchiga.

• **Mõista iseenda parandavate AI agentide põhimõtteid** ja kuidas tugevad mäluhaldussüsteemid toetavad pidevat õppimist ja kohanemist.

## AI agendi mälu mõistmine

Sisuliselt tähendab **mälu AI agentide jaoks mehhanisme, mis võimaldavad neil säilitada ja meenutada informatsiooni**. See informatsioon võib olla spetsiifilised detailid vestlusest, kasutaja eelistused, varasemad tegevused või isegi õpitud mustrid.

Ilma mäluta on AI rakendused sageli olekuta, mis tähendab, et iga interaktsioon algab nullist. See viib korduva ja frustreeriva kasutajakogemuseni, kus agent "unustab" varasema konteksti või eelistused.

### Miks on mälu oluline?

Agendi intelligentsus on tugevalt seotud selle võimega meenutada ja kasutada varasemat informatsiooni. Mälu võimaldab agentidel olla:

• **Reflektsioonivõimelised**: Õppida varasematest tegevustest ja tulemustest.

• **Interaktiivsed**: Säilitada konteksti jooksva vestluse jooksul.

• **Proaktiivsed ja reaktiivsed**: Eelnevalt vajadusi prognoosida või vastavalt ajaloolistele andmetele õigesti reageerida.

• **Autonoomsed**: Töötada iseseisvalt, tuginedes salvestatud teadmistele.

Mälu rakendamise eesmärk on muuta agendid usaldusväärsemaks ja võimekamaks.

### Mälutüübid

#### Töömälu

Mõtle sellele nagu löökpaberile, mida agent kasutab ühe käimasoleva ülesande või mõttekäigu ajal. See hoiab vahetut informatsiooni, mida on vaja järgmise sammu arvutamiseks.

AI agentide jaoks püüab töömälu sageli vestlusest kinni kõige olulisema info, isegi kui kogu vestluse ajalugu on pikk või lühendatud. Fookuses on võtmeelementide, nagu nõuded, ettepanekud, otsused ja tegevused, väljavõtmine.

**Töömälu näide**

Reisibroneerimise agendi puhul võib töömälu hoida kasutaja hetke päringut, näiteks "Ma tahan broneerida reisi Pariisi". See spetsiifiline nõue on agendi vahetus kontekstis, et juhendada praegust interaktsiooni.

#### Lühiajaline mälu

See mälutüüp säilitab infot kogu ühe vestluse või sessiooni kestel. See on hetkevestluse kontekst, mis võimaldab agentil viidata eelnevatele dialoogi sammudele.

**Lühiajalise mälu näide**

Kui kasutaja küsib, "Kui palju maksab lend Pariisi?" ja järgneb "Aga majutuse hind seal?", tagab lühiajaline mälu, et agent teab, et "seal" viitab samas vestluses "Pariisile".

#### Pikaajaline mälu

See on info, mis püsib mitme vestluse või sessiooni vahel. See võimaldab agentidel meenutada kasutaja eelistusi, ajaloolisi interaktsioone või üldteadmisi pikema aja jooksul. See on oluline personaliseerimise jaoks.

**Pikaajalise mälu näide**

Pikaajalise mälu puhul võib olla salvestatud, et "Ben naudib suusatamist ja välitegevusi, armastab kohvi mäevaatega ning soovib vältida keerulisi suusaradu varasema vigastuse tõttu". See info, õpitud varasematest interaktsioonidest, mõjutab soovitusi tulevastes reisiplaanimise sessioonides, muutes need väga personaalseks.

#### Persona mälu

See spetsialiseerunud mälutüüp aitab agendil arendada järjepidevat "isiksust" või "persona". See võimaldab agendil meeles pidada detaile enda või oma ettenähtud rolli kohta, muutes interaktsioonid ladusamaks ja fokuseeritumaks.

**Persona mälu näide**

Kui reisibüroo agent on kujundatud „eksperdi suusareiside planeerijana“, tugevdab persona mälu seda rolli, mõjutades vastuseid nii, et need sobiksid eksperdi tooniga ja teadmistega.

#### Töövoo/episoodiline mälu

See mälu salvestab sammude järjestuse, mida agent võtab keerulise ülesande ajal, kaasa arvatud õnnestumised ja ebaõnnestumised. See on nagu konkreetsete "episoodide" või varasemate kogemuste meelespidamine, et neist õppida.

**Episoodilise mälu näide**

Kui agent püüdis broneerida kindlat lendu, aga see ebaõnnestus saadavuse puudumise tõttu, võiks episoodiline mälu selle ebaõnnestumise salvestada, võimaldades agendil proovida alternatiivseid lende või teavitada kasutajat probleemist teadlikumal viisil järgmise katse puhul.

#### Entiteedi mälu

See hõlmab konkreetsete entiteetide (inimesed, kohad, esemed) ja sündmuste väljavõtmist ja meeldejätmist vestlustest. See võimaldab agendil ehitada struktureeritud arusaama käsitletud võtmeelementidest.

**Entiteedi mälu näide**

Vestlusest varasema reisi teemal võib agent välja võtta "Pariis", "Eiffeli torn" ja "õhtusöök restoranis Le Chat Noir" kui entiteedid. Tulevases interaktsioonis võib agent meenutada "Le Chat Noir’i" ja pakkuda uut broneeringut seal.

#### Struktureeritud RAG (Retrieval Augmented Generation)

Kuigi RAG on laiem tehnika, on "Struktureeritud RAG" rõhutatud kui võimas mälutehnoloogia. See eraldab tihedat, struktureeritud informatsiooni erinevatest allikatest (vestlustest, e-kirjadest, piltidest) ja kasutab seda vastuste täpsuse, meenutamise ja kiiruse parandamiseks. Erinevalt klassikalisest RAG-st, mis tugineb ainult semantilisele sarnasusele, töötab Struktureeritud RAG info loomuliku struktuuriga.

**Struktureeritud RAG näide**

Selle asemel, et ainult märksõnu sobitada, võiks Struktureeritud RAG parsida lennu detailsed andmed (sihtkoht, kuupäev, kellaaeg, lennufirma) e-kirjast ja salvestada need struktureeritud viisil. See võimaldab täpseid päringuid nagu "Millise lennu ma broneerisin Pariisi teisipäeval?".

## Mälu rakendamine ja salvestamine

Mälu rakendamine AI agentidele hõlmab süsteemset protsessi, mis sisaldab **mäluhaldust**: info genereerimist, salvestamist, päringut, integreerimist, uuendamist ning isegi "unustamist" (kustutamist). Päring on eriti oluline osa.

### Spetsialiseerunud mälu tööriistad

#### Mem0

Üks viis agentide mälu salvestamiseks ja haldamiseks on kasutada spetsiaalset tööriista nagu Mem0. Mem0 toimib püsiva mälukihina, võimaldades agentidel meenutada olulisi interaktsioone, salvestada kasutaja eelistusi ja fakte ning õppida edust ja läbikukkumistest ajas. Ülesandeks on muuta olekuta agendid olekuga agentideks.

See toimib **kahefaasilise mälutöötlusega: info eraldamine ja uuendamine**. Esiteks saadetakse agenti vestluslõime sõnumid Mem0 teenusele, mis kasutab suurt keelemudelit (LLM) vestluse ajaloo kokkuvõtmiseks ja uute mälestuste eraldamiseks. Seejärel otsustab LLM-i juhitud uuendusfaas, kas lisada, muuta või kustutada need mälud, salvestades need hübriidandmebaasi, mis võib sisaldada vektor-, graafi- ja võtme-väärtuse andmebaase. See süsteem toetab mitut mälutüüpi ning võib kaasata graafimälu entiteetidevaheliste suhete haldamiseks.

#### Cognee

Teine võimas lähenemine on kasutada **Cognee’d**, avatud lähtekoodiga semantilist mälu AI agentidele, mis teisendab struktureeritud ja struktureerimata andmed päringuteks sobivateks teadmiste graafideks, mida toetavad embeddings’id. Cognee pakub **kahe poega arhitektuuri**, kombineerides vektorite sarnasusotsingu ja graafisuhted, mis võimaldavad agentidel mõista mitte ainult informatsiooni sarnasust, vaid ka mõistete omavahelist seost.

Ta on suurepärane **hübriidpäringus**, mis segab vektorite sarnasust, graafistruktuuri ja LLM-i mõtlemist – alates toorest tükipesast kuni graafitundliku küsimuste vastamiseni. Süsteem hoiab **elavat mälu**, mis areneb ja kasvab, jäädes samal ajal päringuks ühendatud graafina, toetades nii lühiajalist sessiooni konteksti kui ka pikaajalist püsivat mälu.

Cognee märkmiku õpetus ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstreerib selle ühtse mälukihi ehitamist koos praktiliste näidetega mitmekesiste andmeallikate lisamiseks, teadmiste graafi visualiseerimiseks ja erinevate otsingustrateegiatega päringuteks, mis on kohandatud konkreetsete agentide vajadustele.

### Mälu salvestamine RAG-ga

Spetsiaalsete mälutööriistade kõrval nagu Mem0, saate kasutada tugevaid otsinguteenuseid nagu **Azure AI Search mälu salvestamiseks ja pärimiseks**, eriti struktureeritud RAG puhul.

See võimaldab maandada agendi vastused oma andmetele, tagades asjakohasemad ja täpsemad vastused. Azure AI Searchi saab kasutada kasutajapõhiste reisimälestuste, tooteloendite või muude domeenispetsiifiliste teadmiste hoidmiseks.

Azure AI Search toetab funktsioone nagu **Struktureeritud RAG**, mis on suurepärane tiheda, struktureeritud info eraldamiseks ja pärimiseks suurtest andmehulkadest nagu vestluse ajalugu, e-kirjad või isegi pildid. See pakub "ülitäpsust ja meenutust" võrreldes traditsiooniliste tekstiosi töötlemise ja embeddings'i lähenemistega.

## AI agentide iseparandamine

Levinud muster iseparanevate agentide puhul on kasutada **"teadmisagentti"**. See eraldi agent jälgib peamist vestlust kasutaja ja põhiagendi vahel. Selle roll on:

1. **Tuvastada väärtuslikku informatsiooni**: Otsustada, kas vestluse osa on väärt üldteadmiste või spetsiifilise kasutajapreferentsina salvestamist.

2. **Eraldada ja kokku võtta**: Töötleda vestluse põhisisu või eelistuse kokkuvõtteks.

3. **Salvestada teadmistebaasi**: Hoida väljavõetud info sageli vektoriandmebaasis, et seda hiljem pärida.

4. **Täiendada tulevasi päringuid**: Kui kasutaja esitab uue päringu, pärib teadmisteagent seotud info ja lisab selle kasutaja päringu juurde, pakkudes peamisele agendile olulist konteksti (sarnaselt RAG-ga).

### Mälu optimeerimine

• **Latentsuse juhtimine**: Et vältida kasutaja interaktsioonide aeglustumist, võib alguses kasutada odavamat ja kiirendatud mudelit, mis kontrollib info väärtust, kaasates keerukama eralduse/päringu protsessi vaid vajadusel.

• **Teadmistebaasi hooldus**: Kasvava teadmistebaasi puhul saab harvemini kasutatava infot viia "külma hoiustamise" sektsiooni, et kulusid hallata.

## Kas sul on mäluga AI agentide kohta rohkem küsimusi?

Liitu [Azure AI Foundry Discordiga](https://aka.ms/ai-agents/discord), kohtudes teiste õppijatega, osaledes kontoritundides ja saades oma AI agentide küsimustele vastused.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastutusest loobumine**:
See dokument on tõlgitud kasutades tehisintellektil põhinevat tõlke teenust [Co-op Translator](https://github.com/Azure/co-op-translator). Kuigi püüame tagada täpsust, palun arvestage, et automaatsed tõlked võivad sisaldada vigu või ebatäpsusi. Originaaldokument selle emakeeles on autoriteetne allikas. Olulise teabe puhul soovitatakse kasutada professionaalset inimtõlget. Me ei vastuta selle tõlke kasutamisest tingitud arusaamatuste või valesti mõistmiste eest.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->