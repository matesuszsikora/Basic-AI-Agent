LLM Agents & RAG Implementation (Lab 4)
Plik lab4.ipynb to rozbudowany projekt demonstrujący tworzenie inteligentnych agentów opartych na dużych modelach językowych (LLM). Projekt wykorzystuje bibliotekę OpenAI Agents SDK w połączeniu z modelem Llama-3.1-8b-instant (poprzez API Groq) i dzieli się na dwie główne części: budowę agenta narzędziowego (Tool-Calling) oraz implementację systemu RAG (Retrieval-Augmented Generation).

Technologie
Język: Python (Jupyter Notebook)

LLM API: Groq API (model Llama-3.1) / OpenAI Agents SDK

Baza wektorowa: ChromaDB

Zewnętrzne API: WeatherAPI, Wikipedia API





Część 1: Agent z wykorzystaniem narzędzi (Tool Calling)
W tej sekcji zbudowano wielozadaniowego agenta, który potrafi korzystać z zewnętrznych funkcji. Główne wyzwania i zaimplementowane rozwiązania obejmują:

Kalkulator potęg: Stworzenie narzędzia matematycznego z zaawansowanym parsowaniem wejścia (obsługa różnych formatów zapisu: 0.123, 0,123, notacja naukowa 1.23e-1, ułamki 1/2).

Złożona logika: Nauczenie agenta przestrzegania kolejności działań przy wyrażeniach zagnieżdżonych (np. 4^(16^(1/2))) oraz zabezpieczenie przed błędami matematycznymi (dzielenie przez 0).

Integracja API: Dodanie narzędzia sprawdzającego aktualną pogodę na podstawie WeatherAPI.

Multi-tasking: Skonfigurowanie agenta tak, aby potrafił obsłużyć kilka niezależnych zapytań w jednym prompcie (np. policzenie potęgi i podanie pogody jednocześnie).

Guardrails (Bezpieczeństwo i ograniczenia): * Agent odmawia odpowiedzi na tematy niezwiązane z matematyką i pogodą.

Wprowadzono geolokalizacyjny "twardy limit" – agent podaje pogodę wyłącznie dla miast znajdujących się w Polsce.





Część 2: Agent RAG (Retrieval-Augmented Generation)
W tej sekcji zaimplementowano własny system RAG, który zasila model zewnętrzną bazą wiedzy:

Wektoryzacja danych: Automatyczne pobranie artykułu o Układzie Słonecznym z Wikipedii, podzielenie go na 500-znakowe fragmenty (chunks) i zapisanie w wektorowej bazie danych ChromaDB.

Wyszukiwarka semantyczna: Zbudowanie narzędzia query, które odpytuje bazę Chroma i zwraca 3 najbardziej podobne fragmenty do zapytania użytkownika.

Kontrola halucynacji (Test Melmac): Eksperymentalne wstrzyknięcie fałszywej informacji do bazy wektorowej ("W 2025 odkryto planetę Melmac..."). Odpowiednia modyfikacja instrukcji systemowych (System Prompt) zmusiła agenta do zignorowania swojej bazowej wiedzy i opierania się wyłącznie na dostarczonym, zmanipulowanym kontekście.





Jak uruchomić?
Aby poprawnie uruchomić notatnik, musisz zdefiniować w swoim środowisku dwa klucze API:

GROQ_API_KEY - do komunikacji z darmowym modelem Llama poprzez platformę Groq.

WEATHER_API_KEY - wygenerowany klucz ze strony WeatherAPI do pobierania aktualnych danych pogodowych.
