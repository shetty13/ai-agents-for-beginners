# Pamięć dla Agentów AI  
[![Agent Memory](../../../translated_images/pl/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Podczas omawiania unikalnych korzyści związanych z tworzeniem Agentów AI, głównie porusza się dwie kwestie: zdolność do wywoływania narzędzi do wykonywania zadań oraz zdolność do ulepszania się w czasie. Pamięć leży u podstaw tworzenia samo-ulepszających się agentów, którzy mogą tworzyć lepsze doświadczenia dla naszych użytkowników.

W tej lekcji przyjrzymy się, czym jest pamięć dla Agentów AI oraz jak możemy nią zarządzać i wykorzystywać ją na korzyść naszych aplikacji.

## Wprowadzenie

Ta lekcja obejmie:

• **Zrozumienie pamięci Agenta AI**: Czym jest pamięć i dlaczego jest niezbędna dla agentów.

• **Implementacja i przechowywanie pamięci**: Praktyczne metody dodawania funkcji pamięci do twoich agentów AI, ze szczególnym uwzględnieniem pamięci krótkoterminowej i długoterminowej.

• **Sprawianie, by Agenci AI się samo-ulepszali**: Jak pamięć umożliwia agentom uczenie się na podstawie przeszłych interakcji i poprawę w czasie.

## Dostępne implementacje

Ta lekcja zawiera dwa kompleksowe poradniki w formie notebooków:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementuje pamięć z wykorzystaniem Mem0 oraz Azure AI Search wraz z frameworkiem Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementuje strukturę pamięci za pomocą Cognee, automatycznie budując graf wiedzy oparty na embeddings, wizualizując graf i inteligentne wyszukiwanie

## Cele nauki

Po ukończeniu tej lekcji będziesz potrafił:

• **Rozróżniać różne typy pamięci agenta AI**, w tym pamięć roboczą, krótkoterminową i długoterminową oraz wyspecjalizowane formy, takie jak pamięć persony i epizodyczna.

• **Implementować i zarządzać pamięcią krótkoterminową i długoterminową dla agentów AI** korzystając z frameworka Semantic Kernel, wykorzystując narzędzia takie jak Mem0, Cognee, Whiteboard memory oraz integrując się z Azure AI Search.

• **Zrozumieć zasady stojące za samo-ulepszającymi się agentami AI** oraz jak solidne systemy zarządzania pamięcią przyczyniają się do ciągłego uczenia się i adaptacji.

## Zrozumienie pamięci Agenta AI

U podstaw, **pamięć dla agentów AI odnosi się do mechanizmów umożliwiających im utrzymywanie i przypominanie informacji**. Informacje te mogą obejmować szczegóły rozmowy, preferencje użytkownika, wcześniejsze działania lub nawet wyuczone wzorce.

Bez pamięci aplikacje AI są często bezstanowe, co oznacza, że każda interakcja zaczyna się od zera. Prowadzi to do powtarzalnego i frustrującego doświadczenia użytkownika, gdy agent „zapomina” poprzedni kontekst lub preferencje.

### Dlaczego pamięć jest ważna?

Inteligencja agenta jest głęboko powiązana z jego zdolnością do przypominania i wykorzystywania przeszłych informacji. Pamięć pozwala agentom na:

• **Refleksyjność**: Uczenie się na podstawie poprzednich działań i rezultatów.

• **Interaktywność**: Utrzymywanie kontekstu podczas trwającej rozmowy.

• **Proaktywność i reaktywność**: Przewidywanie potrzeb lub odpowiednie reagowanie na podstawie danych historycznych.

• **Autonomię**: Działanie bardziej niezależne dzięki korzystaniu z przechowywanej wiedzy.

Celem implementacji pamięci jest uczynienie agentów bardziej **wiarygodnymi i zdolnymi**.

### Typy pamięci

#### Pamięć robocza

Możesz ją porównać do kartki papieru, której agent używa podczas pojedynczego, trwającego zadania lub procesu myślowego. Przechowuje ona bezpośrednio potrzebne informacje do wykonania następnego kroku.

Dla agentów AI pamięć robocza często wychwytuje najbardziej istotne informacje z rozmowy, nawet jeśli cała historia czatu jest długa lub obcięta. Skupia się na wydobywaniu kluczowych elementów jak wymagania, propozycje, decyzje i działania.

**Przykład pamięci roboczej**

W agencie do rezerwacji podróży pamięć robocza może przechowywać bieżące żądanie użytkownika, np. „Chcę zarezerwować wycieczkę do Paryża”. Ta konkretna potrzeba jest utrzymywana w bezpośrednim kontekście agenta, aby kierować bieżącą interakcją.

#### Pamięć krótkoterminowa

Ten typ pamięci przechowuje informacje przez czas trwania pojedynczej rozmowy lub sesji. To kontekst aktualnego czatu, pozwalający agentowi odwoływać się do wcześniejszych wypowiedzi w dialogu.

**Przykład pamięci krótkoterminowej**

Jeśli użytkownik zapyta „Ile kosztuje lot do Paryża?” a następnie doda „A co z noclegiem tam?”, pamięć krótkoterminowa zapewnia, że agent rozumie, że „tam” odnosi się do „Paryża” w obrębie tej samej rozmowy.

#### Pamięć długoterminowa

To informacje, które utrzymują się między wieloma rozmowami lub sesjami. Pozwala agentom zapamiętywać preferencje użytkownika, historyczne interakcje lub wiedzę ogólną przez dłuższy czas. To ważne dla personalizacji.

**Przykład pamięci długoterminowej**

Pamięć długoterminowa może zapisać, że „Ben lubi narciarstwo i aktywności na świeżym powietrzu, pije kawę z widokiem na góry i chce unikać zaawansowanych tras narciarskich ze względu na wcześniejszą kontuzję”. Te informacje, wyuczone z poprzednich interakcji, wpływają na rekomendacje podczas przyszłych sesji planowania podróży, czyniąc je wysoce spersonalizowanymi.

#### Pamięć persony

Ten wyspecjalizowany typ pamięci pomaga agentowi rozwijać spójną „osobowość” lub „personę”. Umożliwia agentowi zapamiętanie szczegółów o sobie lub o swojej roli, dzięki czemu interakcje są bardziej płynne i skupione.

**Przykład pamięci persony**

Jeśli agent podróżniczy jest zaprojektowany jako „ekspert ds. planowania wyjazdów narciarskich”, pamięć persony może wzmocnić tę rolę, wpływając na odpowiedzi zgodnie z tonem i wiedzą eksperta.

#### Pamięć przepływu pracy/epizodyczna

Ta pamięć zapisuje kolejność kroków, jakie agent podejmuje podczas złożonego zadania, włączając w to sukcesy i porażki. To jak zapamiętywanie konkretnych „epizodów” lub doświadczeń, z których można się uczyć.

**Przykład pamięci epizodycznej**

Jeśli agent próbował zarezerwować określony lot, ale nie powiodło się to z powodu braku dostępności, pamięć epizodyczna może zarejestrować tę nieudaną próbę, pozwalając agentowi spróbować alternatywnych lotów lub poinformować użytkownika o problemie w bardziej świadomy sposób podczas kolejnej próby.

#### Pamięć encji

Polega na wydobywaniu i zapamiętywaniu konkretnych encji (jak osoby, miejsca lub rzeczy) oraz wydarzeń z rozmów. Pozwala agentowi budować strukturalne rozumienie kluczowych elementów omówionych w konwersacji.

**Przykład pamięci encji**

Z rozmowy o przeszłej podróży agent może wyciągnąć takie encje jak „Paryż”, „Wieża Eiffla” oraz „kolacja w restauracji Le Chat Noir”. W przyszłej interakcji agent mógłby przypomnieć sobie „Le Chat Noir” i zaoferować dokonanie nowej rezerwacji w tym miejscu.

#### Strukturalny RAG (Retrieval Augmented Generation)

Choć RAG to szersza technika, „Strukturalny RAG” jest wyróżniany jako potężna technologia pamięci. Wydobywa gęste, ustrukturyzowane informacje z różnych źródeł (rozmowy, e-maile, obrazy) i używa ich do zwiększenia precyzji, recallu i szybkości odpowiedzi. W przeciwieństwie do klasycznego RAG, który opiera się wyłącznie na semantycznym podobieństwie, Strukturalny RAG wykorzystuje wbudowaną strukturę informacji.

**Przykład Strukturalnego RAG**

Zamiast tylko wyszukiwać dopasowania słów kluczowych, Strukturalny RAG mógłby wyodrębnić szczegóły lotu (cel, data, godzina, linie lotnicze) z e-maila i zapisać je w sposób ustrukturyzowany. To pozwala na precyzyjne zapytania typu „Jaki lot do Paryża zarezerwowałem na wtorek?”

## Implementacja i przechowywanie pamięci

Implementacja pamięci dla agentów AI to systematyczny proces **zarządzania pamięcią**, który obejmuje generowanie, przechowywanie, wyszukiwanie, integrowanie, aktualizowanie, a nawet „zapominanie” (czyli usuwanie) informacji. Wyszukiwanie jest szczególnie ważnym aspektem.

### Specjalistyczne narzędzia pamięci

#### Mem0

Jednym ze sposobów przechowywania i zarządzania pamięcią agenta jest użycie specjalistycznych narzędzi jak Mem0. Mem0 działa jako trwała warstwa pamięci, umożliwiając agentom przywoływanie istotnych interakcji, przechowywanie preferencji użytkownika oraz faktograficznego kontekstu, a także uczenie się na podstawie sukcesów i porażek w czasie. Idea polega na tym, że agenci bezstanowi zmieniają się w stanowych.

Działa poprzez **dwufazowy pipeline pamięci: ekstrakcję i aktualizację**. Najpierw wiadomości dodane do wątku agenta są wysyłane do usługi Mem0, która wykorzystuje Duży Model Językowy (LLM) do podsumowania historii rozmowy i wyodrębnienia nowych wspomnień. Następnie faza aktualizacji prowadzona przez LLM decyduje, czy dodać, zmodyfikować lub usunąć te pamięci, przechowując je w hybrydowej bazie danych, która może obejmować wektorowe, grafowe i klucz-wartość. System wspiera różne typy pamięci i może wykorzystać pamięć grafową do zarządzania relacjami między encjami.

#### Cognee

Innym potężnym podejściem jest użycie **Cognee**, open-source'owej semantycznej pamięci dla agentów AI, która przekształca dane strukturalne i niestrukturalne w zapytalne grafy wiedzy oparte na embeddings. Cognee oferuje **architekturę dual-store**, łączącą wyszukiwanie według podobieństwa wektorów z relacjami grafowymi, pozwalając agentom rozumieć nie tylko co jest podobne, ale jak pojęcia się ze sobą łączą.

Wyróżnia się w **hybrydowym wyszukiwaniu**, które łączy wektorowe podobieństwo, strukturę grafu i rozumowanie LLM — od prostego wyszukiwania fragmentów po świadome grafowo odpowiadanie na pytania. System utrzymuje **żywą pamięć**, która ewoluuje i rośnie, a jednocześnie pozostaje zapytalna jako jeden spójny graf, wspierając zarówno krótkoterminowy kontekst sesji, jak i długoterminową, trwałą pamięć.

Poradnik w notebooku Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstruje budowę tej zunifikowanej warstwy pamięci, z praktycznymi przykładami przetwarzania różnorodnych źródeł danych, wizualizacją grafu wiedzy i zadawaniem pytań z wykorzystaniem różnych strategii wyszukiwania dostosowanych do potrzeb agenta.

### Przechowywanie pamięci z RAG

Poza specjalistycznymi narzędziami pamięci jak mem0 , możesz wykorzystać solidne usługi wyszukiwania jak **Azure AI Search jako backend do przechowywania i wyszukiwania pamięci**, zwłaszcza dla strukturalnego RAG.

To pozwala zakotwiczyć odpowiedzi twojego agenta w własnych danych, zapewniając bardziej istotne i dokładne odpowiedzi. Azure AI Search może być używany do przechowywania użytkownikowo-specyficznych wspomnień podróżniczych, katalogów produktów lub jakiejkolwiek innej wiedzy specyficznej dla domeny.

Azure AI Search wspiera funkcje takie jak **Structured RAG**, które doskonale sprawdzają się w wydobywaniu i wyszukiwaniu gęstych, ustrukturyzowanych informacji z dużych zbiorów danych jak historia rozmów, e-maile czy nawet obrazy. Zapewnia to „nadludzką precyzję i recall” w porównaniu do tradycyjnego dzielenia tekstów i podejść embeddingowych.

## Sprawianie, by Agenci AI się Samo-ulepszali

Powszechny wzorzec dla agentów samo-ulepszających się polega na wprowadzeniu **„agenta wiedzy”**. Ten odrębny agent obserwuje główną rozmowę między użytkownikiem a podstawowym agentem. Jego rola to:

1. **Identyfikacja wartościowej informacji**: Określenie, czy jakaś część rozmowy zasługuje na zapis jako wiedza ogólna lub specyficzna preferencja użytkownika.

2. **Ekstrakcja i podsumowanie**: Wyłuskanie kluczowej nauki lub preferencji z rozmowy.

3. **Przechowanie w bazie wiedzy**: Utrwalenie tych informacji, często w bazie wektorowej, aby można je było później odzyskać.

4. **Rozszerzanie przyszłych zapytań**: Gdy użytkownik inicjuje nowe zapytanie, agent wiedzy wyszukuje istotne przechowywane informacje i dołącza je do promptu użytkownika, zapewniając kluczowy kontekst głównemu agentowi (podobnie do RAG).

### Optymalizacje dla pamięci

• **Zarządzanie opóźnieniami**: Aby nie spowalniać interakcji użytkownika, najpierw można użyć tańszego, szybszego modelu do szybkiego sprawdzenia czy dana informacja jest warta zapisu lub wyszukania, wywołując bardziej złożony proces ekstrakcji/wyszukiwania tylko w razie potrzeby.

• **Utrzymanie bazy wiedzy**: Dla rosnącej bazy wiedzy, rzadziej wykorzystywane informacje można przenosić do „zimnego przechowywania” dla obniżenia kosztów.

## Masz więcej pytań o pamięć agentów?

Dołącz do [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord), aby spotkać się z innymi uczącymi się, uczestniczyć w godzinach konsultacji i uzyskać odpowiedzi na swoje pytania dotyczące Agentów AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Zastrzeżenie**:  
Niniejszy dokument został przetłumaczony przy użyciu usługi tłumaczeń AI [Co-op Translator](https://github.com/Azure/co-op-translator). Chociaż dążymy do dokładności, należy pamiętać, że automatyczne tłumaczenia mogą zawierać błędy lub nieścisłości. Oryginalny dokument w języku źródłowym powinien być uznawany za źródło autorytatywne. W przypadku informacji krytycznych zaleca się skorzystanie z profesjonalnego, ludzkiego tłumaczenia. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z korzystania z tego tłumaczenia.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->