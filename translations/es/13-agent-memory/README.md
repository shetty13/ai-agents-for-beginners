# Memoria para Agentes de IA 
[![Agent Memory](../../../translated_images/es/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Al hablar de los beneficios únicos de crear Agentes de IA, se discuten principalmente dos cosas: la capacidad de llamar herramientas para completar tareas y la capacidad de mejorar con el tiempo. La memoria está en la base de la creación de agentes auto-mejorables que pueden ofrecer mejores experiencias a nuestros usuarios.

En esta lección, veremos qué es la memoria para Agentes de IA y cómo podemos gestionarla y usarla para el beneficio de nuestras aplicaciones.

## Introducción

Esta lección cubrirá:

• **Entendiendo la Memoria de Agentes de IA**: Qué es la memoria y por qué es esencial para los agentes.

• **Implementación y Almacenamiento de la Memoria**: Métodos prácticos para agregar capacidades de memoria a tus agentes de IA, enfocándose en memoria a corto y largo plazo.

• **Haciendo que los Agentes de IA se Auto-mejoren**: Cómo la memoria permite que los agentes aprendan de interacciones pasadas y mejoren con el tiempo.

## Implementaciones Disponibles

Esta lección incluye dos tutoriales completos en notebooks:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementa memoria usando Mem0 y Azure AI Search con el framework Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementa memoria estructurada usando Cognee, construyendo automáticamente un grafo de conocimiento respaldado por embeddings, visualizando el grafo y recuperación inteligente

## Objetivos de Aprendizaje

Después de completar esta lección, sabrás cómo:

• **Diferenciar entre varios tipos de memoria en agentes de IA**, incluyendo memoria de trabajo, a corto plazo y a largo plazo, así como formas especializadas como memoria de persona y episódica.

• **Implementar y gestionar la memoria a corto y largo plazo para agentes de IA** usando el framework Semantic Kernel, aprovechando herramientas como Mem0, Cognee, memoria Whiteboard, e integrando con Azure AI Search.

• **Entender los principios detrás de agentes de IA auto-mejorables** y cómo sistemas robustos de gestión de memoria contribuyen al aprendizaje y adaptación continuos.

## Entendiendo la Memoria de Agentes de IA

En esencia, **la memoria para agentes de IA se refiere a los mecanismos que les permiten retener y recordar información**. Esta información puede ser detalles específicos sobre una conversación, preferencias del usuario, acciones pasadas o incluso patrones aprendidos.

Sin memoria, las aplicaciones de IA suelen ser sin estado, lo que significa que cada interacción comienza desde cero. Esto lleva a una experiencia de usuario repetitiva y frustrante donde el agente "olvida" el contexto o preferencias previas.

### ¿Por qué es importante la memoria?

La inteligencia de un agente está profundamente ligada a su capacidad para recordar y utilizar información pasada. La memoria permite que los agentes sean:

• **Reflexivos**: Aprendiendo de acciones y resultados pasados.

• **Interactivos**: Manteniendo el contexto durante una conversación en curso.

• **Proactivos y Reactivos**: Anticipando necesidades o respondiendo apropiadamente basados en datos históricos.

• **Autónomos**: Operando de forma más independiente al recurrir a conocimiento almacenado.

El objetivo de implementar memoria es hacer a los agentes más **fiables y capaces**.

### Tipos de Memoria

#### Memoria de Trabajo

Piensa en esto como un papel en blanco que un agente usa durante una única tarea o proceso de pensamiento en curso. Contiene información inmediata necesaria para calcular el siguiente paso.

Para agentes de IA, la memoria de trabajo a menudo captura la información más relevante de una conversación, incluso si el historial completo del chat es largo o truncado. Se enfoca en extraer elementos clave como requerimientos, propuestas, decisiones y acciones.

**Ejemplo de Memoria de Trabajo**

En un agente de reservas de viajes, la memoria de trabajo podría capturar la solicitud actual del usuario, como "Quiero reservar un viaje a París". Este requisito específico se mantiene en el contexto inmediato del agente para guiar la interacción actual.

#### Memoria a Corto Plazo

Este tipo de memoria retiene información durante la duración de una sola conversación o sesión. Es el contexto del chat actual, permitiendo al agente referirse a turnos previos en el diálogo.

**Ejemplo de Memoria a Corto Plazo**

Si un usuario pregunta, "¿Cuánto costaría un vuelo a París?" y luego continúa con "¿Y el alojamiento allí?", la memoria a corto plazo asegura que el agente entienda que "allí" se refiere a "París" dentro de la misma conversación.

#### Memoria a Largo Plazo

Esta es información que persiste a lo largo de múltiples conversaciones o sesiones. Permite a los agentes recordar preferencias del usuario, interacciones históricas o conocimiento general durante períodos extensos. Esto es importante para la personalización.

**Ejemplo de Memoria a Largo Plazo**

Una memoria a largo plazo podría almacenar que "Ben disfruta el esquí y actividades al aire libre, le gusta el café con vista a la montaña y quiere evitar pistas de esquí avanzadas por una lesión pasada". Esta información, aprendida de interacciones previas, influye en recomendaciones en futuras sesiones de planificación de viajes, haciéndolas altamente personalizadas.

#### Memoria de Persona

Este tipo especial de memoria ayuda a un agente a desarrollar una "personalidad" o "persona" consistente. Permite que el agente recuerde detalles sobre sí mismo o su rol previsto, haciendo las interacciones más fluidas y enfocadas.

**Ejemplo de Memoria de Persona**

Si el agente de viajes está diseñado para ser un "planificador de esquí experto," la memoria de persona podría reforzar este rol, influyendo en sus respuestas para alinearse con el tono y conocimiento de un experto.

#### Memoria de Flujo de Trabajo/Episódica

Esta memoria almacena la secuencia de pasos que un agente realiza durante una tarea compleja, incluyendo éxitos y fallos. Es como recordar "episodios" o experiencias pasadas para aprender de ellas.

**Ejemplo de Memoria Episódica**

Si el agente intentó reservar un vuelo específico pero falló debido a falta de disponibilidad, la memoria episódica podría registrar este fallo, permitiendo que el agente intente vuelos alternativos o informe al usuario sobre el problema de forma más informada durante un intento posterior.

#### Memoria de Entidades

Esto implica extraer y recordar entidades específicas (como personas, lugares o cosas) y eventos de conversaciones. Permite que el agente construya una comprensión estructurada de los elementos clave discutidos.

**Ejemplo de Memoria de Entidades**

De una conversación sobre un viaje pasado, el agente podría extraer "París", "Torre Eiffel" y "cena en el restaurante Le Chat Noir" como entidades. En una futura interacción, el agente podría recordar "Le Chat Noir" y ofrecer hacer una nueva reserva allí.

#### RAG Estructurado (Generación Aumentada por Recuperación)

Aunque RAG es una técnica más amplia, el "RAG estructurado" se destaca como una poderosa tecnología de memoria. Extrae información densa y estructurada de varias fuentes (conversaciones, correos electrónicos, imágenes) y la usa para mejorar la precisión, recuperación y velocidad en las respuestas. A diferencia del RAG clásico que se basa solo en similitud semántica, el RAG estructurado trabaja con la estructura inherente de la información.

**Ejemplo de RAG Estructurado**

En lugar de solo coincidir palabras clave, el RAG estructurado podría analizar detalles de un vuelo (destino, fecha, hora, aerolínea) desde un correo electrónico y almacenarlos de forma estructurada. Esto permite consultas precisas como "¿Qué vuelo reservé a París el martes?"

## Implementación y Almacenamiento de la Memoria

Implementar memoria para agentes de IA implica un proceso sistemático de **gestión de memoria**, que incluye generar, almacenar, recuperar, integrar, actualizar e incluso "olvidar" (o eliminar) información. La recuperación es un aspecto particularmente crucial.

### Herramientas Especializadas de Memoria

#### Mem0

Una forma de almacenar y gestionar la memoria del agente es usando herramientas especializadas como Mem0. Mem0 funciona como una capa de memoria persistente, permitiendo que los agentes recuerden interacciones relevantes, almacenen preferencias del usuario y contexto factual, y aprendan de éxitos y fallos a lo largo del tiempo. La idea aquí es que agentes sin estado se convierten en agentes con estado.

Opera mediante un **flujo de memoria en dos fases: extracción y actualización**. Primero, los mensajes añadidos al hilo de un agente se envían al servicio Mem0, que usa un Modelo de Lenguaje Grande (LLM) para resumir el historial de conversación y extraer nuevas memorias. Posteriormente, una fase de actualización dirigida por LLM determina si agregar, modificar o eliminar estas memorias, almacenándolas en un almacenamiento híbrido de datos que puede incluir bases de datos vectoriales, gráficas y key-value. Este sistema también soporta varios tipos de memoria y puede incorporar memoria de grafo para gestionar relaciones entre entidades.

#### Cognee

Otro enfoque poderoso es usar **Cognee**, una memoria semántica de código abierto para agentes de IA que transforma datos estructurados y no estructurados en grafos de conocimiento consultables respaldados por embeddings. Cognee proporciona una **arquitectura de doble almacenamiento** que combina búsqueda por similitud vectorial con relaciones gráficas, permitiendo que los agentes entiendan no solo qué información es similar, sino cómo los conceptos se relacionan entre sí.

Destaca en la **recuperación híbrida** que mezcla similitud vectorial, estructura de grafo y razonamiento LLM - desde la búsqueda de fragmentos sin procesar hasta la respuesta a preguntas consciente del grafo. El sistema mantiene una **memoria viva** que evoluciona y crece mientras permanece consultable como un grafo conectado, soportando tanto el contexto de sesión a corto plazo como la memoria persistente a largo plazo.

El tutorial en notebook de Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demuestra cómo construir esta capa unificada de memoria, con ejemplos prácticos de ingestión de diversas fuentes de datos, visualización del grafo de conocimiento y consultas con diferentes estrategias de búsqueda adaptadas a las necesidades específicas del agente.

### Almacenando Memoria con RAG

Más allá de herramientas especializadas como Mem0, puedes aprovechar servicios robustos de búsqueda como **Azure AI Search como backend para almacenar y recuperar memorias**, especialmente para RAG estructurado.

Esto te permite fundamentar las respuestas de tu agente con tus propios datos, asegurando respuestas más relevantes y precisas. Azure AI Search puede usarse para almacenar memorias de viajes específicas de usuarios, catálogos de productos o cualquier otro conocimiento específico del dominio.

Azure AI Search soporta capacidades como **RAG Estructurado**, que sobresale en la extracción y recuperación de información densa y estructurada desde grandes conjuntos de datos como historiales de conversación, correos electrónicos o incluso imágenes. Esto provee "precisión y recuperación sobrehumana" comparado con enfoques tradicionales de fragmentación de texto y embeddings.

## Haciendo que los Agentes de IA se Auto-mejoren

Un patrón común para agentes auto-mejorables implica introducir un **"agente de conocimiento"**. Este agente separado observa la conversación principal entre el usuario y el agente primario. Su rol es:

1. **Identificar información valiosa**: Determinar si alguna parte de la conversación vale la pena guardar como conocimiento general o preferencia específica del usuario.

2. **Extraer y resumir**: Destilar el aprendizaje o preferencia esencial de la conversación.

3. **Almacenar en una base de conocimiento**: Persistir esta información extraída, frecuentemente en una base de datos vectorial, para que pueda ser recuperada después.

4. **Aumentar consultas futuras**: Cuando el usuario inicia una nueva consulta, el agente de conocimiento recupera información almacenada relevante y la agrega al prompt del usuario, proporcionando contexto crucial al agente primario (similar a RAG).

### Optimizaciones para la Memoria

• **Gestión de Latencia**: Para evitar ralentizar las interacciones del usuario, un modelo más barato y rápido puede usarse inicialmente para verificar con rapidez si la información es valiosa para almacenar o recuperar, invocando el proceso de extracción/recuperación más complejo solo cuando es necesario.

• **Mantenimiento de la Base de Conocimiento**: Para una base de conocimiento en crecimiento, la información menos usada puede trasladarse a "almacenamiento en frío" para gestionar costos.

## ¿Tienes Más Preguntas Sobre la Memoria de Agentes?

Únete al [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) para encontrarte con otros aprendices, asistir a horas de oficina y resolver tus preguntas sobre Agentes de IA.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso legal**:  
Este documento ha sido traducido utilizando el servicio de traducción automática [Co-op Translator](https://github.com/Azure/co-op-translator). Aunque nos esforzamos por la precisión, tenga en cuenta que las traducciones automáticas pueden contener errores o inexactitudes. El documento original en su idioma nativo debe considerarse la fuente autorizada. Para información crítica, se recomienda una traducción profesional realizada por humanos. No nos responsabilizamos por ningún malentendido o interpretación errónea que surja del uso de esta traducción.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->