# Memory for AI Agents 
[![Agent Memory](../../../translated_images/pcm/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

When we dey yarn about the special benefits wey dey for creating AI Agents, two main tin dem dey talk about: di ability to use tools to complete work and di ability to improve as time dey go. Memory na di foundation for creating self-improving agent wey fit give better experience to our users.

For dis lesson, we go check wetin memory mean for AI Agents and how we fit manage am and use am to benefit our applications.

## Introduction

Dis lesson go cover:

• **Understanding AI Agent Memory**: Wetin memory be and why e important for agents.

• **Implementing and Storing Memory**: How to add memory power to your AI agents, focus on short-term and long-term memory.

• **Making AI Agents Self-Improving**: How memory dey help agents learn from past interactions and improve as time dey go.

## Available Implementations

Dis lesson get two complete notebook tutorials:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implements memory using Mem0 and Azure AI Search with Semantic Kernel framework

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implements structured memory using Cognee, wey dey automatically build knowledge graph wey get backing by embeddings, dey show graph, and sabi retrieve information well

## Learning Goals

After you finish dis lesson, you go sabi how to:

• **Tori between different kinds of AI agent memory**, like working memory, short-term memory, long-term memory, plus special ones like persona and episodic memory.

• **Implement and manage short-term and long-term memory for AI agents** using Semantic Kernel framework, plus use tools like Mem0, Cognee, Whiteboard memory, and join am with Azure AI Search.

• **Understand the idea behind self-improving AI agents** and how better memory management systems dey help learning steady and adaptation.

## Understanding AI Agent Memory

For im core, **memory for AI agents na di ways wey dem fit keep and remember tori**. This tori fit be specific details about conversation, wetin user like, past actions, or even patterns wey dem don learn.

If no memory, AI applications go dey stateless, meaning every interaction go start from zero. E go lead to repetitive and frustrating user experience where agent "forget" wetin dem talk before or wetin user sabi like.

### Why Memory Important?

Agent intelligence strong because e fit recall and use past tori. Memory allow agents to be:

• **Reflective**: Dem dey learn from past actions and results.

• **Interactive**: Dem fit maintain context as conversation dey go.

• **Proactive and Reactive**: Dem fit predict wetin user need or respond well based on tori wey don happen before.

• **Autonomous**: Dem fit work well by demself by using the knowledge wey dem don store before.

The aim of memory na to make agents dey **reliable and capable**.

### Types of Memory

#### Working Memory

Think am like scratch paper wey agent dey use during one task or one thought process wey dey go on. E hold tin wey agent need immediately to fit take next step.

For AI agents, working memory dey usually capture the most important info from conversation, even if full chat history long or cut short. E dey focus on key things like requirements, proposals, decisions, and actions.

**Working Memory Example**

For travel booking agent, working memory fit capture wetin user dey ask now, for example "I want to book trip go Paris". This specific request dey hold for agent immediate mind to guide current talk.

#### Short Term Memory

Dis memory type dey keep info for one conversation or session only. Na wetin dey happen for di current chat, e allow agent to remember previous talk.

**Short Term Memory Example**

If user ask, "How much flight to Paris dey cost?" then follow up with "How about accommodation there?", short-term memory make sure say agent sabi say "there" mean "Paris" for the same conversation.

#### Long Term Memory

Dis one na info wey stay for many conversations or sessions. E let agents remember wetin user like, past interactions, or general knowledge for long time. E important for personalization.

**Long Term Memory Example**

Long-term memory fit store say "Ben like skiing and outdoor activities, like coffee with mountain view, and no like advanced ski slopes because e get injury before". This kind info, wey dem learn from previous talks, go help make better recommendations for next travel bookings wey dey personal.

#### Persona Memory

Dis one na special memory type wey help agent build consistent "character" or "persona". E let agent remember about itself or the role wey e dey play, so conversations fit flow well and stay focused.

**Persona Memory Example**

If travel agent na "expert ski planner," persona memory fit support dis role, so the agent responses go fit expert tone and sabi.

#### Workflow/Episodic Memory

Dis memory dey keep track of all steps wey agent do during one kain hard task, including the wins and failures. Na like remembering past "episodes" or experiences to learn from dem.

**Episodic Memory Example**

If agent try book one flight but e no work because the flight no dey, episodic memory fit record this failure and help agent try another flight or tell user about the wahala better for next try.

#### Entity Memory

Dis one involve finding and remembering specific things (like people, places, or tins) and events from conversation. E help agent build structured understanding of important things wey dem talk about.

**Entity Memory Example**

For one talk about past trip, agent fit extract "Paris," "Eiffel Tower," and "dinner for Le Chat Noir restaurant" as entities. For future talk, agent fit remember "Le Chat Noir" and offer to book new reservation there.

#### Structured RAG (Retrieval Augmented Generation)

Even though RAG na big technique, "Structured RAG" na strong memory technology. E dey pull dense, structured info from different sources (conversation, emails, images) and use am to improve accuracy, recall, and speed for replies. E no just rely on semantic similarity like normal RAG; Structured RAG dey use the natural structure of info.

**Structured RAG Example**

No be to just match keywords; Structured RAG fit decode flight info (destination, date, time, airline) from email and store am structured. This one make e easy to ask specific things like "Which flight I book to Paris on Tuesday?"

## Implementing and Storing Memory

To implement memory for AI agents, you need good **memory management** wey get steps like generate, store, retrieve, connect, update, and even "forget" (delete) info. Retrieval na very important part.

### Specialized Memory Tools

#### Mem0

One way to store and manage agent memory na to use special tools like Mem0. Mem0 dey work as persistent memory layer, e allow agents recall relevant talk, store user preferences and factual info, and learn from wins and losses as time dey go. The idea be say stateless agents go become stateful.

E get **two-phase memory pipeline: extraction and update**. First, messages wey join agent thread go enter Mem0 service, wey use Large Language Model (LLM) to summarize conversation and extract new memory. Then, LLM update phase go decide to add, change, or delete memory. E dey store for hybrid data storage wey fit get vector, graph, and key-value databases. The system fit support many kinds memory and fit carry graph memory to manage relationships between entities.

#### Cognee

Another strong way na to use **Cognee**, open-source semantic memory for AI agents wey fit turn structured and unstructured data into knowledge graphs backed by embeddings. Cognee get **dual-store architecture** wey join vector similarity search with graph relationships, so agent fit understand not just similar info, but how concepts relate.

E strong for **hybrid retrieval** wey mix vector similarity, graph structure, and LLM reasoning - from raw chunk lookup to graph-aware question answering. The system get **living memory** wey dey evolve and grow but still dey searchable as one connected graph, supporting short-term session memory and long-term persistent memory.

Cognee notebook tutorial ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) dey show how to build this single memory layer, with practical examples of adding diverse data sources, showing the knowledge graph, and searching with different strategies for different agent needs.

### Storing Memory with RAG

Besides special memory tools like mem0, you fit also use strong search services like **Azure AI Search as backend for storing and retrieving memories**, especially for structured RAG.

This one allow you ground your agent replies with your own data, to make answers better and more relevant. Azure AI Search fit store travel memories for user, product catalogs, or any special knowledge you get.

Azure AI Search get power like **Structured RAG**, wey dey good at extracting and retrieving dense, structured info from big data sets like chat histories, emails, or images. E give "superhuman precision and recall" compared to normal text chunk and embedding methods.

## Making AI Agents Self-Improve

One normal way for self-improving agents na to add **"knowledge agent"**. This other agent go dey watch main talk between user and main agent. E work na to:

1. **Find valuable info**: Check if any part of conversation worth to save as general knowledge or user preference.

2. **Extract and summarize**: Pull out important learning or preference from di talk.

3. **Store inside knowledge base**: Keep this info, usually for vector database, make e fit come again later.

4. **Add to future queries**: When user start new question, knowledge agent go find important stored info and add am to user prompt, give main agent better context (like RAG).

### Optimizations for Memory

• **Latency Management**: To no slow down user talk, use cheap and fast model first to check if info worth to store or retrieve, then use complex extraction and retrieval if needed.

• **Knowledge Base Maintenance**: For growing knowledge base, less used info fit move go "cold storage" to save cost.

## Got More Questions About Agent Memory?

Join the [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) to meet other learners, attend office hours and get your AI Agents questions answered.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:  
Dis document don translate wit AI translation service [Co-op Translator](https://github.com/Azure/co-op-translator). Even though we try make e correct, abeg sabi say automated translations fit get some mistakes or no too correct. Di original document for im own language na di true correct source. If na important info, e better make professional human translation do am. We no go responsible for any wahala or mistaken meaning wey fit come from using dis translation.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->