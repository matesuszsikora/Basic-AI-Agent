## LLM Agents & RAG Implementation (AI Lab)

Zaawansowany projekt eksplorujący możliwości agentów AI oraz systemów RAG (Retrieval-Augmented Generation).

### Technologie
* **Model:** Llama-3.1-8b-instant (via Groq API)
* **Framework:** Open AI Agents SDK
* **Baza Wektorowa:** ChromaDB
* **Biblioteki:** Wikipedia API, Requests, Math.js logic

### Kluczowe Funkcjonalności
* **Tool Calling:** Agent potrafiący inteligentnie dobierać narzędzia do rozwiązywania problemów (kalkulator potęg z zaawansowanym parsowaniem ułamków i notacji naukowej).
* **System RAG:** Własna implementacja bazy wiedzy opartej na wektorach. Agent przeszukuje zindeksowaną treść Wikipedii, aby odpowiadać na pytania o Układzie Słonecznym.
* **Guardrails & Safety:** * Filtrowanie zapytań – agent odmawia odpowiedzi na tematy inne niż matematyka i pogoda.
    * Ograniczenia geolokalizacyjne – narzędzie pogodowe działa wyłącznie dla miejscowości w Polsce.
* **Multi-tasking:** Zdolność agenta do równoległego wykonywania wielu zadań (np. obliczenia i sprawdzenie pogody) w jednym przebiegu.

