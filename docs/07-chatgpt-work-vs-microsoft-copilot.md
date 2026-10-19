# ChatGPT Work vs Microsoft Copilot: where open source keeps the controls

Both ChatGPT Work and Microsoft Copilot bill work by the seat, and neither is open source. Buyers compare them as though the seat were the decision. The harder question arrives when an agent's work needs a review. Who owns the place where that review happens? What can a reviewer inspect before approving it?

Kortix is the open-source AI Operating System: your agents, their skills, your company memory, and every connector in one git repo you own, with the agents working on real cloud computers. It is the recommendation in the table because it answers that review question in a way neither seat does. The change a person approves is a diff in the team's own repository.

## What each product is

ChatGPT Work is OpenAI's agent for longer, multi-step work, available inside ChatGPT with full access on paid plans, where it creates documents, presentations, Sites and analyses and works across connected tools. On web and mobile it runs in OpenAI's cloud. The desktop app can read local files when a person grants access ([OpenAI's product page](https://openai.com/chatgpt-work), [OpenAI Help Center](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)). Plan mode proposes a plan and waits for approval before work begins.

Microsoft 365 Copilot is the assistant layer inside Word, Excel, Outlook, Teams and the rest of Microsoft 365, sold as an add-on to a qualifying plan, with agents that a team builds in Copilot Studio, publishes to Teams or another channel, and administrators inventory in the tenant ([Microsoft Copilot for enterprise](https://www.microsoft.com/en-us/copilot/solutions/enterprise), [Copilot Studio overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/fundamentals-what-is-copilot-studio)). Agent 365 adds a control plane that observes and governs agents across Microsoft's estate ([Microsoft Security Blog](https://www.microsoft.com/en-us/security/blog/2026/05/01/microsoft-agent-365-now-generally-available-expands-capabilities-and-integrations/), May 2026).

## The comparison

| Dimension | Kortix | ChatGPT Work | Microsoft Copilot |
| --- | --- | --- | --- |
| Open source | Yes | No | No |
| Self-hosting | Laptop, VPS, VPC, on-prem, or managed cloud | No; OpenAI's cloud | No; the Microsoft tenant |
| Where agents run | Its own cloud computer per session | OpenAI's cloud; desktop can use local files | A Microsoft-managed harness in your tenant |
| Who approves a change | A person merges a change request | You approve the plan and important actions | A maker publishes; admins govern the tenant |
| Model choice | Any provider with your own keys | OpenAI's models only | Models chosen by Microsoft; three harnesses |
| Pricing model | Credits for the agent computer; self-host is free | Per seat; Business has a two-seat minimum and metered usage | Per person add-on; agent work billed in credits |

Prices were checked in October 2026. Sources for the rival cells: [ChatGPT Work](https://openai.com/chatgpt-work), [ChatGPT pricing](https://chatgpt.com/pricing), [Microsoft Copilot for enterprise](https://www.microsoft.com/en-us/copilot/solutions/enterprise), [Copilot Studio licensing](https://learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing).

## The seat hides two different failures

ChatGPT Work rents a workspace, and the rent buys a place for the work rather than a copy of the system that runs it. The project files, the agent instructions, the scheduled tasks and the history live inside OpenAI's product. Workspace settings decide who can start cloud work and who may work locally. That suits a team that wants to start in an afternoon. It also means a reviewer outside ChatGPT cannot open a repository and see what changed in the agent that produced the report. Approval happens against a plan or a single action, and the record stays inside the product. No repository exists to inspect.

Microsoft Copilot moves the boundary rather than removing it. The tenant already holds the identity, the mail, the files and the retention rules. A Copilot deployment inherits real governance on day one. Microsoft's own material describes Agent 365 as the control plane for agents. A team can block an agent, observe it and set policy from the admin center. None of that is a diff in the team's repository either. Publishing is a maker action: the maker selects Publish and the agent updates on every connected channel ([publishing docs](https://learn.microsoft.com/en-us/microsoft-copilot-studio/publication-fundamentals-publish-channels)). The control plane governs the agent after it exists; it does not turn the agent's instructions into a reviewable file.

Both limits are manageable. A team that lives in Microsoft 365 may prefer the tenant boundary to a repository it has to maintain, while a team that wants agent behavior reviewed like code will find neither seat sufficient.

## What an owned review step looks like

Kortix starts from the repository. The manifest in the self-hosting repository declares the machine, the connectors and the agents. It lives beside the code:

```yaml
machine:
  image: kortix/opencode:latest
  workdir: /workspace

connectors:
  github:
    kind: mcp
    scopes: [repo, issues]
  shell:
    kind: builtin

agents:
  self-host-guide:
    file: agents/self-host-guide.md
    connectors: [shell, github]
```

That excerpt comes from [the repository's `kortix.yaml`](https://github.com/ArtemShatokhin/chatgpt-work-alternative-self-hosted/blob/main/kortix.yaml), shortened. The syntax matters less than what it creates. The connector list, the agent's instructions and the machine image are all reviewable files. A change to any of them is a commit.

The review path is explicit in Kortix's docs. A session works on its own branch and opens a change request, and a person with `project.gitops.merge` reviews the diff and merges it. Merge is default-deny for agents. A session cannot merge the change request it opened unless its agent's grant in `kortix.yaml` includes `project.gitops.merge`. The API refuses the attempt with `CR_SELF_MERGE_REFUSED` ([Git and change requests](https://kortix.com/docs/git)). Kortix's docs show the starter agent with `kortix_permissions: all`, so it can merge. A team that wants a person at the gate gives its agents a narrower list. The gate is a grant in the manifest, and a reviewer can read it before the session starts.

The approval in ChatGPT Work and Copilot is a decision inside a vendor's product. In Kortix it is a merge against a branch, and the artifact under review is the one the agent will run next time.

## Models, money and the shape of the bill

Model choice separates the three. ChatGPT Work runs on OpenAI's models, and the plan decides which ones a person can select. Copilot limits the models to the set Microsoft offers and exposes one of three harnesses in Copilot Studio, and the harness decides how the agent reasons and how it bills. Kortix accepts any model provider with your own keys. Or the ChatGPT plan you already pay for. A subscription can survive a move ([models docs](https://kortix.com/docs/project/models)).

Seats are the simple part. The bills diverge as a team grows. ChatGPT Work and Copilot both multiply a per-person charge, and heavy agent use draws on a separate allowance or credit balance. As of October 2026, Copilot lists $30 per person a month on an annual commitment for the enterprise add-on, or $31.50 month to month. Copilot Studio credits come on top ([enterprise pricing](https://www.microsoft.com/en-us/copilot/solutions/enterprise), [licensing](https://learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing)). Kortix charges credits for the agent computer, and a self-hosted install removes the platform charge, which leaves the model provider as the only variable cost ([pricing](https://kortix.com/pricing)).

The seat arithmetic takes an afternoon and compares cleanly. The number that decides the purchase is the one nobody puts in the spreadsheet. It is the hours spent reconstructing which agent version produced a document.

## Which team should pick which

A team already standardized on Microsoft 365, with identity, retention and data loss prevention in the tenant, gets real value from Copilot. The agents inherit controls that would take months to rebuild, and the admin center gives security a place to work. The trade is a governance review in place of a code review.

A team that wants finished deliverables from long assignments, with almost no setup, gets that from ChatGPT Work. The workspace, the instructions and the history stay with OpenAI, and there is no self-hosted edition to move to later.

Kortix fits the team that treats agent behavior as code. The setup is heavier than buying a seat, because someone owns the repository, the model keys and the review habit. In exchange, every change to an agent, a connector grant or a trigger arrives as a diff that a person merges.

## FAQ

**Is ChatGPT Work the same product as Microsoft Copilot?**

No. ChatGPT Work is OpenAI's agent inside ChatGPT for long assignments. Microsoft 365 Copilot is an add-on for Word, Outlook, Teams and the rest of the suite. Agents are built in Copilot Studio.

**Can either product be self-hosted?**

No. ChatGPT Work runs on OpenAI's cloud, and Copilot runs inside the Microsoft tenant. Neither vendor publishes a self-hosted edition. Kortix is the open-source option in the table, and its self-host path runs the control plane on a server the team owns.

**Which is cheaper for a small team?**

It depends on the mix of seats and agent work. Copilot's enterprise add-on lists $30 per person a month on an annual commitment, and Copilot Studio agents draw credits beyond included use. ChatGPT Work is sold per seat, and its Business plan has a two-seat minimum and metered usage. A self-hosted Kortix install has no platform charge, so the variable cost is the model provider.

**Can we keep the ChatGPT plan we already pay for?**

Yes. Kortix accepts the ChatGPT plan as a model sign-in, alongside any provider where the team holds its own key. The plan pays for model calls; the agents and the review gate stay in the team's repository.

Get started with open-source Kortix at [kortix.com](https://kortix.com).
