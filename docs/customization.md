# 🎨 **Customization Guide**

This Blueprint is designed to be flexible and easily adaptable to your specific needs. This guide will walk you through some key areas you can customize to make the Blueprint your own.

---


## 📝 **Learn how agents work**

All the code is in the agent files and, except for the OpenAI-based examples, everything runs on your computer.
Take advantage of this!

You can play with different prompts and agent settings in the web application, or you can delve deeper into how an agent is built.
If you look for `pyodide.runPythonAsync` inside the HTML files,
you will find where the python interpreter is used and, more precisely, where (and how!) the agents and the
tools available to them are defined.

## 💡 **Try different models**

If you can run self-hosted models with Ollama, play with different LLMs and learn which one works best for
your use case. For instance, does the thinking mode actually improve the model’s answers? (Hint: you can
add `/think` or `/no_think` to explicitly enable/disable it on qwen3). Or: are all models good at tool
calling? (Hint: [apparently not](https://ollama.com/blog/tool-support), but which one is good enough for you?)
Saying “we use x and y, so we theoretically support any model” is (relatively) easy, but actually running
any model on your hardware is not... So experimenting for *your* use cases is good for you, and sharing
what you learned is good for everyone.

## 🧠 **Try other agentic frameworks**

If you want to get a sense of how many agentic frameworks you can choose from, our [any-agent](https://github.com/mozilla-ai/any-agent) project is a good place to start.
Not all frameworks are fully supported by Pyodide, but some might have features that are useful for you (did anyone say tracing?)

We believe there is value in understanding which framework works best with Wasm agents, and whether it might be worth supporting Wasm versions of the libraries that do not run in browsers yet.

## 🛠️ **Build new tools**

Test your Wasm agents with new tools and learn whether they can make the LLMs they back up more capable
and reliable... Then share those tools, so everyone else can benefit from them!

## 🤝 **Contributing to the Blueprint**

Want to help improve or extend this Blueprint? Check out the **[Contributions Guide](https://github.com/mozilla-ai/wasm-agents-blueprint/blob/main/CONTRIBUTING.md)** to see how you can contribute your ideas, code, or feedback to make this Blueprint even better!
