# Mémoire pour les agents IA  
[![Agent Memory](../../../translated_images/fr/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Lorsqu'on discute des avantages uniques de créer des agents IA, deux éléments sont principalement évoqués : la capacité à appeler des outils pour accomplir des tâches et la capacité à s'améliorer avec le temps. La mémoire est à la base de la création d'un agent auto-améliorant capable de créer de meilleures expériences pour nos utilisateurs.

Dans cette leçon, nous verrons ce qu'est la mémoire pour les agents IA et comment nous pouvons la gérer et l'utiliser au profit de nos applications.

## Introduction

Cette leçon couvrira :

• **Comprendre la mémoire des agents IA** : ce qu'est la mémoire et pourquoi elle est essentielle pour les agents.

• **Implémenter et stocker la mémoire** : méthodes pratiques pour ajouter des capacités de mémoire à vos agents IA, en se concentrant sur la mémoire à court terme et à long terme.

• **Rendre les agents IA auto-améliorants** : comment la mémoire permet aux agents d'apprendre des interactions passées et de s'améliorer au fil du temps.

## Implémentations disponibles

Cette leçon comprend deux tutoriels complets en notebook :

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)** : implémente la mémoire avec Mem0 et Azure AI Search via le framework Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)** : implémente une mémoire structurée avec Cognee, construisant automatiquement un graphe de connaissance basé sur des embeddings, visualisant le graphe, et supportant une récupération intelligente

## Objectifs d'apprentissage

Après avoir terminé cette leçon, vous saurez comment :

• **Différencier les différents types de mémoire des agents IA**, y compris la mémoire de travail, à court terme, à long terme, ainsi que des formes spécialisées telles que la mémoire de persona et épisodique.

• **Implémenter et gérer la mémoire à court terme et à long terme pour les agents IA** en utilisant le framework Semantic Kernel, en tirant parti d'outils comme Mem0, Cognee, Whiteboard memory, et en intégrant Azure AI Search.

• **Comprendre les principes derrière les agents IA auto-améliorants** et comment des systèmes robustes de gestion de mémoire contribuent à un apprentissage et une adaptation continus.

## Comprendre la mémoire des agents IA

Au cœur, **la mémoire pour les agents IA fait référence aux mécanismes qui leur permettent de retenir et de rappeler des informations**. Ces informations peuvent être des détails spécifiques sur une conversation, des préférences utilisateur, des actions passées, voire des schémas appris.

Sans mémoire, les applications IA sont souvent sans état, ce qui signifie que chaque interaction recommence à zéro. Cela conduit à une expérience utilisateur répétitive et frustrante où l'agent « oublie » le contexte ou les préférences précédentes.

### Pourquoi la mémoire est-elle importante ?

L'intelligence d’un agent est profondément liée à sa capacité à se souvenir et à utiliser les informations passées. La mémoire permet aux agents d'être :

• **Réfléchis** : Apprendre des actions et résultats passés.

• **Interactifs** : Maintenir le contexte au cours d'une conversation en cours.

• **Proactifs et Réactifs** : Anticiper les besoins ou répondre de manière appropriée en se basant sur des données historiques.

• **Autonomes** : Opérer de manière plus indépendante en s’appuyant sur des connaissances stockées.

L'objectif de l'implémentation de la mémoire est de rendre les agents plus **fiables et compétents**.

### Types de mémoire

#### Mémoire de travail

Pensez-y comme une feuille de brouillon utilisée par un agent durant une tâche ou un processus de pensée en cours. Elle contient l'information immédiate nécessaire pour calculer l'étape suivante.

Pour les agents IA, la mémoire de travail capture souvent l'information la plus pertinente d'une conversation, même si l'historique complet est long ou tronqué. Elle se concentre sur l'extraction d'éléments clés comme les exigences, propositions, décisions et actions.

**Exemple de mémoire de travail**

Dans un agent de réservation de voyage, la mémoire de travail pourrait capturer la demande actuelle de l'utilisateur, par exemple « Je veux réserver un voyage à Paris ». Cette exigence spécifique est retenue dans le contexte immédiat de l'agent pour guider l'interaction en cours.

#### Mémoire à court terme

Ce type de mémoire conserve l'information pendant la durée d'une seule conversation ou session. C’est le contexte de la discussion en cours, permettant à l’agent de se référer aux tours précédents du dialogue.

**Exemple de mémoire à court terme**

Si un utilisateur demande « Combien coûte un vol pour Paris ? » puis enchaîne avec « Et pour l’hébergement là-bas ? », la mémoire à court terme garantit que l’agent comprend que « là-bas » fait référence à « Paris » dans la même conversation.

