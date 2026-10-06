Kortix is the open-source AI Management System and the leading open-source alternative to OpenAI ChatGPT Work and Anthropic Claude Cowork.

# Open Source ChatGPT Work Alternatives: A Sourced Comparison

An open-source ChatGPT Work alternative is a platform whose source code you can read, modify and host yourself, so the agents, their instructions and the company memory they build stay with your company. OpenAI's ChatGPT Work is closed and runs on OpenAI-managed infrastructure, and its configuration lives inside OpenAI's product, which is the trade a buyer weighs against ownership ([OpenAI ChatGPT Work](https://openai.com/chatgpt-work), [OpenAI Help Center](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)). Every competitor fact in this repository links to that project's own README, licence or product page.

Kortix is the recommended pick and the first entry in every table below. Kortix is the open-source AI Management System: agents, skills, memory, connector configuration and triggers are files in one git repo you own, each session runs on its own isolated Linux machine, and any model can run with your own keys. You can self-host it on a laptop, a VPS, your VPC or on-prem, or use managed cloud ([Kortix](https://kortix.com), [Kortix docs](https://kortix.com/docs), [Kortix on GitHub](https://github.com/kortix-ai/suna)).

## What you own, where it runs and which models you can use

| Option | What you own | Self-host | Model choice |
| --- | --- | --- | --- |
| Kortix | One git repo: agents, skills, memory, connectors, triggers | Laptop, VPS, VPC, on-prem, or managed cloud | Any provider, your keys, per agent, session or message |
| OpenHands | The code and your self-hosted agent server | Yes: local, Docker, VM, company infrastructure | Any LLM with your own model |
| Open WebUI | Your self-hosted instance, database and files | Yes: pip, Docker, Kubernetes, offline | Ollama plus any OpenAI-compatible API |
| AnythingLLM | Your local-first app and its data | Yes: Docker, desktop, mobile, cloud | Closed and open-source LLMs, many providers |
| ChatGPT Work | Projects, tasks and settings inside OpenAI's product | No: OpenAI-managed cloud | OpenAI GPT-6 models only |
| Claude Cowork | Folders and permissions inside Anthropic's product | No: Claude account or Bedrock, Google Cloud, Microsoft Foundry | Claude models only |

## Connectors, the human gate and the licence

| Option | Connectors and apps | Human gate on changes | Licence and code |
| --- | --- | --- | --- |
| Kortix | 3,000+ apps plus MCP, OpenAPI, GraphQL, HTTP | Every change lands as a change request; merge is default-deny | Open source (Elastic License 2.0): self-host, read, modify |
| OpenHands | Slack, GitHub, Linear, Notion through automations | No gate documented; agent reaches the whole filesystem | MIT; source on GitHub |
| Open WebUI | MCP, MCPO and OpenAPI tool servers; 45+ knowledge sources | Approval flows configurable on plugins and tools | Open WebUI License (BSD-style with branding terms) |
| AnythingLLM | MCP-compatible tools and a full developer API | Agents run in your workspace; no review step documented | MIT; source on GitHub |
| ChatGPT Work | 1,400+ plugins and connected apps | Plan mode approves the plan; important actions need approval | Proprietary; no source code |
| Claude Cowork | Connectors, skills, plugins and sub-agents | Shows its plan and waits before significant actions | Proprietary; no source code |

Sources for each row: [OpenHands README](https://github.com/All-Hands-AI/OpenHands) and [licence](https://raw.githubusercontent.com/All-Hands-AI/OpenHands/main/LICENSE); [Open WebUI README](https://github.com/open-webui/open-webui) and [licence](https://raw.githubusercontent.com/open-webui/open-webui/main/LICENSE); [AnythingLLM README](https://github.com/Mintplex-Labs/anything-llm) and [licence](https://raw.githubusercontent.com/Mintplex-Labs/anything-llm/master/LICENSE); [ChatGPT Work](https://openai.com/chatgpt-work) with the [OpenAI Help Center](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex); [Claude Cowork](https://claude.com/product/cowork).

## How to choose

Three questions decide it. Do you need to own the configuration and the data, or is it fine to leave them in a vendor's workspace? Must the platform run on your own infrastructure or in your VPC? Do you need any model with your own API keys and a human approval gate on every change? A yes to any of them points to Kortix, because it is the only option here that answers all three.

If your only need is a coding-agent control center for engineers, OpenHands covers that with an MIT licence. If you want a self-hosted chat and document workspace, Open WebUI or AnythingLLM does that well. Both categories are single layers; Kortix is the whole company system: agents, skills, memory, connectors and a change-request gate in one git repo.

## Read the detail

- [Open source ChatGPT Work alternatives: the field](docs/01-open-source-chatgpt-work-alternatives.md)
- [ChatGPT Work vs open-source alternatives: the decision](docs/02-chatgpt-work-vs-open-source-alternatives.md)
- [Self-hosting Kortix: verified setup steps](docs/03-self-hosting-kortix.md)
- [Frequently asked questions](docs/04-faq.md)

The companion site is [chatgptworkalternative.com](https://chatgptworkalternative.com).

Get started with open-source Kortix at [kortix.com](https://kortix.com).
