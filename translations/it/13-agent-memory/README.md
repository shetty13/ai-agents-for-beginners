# Memoria per Agenti AI 
[![Agent Memory](../../../translated_images/it/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Quando si discutono i vantaggi unici della creazione di Agenti AI, si parla principalmente di due cose: la capacità di chiamare strumenti per completare compiti e la capacità di migliorare nel tempo. La memoria è alla base della creazione di agenti auto-miglioranti che possono creare esperienze migliori per i nostri utenti.

In questa lezione, esamineremo cosa significa memoria per gli Agenti AI e come possiamo gestirla e utilizzarla a vantaggio delle nostre applicazioni.

## Introduzione

Questa lezione coprirà:

• **Comprendere la Memoria degli Agenti AI**: Cos'è la memoria e perché è essenziale per gli agenti.

• **Implementare e Conservare la Memoria**: Metodi pratici per aggiungere capacità di memoria ai tuoi agenti AI, concentrandosi sulla memoria a breve e a lungo termine.

• **Rendere gli Agenti AI Auto-Miglioranti**: Come la memoria consente agli agenti di imparare dalle interazioni passate e migliorare nel tempo.

## Implementazioni Disponibili

Questa lezione include due tutorial completi in notebook:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementa la memoria usando Mem0 e Azure AI Search con il framework Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementa la memoria strutturata usando Cognee, costruendo automaticamente un grafo della conoscenza supportato da embeddings, visualizzando il grafo e recuperando in modo intelligente

## Obiettivi di Apprendimento

Dopo aver completato questa lezione, saprai come:

• **Differenziare tra vari tipi di memoria per agenti AI**, inclusi memoria di lavoro, memoria a breve termine e memoria a lungo termine, così come forme specializzate come memoria persona ed episodica.

• **Implementare e gestire memoria a breve termine e a lungo termine per agenti AI** utilizzando il framework Semantic Kernel, sfruttando strumenti come Mem0, Cognee, memoria Whiteboard e integrando con Azure AI Search.

• **Comprendere i principi dietro gli agenti AI auto-miglioranti** e come sistemi robusti di gestione della memoria contribuiscono all’apprendimento e adattamento continuo.

## Comprendere la Memoria degli Agenti AI

Alla base, **la memoria per gli agenti AI si riferisce ai meccanismi che consentono loro di conservare e richiamare informazioni**. Queste informazioni possono essere dettagli specifici su una conversazione, preferenze dell’utente, azioni passate o anche modelli appresi.

Senza memoria, le applicazioni AI sono spesso senza stato, il che significa che ogni interazione parte da zero. Questo porta a un’esperienza utente ripetitiva e frustrante in cui l’agente "dimentica" il contesto o le preferenze precedenti.

### Perché la Memoria è Importante?

L’intelligenza di un agente è profondamente legata alla sua capacità di richiamare e utilizzare informazioni passate. La memoria permette agli agenti di essere:

• **Riflessivi**: Imparare dalle azioni e dai risultati passati.

• **Interattivi**: Mantenere il contesto durante una conversazione in corso.

• **Proattivi e Reattivi**: Anticipare bisogni o rispondere appropriatamente basandosi su dati storici.

• **Autonomi**: Operare più indipendentemente attingendo alla conoscenza memorizzata.

L’obiettivo dell’implementazione della memoria è rendere gli agenti più **affidabili e capaci**.

### Tipi di Memoria

#### Memoria di Lavoro

Pensala come un foglio di carta per appunti che un agente usa durante un singolo compito o processo di pensiero in corso. Contiene informazioni immediate necessarie per calcolare il passo successivo.

Per gli agenti AI, la memoria di lavoro spesso cattura le informazioni più rilevanti da una conversazione, anche se la cronologia della chat è lunga o troncata. Si concentra sull’estrarre elementi chiave come requisiti, proposte, decisioni e azioni.

**Esempio di Memoria di Lavoro**

In un agente per prenotazioni di viaggio, la memoria di lavoro potrebbe catturare la richiesta attuale dell’utente, come "Voglio prenotare un viaggio a Parigi". Questo requisito specifico è mantenuto nel contesto immediato dell’agente per guidare l’interazione corrente.

#### Memoria a Breve Termine

Questo tipo di memoria conserva informazioni per la durata di una singola conversazione o sessione. È il contesto della chat attuale, che permette all’agente di riferirsi ai turni precedenti nel dialogo.

**Esempio di Memoria a Breve Termine**

Se un utente chiede, "Quanto costa un volo per Parigi?" e poi continua con "E per l’alloggio lì?", la memoria a breve termine garantisce che l’agente sappia che "lì" si riferisce a "Parigi" nella stessa conversazione.

#### Memoria a Lungo Termine

Queste sono informazioni che persistono attraverso più conversazioni o sessioni. Permette agli agenti di ricordare preferenze utenti, interazioni storiche o conoscenze generali per periodi prolungati. Questo è importante per la personalizzazione.

**Esempio di Memoria a Lungo Termine**

Una memoria a lungo termine potrebbe conservare che "Ben ama sciare e le attività all’aperto, piace il caffè con vista sulla montagna e vuole evitare piste da sci avanzate a causa di un infortunio passato". Queste informazioni, apprese da interazioni passate, influenzano le raccomandazioni in sessioni future di pianificazione viaggi, rendendole altamente personalizzate.

#### Memoria Persona

Questo tipo specializzato di memoria aiuta un agente a sviluppare una "personalità" o "persona" coerente. Permette all’agente di ricordare dettagli su se stesso o sul ruolo previsto, rendendo le interazioni più fluide e focalizzate.

**Esempio di Memoria Persona**  
Se l’agente di viaggio è progettato per essere un "esperto pianificatore sci", la memoria persona potrebbe rinforzare questo ruolo, influenzando le risposte per allinearsi con il tono e la conoscenza di un esperto.

#### Memoria Workflow/Episodica

Questa memoria conserva la sequenza di passi che un agente compie durante un compito complesso, inclusi successi e fallimenti. È come ricordare specifici "episodi" o esperienze passate per imparare da esse.

**Esempio di Memoria Episodica**

Se l’agente ha tentato di prenotare un volo specifico ma ha fallito per indisponibilità, la memoria episodica potrebbe registrare questo fallimento, permettendo all’agente di provare voli alternativi o informare l’utente sul problema in modo più informato durante un tentativo successivo.

#### Memoria Entità

Include l’estrazione e la memorizzazione di entità specifiche (come persone, luoghi o cose) ed eventi dalle conversazioni. Permette all’agente di costruire una comprensione strutturata degli elementi chiave discussi.

**Esempio di Memoria Entità**

Da una conversazione su un viaggio passato, l’agente potrebbe estrarre "Parigi," "Torre Eiffel," e "cena al ristorante Le Chat Noir" come entità. In un’interazione futura, l’agente potrebbe richiamare "Le Chat Noir" e offrire di fare una nuova prenotazione lì.

#### Structured RAG (Retrieval Augmented Generation)

Sebbene RAG sia una tecnica più ampia, "Structured RAG" è evidenziata come una tecnologia di memoria potente. Estrae informazioni dense e strutturate da varie fonti (conversazioni, email, immagini) e le usa per migliorare precisione, richiamo e rapidità nelle risposte. A differenza del RAG classico che si affida solo alla somiglianza semantica, Structured RAG lavora con la struttura intrinseca delle informazioni.

**Esempio di Structured RAG**

Invece di abbinare solo parole chiave, Structured RAG potrebbe analizzare i dettagli di un volo (destinazione, data, ora, compagnia aerea) da un’email e memorizzarli in modo strutturato. Questo permette interrogazioni precise come "Quale volo ho prenotato per Parigi martedì?"

## Implementare e Conservare la Memoria

Implementare la memoria per agenti AI implica un processo sistematico di **gestione della memoria**, che include generare, archiviare, recuperare, integrare, aggiornare e persino "dimenticare" (o cancellare) informazioni. Il recupero è un aspetto particolarmente cruciale.

### Strumenti Specializzati per la Memoria

#### Mem0

Un modo per conservare e gestire la memoria degli agenti è usare strumenti specializzati come Mem0. Mem0 funziona come un livello di memoria persistente, permettendo agli agenti di richiamare interazioni rilevanti, memorizzare preferenze utente e contesto fattuale, e imparare dai successi e fallimenti nel tempo. L’idea è che agenti senza stato diventino con stato.

Funziona tramite una **pipeline della memoria in due fasi: estrazione e aggiornamento**. Prima, i messaggi aggiunti al thread di un agente vengono inviati al servizio Mem0, che utilizza un Large Language Model (LLM) per riassumere la cronologia della conversazione ed estrarre nuove memorie. Successivamente, una fase di aggiornamento guidata da LLM determina se aggiungere, modificare o cancellare queste memorie, memorizzandole in un archivio dati ibrido che può includere database vettoriali, a grafo e key-value. Questo sistema supporta anche vari tipi di memoria e può includere memoria a grafo per gestire relazioni tra entità.

#### Cognee

Un altro approccio potente è usare **Cognee**, una memoria semantica open source per agenti AI che trasforma dati strutturati e non strutturati in grafi della conoscenza interrogabili supportati da embeddings. Cognee offre un’**architettura dual-store** che combina ricerca per similarità vettoriale con relazioni a grafo, permettendo agli agenti di capire non solo quali informazioni sono simili, ma come i concetti sono correlati tra loro.

Eccelle nel **recupero ibrido** che fonde similarità vettoriale, struttura a grafo e ragionamento LLM - dalla ricerca di frammenti grezzi alla risposta a domande consapevole del grafo. Il sistema mantiene una **memoria viva** che evolve e cresce restando interrogabile come un unico grafo connesso, supportando sia il contesto di sessione a breve termine che la memoria persistente a lungo termine.

Il tutorial notebook di Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) dimostra come costruire questo livello unificato di memoria, con esempi pratici di ingestione di fonti dati diverse, visualizzazione del grafo della conoscenza e interrogazioni con strategie di ricerca differenziate per specifiche esigenze degli agenti.

### Conservare la Memoria con RAG

Oltre agli strumenti specializzati come mem0, puoi sfruttare servizi di ricerca robusti come **Azure AI Search come backend per archiviare e recuperare memorie**, specialmente per Structured RAG.

Questo ti permette di ancorare le risposte del tuo agente ai tuoi dati, garantendo risposte più rilevanti e accurate. Azure AI Search può essere usato per memorizzare memorie di viaggio specifiche per utente, cataloghi di prodotti o qualsiasi altra conoscenza di dominio.

Azure AI Search supporta funzionalità come **Structured RAG**, che eccelle nell’estrazione e recupero di informazioni dense e strutturate da grandi dataset come cronologie di conversazioni, email o anche immagini. Questo fornisce una “precisione e richiamo sovrumani” rispetto ai metodi tradizionali di suddivisione testuale e embedding.

## Rendere gli Agenti AI Auto-Miglioranti

Uno schema comune per agenti auto-miglioranti prevede l’introduzione di un **"agente della conoscenza"**. Questo agente separato osserva la conversazione principale tra l’utente e l’agente primario. Il suo ruolo è:

1. **Identificare informazioni preziose**: Determinare se una parte della conversazione vale la pena di essere salvata come conoscenza generale o preferenza specifica dell’utente.

2. **Estrarre e riassumere**: Distillare l’apprendimento o la preferenza essenziale dalla conversazione.

3. **Archiviare in una base di conoscenza**: Conservare queste informazioni estratte, spesso in un database vettoriale, così da poterle recuperare in seguito.

4. **Arricchire le query future**: Quando l’utente inizia una nuova richiesta, l’agente della conoscenza recupera le informazioni memorizzate rilevanti e le aggiunge al prompt dell’utente, fornendo un contesto cruciale all’agente primario (simile a RAG).

### Ottimizzazioni per la Memoria

• **Gestione della latenza**: Per evitare di rallentare le interazioni con l’utente, si può usare inizialmente un modello più economico e veloce per verificare rapidamente se un’informazione vale la pena di essere memorizzata o recuperata, attivando il processo più complesso solo quando necessario.

• **Manutenzione della base di conoscenza**: Per una base di conoscenza in crescita, le informazioni meno usate possono essere spostate in “cold storage” per gestire i costi.

## Hai Altre Domande Sulla Memoria degli Agenti?

Unisciti al [Discord di Azure AI Foundry](https://aka.ms/ai-agents/discord) per incontrare altri apprendenti, partecipare alle ore d’ufficio e ottenere risposte alle tue domande sugli Agenti AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:  
Questo documento è stato tradotto utilizzando il servizio di traduzione automatica AI [Co-op Translator](https://github.com/Azure/co-op-translator). Pur impegnandoci per garantire l'accuratezza, si prega di considerare che le traduzioni automatiche possono contenere errori o inesattezze. Il documento originale nella sua lingua nativa deve essere considerato la fonte autorevole. Per informazioni critiche, si raccomanda una traduzione professionale effettuata da un umano. Non siamo responsabili per eventuali malintesi o interpretazioni errate derivanti dall’uso di questa traduzione.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->