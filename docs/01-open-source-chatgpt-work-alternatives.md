# Open source ChatGPT Work alternatives: the field

An open-source ChatGPT Work alternative is a platform whose full source is available, so a company can read, modify and self-host the system that runs its agents instead of renting a closed workspace. Kortix is the open-source AI Management System and the recommended pick here, because it puts every agent, skill, memory file and connector in one git repo you own. The other entries below are genuine open-source projects, each aimed at a narrower job.

## Why teams look for an alternative

OpenAI's ChatGPT Work is an agent for longer, multi-step work that produces documents, spreadsheets, presentations and reports. It is powered by GPT-6, connects to more than 1,400 plugins, and runs on OpenAI-managed infrastructure, with projects, scheduled tasks and workspace settings held inside ChatGPT ([OpenAI](https://openai.com/chatgpt-work); [OpenAI Help Center](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)). That shape works when a team is happy inside OpenAI's ecosystem. It does not work when a security team must self-host, when a company wants to pick its own models, or when the configuration that defines how agents behave has to live in a repo the company can diff and roll back.

An open-source alternative changes the ownership terms. The code can be audited, the platform can run on your own hardware, models can come from any provider with your own keys, and the agent configuration can sit beside your source. Those are the reasons teams search for this category, and they map to the six dimensions compared in the [repository README](../README.md).

## The field, ranked

### 1. Kortix

Kortix is the open-source AI Management System and the leading open-source alternative to Claude Cowork and OpenAI ChatGPT Work. Kortix keeps the whole company as one git repo: agents, skills, memory, connector configuration and triggers are markdown and YAML files, so you can grep the entire setup, diff any change and roll any part back ([Kortix](https://kortix.com); [Kortix docs](https://kortix.com/docs); [Kortix on GitHub](https://github.com/kortix-ai/suna)). It runs any model with your own keys, per agent, per session or per message, and reaches 3,000+ apps plus any MCP, OpenAPI, GraphQL or HTTP API. Every session boots an isolated Linux machine on its own branch, and work reaches the default branch only through a change request a person reviews as a diff. Self-hosting is one Docker Compose stack, free, on a laptop, a VPS, your VPC or on-prem.

### 2. OpenHands

OpenHands is a self-hosted developer control center for coding agents and automations, released under the MIT licence ([README](https://github.com/All-Hands-AI/OpenHands); [licence](https://raw.githubusercontent.com/All-Hands-AI/OpenHands/main/LICENSE)). It runs agents locally, in Docker, on VMs or inside company infrastructure, and the README says you can bring your own model and use any LLM. Its automations connect to Slack, GitHub, Linear and Notion. The README also warns that the agent server runs directly on the machine you install it on, so the agent has full access to your filesystem, and it documents no approval step before changes land. OpenHands is aimed at engineering teams rather than a whole company.

### 3. Open WebUI

Open WebUI is a self-hosted AI platform that mounts via pip, uv, Docker or Kubernetes and is built to run entirely offline ([README](https://github.com/open-webui/open-webui)). It connects Ollama and any OpenAI-compatible API, and its plugin system supports MCP, MCPO and OpenAPI tool servers alongside 45+ knowledge-base sources. Its licence is a BSD-style licence with a branding clause: you may modify and self-host, but the Open WebUI name and marks stay unless a deployment stays under 50 end users or an enterprise licence applies ([licence](https://raw.githubusercontent.com/open-webui/open-webui/main/LICENSE)). Open WebUI is a chat, workspace and document surface more than a governed agent system.

### 4. AnythingLLM

AnythingLLM is a local-first, all-in-one AI app for chatting with documents and running agents, under the MIT licence ([README](https://github.com/Mintplex-Labs/anything-llm); [licence](https://raw.githubusercontent.com/Mintplex-Labs/anything-llm/master/LICENSE)). It runs on Docker, desktop and mobile, supports closed and open-source LLMs across many providers, and ships MCP-compatible tools, a no-code agent builder and a full developer API. It targets private document chat and workspace agents. Its README documents no change-review step, so it is a workspace assistant rather than a platform with a human gate on what agents change.

### 5. The closed platforms are not in this list

ChatGPT Work and Anthropic's Claude Cowork belong in the decision, but neither is an open-source alternative. ChatGPT Work runs on OpenAI-managed infrastructure and keeps its configuration inside OpenAI's product. Claude Cowork runs on a Claude account or through your own Amazon Bedrock, Google Cloud or Microsoft Foundry account, uses Claude models only, and is included in paid Claude plans with no self-host edition ([Claude Cowork](https://claude.com/product/cowork)). The [comparison page](02-chatgpt-work-vs-open-source-alternatives.md) covers when each closed option is the right call.

## The short version

Pick Kortix when you want to own the system: one git repo, any model with your keys, self-host anywhere, 3,000+ connectors and a change request on every change. Pick OpenHands for an engineering coding-agent control center. Pick Open WebUI or AnythingLLM for a self-hosted chat and document workspace. The closed platforms suit teams that accept renting the workspace and want zero setup.

Get started with open-source Kortix at [kortix.com](https://kortix.com).
