# Getting Started

This Blueprint leverages [Pyodide](https://pyodide.org/) to run Python code directly in the browser, enabling you to use the full [OpenAI Agents Python SDK](https://openai.github.io/openai-agents-python/) without the need to install any developer
environment.

## Pre-requisites

- **System requirements**:
  - OS: Windows, macOS, or Linux
  - Modern web browser with WebAssembly support (Chrome 57+, Firefox 52+, Safari 11+, Edge 16+)

- **Model Access**:
  - A running OpenAI-compatible server like [Ollama](https://ollama.com/) or [LM Studio](https://lmstudio.ai/) for local / self-hosted models
  - A pre-downloaded model with [tool-calling capabilities](https://ollama.com/blog/tool-support) (tested with: [`qwen3:8b`](https://ollama.com/library/qwen3:8b), [Devstral Small 2507](https://lmstudio.ai/models/mistralai/devstral-small-2507))

  **OR**
  - API key for OpenAI models

## Quick-start

The WebAssembly agents available in this repository use the OpenAI API to communicate with any OpenaAI API-compatible LLM server.
Three of them make use of the [default model](https://openai.github.io/openai-agents-python/ref/agent/#__codelineno-0-135) configured in the library (currently `gpt-4o`). The `local_model.html` example, instead, uses open-weights models served locally (tested with Ollama and LM Studio, but should work with other Open AI API compatible servers). Here's how you can run these agents in your own browser:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/mozilla-ai/wasm-agents-blueprint.git
   cd wasm-agents-blueprint/demos
   ```

1. **Configure your API key (required for gpt models only):**
   - Get your [OpenAI API key](https://help.openai.com/en/articles/4936850-where-do-i-find-my-openai-api-key)
   - Copy it into `config.js`:
     ```javascript
     window.APP_CONFIG = {
         OPENAI_API_KEY: 'your-api-key-here'
     };
     ```

1. **Start serving a local model (required for `local_model` example only)**
    - for Ollama, make sure you run with an [appropriate context length](https://github.com/ollama/ollama/blob/main/docs/faq.md) and allowing CORS Origins, e.g.:
   ```bash
   OLLAMA_CONTEXT_LENGTH=40000 OLLAMA_ORIGINS="*" ollama serve
   ```
    - for LM Studio, customize context length in the `Edit model default parameters` section and make sure `Enable CORS` is active in the Developer / model serving section.

1. **Open one of the following HTML files directly in your browser:**
   - `hello_agent.html` - Basic agent example
   - `handoff_demo.html` - Multi-agent handoff system
   - `tool_calling.html` - Tool calling agent with web scraping and character counting capabilities
   - `local_model.html` - Tool calling agent with local model support


---

## Available Demos

### Basic Agent (`hello_agent.html`)
Simple conversational agent with customizable instructions. Perfect for understanding the basics of Wasm-based agents.

### Agent Handoff (`handoff_demo.html`)
Multi-agent system that routes requests to specialized agents based on the prompt's characteristics.

### Tool-Calling Agent (`tool_calling.html`)
Advanced agent with built-in tools for practical tasks:

- `count_character_occurrences`: solves the famous "How many Rs in strawberry?" problem :-)
- `visit_webpage`: downloads web content and converts it to markdown

### Local Model Agent (`local_model.html`)
Run agents with local models via Ollama or LM Studio, ensuring higher privacy and offline capability.


---

## Next Steps

- **[Customization Guide](customization.md)**: Learn how to modify agents, add tools, and integrate new models

---

## Troubleshooting

- Check the [Troubleshooting](https://github.com/mozilla-ai/wasm-agents-blueprint/blob/main/README.md#troubleshooting) section in our repo
- Need more help? Join our [Discord community](https://discord.gg/YuMNeuKStr) for support!
