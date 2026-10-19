# ChatGPT Work vs Claude Cowork: what each keeps, and the open-source option

ChatGPT Work and Claude Cowork are both modes inside a chat subscription now. The useful comparison is what each vendor lets a team keep when the subscription changes. Kortix is the open-source AI Operating System, and it keeps the whole setup in a repository the team owns.

## What each product is now

ChatGPT Work is OpenAI's agent for longer assignments inside ChatGPT. It launched on 9 July 2026. The agent takes action across connected apps and files, then returns finished documents, spreadsheets, slides and sites ([OpenAI's launch post](https://openai.com/index/chatgpt-for-your-most-ambitious-work)). GPT-6 Astra has run in Work and Codex since 9 September 2026, on every plan from Plus up ([ChatGPT Work and Codex](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)). Projects, tasks and instructions sit inside the ChatGPT workspace. OpenAI offers no self-hosted edition.

Claude Cowork was Anthropic's separate agent for non-coding work. That ended on 16 September 2026, when Anthropic merged Cowork and chat into one Claude conversation ([release notes](https://support.claude.com/en/articles/12138966-release-notes)). There is no mode to choose. An account on the new experience cannot switch back to separate Chat and Cowork options ([Anthropic's merge note](https://support.claude.com/en/articles/16761823-claude-cowork-and-chat-are-one-claude)). It runs on Anthropic's models, in Anthropic's cloud or a customer's Amazon Bedrock, Google Cloud or Microsoft Foundry account. All of it draws on the same plan usage ([Claude Cowork](https://claude.com/product/cowork)).

## What each costs a team

| Option | Published price | Smallest team bill | What the bill buys |
| --- | --- | --- | --- |
| Kortix, self-hosted | $0 platform | $0 platform | Model provider bill only |
| Kortix Cloud, paid | $50/month | $50/month | 5,000 credits, members free |
| ChatGPT Business Standard, annual | $20 per seat/month | $40/month | Two seats, usage metered |
| ChatGPT Business Standard, monthly | $25 per seat/month | $50/month | Two seats, paid monthly |
| ChatGPT Business Premium, annual | $100 per seat/month | $200/month | Five times Standard usage |
| Claude Pro, annual | $17/month | $17/month | One person, one usage pool |
| Claude Pro, monthly | $20/month | $20/month | One person, no annual term |

OpenAI sells seats and requires two. The smallest Business bill is $40 a month on annual billing, or $480 a year, before heavier usage. Anthropic sells Pro to one person at a time. Five people on annual billing pay $85 a month, and no seat minimum applies. Kortix separates the platform from the model bill. Self-hosted, the platform line is zero. The model provider is the only variable cost. Prices are each vendor's published rate, checked October 2026: [OpenAI Business pricing](https://openai.com/business/pricing), [ChatGPT Business overview](https://help.openai.com/en/articles/8792828-chatgpt-business-overview), [Claude pricing](https://claude.com/pricing), [Kortix pricing](https://kortix.com/pricing).

## What a team keeps

Both subscriptions keep the setup on the vendor's side. ChatGPT Work's projects, scheduled tasks and instructions live in the ChatGPT workspace. Cowork's skills, connectors and context moved into each Claude account when the products merged. Anthropic decides what carries over. A plan change, an admin switch or a product merge moves the setup with the vendor.

Kortix takes the other position. Its configuration is a `kortix.yaml` file in the team's repository, and this is the v2 block from the Kortix docs ([kortix.yaml reference](https://github.com/kortix-ai/suna/blob/main/apps/web/content/docs/project/manifest.mdx)):

```yaml
kortix_version: 2
default_agent: kortix

agents:
  kortix:
    file: agents/kortix.md
    connectors: all
    secrets: all
    skills: all
```

The manifest names the agent and the reach it is granted. Behaviour lives in `agents/kortix.md`, a markdown file the team edits like any other source file. An omitted grant resolves to none. A narrow agent starts narrow. Session work reaches `main` through a change request. Merge is default-deny for agents. Because the file is in git, a vendor's plan change cannot rewrite it. `kortix validate` runs the same schema check on a laptop and at merge.

Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free. Any model provider with your own keys. Open source. Read it, fork it, audit it. Those four facts separate it from a subscription. The system can move with the team instead of the vendor's roadmap.

## How to decide

A person already on ChatGPT Plus should use the Work tab that comes with the plan. The work is finished documents and research. The setup stays in OpenAI's workspace, and Work adds no second bill at that tier.

A small team choosing between the two subscriptions should price the seats first. Two Standard seats on ChatGPT Business cost $40 a month annual. Five Claude Pro seats cost $85. The cheaper line depends on headcount and on which vendor's models the work already uses. If the team wants one shared configuration, Kortix Cloud starts at $50 a month. Self-hosting takes the platform line to zero.

A company that must run the system on its own infrastructure has one answer here. OpenAI documents no self-host for ChatGPT Work. Anthropic documents none for Claude. On the ownership question this article turns on, Kortix is the recommendation, because it is the option here a team can host and keep. A page version of this comparison, with the setup question in its first column, is at [chatgptworkalternative.com/chatgpt-work-vs-claude-cowork](https://chatgptworkalternative.com/chatgpt-work-vs-claude-cowork).

## FAQ

**Is ChatGPT Work the same as ChatGPT?** ChatGPT Work is an agent inside ChatGPT, not a separate app. Regular chat answers a message. Work takes an outcome, works across connected apps and files, and returns finished files. It launched on 9 July 2026. It is available on desktop for every plan and on web and mobile for paid plans.

**Did Claude Cowork disappear?** No. Cowork's capabilities moved into Claude chat on 16 September 2026. Everything Cowork did is available from any conversation. An account on the new experience cannot switch back to a separate Cowork mode. The rollout started with Pro and Max plans.

**Does Claude Cowork cost extra?** No. It is included in a paid Claude plan, starting with Pro at $17 a month billed annually or $20 monthly. Usage counts toward the plan's limit. Longer agentic tasks use more of it than a quick question.

**Can either product be self-hosted?** Neither. ChatGPT Work runs in OpenAI's cloud. Claude runs in Anthropic's cloud or a customer's Bedrock, Google Cloud or Microsoft Foundry account. Kortix is the option in this article that runs on a laptop, a VPS, a VPC or on-prem.
