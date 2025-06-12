# wasm-agents
Testing WASM-powered AI agents

OpenAI agents (require `OPENAI_API_KEY`):

- `hello_wasm_agent.html`: basic example, can be directly opened and ran from disk
- `handoff.html`: handoff example with multiple sub-agents (the Spanish agent replies in rhyme, the English one replies in haikus)
- `tool_calling.html`: tool calling example, has two tools (`count_character_occurrences` to finally answer the question "How many Rs are in strawberry?", and `visit_webpage` to download any webpage).
- `ollama.html`: a simplified version of `hello_wasm_agent` that relies on a local model served with ollama (`gemma:latest` by default). NOTE that you should start ollama as `OLLAMA_ORIGINS=* ollama serve`
to avoid CORS issues

NOTE: the more cross-site HTTP requests you will do, the more CORS-related issues might arise. For this reason, you should use an extension such as CORS Everywhere (and if that still does not work, self-host the html file e.g. by serving it with `python -m http.server`).
