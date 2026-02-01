# ZyxoAI — Prototype

ZyxoAI is a friendly, prototype AI assistant that can generate posters/images and edit text files via LLM/image API calls. This repository contains a minimal, low-code, single-file web prototype (index.html) so you can try ZyxoAI locally without setting up a server.

Important: This is a prototype. For simplicity the page runs API calls directly from your browser, which exposes your API key to the client. Do NOT use a secret key with any sensitive data. Prefer running a small server or serverless function for production and store keys in server-side secrets.

Files in this repo
- `index.html` — Single-file low-code prototype UI. Enter your API key at the top, then use the prompt box to ask ZyxoAI to generate posters/images or to edit uploaded text files.

Quick start
1. Clone the repository and open `index.html` in a modern browser (or use GitHub Pages).
2. Click "Set API Key" and paste your API key for the provider you intend to use (the page is provider-agnostic; see notes below).
3. Enter a prompt and choose an action:
   - Generate Poster / Image — the page will call the configured image endpoint and show the image result.
   - Edit File — upload a text file and a short instruction (e.g. "shorten this to 200 words"). The example will call a chat/edit endpoint and display the edited text.

Provider notes
- The prototype includes placeholder example code for calling a typical REST LLM/image API (e.g. OpenAI, Stability). You must update the endpoint URLs and request format to match your provider's API.
- Calling APIs directly from the browser is insecure because the key is exposed to anyone who can view network requests. For production host a small backend that proxies requests and keeps the key secret.

Security and next steps
- Replace direct browser calls with a server-side proxy (serverless function or small express app) that stores the API key in environment secrets.
- Add authentication, rate-limiting, and input sanitization.
- Add proper error handling, logging, and monitoring.

License
This project is licensed under the MIT License. See LICENSE for details.
