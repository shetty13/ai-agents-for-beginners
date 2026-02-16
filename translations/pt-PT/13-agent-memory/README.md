# Memória para Agentes de IA
[![Agent Memory](../../../translated_images/pt-PT/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Ao discutir os benefícios únicos de criar Agentes de IA, são principalmente duas as coisas debatidas: a capacidade de chamar ferramentas para completar tarefas e a capacidade de melhorar ao longo do tempo. A memória está na base da criação de um agente autoaperfeiçoador que pode criar melhores experiências para os nossos utilizadores.

Nesta lição, vamos ver o que é a memória para Agentes de IA e como podemos geri-la e utilizá-la em benefício das nossas aplicações.

## Introdução

Esta lição vai cobrir:

• **Compreensão da Memória dos Agentes de IA**: O que é memória e por que é essencial para os agentes.

• **Implementação e Armazenamento da Memória**: Métodos práticos para adicionar capacidades de memória aos seus agentes de IA, focando na memória de curto e longo prazo.

• **Tornar os Agentes de IA Autoaperfeiçoantes**: Como a memória permite que os agentes aprendam de interações passadas e melhorem ao longo do tempo.

## Implementações Disponíveis

Esta lição inclui dois tutoriais completos em notebook:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementa memória usando Mem0 e Azure AI Search com o framework Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementa memória estruturada usando Cognee, construindo automaticamente um grafo de conhecimento sustentado por embeddings, visualizando o grafo e recuperação inteligente

## Objetivos de Aprendizagem

Depois de concluir esta lição, saberá como:

• **Diferenciar entre vários tipos de memória de agentes de IA**, incluindo memória de trabalho, curto prazo e longo prazo, bem como formas especializadas como memória de persona e memória episódica.

• **Implementar e gerir memória de curto e longo prazo para agentes de IA** usando o framework Semantic Kernel, aproveitando ferramentas como Mem0, Cognee, Whiteboard memory, e integrando com Azure AI Search.

• **Compreender os princípios por trás dos agentes de IA autoaperfeiçoantes** e como sistemas robustos de gestão de memória contribuem para aprendizagem e adaptação contínuas.

## Compreendendo a Memória dos Agentes de IA

Na sua essência, **memória para agentes de IA refere-se aos mecanismos que lhes permitem reter e recordar informação**. Esta informação pode ser detalhes específicos sobre uma conversa, preferências do utilizador, ações passadas, ou mesmo padrões aprendidos.

Sem memória, as aplicações de IA são frequentemente sem estado, o que significa que cada interação começa do zero. Isto leva a uma experiência repetitiva e frustrante onde o agente "esquece" o contexto ou preferências anteriores.

### Porque é a Memória Importante?

A inteligência de um agente está profundamente ligada à sua capacidade de recordar e utilizar a informação passada. A memória permite que os agentes sejam:

• **Reflexivos**: Aprendendo com ações e resultados passados.

• **Interativos**: Mantendo o contexto ao longo de uma conversa em curso.

• **Proativos e Reativos**: Antecipando necessidades ou respondendo adequadamente com base em dados históricos.

• **Autónomos**: Operando de forma mais independente ao recorrer ao conhecimento armazenado.

O objetivo da implementação da memória é tornar os agentes mais **fiáveis e capazes**.

### Tipos de Memória

#### Memória de Trabalho

Pense nisto como uma folha de rascunho que um agente usa durante uma tarefa ou processo de pensamento em curso. Ela contém informação imediata necessária para calcular o próximo passo.

Para agentes de IA, a memória de trabalho frequentemente captura a informação mais relevante de uma conversa, mesmo que o histórico completo do chat seja longo ou truncado. Concentra-se em extrair elementos-chave como requisitos, propostas, decisões e ações.

**Exemplo de Memória de Trabalho**

Num agente de reserva de viagens, a memória de trabalho pode capturar o pedido atual do utilizador, como "Quero reservar uma viagem para Paris". Este requisito específico é mantido no contexto imediato do agente para orientar a interação atual.

#### Memória de Curto Prazo

Este tipo de memória retém informação durante uma única conversa ou sessão. É o contexto do chat atual, permitindo que o agente se refira a turnos anteriores no diálogo.

**Exemplo de Memória de Curto Prazo**

Se um utilizador perguntar, "Quanto custa um voo para Paris?" e depois perguntar "E a acomodação lá?", a memória de curto prazo garante que o agente sabe que "lá" refere-se a "Paris" dentro da mesma conversa.

#### Memória de Longo Prazo

Esta é informação que persiste em múltiplas conversas ou sessões. Permite que os agentes se lembrem de preferências do utilizador, interações históricas, ou conhecimento geral ao longo de períodos prolongados. Isto é importante para a personalização.

**Exemplo de Memória de Longo Prazo**

Uma memória de longo prazo pode armazenar que "o Ben gosta de esqui e atividades ao ar livre, gosta de café com vista para a montanha, e quer evitar pistas de esqui avançadas devido a uma lesão passada". Esta informação, aprendida de interações anteriores, influencia recomendações em futuras sessões de planeamento de viagens, tornando-as altamente personalizadas.

#### Memória de Persona

Este tipo de memória especializado ajuda um agente a desenvolver uma "personalidade" ou "persona" consistente. Permite que o agente se lembre de detalhes sobre si próprio ou o seu papel pretendido, tornando as interações mais fluidas e focadas.

**Exemplo de Memória de Persona**

Se o agente de viagens for desenhado para ser um "planeador de esqui especialista", a memória de persona pode reforçar este papel, influenciando as suas respostas para alinhar com o tom e conhecimento de um especialista.

#### Memória de Workflow/Episódica

Esta memória armazena a sequência de passos que um agente toma durante uma tarefa complexa, incluindo sucessos e falhas. É como recordar "episódios" específicos ou experiências passadas para aprender com eles.

**Exemplo de Memória Episódica**

Se o agente tentou reservar um voo específico mas falhou devido a indisponibilidade, a memória episódica poderia registar esse fracasso, permitindo que o agente tente voos alternativos ou informe o utilizador sobre o problema de forma mais informada numa tentativa subsequente.

#### Memória de Entidade

Isto envolve extrair e recordar entidades específicas (como pessoas, lugares ou coisas) e eventos de conversas. Permite que o agente construa uma compreensão estruturada dos elementos-chave discutidos.

**Exemplo de Memória de Entidade**

Numa conversa sobre uma viagem passada, o agente pode extrair "Paris", "Torre Eiffel" e "jantar no restaurante Le Chat Noir" como entidades. Numa interação futura, o agente pode recordar "Le Chat Noir" e oferecer-se para fazer uma nova reserva lá.

#### RAG Estruturado (Retrieval Augmented Generation)

Embora RAG seja uma técnica mais ampla, o "RAG Estruturado" é destacado como uma tecnologia de memória poderosa. Extrai informação densa e estruturada de várias fontes (conversas, emails, imagens) e usa-a para melhorar precisão, recordação e velocidade nas respostas. Ao contrário do RAG clássico que depende apenas da similaridade semântica, o RAG Estruturado trabalha com a estrutura inerente da informação.

**Exemplo de RAG Estruturado**

Em vez de apenas associar palavras-chave, o RAG Estruturado pode analisar detalhes de um voo (destino, data, hora, companhia aérea) de um email e armazená-los de forma estruturada. Isto permite consultas precisas como "Que voo reservei para Paris na terça-feira?"

## Implementação e Armazenamento da Memória

Implementar memória para agentes de IA envolve um processo sistemático de **gestão da memória**, que inclui gerar, armazenar, recuperar, integrar, atualizar e até "esquecer" (ou eliminar) informação. A recuperação é um aspeto particularmente crucial.

### Ferramentas Especializadas de Memória

#### Mem0

Uma forma de armazenar e gerir memória de agente é usar ferramentas especializadas como Mem0. Mem0 funciona como uma camada de memória persistente, permitindo que os agentes recordem interações relevantes, armazenem preferências do utilizador e contexto factual, e aprendam com sucessos e falhas ao longo do tempo. A ideia é que agentes sem estado se transformem em agentes com estado.

Funciona através de um **pipeline de memória em duas fases: extração e atualização**. Primeiro, mensagens adicionadas ao thread de um agente são enviadas para o serviço Mem0, que usa um Modelo de Linguagem Grande (LLM) para resumir o histórico da conversa e extrair novas memórias. Posteriormente, uma fase de atualização conduzida por um LLM determina se deve adicionar, modificar ou eliminar essas memórias, armazenando-as numa base de dados híbrida que pode incluir bases de dados vetoriais, grafos e chave-valor. Este sistema também suporta vários tipos de memória e pode incorporar memória de grafo para gerir relações entre entidades.

#### Cognee

Outra abordagem poderosa é usar o **Cognee**, uma memória semântica open-source para agentes de IA que transforma dados estruturados e não estruturados em grafos de conhecimento consultáveis suportados por embeddings. O Cognee fornece uma **arquitetura de armazenamento dual** que combina pesquisa por similaridade vetorial com relacionamentos de grafo, capacitando agentes a entender não apenas que informação é semelhante, mas como os conceitos se relacionam entre si.

Destaca-se na **recuperação híbrida** que mistura similaridade vetorial, estrutura de grafo e raciocínio LLM - desde a consulta de fragmentos brutos até respostas conscientes do grafo. O sistema mantém uma **memória viva** que evolui e cresce enquanto permanece consultável como um grafo conectado, suportando tanto contexto de sessão de curto prazo como memória persistente de longo prazo.

O tutorial em notebook de Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstra a construção desta camada de memória unificada, com exemplos práticos de ingestão de fontes de dados diversas, visualização do grafo de conhecimento e consulta com diferentes estratégias de pesquisa adaptadas às necessidades específicas do agente.

### Armazenar Memória com RAG

Para além das ferramentas especializadas de memória como Mem0, pode aproveitar serviços robustos de pesquisa como **Azure AI Search como backend para armazenar e recuperar memórias**, especialmente para RAG estruturado.

Isto permite fundamentar as respostas do seu agente com os seus próprios dados, assegurando respostas mais relevantes e precisas. O Azure AI Search pode ser usado para armazenar memórias específicas de viagens do utilizador, catálogos de produtos, ou qualquer outro conhecimento específico de domínio.

O Azure AI Search suporta capacidades como **RAG Estruturado**, que se destaca na extração e recuperação de informação densa e estruturada de grandes conjuntos de dados como históricos de conversas, emails, ou até imagens. Isto proporciona "precisão e recordação sobre-humanas" comparadas às abordagens tradicionais de fragmentação de texto e embeddings.

## Tornando os Agentes de IA Autoaperfeiçoantes

Um padrão comum para agentes autoaperfeiçoantes envolve introduzir um **"agente de conhecimento"**. Este agente separado observa a conversa principal entre o utilizador e o agente primário. O seu papel é:

1. **Identificar informação valiosa**: Determinar se alguma parte da conversa vale a pena guardar como conhecimento geral ou preferência específica do utilizador.

2. **Extrair e resumir**: Destilar a aprendizagem essencial ou preferência da conversa.

3. **Armazenar numa base de conhecimento**: Persistir esta informação extraída, frequentemente numa base de dados vetorial, para que possa ser recuperada posteriormente.

4. **Aumentar consultas futuras**: Quando o utilizador inicia uma nova consulta, o agente de conhecimento recupera informação armazenada relevante e anexa-a ao prompt do utilizador, fornecendo contexto crucial ao agente principal (semelhante a RAG).

### Otimizações para a Memória

• **Gestão da Latência**: Para evitar atrasar as interações do utilizador, pode ser usado inicialmente um modelo mais barato e rápido para verificar rapidamente se a informação vale a pena armazenar ou recuperar, só acionando o processo mais complexo de extração/recuperação quando necessário.

• **Manutenção da Base de Conhecimento**: Para uma base de conhecimento em crescimento, a informação menos frequentemente usada pode ser movida para "armazenamento frio" para gerir custos.

## Tem Mais Perguntas Sobre Memória de Agentes?

Junte-se ao [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) para encontrar outros aprendizes, participar em sessões de esclarecimento e obter respostas às suas perguntas sobre Agentes de IA.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos por alcançar a precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original na sua língua nativa deve ser considerado a fonte oficial. Para informações críticas, recomenda-se tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações erradas decorrentes da utilização desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->