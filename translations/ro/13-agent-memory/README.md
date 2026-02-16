# Memoria pentru Agenții AI 
[![Agent Memory](../../../translated_images/ro/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Când discutăm despre beneficiile unice ale creării Agenților AI, două lucruri sunt în principal dezbătute: capacitatea de a apela instrumente pentru a finaliza sarcini și capacitatea de a se îmbunătăți în timp. Memoria este la baza creării unui agent care se auto-îmbunătățește și care poate crea experiențe mai bune pentru utilizatorii noștri.

În această lecție, vom analiza ce este memoria pentru Agenții AI și cum o putem gestiona și folosi în beneficiul aplicațiilor noastre.

## Introducere

Această lecție va acoperi:

• **Înțelegerea Memoriei Agenților AI**: Ce este memoria și de ce este esențială pentru agenți.

• **Implementarea și Stocarea Memoriei**: Metode practice pentru adăugarea capabilităților de memorie agenților AI, concentrându-ne pe memoria pe termen scurt și pe termen lung.

• **Făcând Agenții AI să se Auto-Îmbunătățească**: Cum memoria permite agenților să învețe din interacțiunile anterioare și să se îmbunătățească în timp.

## Implementări Disponibile

Această lecție include două tutoriale cu notebook-uri cuprinzătoare:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementează memoria folosind Mem0 și Azure AI Search cu cadrul Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementează memoria structurată folosind Cognee, construind automat un graf de cunoștințe susținut de embeddings, vizualizând graful și recuperarea inteligentă

## Obiectivele de Învățare

După ce vei finaliza această lecție, vei ști să:

• **Diferențiezi între diverse tipuri de memorie pentru agenții AI**, inclusiv memoria de lucru, pe termen scurt și lung, precum și forme specializate precum memoria de persoană și episodică.

• **Implementezi și gestionezi memoria pe termen scurt și lung pentru agenții AI** folosind cadrul Semantic Kernel, valorificând instrumente precum Mem0, Cognee, memoria Whiteboard și integrând cu Azure AI Search.

• **Înțelegi principiile din spatele agenților AI auto-îmbunătățitori** și cum sistemele robuste de gestionare a memoriei contribuie la învățarea și adaptarea continuă.

## Înțelegerea Memoriei Agenților AI

În esență, **memoria pentru agenții AI se referă la mecanismele care le permit să rețină și să recupereze informații**. Aceste informații pot fi detalii specifice despre o conversație, preferințele utilizatorului, acțiuni anterioare sau chiar modele învățate.

Fără memorie, aplicațiile AI sunt adesea fără stare, ceea ce înseamnă că fiecare interacțiune pornește de la zero. Aceasta conduce la o experiență repetitivă și frustrantă pentru utilizator, în care agentul „uită” contextul sau preferințele anterioare.

### De ce este importantă memoria?

Inteligența unui agent este profund legată de abilitatea sa de a-și aminti și utiliza informații din trecut. Memoria permite agenților să fie:

• **Reflectivi**: învățând din acțiunile și rezultatele trecute.

• **Interactivi**: menținând contextul pe parcursul unei conversații în desfășurare.

• **Proactivi și Reacționari**: anticipând nevoile sau reacționând adecvat pe baza datelor istorice.

• **Autonomi**: operând mai independent, bazându-se pe cunoștințele stocate.

Scopul implementării memoriei este de a face agenții mai **de încredere și capabili**.

### Tipuri de Memorie

#### Memoria de Lucru

Gândește-te la aceasta ca la o foaie de hârtie pe care agentul o folosește în timpul unei sarcini sau unui proces de gândire în desfășurare. Ea reține informațiile imediate necesare pentru a calcula pasul următor.

Pentru agenții AI, memoria de lucru adesea captează cele mai relevante informații dintr-o conversație, chiar dacă istoricul întreg al chatului este lung sau este trunchiat. Se concentrează pe extragerea elementelor cheie precum cerințe, propuneri, decizii și acțiuni.

**Exemplu de Memorie de Lucru**

Într-un agent de rezervare călătorii, memoria de lucru poate captura cererea curentă a utilizatorului, cum ar fi „Vreau să rezerv o călătorie la Paris”. Această cerință specifică este reținută în contextul imediat al agentului pentru a ghida interacțiunea curentă.

#### Memoria pe Termen Scurt

Acest tip de memorie păstrează informația pentru durata unei singure conversații sau sesiuni. Este contextul chatului curent, permițând agentului să se refere la turele anterioare din dialog.

**Exemplu de Memorie pe Termen Scurt**

Dacă un utilizator întreabă „Cât costă un zbor spre Paris?” și apoi continuă cu „Dar despre cazare acolo?”, memoria pe termen scurt asigură că agentul știe că „acolo” se referă la „Paris” în cadrul aceleiași conversații.

#### Memoria pe Termen Lung

Aceasta este informația care persistă peste mai multe conversații sau sesiuni. Permite agenților să își amintească preferințele utilizatorilor, interacțiunile istorice sau cunoștințele generale pe perioade extinse. Este importantă pentru personalizare.

**Exemplu de Memorie pe Termen Lung**

O memorie pe termen lung ar putea reține că „Ben iubește schiatul și activitățile în aer liber, îi place cafeaua cu vedere la munte și dorește să evite pârtiile avansate din cauza unei accidentări anterioare”. Această informație, învățată din interacțiuni anterioare, influențează recomandările în sesiunile viitoare de planificare a călătoriilor, făcându-le foarte personalizate.

#### Memoria de Persoană

Acest tip specializat de memorie ajută un agent să dezvolte o „personalitate” sau „persoană” consistentă. Permite agentului să rețină detalii despre el însuși sau despre rolul său prevăzut, făcând interacțiunile mai fluide și concentrate.

**Exemplu de Memorie de Persoană**  
Dacă agentul de călătorii este proiectat să fie un „expert în planificarea schiatului”, memoria de persoană poate întări acest rol, influențând răspunsurile pentru a se alinia cu tonul și cunoștințele unui expert.

#### Memoria Fluxului de Lucru/Episodică

Această memorie stochează secvența de pași făcuți de un agent în timpul unei sarcini complexe, inclusiv succesele și eșecurile. Este ca și cum ar reține „episoade” specifice sau experiențe trecute pentru a învăța din ele.

**Exemplu de Memorie Episodică**

Dacă agentul a încercat să rezerve un zbor specific, dar a eșuat din cauza lipsei disponibilității, memoria episodică ar putea înregistra acest eșec, permițând agentului să încerce zboruri alternative sau să informeze utilizatorul despre problemă într-un mod mai bine informat la încercarea următoare.

#### Memoria Entităților

Aceasta implică extragerea și reținerea entităților specifice (precum persoane, locuri sau lucruri) și a evenimentelor din conversații. Permite agentului să construiască o înțelegere structurată a elementelor cheie discutate.

**Exemplu de Memorie Entități**

Dintr-o conversație despre o călătorie trecută, agentul ar putea extrage „Paris”, „Turnul Eiffel” și „cina la restaurantul Le Chat Noir” ca entități. Într-o interacțiune viitoare, agentul ar putea reține „Le Chat Noir” și să ofere să facă o nouă rezervare acolo.

#### Structured RAG (Generarea Augmentată prin Recuperare Structurată)

Deși RAG este o tehnică mai largă, „Structured RAG” este evidențiată ca o tehnologie puternică de memorie. Aceasta extrage informații dense, structurate din diverse surse (conversații, emailuri, imagini) și le folosește pentru a spori precizia, recuperarea și viteza răspunsurilor. Spre deosebire de RAG clasic care se bazează doar pe similaritatea semantică, Structured RAG funcționează cu structura inerentă a informației.

**Exemplu Structured RAG**

În loc să se potrivească doar cuvinte-cheie, Structured RAG ar putea analiza detalii despre un zbor (destinație, dată, oră, companie aeriană) dintr-un email și să le stocheze într-un mod structurat. Acest lucru permite interogări precise precum „Ce zbor am rezervat spre Paris marți?”

## Implementarea și Stocarea Memoriei

Implementarea memoriei pentru agenții AI implică un proces sistematic de **gestionare a memoriei**, care include generarea, stocarea, recuperarea, integrarea, actualizarea și chiar „uitarea” (sau ștergerea) informației. Recuperarea este un aspect deosebit de crucial.

### Instrumente Specializate de Memorie

#### Mem0

Un mod de a stoca și gestiona memoria agentului este folosind instrumente specializate precum Mem0. Mem0 funcționează ca un strat persistent de memorie, permițând agenților să-și amintească interacțiunile relevante, să stocheze preferințele utilizatorului și contextul factual și să învețe din succese și eșecuri în timp. Ideea este că agenții fără stare devin agenți cu stare.

Funcționează printr-un **proces în două faze de memorie: extragere și actualizare**. Mai întâi, mesajele adăugate la firul de conversație al agentului sunt trimise către serviciul Mem0, care folosește un Large Language Model (LLM) pentru a rezuma istoricul conversației și a extrage noi amintiri. Ulterior, o fază de actualizare condusă de LLM determină dacă să adauge, să modifice sau să șteargă aceste memorii, stocându-le într-un magazin de date hibrid care poate include baze de date vectoriale, grafice și cheie-valoare. Acest sistem suportă, de asemenea, diferite tipuri de memorie și poate încorpora memoria grafică pentru gestionarea relațiilor dintre entități.

#### Cognee

O altă abordare puternică este folosirea **Cognee**, o memorie semantică open-source pentru agenții AI care transformă date structurate și nestructurate în grafuri de cunoștințe interogabile, susținute de embeddings. Cognee oferă o **arhitectură duală** combinând căutarea după similaritatea vectorială cu relațiile grafice, permițând agenților să înțeleagă nu doar ce informații sunt similare, ci și cum conceptele se leagă între ele.

Excelează în **recuperarea hibridă** care îmbină similaritatea vectorială, structura grafică și raționamentul LLM – de la căutarea în segmente brute până la răspunsuri la întrebări conștiente de graf. Sistemul menține o **memorie vie** care evoluează și crește, rămânând interogabilă ca un graf conectat, susținând atât contextul sessional pe termen scurt, cât și memoria persistentă pe termen lung.

Tutorialul de notebook Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstrează construirea acestui strat unificat de memorie, cu exemple practice de preluare a surselor diverse de date, vizualizarea grafului de cunoștințe și interogarea cu diferite strategii de căutare adaptate nevoilor specifice ale agentului.

### Stocarea Memoriei cu RAG

Dincolo de instrumentele specializate de memorie precum mem0, poți folosi servicii robuste de căutare precum **Azure AI Search ca backend pentru stocarea și recuperarea amintirilor**, în special pentru Structured RAG.

Acest lucru îți permite să bazezi răspunsurile agentului pe propriile date, asigurând răspunsuri mai relevante și mai precise. Azure AI Search poate fi folosit pentru a stoca amintirile specifice călătoriilor unui utilizator, cataloage de produse sau orice alt cunoștințe specifice unui domeniu.

Azure AI Search suportă capabilități precum **Structured RAG**, care excelează în extragerea și recuperarea informațiilor dense, structurate din seturi mari de date precum istoricul conversațiilor, emailuri sau chiar imagini. Aceasta oferă „precizie și recuperare supra-umană” comparativ cu metodele tradiționale de segmentare a textului și embedding.

## Făcând Agenții AI să se Auto-Îmbunătățească

Un model comun pentru agenții care se auto-îmbunătățesc presupune introducerea unui **„agent de cunoștințe”**. Acest agent separat observă conversația principală între utilizator și agentul principal. Rolul său este să:

1. **Identifice informațiile valoroase**: să determine dacă vreo parte a conversației merită să fie salvată ca cunoștințe generale sau preferințe specifice utilizatorului.

2. **Extrage și rezumează**: să distileze învățătura sau preferința esențială din conversație.

3. **Stocheze într-o bază de cunoștințe**: să persiste această informație extrasă, adesea într-o bază de date vectorială, pentru a fi recuperată ulterior.

4. **Completeze interogările viitoare**: când utilizatorul inițiază o interogare nouă, agentul de cunoștințe recuperează informațiile relevante stocate și le atașează la promptul utilizatorului, oferind context crucial agentului principal (similar cu RAG).

### Optimizări pentru Memorie

• **Gestionarea Latentei**: Pentru a evita încetinirea interacțiunilor cu utilizatorul, se poate folosi inițial un model mai ieftin și mai rapid pentru a verifica rapid dacă informația merită stocată sau recuperată, invocând procesul mai complex de extragere/recuperare doar când este necesar.

• **Mentenanța Bazei de Cunoștințe**: Pentru o bază de cunoștințe în creștere, informațiile mai rar folosite pot fi mutate în „stocare rece” pentru a gestiona costurile.

## Ai Mai Multe Întrebări Despre Memoria Agenților?

Alătură-te comunității [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) pentru a întâlni alți cursanți, a participa la ore de birou și a-ți rezolva întrebările despre Agenții AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Declinare a responsabilității**:  
Acest document a fost tradus folosind serviciul de traducere AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim pentru acuratețe, vă rugăm să rețineți că traducerile automate pot conține erori sau inexactități. Documentul original în limba sa nativă trebuie considerat sursa autorizată. Pentru informații critice, se recomandă o traducere profesională realizată de un traducător uman. Nu ne asumăm responsabilitatea pentru eventualele neînțelegeri sau interpretări greșite care pot apărea în urma utilizării acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->