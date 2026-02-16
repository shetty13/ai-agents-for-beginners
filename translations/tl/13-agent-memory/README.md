# Memory para sa AI Agents 
[![Agent Memory](../../../translated_images/tl/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Kapag pinag-uusapan ang mga natatanging benepisyo ng paglikha ng AI Agents, dalawang bagay ang kadalasang tinatalakay: ang kakayahang tumawag ng mga tool para tapusin ang mga gawain at ang kakayahang umunlad sa paglipas ng panahon. Ang memorya ay nasa pundasyon ng paglikha ng self-improving na ahente na makagagawa ng mas magagandang karanasan para sa ating mga gumagamit.

Sa araling ito, tatalakayin natin kung ano ang memorya para sa AI Agents at kung paano natin ito mapapangasiwaan at magagamit para sa kapakinabangan ng ating mga aplikasyon.

## Panimula

Saklaw ng araling ito:

• **Pag-unawa sa AI Agent Memory**: Ano ang memorya at bakit mahalaga ito para sa mga ahente.

• **Pagsasakatuparan at Pag-iimbak ng Memorya**: Mga praktikal na paraan para magdagdag ng memory capabilities sa iyong AI agents, na nakatuon sa short-term at long-term memory.

• **Paggawa ng AI Agents na Self-Improving**: Paano pinapayagan ng memorya ang mga ahente na matuto mula sa mga nakaraang interaksyon at umunlad sa paglipas ng panahon.

## Mga Available na Implementasyon

Kasama sa araling ito ang dalawang komprehensibong notebook tutorials:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Nagsasakatuparan ng memorya gamit ang Mem0 at Azure AI Search gamit ang Semantic Kernel framework

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Nagsasakatuparan ng istrukturadong memorya gamit ang Cognee, awtomatikong bumubuo ng knowledge graph na suportado ng embeddings, nagvi-visualize ng graph, at intelihenteng retrieval

## Mga Layunin sa Pagkatuto

Pagkatapos makumpleto ang araling ito, malalaman mo kung paano:

• **I-iba-iba ang iba't ibang uri ng AI agent memory**, kabilang ang working, short-term, at long-term memory, pati na rin ang mga espesyalisadong anyo tulad ng persona at episodic memory.

• **Isagawa at pamahalaan ang short-term at long-term memory para sa AI agents** gamit ang Semantic Kernel framework, na gumagamit ng mga tool tulad ng Mem0, Cognee, Whiteboard memory, at pag-integrate sa Azure AI Search.

• **Unawain ang mga prinsipyo sa likod ng self-improving AI agents** at kung paano nakakatulong ang matatag na mga sistema ng pamamahala ng memorya sa patuloy na pag-aaral at pag-angkop.

## Pag-unawa sa AI Agent Memory

Sa pinaka-puso nito, **ang memorya para sa AI agents ay tumutukoy sa mga mekanismo na nagpapahintulot sa kanila na mag-imbak at magalala ng impormasyon**. Ang impormasyong ito ay maaaring mga partikular na detalye tungkol sa isang pag-uusap, mga kagustuhan ng gumagamit, mga nakaraang aksyon, o kahit na mga natutunang pattern.

Kung walang memorya, madalas stateless ang mga AI application, ibig sabihin bawat interaksyon ay nagsisimula sa simula. Nagdudulot ito ng paulit-ulit at nakakainis na karanasan para sa gumagamit kung saan "nakakalimot" ang ahente sa mga naunang konteksto o kagustuhan.

### Bakit Mahalaga ang Memorya?

Malalim ang pagkakaugnay ng katalinuhan ng isang ahente sa kakayahan nitong alalahanin at gamitin ang mga nakaraang impormasyon. Pinapayagan ng memorya ang mga ahente na maging:

• **Reflective**: Matuto mula sa mga nakaraang aksyon at kinalabasan.

• **Interactive**: Panatilihin ang konteksto sa isang patuloy na pag-uusap.

• **Proactive at Reactive**: Asahan ang mga pangangailangan o tumugon nang naaayon batay sa nakaraang datos.

• **Autonomous**: Gumana nang mas independyente sa pamamagitan ng paggamit ng naka-imbak na kaalaman.

Ang layunin ng pagsasakatuparan ng memorya ay gawing mas **mapagkakatiwalaan at may kakayahan** ang mga ahente.

### Mga Uri ng Memorya

#### Working Memory

Isipin ito bilang isang piraso ng scratch paper na ginagamit ng ahente habang nagsasagawa ng isang gawain o pag-iisip na nagpapatuloy. Dito itinatago ang agarang kinakailangang impormasyon upang makalkula ang susunod na hakbang.

Para sa AI agents, kadalasang kinukuha ng working memory ang pinaka-mahahalagang impormasyon mula sa isang pag-uusap, kahit na mahaba o putol ang buong chat history. Nakatuon ito sa pagkuha ng mga mahahalagang elemento tulad ng mga pangangailangan, panukala, desisyon, at mga aksyon.

**Halimbawa ng Working Memory**

Sa isang travel booking agent, maaaring i-capture ng working memory ang kasalukuyang kahilingan ng gumagamit, tulad ng "Gusto kong mag-book ng biyahe sa Paris". Ang espesipikong pangangailangan na ito ay hinahawakan sa agarang konteksto ng ahente upang gabayan ang kasalukuyang interaksyon.

#### Short Term Memory

Ang uri ng memoryang ito ay nagtatago ng impormasyon para sa tagal ng isang pag-uusap o sesyon. Ito ang konteksto ng kasalukuyang usapan, na nagbibigay-daan sa ahente na tumukoy muli sa mga nakaraang bahagi ng dayalogo.

**Halimbawa ng Short Term Memory**

Kung ang isang gumagamit ay nagtanong, "Magkano ang flight papuntang Paris?" at sumunod na nagtanong, "Paano naman ang tirahan doon?", sinisiguro ng short-term memory na alam ng ahente na ang "doon" ay tumutukoy sa "Paris" sa loob ng iisang pag-uusap.

#### Long Term Memory

Ito ay impormasyon na nananatili sa maraming mga pag-uusap o sesyon. Pinapayagan nito ang mga ahente na maalala ang mga kagustuhan ng gumagamit, mga nakaraang interaksyon, o pangkalahatang kaalaman sa mahabang panahon. Mahalaga ito para sa personalisasyon.

**Halimbawa ng Long Term Memory**

Maaaring itago ng long-term memory na "Si Ben ay mahilig sa skiing at mga outdoor na aktibidad, gusto ng kape na may tanawin ng bundok, at nais iwasan ang mga advanced na ski slope dahil sa isang dating pinsala". Ang impormasyong ito, na natutunan mula sa mga nakaraang interaksyon, ay nakakaapekto sa mga rekomendasyon sa mga susunod na sesyon ng pagpaplano ng biyahe, na ginagawa silang mas personalisado.

#### Persona Memory

Ang espesyalisadong uri ng memoryang ito ay tumutulong sa ahente na magkaroon ng isang konsistenteng "personalidad" o "persona". Pinapayagan nito ang ahente na maalala ang mga detalye tungkol sa sarili nito o sa kanyang nakatalagang papel, na ginagawa ang mga interaksyon na mas maayos at nakatuon.

**Halimbawa ng Persona Memory**

Kung ang travel agent ay dinisenyo bilang "ekspertong planner ng ski," maaaring palakasin ng persona memory ang papel na ito, na nakakaapekto sa mga tugon nito upang tumugma sa tono at kaalaman ng isang eksperto.

#### Workflow/Episodic Memory

Itong memorya ay nagtatago ng pagkakasunod-sunod ng mga hakbang na ginawa ng ahente sa isang komplikadong gawain, kabilang ang mga tagumpay at kabiguan. Para itong pag-alala ng mga partikular na "episode" o mga nakaraang karanasan upang matuto mula dito.

**Halimbawa ng Episodic Memory**

Kung sinubukan ng ahente na mag-book ng isang partikular na flight ngunit nabigo dahil sa hindi pagkakaroon, maaaring i-record ng episodic memory ang pagkabigong ito, na nagbibigay-daan sa ahente na subukan ang mga alternatibong flight o ipaalam sa gumagamit ang tungkol sa isyu sa mas maalam na paraan sa susunod na pagtatangka.

#### Entity Memory

Ito ay may kaugnayan sa pagkuha at pag-alaala ng mga partikular na entidad (tulad ng mga tao, lugar, o bagay) at mga pangyayari mula sa mga pag-uusap. Pinapayagan nito ang ahente na bumuo ng isang istrakturadong pag-unawa sa mga mahahalagang elemento na tinalakay.

**Halimbawa ng Entity Memory**

Mula sa isang pag-uusap tungkol sa nakaraang biyahe, maaaring kuhanin ng ahente ang "Paris," "Eiffel Tower," at "hapunan sa Le Chat Noir restaurant" bilang mga entidad. Sa isang susunod na interaksyon, maaaring maalala ng ahente ang "Le Chat Noir" at mag-alok na gumawa ng bagong reserbasyon doon.

#### Structured RAG (Retrieval Augmented Generation)

Habang ang RAG ay isang mas malawak na teknik, ang "Structured RAG" ay pinag-highlight bilang isang makapangyarihang teknolohiya ng memorya. Kinukuha nito ang siksik, istrukturadong impormasyon mula sa iba't ibang mga pinanggalingan (mga pag-uusap, email, larawan) at ginagamit ito upang mapahusay ang katumpakan, recall, at bilis sa mga tugon. Hindi tulad ng klasikong RAG na nakabatay lamang sa semantic similarity, ang Structured RAG ay nagtatrabaho gamit ang likas na istruktura ng impormasyon.

**Halimbawa ng Structured RAG**

Sa halip na tumugma lang sa mga keyword, maaaring i-parse ng Structured RAG ang mga detalye ng flight (destinasyon, petsa, oras, airline) mula sa isang email at iimbak ito sa istrukturadong paraan. Nagbibigay ito ng tumpak na mga query tulad ng "Anong flight ang na-book ko papuntang Paris noong Martes?"

## Pagsasakatuparan at Pag-iimbak ng Memorya

Ang pagsasakatuparan ng memorya para sa AI agents ay nangangailangan ng sistematikong proseso ng **pamamahala ng memorya**, na kinabibilangan ng pagbuo, pag-iimbak, pagkuha, pagsasama, pag-update, at maging ng "pagkawala" (o pagtanggal) ng impormasyon. Ang retrieval ay isang partikular na mahalagang aspeto.

### Espesyalisadong Mga Tool para sa Memorya

#### Mem0

Isang paraan upang mag-imbak at pamahalaan ang memorya ng ahente ay gamit ang espesyalisadong mga tool tulad ng Mem0. Ang Mem0 ay gumagana bilang isang persistent memory layer, na nagpapahintulot sa mga ahente na maalala ang mga kaugnay na interaksyon, itago ang mga kagustuhan ng gumagamit at totoong konteksto, at matuto mula sa mga tagumpay at kabiguan sa paglipas ng panahon. Ang ideya dito ay na ang mga stateless na ahente ay magiging stateful.

Ito ay gumagana sa pamamagitan ng isang **dalawang-phase memory pipeline: extraction at update**. Una, ang mga mensahe na idinadagdag sa thread ng ahente ay ipinapadala sa serbisyo ng Mem0, na gumagamit ng Large Language Model (LLM) upang lagumin ang kasaysayan ng pag-uusap at kunin ang mga bagong memorya. Kasunod nito, isang LLM-driven update phase ang tumutukoy kung magdadagdag, magbabago, o magtatanggal ng mga memorya, iniimbak ang mga ito sa isang hybrid data store na maaaring magsama ng vector, graph, at key-value na mga database. Sinusuportahan din ng sistemang ito ang iba't ibang uri ng memorya at maaaring mag-incorporate ng graph memory para pamahalaan ang mga relasyon sa pagitan ng mga entidad.

#### Cognee

Isa pang makapangyarihang lapit ay ang paggamit ng **Cognee**, isang open-source semantic memory para sa AI agents na nagko-convert ng istrukturado at hindi istrukturadong data sa queryable knowledge graphs na suportado ng embeddings. Nagbibigay ang Cognee ng **dual-store architecture** na pinagsasama ang vector similarity search at graph relationships, na nagpapahintulot sa mga ahente na maunawaan hindi lamang kung ano ang magkakapareho, kundi kung paano nag-uugnay ang mga konsepto sa isa't isa.

Mahusay ito sa **hybrid retrieval** na pinagsasama ang vector similarity, graph structure, at LLM reasoning - mula sa raw chunk lookup hanggang sa graph-aware na pagsagot sa mga tanong. Pinananatili ng sistema ang **living memory** na nag-e-evolve at lumalago habang nananatiling queryable bilang isang konektadong graph, na sumusuporta sa parehong short-term session context at long-term persistent memory.

Ipinapakita ng Cognee notebook tutorial ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) ang pagtatayo ng unified memory layer na ito, na may mga praktikal na halimbawa ng pag-ingest ng iba't ibang data source, pag-visualize ng knowledge graph, at pag-query gamit ang iba't ibang mga search strategies na iniakma sa mga partikular na pangangailangan ng ahente.

### Pag-iimbak ng Memorya gamit ang RAG

Bukod sa mga espesyalisadong memory tool tulad ng mem0 , maaari mong gamitin ang matibay na mga search service tulad ng **Azure AI Search bilang backend para sa pag-iimbak at pagkuha ng mga memorya**, lalo na para sa structured RAG.

Pinapayagan ka nitong gawing grounded ang mga tugon ng iyong ahente sa sarili mong data, na tinitiyak ang mas may kaugnayan at tumpak na mga sagot. Maaaring gamitin ang Azure AI Search para i-imbak ang mga user-specific travel memories, product catalogs, o anumang domain-specific knowledge.

Sinusuportahan ng Azure AI Search ang mga kakayahan tulad ng **Structured RAG**, na mahusay sa pagkuha at paggamit ng siksik, istrukturadong impormasyon mula sa malalaking dataset tulad ng kasaysayan ng pag-uusap, email, o kahit mga larawan. Nagbibigay ito ng "superhuman precision and recall" kumpara sa tradisyonal na text chunking at embedding na mga pamamaraan.

## Paggawa ng AI Agents na Self-Improve

Isang karaniwang pattern para sa self-improving agents ay ang pagpapakilala ng isang **"knowledge agent"**. Ang hiwalay na ahenteng ito ay nagmamasid sa pangunahing pag-uusap sa pagitan ng gumagamit at ng pangunahing ahente. Ang layunin nito ay:

1. **Kilalanin ang mahalagang impormasyon**: Tukuyin kung alinmang bahagi ng pag-uusap ang karapat-dapat i-save bilang pangkalahatang kaalaman o partikular na kagustuhan ng gumagamit.

2. **I-extract at lagumin**: Kunin ang mahahalagang aral o kagustuhan mula sa pag-uusap.

3. **I-imbak sa knowledge base**: Itabi ang nakuha na impormasyon, madalas sa isang vector database, upang madaling makuha pagkatapos.

4. **Dagdagan ang mga susunod na query**: Kapag ang gumagamit ay nagsimula ng bagong query, kinukuha ng knowledge agent ang mga kaugnay na nakaimbak na impormasyon at idinadagdag ito sa prompt ng gumagamit, nagbibigay ng mahalagang konteksto sa pangunahing ahente (katulad ng RAG).

### Mga Optimisasyon para sa Memorya

• **Pamahalaan ang Latency**: Upang maiwasan ang pagpapabagal ng interaksyon ng gumagamit, maaaring gamitin muna ang mas mura at mabilis na modelo upang mabilis na siyasatin kung mahalaga bang i-imbak o hanapin ang impormasyon, at saka lamang tawagin ang mas komplikadong proseso ng extraction/retrieval kung kinakailangan.

• **Pangangalaga sa Knowledge Base**: Para sa lumalaking knowledge base, ang mga impormasyong hindi madalas gamitin ay maaaring ilipat sa "cold storage" upang mabawasan ang gastos.

## May Karagdagang Mga Tanong Tungkol sa Agent Memory?

Sumali sa [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) upang makilala ang ibang mga nag-aaral, dumalo sa office hours, at sagutin ang iyong mga tanong tungkol sa AI Agents.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Paunawa**:
Ang dokumentong ito ay isinalin gamit ang serbisyong AI na pagsasalin na [Co-op Translator](https://github.com/Azure/co-op-translator). Bagamat pinagsisikapan naming maging tumpak, pakatandaan na maaaring may mga pagkakamali o hindi pagkakatotoo ang mga awtomatikong pagsasalin. Ang orihinal na dokumento sa orihinal nitong wika ang dapat ituring na opisyal na sanggunian. Para sa mahahalagang impormasyon, inirerekomenda ang propesyonal na pagsasalin ng tao. Hindi kami mananagot sa anumang hindi pagkakaunawaan o maling interpretasyon na maaaring magmula sa paggamit ng pagsasaling ito.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->