#### Mémoire à long terme

Il s'agit d'informations qui persistent à travers plusieurs conversations ou sessions. Elle permet aux agents de se souvenir des préférences utilisateur, interactions historiques ou connaissances générales sur de longues périodes. Ceci est important pour la personnalisation.

**Exemple de mémoire à long terme**

Une mémoire à long terme pourrait stocker que « Ben aime le ski et les activités de plein air, apprécie le café avec vue sur la montagne, et veut éviter les pistes de ski avancées à cause d’une blessure passée ». Cette information, apprise lors d’interactions précédentes, influence les recommandations lors des futures sessions de planification de voyage, les rendant très personnalisées.

#### Mémoire de persona

Ce type de mémoire spécialisé aide un agent à développer une « personnalité » ou « persona » cohérente. Il permet à l’agent de retenir des détails sur lui-même ou son rôle prévu, rendant les interactions plus fluides et ciblées.

**Exemple de mémoire de persona**  
Si l’agent de voyage est conçu comme un « expert en planification de ski », la mémoire de persona pourrait renforcer ce rôle en influençant ses réponses pour correspondre au ton et aux connaissances d’un expert.

#### Mémoire de flux de travail / épisodique

Cette mémoire enregistre la séquence d’étapes qu’un agent effectue lors d’une tâche complexe, y compris les succès et échecs. C’est comme se souvenir d’épisodes spécifiques ou d’expériences passées pour en tirer des enseignements.

**Exemple de mémoire épisodique**

Si l’agent a tenté de réserver un vol spécifique mais a échoué à cause d’une indisponibilité, la mémoire épisodique pourrait enregistrer cet échec, permettant à l’agent d’essayer des vols alternatifs ou d’informer l’utilisateur de façon plus éclairée lors d’une tentative ultérieure.

#### Mémoire d’entité

Cela implique d’extraire et de retenir des entités spécifiques (comme des personnes, lieux ou objets) et des événements provenant des conversations. Cela permet à l’agent de construire une compréhension structurée des éléments clés discutés.

**Exemple de mémoire d’entité**

Lors d’une conversation sur un voyage passé, l’agent pourrait extraire « Paris », « Tour Eiffel » et « dîner au restaurant Le Chat Noir » comme entités. Lors d’une interaction future, l’agent pourrait se souvenir de « Le Chat Noir » et proposer d’en faire une nouvelle réservation.

#### RAG structuré (Retrieval Augmented Generation)

Bien que RAG soit une technique plus large, le « RAG structuré » est mis en avant comme une technologie de mémoire puissante. Il extrait des informations denses et structurées de diverses sources (conversations, emails, images) et l’utilise pour améliorer la précision, le rappel et la rapidité des réponses. Contrairement au RAG classique qui se base uniquement sur la similarité sémantique, le RAG structuré exploite la structure inhérente de l’information.

**Exemple de RAG structuré**

Au lieu de simplement faire correspondre des mots-clés, le RAG structuré pourrait analyser les détails d’un vol (destination, date, heure, compagnie aérienne) depuis un email et les stocker de manière structurée. Cela permet des requêtes précises comme « Quel vol ai-je réservé pour Paris mardi ? »

## Implémenter et stocker la mémoire

L’implémentation de la mémoire pour les agents IA implique un processus systématique de **gestion de la mémoire**, qui comprend la génération, le stockage, la récupération, l’intégration, la mise à jour, et même l’« oubli » (ou suppression) d’informations. La récupération est un aspect particulièrement crucial.

### Outils spécialisés de mémoire

#### Mem0

Une façon de stocker et gérer la mémoire d’agent est d’utiliser des outils spécialisés comme Mem0. Mem0 fonctionne comme une couche de mémoire persistante, permettant aux agents de se souvenir des interactions pertinentes, de stocker les préférences utilisateur et le contexte factuel, et d’apprendre des réussites et échecs au fil du temps. L’idée est ici que les agents sans état deviennent des agents avec état.

Cela fonctionne via un **pipeline mémoire en deux phases : extraction et mise à jour**. D’abord, les messages ajoutés au fil de discussion d’un agent sont envoyés au service Mem0, qui utilise un modèle de langage large (LLM) pour résumer l’historique de la conversation et extraire de nouvelles mémoires. Ensuite, une phase de mise à jour pilotée par un LLM détermine s’il faut ajouter, modifier ou supprimer ces mémoires, en les stockant dans une base de données hybride pouvant inclure des bases vectorielles, graphe et clé-valeur. Ce système supporte également divers types de mémoire et peut intégrer la mémoire graphe pour gérer les relations entre entités.

