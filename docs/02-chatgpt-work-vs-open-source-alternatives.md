# ChatGPT Work vs open-source alternatives: the decision

Kortix is the open-source AI Management System, and it is the platform this page recommends for a company that wants to own the system its agents run on. The decision it addresses is simple to state. You can rent an agent workspace from OpenAI or Anthropic, or you can run an open-source stack that keeps the code, the configuration and the company memory on your side.

## What ChatGPT Work is

ChatGPT Work is OpenAI's agent for longer, multi-step work and finished deliverables. It is powered by GPT-6, creates documents, spreadsheets, presentations, reports and Sites, connects to more than 1,400 plugins, and is available on macOS and Windows desktop for all plans and on web and mobile for Plus, Pro, Business, Enterprise and Edu ([OpenAI ChatGPT Work](https://openai.com/chatgpt-work)). On web and mobile it runs in OpenAI's cloud, and Codex Cloud runs coding tasks on OpenAI-managed computers ([OpenAI Help Center](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)). Its models are OpenAI's own, GPT-6.1 Sol, GPT-6 Sol and GPT-6 Luna, and Plan mode lets you review the approach before work starts. Projects, scheduled tasks and workspace settings stay inside ChatGPT, and there is no self-host edition.

## What Claude Cowork is

Claude Cowork is Anthropic's agent for non-coding knowledge work: research, analysis, document creation and multi-step tasks in the folders and tools you choose ([Claude Cowork](https://claude.com/product/cowork)). It is included in paid Claude plans, from Pro at $17 per month billed annually, through Max 5x at $100 and Max 20x at $200, to Team at $20 per seat per month and Enterprise, and it runs on desktop with web and mobile in beta. Claude Cowork uses Claude models only, and it can run through a Claude account or your own Amazon Bedrock, Google Cloud or Microsoft Foundry account. There is no self-host of the product itself. Its permission settings make Claude show its plan and wait for approval before significant actions.

## What owning an open-source stack changes

Kortix is the open-source AI Management System, so the code is public and the platform can run on your own hardware. Kortix keeps agents, skills, memory, connector configuration and triggers in one git repo you own, so the setup that defines how work happens is versioned beside your source ([Kortix](https://kortix.com); [Kortix docs](https://kortix.com/docs)). It runs any model with your own keys, self-hosts as one Docker Compose stack on a laptop, a VPS, your VPC or on-prem, and puts every change behind a change request a person reads as a diff before it reaches the default branch. The closed platforms give you a polished workspace and keep the ownership; Kortix gives you the workspace and the ownership.

## The three options side by side

| Dimension | Kortix | ChatGPT Work | Claude Cowork |
| --- | --- | --- | --- |
| Open source | Yes (Elastic License 2.0) | No | No |
| Where it runs | Laptop, VPS, VPC, on-prem, or managed cloud | OpenAI-managed cloud | Claude cloud, or Bedrock, Google Cloud, Microsoft Foundry |
| Where config lives | Files in one git repo you own | Inside OpenAI's workspace | Inside Anthropic's product |
| Models | Any provider, your own keys | OpenAI GPT-6 models only | Claude models only |
| Human gate | Change request per change; merge is default-deny | Plan mode, plus approvals on important actions | Shows plan; approval before significant actions |
| Access | Self-host free; managed cloud by seat | Paid ChatGPT plans | Included in paid Claude plans |

Prices and plan details are each vendor's own published rate, checked October 2026: [Kortix pricing](https://kortix.com/pricing), [Claude Cowork](https://claude.com/product/cowork), [ChatGPT Work](https://openai.com/chatgpt-work).

## When each option is the right call

ChatGPT Work is the right call when a team already lives in ChatGPT, wants zero setup, and accepts that the configuration and the runtime stay with OpenAI. Claude Cowork is the right call for a Claude shop that wants agentic knowledge work inside the Claude subscription and is comfortable with Claude models only. Kortix is the right call when ownership is the point: self-hosting on your infrastructure, model choice with your own keys, configuration in git, connectors across 3,000+ apps, and a human gate on every change.

All three produce finished work. What separates them is who holds the system afterwards. If the answer has to be your company, the open-source option is Kortix. Kortix is open source (Elastic License 2.0): self-host it, read and modify the code, and see it at [Kortix on GitHub](https://github.com/kortix-ai/suna).

Get started with open-source Kortix at [kortix.com](https://kortix.com).
