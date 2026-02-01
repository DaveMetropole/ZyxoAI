# ZyxoAI — Prototype (No-key Ask + Math)

ZyxoAI is a friendly prototype AI assistant. This branch adds free, no-key features:
- Ask (Wikipedia): ask subject questions (history, science, English, etc.) — answers are pulled from Wikipedia summaries (no API key required).
- Math evaluator: evaluate algebraic/arithmetic expressions in the browser using math.js (no API key required).
- File edit (basic/no-key fallback): simple heuristic edits (shorten, simplify) without an LLM — useful for quick experiments.
- Poster/Image generation and advanced LLM edits are still supported conceptually, but require an external API provider (placeholders remain in index.html).

How to try (quick)
1. Clone the repo:
   - `git clone https://github.com/DaveMetropole/ZyxoAI.git`
   - `cd ZyxoAI`
2. Open a local server (do not use file:// for fetch to work properly):
   - `python3 -m http.server 8000`
   - Open `http://localhost:8000/index.html`
3. Use the UI:
   - Choose "Ask (Wikipedia)" and enter a subject question (e.g., "Photosynthesis", "World War I causes", "Explain Newton's laws").
   - Choose "Math" and enter expressions like `2+2`, `integrate(x^2, x)` — math.js supports many operations.
   - For editing, upload a text file and give a simple instruction (the edit is a naive fallback without an LLM).

Why this is "no-key" and free
- Wikipedia's APIs are public and CORS-friendly (with origin=*), so the browser can fetch summaries and page content directly — this yields short, sourced answers without keys.
- Math evaluation uses an in-browser library (math.js), so it does not contact any external service.

Limitations and important notes
- Coverage & depth: Wikipedia summaries are good for many topics but may be incomplete or not tailored to a grade level — ask follow-ups like "Explain it for a 12-year-old" to get simpler wording.
- Bias & accuracy: Wikipedia is generally high-quality but can contain errors. Always cross-check important facts.
- CORS & other websites: Fetching arbitrary sites from the browser is often blocked by CORS. The prototype includes an optional public proxy (AllOrigins) but public proxies are rate-limited and not suitable for production.
- No LLM behind editing: The "Edit" feature in the no-key mode is a naive heuristic. For robust editing or rewriting you still need an LLM provider (OpenAI, Anthropic, etc.).
- Security: Never store production API keys in the browser. Use a server-side proxy for production.

Next steps (optional)
- I can adapt index.html to call a specific free provider (if you want to use any other public, no-key data sources) — say which provider.
- I can add a tiny serverless proxy so you can fetch arbitrary web pages server-side (avoids CORS) — this requires deploying a small function (example provided).
- If you want, I can push these changes to the repository for you (I need repo write permission). Reply "Please push" if you've authorized me.

License
This project is MIT-licensed. See LICENSE if you add it.
