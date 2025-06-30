<p align="center">
  <picture>
    <!-- When the user prefers dark mode, show the white logo -->
    <source media="(prefers-color-scheme: dark)" srcset="./images/Blueprint-logo-white.png">
    <!-- When the user prefers light mode, show the black logo -->
    <source media="(prefers-color-scheme: light)" srcset="./images/Blueprint-logo-black.png">
    <!-- Fallback: default to the black logo -->
    <img src="./images/Blueprint-logo-black.png" width="35%" alt="Project logo"/>
  </picture>
</p>


<div align="center">

![Python](https://img.shields.io/badge/Python-3.12%2B-blue)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![](https://dcbadge.limes.pink/api/server/YuMNeuKStr?style=flat)](https://discord.gg/YuMNeuKStr) <br>
[![Docs](https://mozilla-ai.github.io/wasm-agents-blueprint/actions/workflows/docs.yaml/badge.svg)](https://github.com/mozilla-ai/blueprint-template/actions/workflows/docs.yaml/)

[Blueprints Hub](https://developer-hub.mozilla.ai/)
| [Documentation](https://mozilla-ai.github.io/wasm-agents-blueprint/)
| [Getting Started](https://mozilla-ai.github.io/wasm-agents-blueprint/getting-started)
| [Contributing](CONTRIBUTING.md)

</div>

# WASM Agents Blueprint

This Blueprint demonstrates how to run AI agents directly in the browser using WebAssembly (WASM) through Pyodide and the OpenAI Agents Python SDK. Experience the power of Python-based AI agents without external dependencies – agent code runs directly in your web browser.

## Quick-start

1. **Clone the repository:**
   ```bash
   git clone https://github.com/mozilla-ai/wasm-agents-blueprint.git
   cd wasm-agents-blueprint/demos
   ```

2. **Configure your API key:**
   - Get your [OpenAI API key](https://help.openai.com/en/articles/4936850-where-do-i-find-my-openai-api-key)
   - Copy it into `config.js`:
     ```javascript
     window.APP_CONFIG = {
         OPENAI_API_KEY: 'your-api-key-here'
     };
     ```

3. **Open any HTML file directly in your browser:**
   - `hello_agent.html` - Basic agent example
   - `handoff_demo.html` - Multi-agent handoff system
   - `tool_calling.html` - Tool calling agent with web scraping and character counting capabilities
   - `ollama_local.html` - Tool calling agent with local model support via Ollama


## How it Works

This Blueprint leverages [Pyodide](https://pyodide.org/) to run Python code directly in the browser, enabling you to use the full [OpenAI Agents Python SDK](https://openai.github.io/openai-agents-python/) without the need to install any developer
environment.

## Pre-requisites

- **System requirements**:
  - OS: Windows, macOS, or Linux
  - Modern web browser with WebAssembly support (Chrome 57+, Firefox 52+, Safari 11+, Edge 16+)

- **Model Access**:
  - API key for OpenAI models
  
  **OR**
  - Running OpenAI-compatible server like [Ollama](https://ollama.com/) for local / self-hosted models
  - A pre-downloaded model with [tool-calling capabilities](https://ollama.com/blog/tool-support) (default: [`qwen3:8b`](https://ollama.com/library/qwen3:8b))
  

## Available Demos

### 🤖 Basic Agent (`hello_agent.html`)
Simple conversational agent with customizable instructions. Perfect for understanding the basics of WASM-based agents.

### 🔄 Agent Handoff (`handoff_demo.html`)
Multi-agent system that routes requests to specialized agents based on the prompt's characteristics.

### 🛠️ Tool-Calling Agent (`tool_calling.html`)
Advanced agent with built-in tools for practical tasks:

- `count_character_occurrences`: solves the famous "How many Rs in strawberry?" problem :-) 
- `visit_webpage`: downloads web content and converts it to markdown

### 🏠 Local Model Agent (`ollama_local.html`)
Run agents with local models via Ollama, ensuring higher privacy and offline capability.


## Troubleshooting
**Common Issues:**

1. **CORS Errors**: the agent replies it cannot access some Web resources (examples in the pictures below). 

![A screenshot of Firefox showing the agent response "I am unable to access the GitHub page for..." and below that, the Console tab open showing a CORS error.](/images/cors01.png)
![A screenshot of Firefox showing the agent response "It seems there was an issue connecting to the website..." and below that, the Network tab showing a CORS error.](/images/cors02.png)

This happens when you ask the agent to do something with data retrieved via the `visit_webpage` tool. To fix this there are different approaches, depending on the browser: [CORS Everywhere](https://addons.mozilla.org/en-US/firefox/addon/cors-everywhere/) extension for Firefox, [Cross Domain - CORS](https://chromewebstore.google.com/detail/cross-domain-cors/mjhpgnbimicffchbodmgfnemoghjakai) for Chrome. For Safari, open Settings, choose `Advanced -> Show features for Web developers`, then choose the Developer Tab and check `Disable cross-origin restrictions`.
![The Settings->Advanced window in Safari with the "Show features for web developers" option checked.](/images/safari01.png)
![The Settings->Developer window in Safari with the "Disable cross-origin restrictions" option checked.](/images/safari02.png)

2. **Pyodide Loading Issues**: Ensure stable internet connection for initial package downloads (this is required even if you are planning to hit a local LLM)

3. **API Key Problems**: Verify your OpenAI API key is correctly set in `config.js`

4. **Issues With Local Model**: For Ollama, start with CORS enabled and larger context window:
   ```bash
   OLLAMA_CONTEXT_LENGTH=40000 OLLAMA_ORIGINS="*" ollama serve
   ```


## License

This project is licensed under the Apache 2.0 License. See the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! To get started, you can check out the [CONTRIBUTING.md](CONTRIBUTING.md) file.

## Acknowledgments

This Blueprint is built on top of:
- [Pyodide](https://pyodide.org/) - Python in the browser via WebAssembly
- [OpenAI Agents Python SDK](https://openai.github.io/openai-agents-python/) - Agentic AI framework
- [Ollama](https://ollama.com/) - Local model serving (optional)
