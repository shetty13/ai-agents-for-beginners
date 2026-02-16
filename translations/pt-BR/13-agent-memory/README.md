# Memória para Agentes de IA 
[![Agent Memory](../../../translated_images/pt-BR/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Ao discutir os benefícios únicos de criar Agentes de IA, duas coisas são principalmente abordadas: a capacidade de chamar ferramentas para completar tarefas e a capacidade de melhorar ao longo do tempo. A memória está na base da criação de agentes autoaperfeiçoáveis que podem criar melhores experiências para nossos usuários.

Nesta lição, veremos o que é memória para Agentes de IA e como podemos gerenciá-la e usá-la em benefício das nossas aplicações.

## Introdução

Esta lição cobrirá:

• **Compreendendo a Memória do Agente de IA**: O que é memória e por que é essencial para os agentes.

• **Implementando e Armazenando Memória**: Métodos práticos para adicionar capacidades de memória aos seus agentes de IA, focando em memória de curto prazo e memória de longo prazo.

• **Fazendo Agentes de IA Autoaperfeiçoáveis**: Como a memória permite que os agentes aprendam com interações passadas e melhorem ao longo do tempo.

## Implementações Disponíveis

Esta lição inclui dois tutoriais completos em notebook:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementa memória usando Mem0 e Azure AI Search com o framework Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementa memória estruturada usando Cognee, construindo automaticamente grafo de conhecimento apoiado por embeddings, visualizando grafo e recuperação inteligente

## Objetivos de Aprendizado

Após completar esta lição, você saberá como:

• **Diferenciar entre vários tipos de memória para agentes de IA**, incluindo memória operacional, de curto prazo e de longo prazo, bem como formas especializadas como memória de persona e episódica.

• **Implementar e gerenciar memória de curto e longo prazo para agentes de IA** usando o framework Semantic Kernel, aproveitando ferramentas como Mem0, Cognee, memória Whiteboard e integrando com Azure AI Search.

• **Entender os princípios por trás dos agentes de IA autoaperfeiçoáveis** e como sistemas robustos de gerenciamento de memória contribuem para aprendizado e adaptação contínuos.

## Compreendendo a Memória do Agente de IA

Em sua essência, **memória para agentes de IA refere-se aos mecanismos que permitem a eles reter e recordar informações**. Essas informações podem ser detalhes específicos sobre uma conversa, preferências do usuário, ações passadas ou até padrões aprendidos.

Sem memória, aplicações de IA frequentemente são stateless, significando que cada interação começa do zero. Isso leva a uma experiência de usuário repetitiva e frustrante, onde o agente "esquece" contextos ou preferências anteriores.

### Por que a Memória é Importante?

A inteligência de um agente está profundamente ligada à sua capacidade de recordar e utilizar informações passadas. A memória permite que os agentes sejam:

• **Reflexivos**: Aprendendo com ações e resultados anteriores.

• **Interativos**: Mantendo contexto durante uma conversa em andamento.

• **Proativos e Reativos**: Antecipando necessidades ou respondendo adequadamente com base em dados históricos.

• **Autônomos**: Operando com mais independência ao utilizar conhecimento armazenado.

O objetivo da implementação da memória é tornar os agentes mais **confiáveis e capazes**.

### Tipos de Memória

#### Memória Operacional

Pense nela como um pedaço de papel de rascunho que um agente usa durante uma única tarefa ou processo de pensamento em andamento. Ela mantém informações imediatas necessárias para calcular o próximo passo.

Para agentes de IA, a memória operacional frequentemente captura as informações mais relevantes de uma conversa, mesmo que o histórico completo do chat seja longo ou truncado. Ela foca em extrair elementos-chave como requisitos, propostas, decisões e ações.

**Exemplo de Memória Operacional**

Em um agente de reserva de viagens, a memória operacional pode capturar o pedido atual do usuário, como "Quero reservar uma viagem para Paris". Esse requisito específico é mantido no contexto imediato do agente para guiar a interação atual.

#### Memória de Curto Prazo

Esse tipo de memória retém informações durante o período de uma única conversa ou sessão. É o contexto do chat atual, permitindo que o agente se refira a diálogos anteriores.

**Exemplo de Memória de Curto Prazo**

Se um usuário pergunta, "Quanto custaria um voo para Paris?" e depois complementa com "E a acomodação lá?", a memória de curto prazo garante que o agente saiba que "lá" se refere a "Paris" dentro da mesma conversa.

#### Memória de Longo Prazo

São informações que persistem ao longo de múltiplas conversas ou sessões. Permite que os agentes lembrem preferências do usuário, interações históricas ou conhecimento geral ao longo de períodos estendidos. Isso é importante para personalização.

**Exemplo de Memória de Longo Prazo**

Uma memória de longo prazo pode armazenar que "Ben gosta de esquiar e atividades ao ar livre, aprecia café com vista para a montanha e prefere evitar pistas avançadas devido a uma lesão anterior". Essa informação, aprendida em interações anteriores, influencia recomendações em futuras sessões de planejamento de viagens, tornando-as altamente personalizadas.

#### Memória de Persona

Este tipo especializado de memória ajuda o agente a desenvolver uma "personalidade" ou "persona" consistente. Permite que o agente se lembre de detalhes sobre si mesmo ou seu papel pretendido, tornando as interações mais fluidas e focadas.

**Exemplo de Memória de Persona**

Se o agente de viagens é projetado para ser um "especialista em planejamento de esqui," a memória de persona pode reforçar esse papel, influenciando suas respostas para alinhar com o tom e conhecimento de um especialista.

#### Memória de Fluxo de Trabalho/Episódica

Essa memória armazena a sequência de passos que um agente toma durante uma tarefa complexa, incluindo sucessos e falhas. É como lembrar episódios específicos ou experiências passadas para aprender com eles.

**Exemplo de Memória Episódica**

Se o agente tentou reservar um voo específico que falhou por indisponibilidade, a memória episódica poderia registrar essa falha, permitindo que o agente tente voos alternativos ou informe o usuário sobre o problema de forma mais informada em uma tentativa subsequente.

#### Memória de Entidade

Envolve extrair e lembrar entidades específicas (como pessoas, lugares ou coisas) e eventos de conversas. Permite que o agente construa uma compreensão estruturada dos elementos-chave discutidos.

**Exemplo de Memória de Entidade**

De uma conversa sobre uma viagem passada, o agente pode extrair "Paris," "Torre Eiffel," e "jantar no restaurante Le Chat Noir" como entidades. Em uma interação futura, o agente poderia lembrar de "Le Chat Noir" e oferecer fazer uma nova reserva lá.

#### RAG Estruturado (Retrieval Augmented Generation)

Embora RAG seja uma técnica mais ampla, "RAG Estruturado" é destacado como uma tecnologia poderosa de memória. Ele extrai informações densas e estruturadas de várias fontes (conversas, e-mails, imagens) e as usa para melhorar a precisão, recuperação e velocidade nas respostas. Ao contrário do RAG clássico que depende apenas da similaridade semântica, o RAG Estruturado trabalha com a estrutura inerente da informação.

**Exemplo de RAG Estruturado**

Ao invés de apenas combinar palavras-chave, o RAG Estruturado poderia analisar detalhes de voos (destino, data, hora, companhia aérea) de um e-mail e armazená-los de forma estruturada. Isso permite consultas precisas como "Qual voo eu reservei para Paris na terça-feira?"

## Implementando e Armazenando Memória

Implementar memória para agentes de IA envolve um processo sistemático de **gerenciamento de memória**, que inclui gerar, armazenar, recuperar, integrar, atualizar e até "esquecer" (ou deletar) informações. A recuperação é um aspecto particularmente crucial.

### Ferramentas Especializadas de Memória

#### Mem0

Uma forma de armazenar e gerenciar a memória do agente é usando ferramentas especializadas como o Mem0. Mem0 funciona como uma camada de memória persistente, permitindo que agentes recordem interações relevantes, armazenem preferências do usuário e contexto factual, e aprendam com sucessos e falhas ao longo do tempo. A ideia é que agentes sem estado se tornem agentes com estado.

Ele opera por meio de um **pipeline de memória em duas fases: extração e atualização**. Primeiro, mensagens adicionadas ao thread de um agente são enviadas ao serviço Mem0, que usa um Modelo de Linguagem Grande (LLM) para resumir o histórico da conversa e extrair novas memórias. Posteriormente, uma fase de atualização conduzida por LLM determina se adiciona, modifica ou exclui essas memórias, armazenando-as em uma base de dados híbrida que pode incluir bancos vetoriais, de grafo e chave-valor. Esse sistema também suporta vários tipos de memória e pode incorporar memória em grafo para gerenciar relacionamentos entre entidades.

#### Cognee

Outra abordagem poderosa é usar o **Cognee**, uma memória semântica open-source para agentes de IA que transforma dados estruturados e não estruturados em grafos de conhecimento consultáveis apoiados por embeddings. O Cognee fornece uma **arquitetura de armazenamento dupla** combinando busca por similaridade vetorial com relacionamentos em grafo, permitindo que agentes entendam não apenas o que é informação similar, mas como os conceitos se relacionam entre si.

Ele se destaca na **recuperação híbrida** que combina similaridade vetorial, estrutura de grafo e raciocínio de LLM - desde buscas por chunk raw até perguntas conscientes do grafo. O sistema mantém uma **memória viva** que evolui e cresce enquanto permanece consultável como um grafo conectado, suportando tanto o contexto de sessão de curto prazo quanto a memória persistente de longo prazo.

O tutorial em notebook do Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstra a construção dessa camada unificada de memória, com exemplos práticos de ingestão de diversas fontes de dados, visualização do grafo de conhecimento e consultas com diferentes estratégias de busca adaptadas às necessidades específicas do agente.

### Armazenando Memória com RAG

Além de ferramentas especializadas de memória como Mem0, você pode aproveitar serviços robustos de busca como **Azure AI Search como backend para armazenar e recuperar memórias**, especialmente para RAG estruturado.

Isso permite fundamentar as respostas do seu agente com seus próprios dados, assegurando respostas mais relevantes e precisas. O Azure AI Search pode ser usado para armazenar memórias de viagem específicas do usuário, catálogos de produtos ou qualquer outro conhecimento de domínio específico.

O Azure AI Search suporta capacidades como **RAG Estruturado**, que se destaca na extração e recuperação de informação densa e estruturada de grandes conjuntos de dados como históricos de conversas, e-mails ou até imagens. Isso proporciona "precisão e recuperação superhumanas" comparadas a abordagens tradicionais de divisão e embedding de texto.

## Fazendo Agentes de IA Autoaperfeiçoáveis

Um padrão comum para agentes autoaperfeiçoáveis envolve introduzir um **"agente de conhecimento"**. Esse agente separado observa a conversa principal entre o usuário e o agente primário. Seu papel é:

1. **Identificar informações valiosas**: Determinar se alguma parte da conversa vale a pena ser salva como conhecimento geral ou preferência específica do usuário.

2. **Extrair e resumir**: Destilar o aprendizado ou preferência essencial da conversa.

3. **Armazenar em uma base de conhecimento**: Persistir essa informação extraída, frequentemente em um banco de dados vetorial, para que possa ser recuperada depois.

4. **Aumentar consultas futuras**: Quando o usuário iniciar uma nova consulta, o agente de conhecimento recupera informações relevantes armazenadas e as adiciona ao prompt do usuário, fornecendo contexto crucial ao agente primário (similarly a RAG).

### Otimizações para Memória

• **Gerenciamento de Latência**: Para evitar desacelerar interações do usuário, um modelo mais barato e rápido pode ser usado inicialmente para verificar com rapidez se uma informação é valiosa para armazenar ou recuperar, invocando o processo mais complexo de extração/recuperação somente quando necessário.

• **Manutenção da Base de Conhecimento**: Para uma base de conhecimento em crescimento, informações menos usadas com frequência podem ser movidas para "armazenamento frio" para gerenciar custos.

## Tem Mais Perguntas Sobre Memória de Agentes?

Junte-se ao [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) para encontrar outros aprendizes, participar de horários de atendimento e obter respostas para suas perguntas sobre Agentes de IA.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:  
Este documento foi traduzido utilizando o serviço de tradução automática [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos pela precisão, por favor, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte autoritativa. Para informações críticas, recomenda-se a tradução profissional feita por um humano. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações equivocadas decorrentes do uso desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->