#### Cognee

Une autre approche puissante est l’utilisation de **Cognee**, une mémoire sémantique open source pour agents IA qui transforme données structurées et non structurées en graphes de connaissances interrogeables basés sur des embeddings. Cognee fournit une **architecture à double stockage** combinant recherche de similarité vectorielle et relations graphiques, permettant aux agents de comprendre non seulement quelles informations sont similaires, mais aussi comment les concepts sont reliés.

Il excelle dans la **récupération hybride** qui mêle similarité vectorielle, structure du graphe, et raisonnement LLM – allant de la recherche brute par morceaux à la réponse à des questions conscientes du graphe. Le système maintient une **mémoire vivante** qui évolue et grandit tout en restant interrogeable sous la forme d’un graphe connecté, supportant à la fois le contexte de session court terme et la mémoire persistante long terme.

Le tutoriel notebook Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) montre comment construire cette couche de mémoire unifiée, avec des exemples pratiques d’ingestion de sources de données diverses, de visualisation du graphe de connaissance, et d’interrogation via différentes stratégies de recherche adaptées aux besoins spécifiques des agents.

### Stocker la mémoire avec RAG

Au-delà des outils spécialisés comme mem0, vous pouvez exploiter des services de recherche robustes tels que **Azure AI Search comme backend pour stocker et récupérer les mémoires**, en particulier pour le RAG structuré.

Cela vous permet d’ancrer les réponses de votre agent avec vos propres données, garantissant des réponses plus pertinentes et précises. Azure AI Search peut être utilisé pour stocker des mémoires de voyage spécifiques à l’utilisateur, des catalogues produits ou toute autre connaissance spécifique à un domaine.

Azure AI Search prend en charge des capacités comme le **RAG structuré**, qui excelle dans l’extraction et la récupération d’informations denses et structurées provenant de grands ensembles de données comme l’historique de conversations, emails, voire images. Cela offre une « précision et un rappel surhumains » par rapport aux approches traditionnelles de découpage de texte et d’embeddings.

## Rendre les agents IA auto-améliorants

Un schéma courant pour les agents auto-améliorants consiste à introduire un **« agent de connaissance »**. Cet agent séparé observe la conversation principale entre l’utilisateur et l’agent principal. Son rôle est de :

1. **Identifier les informations précieuses** : déterminer si une partie de la conversation mérite d’être sauvegardée comme connaissance générale ou préférence spécifique utilisateur.

2. **Extraire et résumer** : distiller l’apprentissage ou la préférence essentielle de la conversation.

3. **Stocker dans une base de connaissances** : persister cette information extraite, souvent dans une base vectorielle, pour la récupérer ultérieurement.

4. **Augmenter les requêtes futures** : lorsque l’utilisateur initie une nouvelle requête, l’agent de connaissance récupère les informations pertinentes stockées et les ajoute à l’invite de l’utilisateur, fournissant un contexte crucial à l’agent principal (similaire au RAG).

### Optimisations pour la mémoire

• **Gestion de la latence** : pour éviter de ralentir les interactions utilisateur, un modèle moins coûteux et plus rapide peut être utilisé initialement pour vérifier rapidement si l’information est valable à stocker ou récupérer, en invoquant seulement le processus d’extraction/récupération plus complexe lorsque nécessaire.

• **Maintenance de la base de connaissances** : pour une base croissante, les informations moins fréquemment utilisées peuvent être déplacées en « stockage froid » pour gérer les coûts.

## Vous avez plus de questions sur la mémoire des agents ?

Rejoignez le [Discord Azure AI Foundry](https://aka.ms/ai-agents/discord) pour rencontrer d’autres apprenants, participer aux heures de bureau et obtenir des réponses à vos questions sur les agents IA.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Clause de non-responsabilité** :  
Ce document a été traduit à l’aide du service de traduction automatique [Co-op Translator](https://github.com/Azure/co-op-translator). Bien que nous nous efforçons d’assurer l’exactitude, veuillez noter que les traductions automatiques peuvent comporter des erreurs ou des inexactitudes. Le document original dans sa langue d’origine doit être considéré comme la source faisant autorité. Pour les informations critiques, une traduction professionnelle réalisée par un humain est recommandée. Nous déclinons toute responsabilité en cas de malentendus ou de mauvaises interprétations résultant de l’utilisation de cette traduction.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->