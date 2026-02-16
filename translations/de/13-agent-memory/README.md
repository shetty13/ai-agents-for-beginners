# Speicher für KI-Agenten 
[![Agent Memory](../../../translated_images/de/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Beim Gespräch über die einzigartigen Vorteile der Erstellung von KI-Agenten werden hauptsächlich zwei Dinge diskutiert: die Fähigkeit, Werkzeuge zur Erfüllung von Aufgaben aufzurufen, und die Fähigkeit, sich im Laufe der Zeit zu verbessern. Speicher bildet die Grundlage für die Erstellung selbstverbessernder Agenten, die bessere Erlebnisse für unsere Nutzer schaffen können.

In dieser Lektion betrachten wir, was Speicher für KI-Agenten bedeutet und wie wir ihn verwalten und zum Nutzen unserer Anwendungen einsetzen können.

## Einführung

Diese Lektion behandelt:

• **Verständnis des Speichers von KI-Agenten**: Was Speicher ist und warum er für Agenten wichtig ist.

• **Implementierung und Speicherung von Speicher**: Praktische Methoden zum Hinzufügen von Speicherfunktionen zu Ihren KI-Agenten, mit Fokus auf Kurzzeit- und Langzeitspeicher.

• **Selbstverbesserung von KI-Agenten**: Wie Speicher es den Agenten ermöglicht, aus vergangenen Interaktionen zu lernen und sich im Laufe der Zeit zu verbessern.

## Verfügbare Implementierungen

Diese Lektion enthält zwei umfassende Notebook-Tutorials:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementiert Speicher mit Mem0 und Azure AI Search im Semantic Kernel-Framework

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementiert strukturierten Speicher mit Cognee, das automatisch ein wissensgraphgestütztes System durch Embeddings aufbaut, den Graph visualisiert und intelligente Abfragen unterstützt

## Lernziele

Nach Abschluss dieser Lektion werden Sie wissen, wie Sie:

• **Zwischen verschiedenen Arten von KI-Agentenspeicher unterscheiden**, einschließlich Arbeits-, Kurzzeit- und Langzeitspeicher sowie spezialisierten Formen wie Persona- und episodischem Speicher.

• **Kurzzeit- und Langzeitspeicher für KI-Agenten implementieren und verwalten** mithilfe des Semantic Kernel-Frameworks unter Verwendung von Tools wie Mem0, Cognee, Whiteboard-Speicher sowie der Integration mit Azure AI Search.

• **Die Prinzipien hinter selbstverbessernden KI-Agenten verstehen** und wie robuste Speichersysteme zu kontinuierlichem Lernen und Anpassung beitragen.

## Verständnis des Speichers von KI-Agenten

Im Kern bezeichnet **Speicher für KI-Agenten die Mechanismen, die es ihnen ermöglichen, Informationen zu behalten und abzurufen**. Diese Informationen können spezifische Details über ein Gespräch, Nutzerpräferenzen, vergangene Aktionen oder sogar gelernte Muster sein.

Ohne Speicher sind KI-Anwendungen oft zustandslos, was bedeutet, dass jede Interaktion von vorne beginnt. Dies führt zu einer sich wiederholenden und frustrierenden Nutzererfahrung, bei der der Agent den vorherigen Kontext oder Präferenzen "vergisst".

### Warum ist Speicher wichtig?

Die Intelligenz eines Agenten ist eng mit seiner Fähigkeit verbunden, vergangene Informationen abzurufen und zu nutzen. Speicher ermöglicht es Agenten, zu sein:

• **Reflektierend**: Aus vergangenen Aktionen und Ergebnissen zu lernen.

• **Interaktiv**: Den Kontext eines laufenden Gesprächs zu erhalten.

• **Proaktiv und Reaktiv**: Bedürfnisse vorherzusehen oder passend basierend auf historischen Daten zu reagieren.

• **Autonom**: Selbstständiger zu agieren, indem auf gespeichertes Wissen zurückgegriffen wird.

Ziel der Implementierung von Speicher ist es, Agenten **zuverlässiger und leistungsfähiger** zu machen.

### Arten von Speicher

#### Arbeitsgedächtnis

Man kann es sich wie ein Notizblatt vorstellen, das ein Agent während einer einzelnen, laufenden Aufgabe oder Gedankenkette verwendet. Es hält unmittelbare Informationen, die benötigt werden, um den nächsten Schritt zu berechnen.

Für KI-Agenten fängt das Arbeitsgedächtnis oft die relevantesten Informationen aus einem Gespräch ein, selbst wenn der gesamte Chatverlauf lang oder gekürzt ist. Der Fokus liegt auf der Extraktion von Schlüsselelementen wie Anforderungen, Vorschlägen, Entscheidungen und Aktionen.

**Beispiel für Arbeitsgedächtnis**

Bei einem Reisebuchungsagenten könnte das Arbeitsgedächtnis die aktuelle Anfrage des Nutzers enthalten, wie "Ich möchte eine Reise nach Paris buchen". Diese spezifische Anforderung wird im unmittelbaren Kontext des Agenten gehalten, um die aktuelle Interaktion zu steuern.

#### Kurzzeitgedächtnis

Dieser Speichertyp bewahrt Informationen für die Dauer eines einzelnen Gesprächs oder einer Sitzung. Es ist der Kontext des aktuellen Chats, der es dem Agenten erlaubt, auf vorherige Gesprächsschritte Bezug zu nehmen.

**Beispiel für Kurzzeitgedächtnis**

Wenn ein Nutzer fragt: „Wie viel würde ein Flug nach Paris kosten?“ und dann nachfragt: „Und wie sieht es mit der Unterkunft dort aus?“, sorgt das Kurzzeitgedächtnis dafür, dass der Agent weiß, dass sich "dort" im selben Gespräch auf "Paris" bezieht.

#### Langzeitgedächtnis

Dies sind Informationen, die über mehrere Gespräche oder Sitzungen hinweg erhalten bleiben. Sie ermöglichen es Agenten, Nutzerpräferenzen, historische Interaktionen oder allgemeines Wissen über längere Zeiträume zu speichern. Dies ist wichtig für die Personalisierung.

**Beispiel für Langzeitgedächtnis**

Das Langzeitgedächtnis könnte speichern, dass „Ben Skifahren und Outdoor-Aktivitäten mag, Kaffee mit Bergblick bevorzugt und aufgrund einer früheren Verletzung fortgeschrittene Skipisten meiden will“. Diese Informationen, die aus früheren Interaktionen stammen, beeinflussen Empfehlungen in zukünftigen Reiseplanungs-Sitzungen und machen diese hochgradig personalisiert.

#### Persona-Speicher

Dieser spezialisierte Speichertyp hilft einem Agenten, eine konsistente „Persönlichkeit“ oder „Persona“ zu entwickeln. Er erlaubt es dem Agenten, Details über sich selbst oder seine angestrebte Rolle zu speichern, was Interaktionen flüssiger und fokussierter macht.

**Beispiel für Persona-Speicher**

Wenn der Reiseagent als „Experte für Skiplanung“ konzipiert ist, könnte das Persona-Speicher diese Rolle verstärken und die Antworten im Ton und Wissen eines Experten beeinflussen.

#### Workflow-/episodischer Speicher

Dieser Speicher hält die Abfolge von Schritten fest, die ein Agent während einer komplexen Aufgabe durchführt, einschließlich Erfolgen und Misserfolgen. Es ist wie das Erinnern an spezifische „Episoden“ oder vergangene Erfahrungen, um daraus zu lernen.

**Beispiel für episodischen Speicher**

Wenn der Agent versucht hat, einen bestimmten Flug zu buchen, dies jedoch aufgrund von Nichtverfügbarkeit scheiterte, könnte der episodische Speicher diesen Misserfolg festhalten, was es dem Agenten erlaubt, alternative Flüge zu versuchen oder den Nutzer bei einem erneuten Versuch besser zu informieren.

#### Entitätenspeicher

Dies beinhaltet das Extrahieren und Merken spezifischer Entitäten (wie Personen, Orte oder Dinge) und Ereignisse aus Gesprächen. Es ermöglicht dem Agenten, ein strukturiertes Verständnis der diskutierten Schlüsselthemen aufzubauen.

**Beispiel für Entitätenspeicher**

Aus einem Gespräch über eine vergangene Reise könnte der Agent „Paris“, „Eiffelturm“ und „Abendessen im Restaurant Le Chat Noir“ als Entitäten extrahieren. In einer zukünftigen Interaktion könnte der Agent „Le Chat Noir“ abrufen und anbieten, dort eine neue Reservierung vorzunehmen.

#### Strukturierte RAG (Retrieval Augmented Generation)

Während RAG eine weit gefasste Technik ist, wird „Strukturierte RAG“ als mächtige Speichertechnologie hervorgehoben. Sie extrahiert dichte, strukturierte Informationen aus verschiedenen Quellen (Gesprächen, E-Mails, Bildern) und nutzt sie, um Präzision, Abrufqualität und Geschwindigkeit der Antworten zu verbessern. Im Gegensatz zum klassischen RAG, das nur auf semantischer Ähnlichkeit beruht, arbeitet Strukturierte RAG mit der inhärenten Struktur der Informationen.

**Beispiel für strukturierte RAG**

Anstatt nur Schlüsselwörter abzugleichen, könnte Strukturierte RAG Flugdaten (Reiseziel, Datum, Uhrzeit, Fluggesellschaft) aus einer E-Mail parsen und strukturiert speichern. Dies ermöglicht präzise Abfragen wie „Welchen Flug habe ich am Dienstag nach Paris gebucht?“

## Implementierung und Speicherung von Speicher

Die Implementierung von Speicher für KI-Agenten umfasst einen systematischen Prozess des **Speichermanagements**, welcher die Erzeugung, Speicherung, Abruf, Integration, Aktualisierung und sogar das „Vergessen“ (oder Löschen) von Informationen einschließt. Besonders wichtig ist der Abruf.

### Spezialisierte Speicherwerkzeuge

#### Mem0

Eine Möglichkeit, Agentenspeicher zu speichern und zu verwalten, ist die Nutzung spezialisierter Werkzeuge wie Mem0. Mem0 fungiert als persistente Speicherschicht, die es Agenten erlaubt, relevante Interaktionen zu erinnern, Nutzerpräferenzen und faktischen Kontext zu speichern sowie aus Erfolgen und Misserfolgen im Zeitverlauf zu lernen. Die Idee ist, zustandslose Agenten in zustandsbehaftete zu verwandeln.

Es arbeitet durch eine **zweiphasige Speicher-Pipeline: Extraktion und Aktualisierung**. Zunächst werden Nachrichten, die einem Agenten-Thread hinzugefügt werden, an den Mem0-Dienst gesendet, der mit einem Large Language Model (LLM) den Gesprächsverlauf zusammenfasst und neue Erinnerungen extrahiert. Danach bestimmt eine LLM-gesteuerte Aktualisierungsphase, ob diese Erinnerungen hinzugefügt, geändert oder gelöscht werden, und speichert sie in einem hybriden Datenspeicher, der Vektor-, Graph- und Key-Value-Datenbanken umfassen kann. Dieses System unterstützt außerdem verschiedene Speicherarten und kann Graphspeicher zur Verwaltung von Beziehungen zwischen Entitäten einbinden.

#### Cognee

Ein weiterer leistungsfähiger Ansatz ist die Nutzung von **Cognee**, einem Open-Source-sematischen Speicher für KI-Agenten, der strukturierte und unstrukturierte Daten in abfragbare Wissensgraphen umwandelt, unterstützt durch Embeddings. Cognee bietet eine **Dual-Store-Architektur**, die Vektorsuche mit Graphbeziehungen kombiniert und es Agenten ermöglicht, nicht nur zu verstehen, welche Informationen ähnlich sind, sondern auch wie Konzepte zueinander in Beziehung stehen.

Es zeichnet sich aus durch **hybriden Abruf**, der Vektorähnlichkeit, Graphstruktur und LLM-Reasoning verbindet – vom einfachen Chunk-Lookup bis hin zu graphbewusster Fragebeantwortung. Das System pflegt einen **lebendigen Speicher**, der sich entwickelt und wächst, dabei aber als ein zusammenhängender Graph abgefragt werden kann, und unterstützt sowohl kurzzeitigen Sitzungs-Kontext als auch langfristigen persistenten Speicher.

Das Cognee-Notebook-Tutorial ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstriert den Aufbau dieser einheitlichen Speicherschicht mit praktischen Beispielen zum Einlesen verschiedener Datenquellen, Visualisierung des Wissensgraphen und Abfragen mit unterschiedlichen Suchstrategien, die auf spezifische Agentenbedürfnisse zugeschnitten sind.

### Speicherung von Speicher mit RAG

Neben spezialisierten Speicherwerkzeugen wie Mem0 können Sie robuste Suchdienste wie **Azure AI Search als Backend zur Speicherung und zum Abruf von Erinnerungen** verwenden, insbesondere für strukturierte RAG.

Dies ermöglicht es, die Antworten Ihres Agenten mit Ihren eigenen Daten zu untermauern und so relevantere und genauere Antworten zu gewährleisten. Azure AI Search kann verwendet werden, um nutzerspezifische Reisespeicher, Produktkataloge oder jegliches anderes domänenspezifisches Wissen zu speichern.

Azure AI Search unterstützt Funktionen wie **Strukturierte RAG**, die darin brilliert, dichte, strukturierte Informationen aus großen Datensätzen wie Gesprächsverläufen, E-Mails oder sogar Bildern zu extrahieren und abzurufen. Dies bietet im Vergleich zu herkömmlichen Textchunking- und Embedding-Ansätzen „übermenschliche Präzision und Abrufqualität“.

## KI-Agenten selbstverbessern

Ein häufiges Muster für selbstverbessernde Agenten ist die Einführung eines **„Wissensagenten“**. Dieser separate Agent beobachtet das Hauptgespräch zwischen Nutzer und primärem Agenten. Seine Aufgabe ist es:

1. **Wertvolle Informationen identifizieren**: Herausfinden, ob Teile der Konversation als allgemeines Wissen oder spezifische Nutzerpräferenzen gespeichert werden sollten.

2. **Extrahieren und zusammenfassen**: Die wesentlichen Erkenntnisse oder Präferenzen aus der Konversation destillieren.

3. **Speicherung in einer Wissensdatenbank**: Diese extrahierten Informationen persistent speichern, oft in einer Vektordatenbank, sodass sie später abgerufen werden können.

4. **Erweiterung zukünftiger Anfragen**: Wenn der Nutzer eine neue Anfrage startet, ruft der Wissensagent relevante gespeicherte Informationen ab und fügt sie dem Prompt des Nutzers hinzu, um dem primären Agenten wichtigen Kontext zu geben (ähnlich wie bei RAG).

### Optimierungen für Speicher

• **Latenzmanagement**: Um Verzögerungen bei Nutzerinteraktionen zu vermeiden, kann zunächst ein günstigeres, schnelleres Modell eingesetzt werden, das schnell prüft, ob Informationen es wert sind, gespeichert oder abgerufen zu werden, und erst bei Bedarf der komplexere Extraktions-/Abrufprozess aktiviert wird.

• **Wartung der Wissensbasis**: Für eine wachsende Wissensbasis kann weniger häufig genutzte Information in „Cold Storage“ verschoben werden, um Kosten zu steuern.

## Haben Sie noch Fragen zum Agentenspeicher?

Treten Sie dem [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) bei, um andere Lernende zu treffen, an Office Hours teilzunehmen und Ihre Fragen zu KI-Agenten zu stellen.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Haftungsausschluss**:  
Dieses Dokument wurde mit dem KI-Übersetzungsdienst [Co-op Translator](https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir auf Genauigkeit achten, können automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten. Das Originaldokument in seiner Ursprungssprache gilt als maßgebliche Quelle. Für wichtige Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die durch die Nutzung dieser Übersetzung entstehen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->