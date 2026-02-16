# Kumbukumbu kwa Wakala wa AI  
[![Agent Memory](../../../translated_images/sw/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Wakati wa kujadili faida za kipekee za kuunda Wakala wa AI, mambo mawili kuu yanajadiliwa: uwezo wa kuita zana kumaliza kazi na uwezo wa kuboresha kwa wakati. Kumbukumbu iko msingi wa kuunda wakala anayejiendeleza mwenyewe ambaye anaweza kuunda uzoefu bora kwa watumiaji wetu.

Katika somo hili, tutaangalia ni nini kumbukumbu kwa Wakala wa AI na jinsi tunavyoweza kuisimamia na kuitumia kwa manufaa ya programu zetu.

## Utangulizi

Somo hili litashughulikia:

• **Kuelewa Kumbukumbu ya Wakala wa AI**: Kumbukumbu ni nini na kwa nini ni muhimu kwa wakala.

• **Kutekeleza na Kuhifadhi Kumbukumbu**: Mbinu za vitendo za kuongeza uwezo wa kumbukumbu kwa wakala wako wa AI, ukizingatia kumbukumbu ya muda mfupi na muda mrefu.

• **Kufanya Wakala wa AI Kujijiendeleza**: Jinsi kumbukumbu inavyowezesha wakala kujifunza kutoka kwa mwingiliano wa zamani na kuboresha kwa wakati.

## Utekelezaji Unaopatikana

Somo hili linajumuisha mafunzo mawili ya daftari (notebook) ya kina:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Hutekeleza kumbukumbu kwa kutumia Mem0 na Azure AI Search kwa Mfumo wa Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Hutekeleza kumbukumbu yenye muundo kwa kutumia Cognee, inayojenga jukwaa la maarifa lililoegemea embeddings, kuonyesha grafu, na upatikanaji wa busara

## Malengo ya Kujifunza

Baada ya kumaliza somo hili, utajua jinsi ya:

• **Kutofautisha aina mbalimbali za kumbukumbu za wakala wa AI**, ikiwa ni pamoja na kumbukumbu ya kufanya kazi, ya muda mfupi, na ya muda mrefu, pamoja na aina maalum kama kumbukumbu ya tabia na kumbukumbu ya kipindi.

• **Kutekeleza na kusimamia kumbukumbu ya muda mfupi na muda mrefu kwa wakala wa AI** kwa kutumia mfumo wa Semantic Kernel, ukitumia zana kama Mem0, Cognee, kumbukumbu ya Whiteboard, na unganisho na Azure AI Search.

• **Kuelewa kanuni nyuma ya wakala wa AI wanaojiendeleza wenyewe** na jinsi mifumo thabiti ya usimamizi wa kumbukumbu inavyosaidia kujifunza na kuendana mabadiliko kwa kuendelea.

## Kuelewa Kumbukumbu ya Wakala wa AI

Kwa msingi wake, **kumbukumbu kwa wakala wa AI inahusu mifumo inayowawezesha kuhifadhi na kukumbuka taarifa**. Taarifa hii inaweza kuwa maelezo maalum kuhusu mazungumzo, mapendeleo ya mtumiaji, vitendo vya zamani, au hata mifumo iliyojifunza.

Bila kumbukumbu, programu za AI mara nyingi hazina hali, ambayo ina maana kila mwingiliano huanza kutoka mwanzo. Hii husababisha uzoefu wa mtumiaji unaorudia na kusumbua ambapo wakala "anasahau" muktadha wa awali au mapendeleo.

### Kwanini Kumbukumbu ni Muhimu?

Akili ya wakala imeunganishwa sana na uwezo wake wa kukumbuka na kutumia taarifa za zamani. Kumbukumbu hufanya wakala kuwa:

• **Wa kutafakari**: Kujifunza kutoka kwa vitendo na matokeo ya zamani.

• **Wa kuingiliana**: Kuhifadhi muktadha wa mazungumzo yanayoendelea.

• **Wa kujiandaa na kuwajibika**: Kutegemea mahitaji au kujibu ipasavyo kulingana na data ya historia.

• **Huru**: Kuendesha kazi kwa uhuru zaidi kwa kutumia maarifa yaliyohifadhiwa.

Lengo la kutekeleza kumbukumbu ni kufanya wakala wawe **wa kuaminika na wenye uwezo zaidi**.

### Aina za Kumbukumbu

#### Kumbukumbu ya Kufanya Kazi

Fikiria hii kama karatasi ya kuandika ya dawati ambayo wakala hutumia wakati wa kazi moja inayochukua muda au mchakato wa kufikiri. Inahifadhi taarifa za papo hapo zinazohitajika kwa hatua inayofuata.

Kwa wakala wa AI, kumbukumbu ya kufanya kazi mara nyingi huhifadhi taarifa muhimu kutoka kwa mazungumzo, hata kama historia nzima ya mazungumzo ni ndefu au imekatwa. Inazingatia kutoa vipengele muhimu kama mahitaji, mapendekezo, maamuzi, na vitendo.

**Mfano wa Kumbukumbu ya Kufanya Kazi**

Katika wakala wa booking wa kusafiri, kumbukumbu ya kufanya kazi inaweza kushikilia ombi la mtumiaji kwa sasa, kama "Nataka kutia booking safari ya kwenda Paris". Hii mahitaji maalum huhifadhiwa katika muktadha wa papo hapo wa wakala kumsaidia kuongoza mwingiliano wa sasa.

#### Kumbukumbu ya Muda Mfupi

Aina hii ya kumbukumbu huhifadhi taarifa kwa muda wa mazungumzo au kikao kimoja. Ni muktadha wa mazungumzo ya sasa, kuwezesha wakala kurejea nyuma kwa mizunguko ya awali katika mazungumzo.

**Mfano wa Kumbukumbu ya Muda Mfupi**

Ikiwa mtumiaji anauliza, "Ghara ya ndege kwenda Paris ni kiasi gani?" na kisha anauliza, "Je kuhusu malazi huko?", kumbukumbu ya muda mfupi huhakikisha wakala anajua "huko" inarejelea "Paris" ndani ya mazungumzo hayo hayo.

#### Kumbukumbu ya Muda Mrefu

Hii ni taarifa inayodumu katika mazungumzo au vikao vingi. Huiruhusu wakala kukumbuka mapendeleo ya mtumiaji, mwingiliano wa kihistoria, au maarifa ya jumla kwa kipindi kirefu. Hii ni muhimu kwa ubinafsishaji.

**Mfano wa Kumbukumbu ya Muda Mrefu**

Kumbukumbu ya muda mrefu inaweza kuhifadhi kuwa "Ben anafurahia skiing na shughuli za nje, anapenda kahawa akiwa na muonekano wa mlima, na anataka kuepuka nyimbo za skiing za juu kutokana na jeraha la zamani". Taarifa hii, iliyojifunzwa kutoka mwingiliano wa awali, inaathiri mapendekezo katika mipango ya kusafiri ya baadaye, kufanya ziwe za kibinafsi sana.

#### Kumbukumbu ya Tabia

Aina hii maalum ya kumbukumbu husaidia wakala kukuza "tabia" au "persona" iliyokamilika. Huiruhusu wakala kukumbuka maelezo kuhusu yeye mwenyewe au jukumu lake lililokusudiwa, na kufanya mwingiliano kuwa rahisi na wa kipekee.

**Mfano wa Kumbukumbu ya Tabia**

Ikiwa wakala wa kusafiri ameundwa kuwa "mtaalamu wa kupanga skiing," kumbukumbu ya tabia inaweza kuimarisha jukumu hili, kuathiri majibu yake ili yaendane na sauti na maarifa ya mtaalamu.

#### Kumbukumbu ya Mtiririko/Kipindi

Kumbukumbu hii huhifadhi mfuatano wa hatua ambazo wakala huchukua wakati wa kazi tata, ikijumuisha mafanikio na matatizo. Ni kama kukumbuka "vipindi" maalum au uzoefu wa zamani kwa ajili ya kujifunza.

**Mfano wa Kumbukumbu ya Kipindi**

Ikiwa wakala alijaribu kutia booking ndege maalum lakini haikuweza kufanikisha kwa sababu ya kukosekana, kumbukumbu ya kipindi inaweza kurekodi kushindwa huku, kuruhusu wakala kujaribu ndege mbadala au kumjulisha mtumiaji kuhusu tatizo kwa njia iliyo na taarifa zaidi wakati wa jaribio lijalo.

#### Kumbukumbu ya Kielelezo

Hii inahusisha kutoa na kukumbuka vitu maalum (kama watu, maeneo, au vitu) na matukio kutoka kwa mazungumzo. Huiruhusu wakala kujenga ufahamu wenye muundo wa vipengele muhimu vilivyojadiliwa.

**Mfano wa Kumbukumbu ya Kielelezo**

Kutoka kwa mazungumzo kuhusu safari ya zamani, wakala anaweza kutoa "Paris," "Mnara wa Eiffel," na "chakula cha jioni kwenye mgahawa wa Le Chat Noir" kama vitu. Katika mwingiliano wa baadaye, wakala anaweza kukumbuka "Le Chat Noir" na kutoa kufanya uhifadhi mpya hapo.

#### RAG ya Muundo (Retrieval Augmented Generation)

Ingawa RAG ni mbinu pana, "RAG ya Muundo" imetajwa kama teknolojia ya kumbukumbu yenye nguvu. Hutolewa taarifa nzito, zenye muundo kutoka vyanzo mbalimbali (mazungumzo, barua pepe, picha) na kuitumia kuboresha usahihi, kumbukumbu, na kasi ya majibu. Tofauti na RAG ya kawaida inayotegemea ulinganifu wa semantiki pekee, RAG ya Muundo hufanya kazi na muundo wa asili wa taarifa.

**Mfano wa RAG ya Muundo**

Badala ya kulinganisha maneno muhimu tu, RAG ya Muundo inaweza kuchambua maelezo ya ndege (mwendokasi, tarehe, muda, shirika la ndege) kutoka kwa barua pepe na kuyaweka kwa muundo maalum. Hii huruhusu maswali kamili kama "Ndege gani nilitibia booking kwenda Paris siku ya Jumanne?"

## Kutekeleza na Kuhifadhi Kumbukumbu

Kutekeleza kumbukumbu kwa wakala wa AI kunahusu mchakato wa kimfumo wa **usimamizi wa kumbukumbu**, ambao unajumuisha kuzalisha, kuhifadhi, kupata, kuunganisha, kusasisha, na hata "kusahau" (au kufuta) taarifa. Upataji ni sehemu muhimu sana.

### Zana Maalum za Kumbukumbu

#### Mem0

Njia moja ya kuhifadhi na kusimamia kumbukumbu za wakala ni kutumia zana maalum kama Mem0. Mem0 hufanya kazi kama safu ya kumbukumbu inayodumu, ikiruhusu wakala kukumbuka mwingiliano muhimu, kuhifadhi mapendeleo ya mtumiaji na muktadha wa ukweli, na kujifunza kutoka kwa mafanikio na kushindwa kwa muda. Wazo hapa ni kwamba wakala wasio na hali wanageuka kuwa wenye hali.

Inafanya kazi kupitia **hatua mbili za mchakato wa kumbukumbu: kutoa na kusasisha**. Kwanza, ujumbe unaoingizwa kwenye muktadha wa wakala hutumwa kwa huduma ya Mem0, ambayo hutumia Mfano Mkubwa wa Lugha (LLM) kufupisha historia ya mazungumzo na kutoa kumbukumbu mpya. Baadaye, awamu ya kusasisha inayofanywa na LLM huchagua ikiwa kuongeza, kubadilisha, au kufuta kumbukumbu hizi, zikihifadhiwa katika duka la data lenye mchanganyiko wa hifadhidata za vector, grafu, na key-value. Mfumo huu pia unaunga mkono aina mbalimbali za kumbukumbu na unaweza kujumuisha kumbukumbu za grafu kwa kusimamia uhusiano kati ya vitu.

#### Cognee

Njia nyingine yenye nguvu ni kutumia **Cognee**, kumbukumbu ya semantiki ya chanzo wazi kwa wakala wa AI inayobadilisha data ya muundo na isiyo na muundo kuwa grafu za maarifa zinazoweza kufuatiliwa kwa msaada wa embeddings. Cognee hutoa **miundo miwili ya kuhifadhi** inayochanganya utafutaji wa ulinganifu wa vector na uhusiano wa grafu, kuwezesha wakala kuelewa si tu taarifa zinazofanana, bali jinsi dhana zinavyohusiana.

Inazidi kufaa katika **upataji wa mseto** unaochanganya ulinganifu wa vector, muundo wa grafu, na mantiki ya LLM - kutoka kutafuta vipande vya awali hadi kujibu maswali kwa ufahamu wa grafu. Mfumo huu unaendelea kumbukumbu inayostawi na kukuwa huku ukibaki kuwa na uwezo wa kufutiwa kama grafu moja iliyounganishwa, ukitoa muktadha wa kikao cha muda mfupi na kumbukumbu ya muda mrefu inayodumu.

Mafunzo ya daftari la Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) yanaonyesha ujenzi wa safu hii ya kumbukumbu pamoja, na mifano ya vitendo ya kuingiza vyanzo tofauti vya data, kuonyesha grafu ya maarifa, na kuomba kwa mikakati tofauti ya utafutaji inayokidhi mahitaji maalum ya wakala.

### Kuhifadhi Kumbukumbu kwa RAG

Zaidi ya zana maalum za kumbukumbu kama mem0 , unaweza kutumia huduma imara za utafutaji kama **Azure AI Search kama msingi wa kuhifadhi na kupata kumbukumbu**, hasa kwa RAG yenye muundo.

Hii inaruhusu kuweka majibu ya wakala yako juu ya data yako mwenyewe, kuhakikisha majibu yanayohusiana na sahihi zaidi. Azure AI Search inaweza kutumika kuhifadhi kumbukumbu za safari za mtumiaji, makatalogi ya bidhaa, au maarifa yoyote maalum ya eneo.

Azure AI Search inaunga mkono uwezo kama **Structured RAG**, inayobobea katika kutoa na kupata taarifa nzito, zenye muundo kutoka kwa seti kubwa za data kama historia za mazungumzo, barua pepe, au hata picha. Hii huruhusu "usahihi na kumbukumbu wa kiwango cha juu" ikilinganishwa na mbinu za kawaida za kugawanya maandishi na embeddings.

## Kufanya Wakala wa AI Kujiboresha Kwawe

Mfumo wa kawaida kwa wakala wanaojiendeleza ni kuanzisha **“wakala wa maarifa”**. Wakala huyu wa pekee hufuata mazungumzo kuu kati ya mtumiaji na wakala mkuu. Jukumu lake ni:

1. **Kubaini taarifa yenye thamani**: Kuamua kama sehemu yoyote ya mazungumzo inastahili kuhifadhiwa kama maarifa ya jumla au upendeleo maalum wa mtumiaji.

2. **Kutoa na kufupisha**: Kuchambua maarifa muhimu au upendeleo kutoka kwa mazungumzo.

3. **Kuhifadhi katika msingi wa maarifa**: Kuhifadhi taarifa hii iliyotolewa, mara nyingi katika hifadhidata ya vector, ili iweze kupatikana baadaye.

4. **Kuongeza kwenye maswali ya baadaye**: Wakati mtumiaji anapoanzisha swali jipya, wakala wa maarifa hupata taarifa husika zilizohifadhiwa na kuziambatisha kwenye kauli ya mtumiaji, kutoa muktadha muhimu kwa wakala mkuu (kama RAG).

### Uboreshaji wa Kumbukumbu

• **Usimamizi wa Wakati wa Jibu (Latency)**: Ili kuepuka kuchelewesha mwingiliano wa mtumiaji, mfano wa gharama nafuu na haraka unaweza kutumika awali kwa haraka kuangalia kama taarifa ni ya thamani kuhifadhiwa au kupatikana, kisha mchakato mgumu wa kutoa/kuupata taarifa mtumike tu inapohitajika.

• **Matengenezo ya Msingi wa Maarifa**: Kwa msingi wa maarifa unaoendelea kuongezeka, taarifa zisizotumika mara kwa mara zinaweza kuhamishwa hadi "hifadhi ya baridi" kudhibiti gharama.

## Una Maswali Zaidi Kuhusu Kumbukumbu ya Wakala?

Jiunge na [Discord ya Azure AI Foundry](https://aka.ms/ai-agents/discord) kutana na wanafunzi wengine, hudhuria saa za ofisi na upate majibu kwa maswali yako kuhusu Wakala wa AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Angalizo**:
Nyaraka hii imetafsiriwa kwa kutumia huduma ya tafsiri ya AI [Co-op Translator](https://github.com/Azure/co-op-translator). Ingawa tunajitahidi kwa usahihi, tafadhali fahamu kwamba tafsiri za kiotomatiki zinaweza kuwa na makosa au upungufu. Nyaraka asili katika lugha yake ya asili inapaswa kuchukuliwa kama chanzo cha mamlaka. Kwa taarifa muhimu, tafsiri ya kitaalamu ya binadamu inashauriwa. Hatubebeki lawama kwa maelewano mabaya au ufafanuzi usio sahihi unaotokana na matumizi ya tafsiri hii.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->