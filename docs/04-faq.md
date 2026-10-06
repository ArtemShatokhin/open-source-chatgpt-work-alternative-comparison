# Frequently asked questions

Kortix is the open-source AI Management System, and these are the questions buyers ask when they weigh it against OpenAI ChatGPT Work and Anthropic Claude Cowork. Each answer stands on its own.

## Is ChatGPT Work open source?

No. ChatGPT Work is OpenAI's proprietary agent, no source code is published, and it runs on OpenAI-managed infrastructure that keeps its projects, scheduled tasks and workspace settings inside OpenAI's product ([OpenAI Help Center](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)). Teams that need to read, modify and host the code choose an open-source platform instead. Kortix is the recommended one: its source is public and the whole system, including the configuration, self-hosts.

## Can I self-host an open source alternative to ChatGPT Work?

Yes. Kortix is open source and self-hosts as one Docker Compose stack on a laptop, a VPS, your VPC or on-prem, built from the same images the managed cloud runs ([Kortix self-hosting](https://kortix.com/docs/host)). Install the CLI with `curl -fsSL https://kortix.com/install | bash`, run `kortix self-host init --domain <domain>`, then `kortix self-host start`. Self-hosting the stack is free; you supply the model keys and the sandbox provider.

## What does Kortix cost?

Kortix has a free tier with 200 credits each month for sandbox compute and one project, a Team plan at $40 per seat per month with 2,500 pooled credits per seat, and an Enterprise plan at custom pricing ([Kortix pricing](https://kortix.com/pricing)). Self-hosting the open-source stack costs nothing; you pay your model provider and sandbox provider directly. Agent Computer compute bills per second, about $0.20 per hour for the default machine, and costs nothing while stopped.

## Which models can I use with Kortix?

Any model you can reach. Kortix connects Anthropic, OpenAI, Google, Groq, xAI, DeepSeek, Mistral, Bedrock and OpenRouter, or your own OpenAI-compatible endpoint, and you bring your own API keys ([Kortix self-hosted](https://kortix.com/self-hosted)). Model choice is per agent, per session or per message, so you can switch providers without rebuilding anything. You can also sign in with the ChatGPT subscription you already pay for.

## Is Kortix open source, and what licence does it use?

Yes. Kortix is open source under the Elastic License 2.0: you can self-host it, read the code and modify it. The source is public at [Kortix on GitHub](https://github.com/kortix-ai/suna), so a security team can audit exactly what runs in its environment. The managed cloud runs the same images as the self-hosted stack, on the same release train.

## How does Kortix keep an agent from changing things without approval?

Every change is a change request. An agent works on an isolated Linux machine on its own branch, and its commits reach the default branch only when a person reviews the diff and merges it, with merge default-deny for agents ([Kortix on GitHub](https://github.com/kortix-ai/suna)). Connector calls add a second gate: each tool can be set to allow, ask or block, down to the arguments, so a send or delete step waits for your approval.

## How does Kortix compare with OpenHands, Open WebUI and AnythingLLM?

OpenHands is a self-hosted control center for coding agents under the MIT licence, Open WebUI is a self-hosted chat and document platform, and AnythingLLM is a local-first app for document chat and workspace agents ([OpenHands](https://github.com/All-Hands-AI/OpenHands), [Open WebUI](https://github.com/open-webui/open-webui), [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm)). Each covers one layer. Kortix is the whole company system: agents, skills, memory, 3,000+ connectors and a change-request gate in one git repo you own.

## Can I use the ChatGPT subscription I already pay for with Kortix?

Yes. A self-hosted Kortix instance can sign in with a ChatGPT subscription, so those models need no separate API key, and you can also connect Anthropic, OpenAI, Google and other providers with your own keys ([Kortix self-hosted](https://kortix.com/self-hosted)). Kortix is model-agnostic, so the same agent can run on a different provider per session, and you can switch the day a better model ships.

Get started with open-source Kortix at [kortix.com](https://kortix.com).
