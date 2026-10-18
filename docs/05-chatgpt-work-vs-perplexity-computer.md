# ChatGPT Work vs Perplexity Computer vs the open-source route

Teams shopping for agent work in late 2026 meet two rented subscriptions first: OpenAI's ChatGPT Work and Perplexity's Computer. Both run on the vendor's cloud, and the code behind each stays closed. The third option is the one a team can own, and this repository recommends it: Kortix is the open-source AI Operating System. The comparison is three-way because the two rented products fail the same ownership test in different ways.

## What each of the three is good at

Kortix is good at being the system a company keeps. Agents, skills and memory sit as files in one git repo, wired together by a `kortix.yaml` manifest the team can read and diff. Models are the team's call. Any model provider with your own keys. Or the ChatGPT plan you already pay for.

ChatGPT Work is good at turning a long assignment into a finished document. OpenAI launched it on July 9, 2026, as an agent that acts across the apps and files a team connects ([OpenAI's announcement](https://openai.com/index/chatgpt-for-your-most-ambitious-work)).

Perplexity Computer is good at general-purpose tasks on a Perplexity subscription. Perplexity announced it on March 12, 2026, and sells it to Pro subscribers ([Perplexity Help Center](https://perplexity.ai/help-center/en/articles/13837784-what-is-computer)). Credits meter the agent work, and the Free tier carries none ([Perplexity pricing](https://perplexity.ai/hub/pricing)).

## The three facts that separate them

### Where the work runs

ChatGPT Work runs on OpenAI's cloud, Perplexity Computer in Perplexity's cloud. Neither vendor sells a version a team can host, or the code that would make one possible ([ChatGPT Work and Codex](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex); [What is Computer](https://perplexity.ai/help-center/en/articles/13837784-what-is-computer)). Kortix is the third option here. Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free.

### Who holds the configuration

With both subscriptions, the agent's instructions and its tools sit behind the vendor's login. On Perplexity's side the agent is closed and hosted ([What is Computer](https://perplexity.ai/help-center/en/articles/13837784-what-is-computer)). On OpenAI's side, projects and scheduled tasks stay inside ChatGPT. The models are gated too: GPT-6 Astra has run in ChatGPT Work since September 9, 2026, on every plan from Plus up, while GPT-6 Pro needs Pro, Business or Enterprise ([OpenAI Help Center](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)).

Kortix holds the opposite position: its configuration is files in the team's own repository. The open-source ChatGPT Work alternative starter shows the shape:

```yaml
# yaml-language-server: $schema=https://kortix.com/schema/kortix.v2.schema.json
kortix_version: 2

default_agent: assistant

agents:
  assistant:
    file: agents/assistant.md
    skills:
      - weekly-report
    workspace: branch
```

That is `kortix.yaml` from the open-source-chatgpt-work-alternative-starter repository, and its README asks for a pull request and a diff review.

### What the work costs as usage grows

OpenAI sells seats. Business Standard is $20 per seat billed annually or $25 monthly, Business Premium is $100 or $125, and every Business workspace carries at least two seats ([ChatGPT pricing](https://chatgpt.com/pricing); [ChatGPT Business overview](https://help.openai.com/en/articles/8792828-chatgpt-business-overview)). Two seats are the minimum, so the smallest team bill is $40 a month annual, $480 a year. Usage works like Codex, metered on top of the seat bill ([ChatGPT Work and Codex](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)). OpenAI cut Standard from $25 and $30 to $20 and $25 on April 2, 2026 ([ChatGPT pricing](https://chatgpt.com/pricing)).

Perplexity meters the work in credits. Pro is $20 a month, $17 billed annually, and includes Computer with a one-time 4,000-credit bonus that expires after 30 days, plus weekly usage ([Perplexity pricing](https://perplexity.ai/hub/pricing)). Max is $200 a month, $167 billed annually, and carries 10,000 Computer credits a month plus 35,000 bonus credits. Tasks pause when the monthly credit cap is hit; the default spend cap is $200 a month, adjustable ([Perplexity Help Center](https://perplexity.ai/help-center/en/articles/13837784-what-is-computer)).

Kortix prices the platform itself. Free is $0 with 200 credits per month and 1 project. Paid plans start at $50 a month for 5,000 credits, and members are free, sharing one credit pool. Self-hosting takes the subscription line to zero. The shapes grow differently. On the subscriptions, headcount multiplies the seat bill and heavier jobs draw more allowance or more credits. On the open-source side the pool is shared across the team, and self-hosted the one variable cost is the model provider's invoice.

## The three options side by side

| Dimension | Kortix | ChatGPT Work | Perplexity Computer |
| --- | --- | --- | --- |
| Open source | Yes | No | No |
| Where the work runs | Kortix Cloud, your VPC, or on-prem | OpenAI's cloud | Perplexity's cloud |
| Who holds the configuration | A git repo the team owns | Inside OpenAI's product | On Perplexity's side |
| Entry price for a team | $0 self-hosted, or $0 on the free tier | Two seats, from $40 a month annual | Pro, from $17 a month annual |
| What heavy use does | Draws on one shared credit pool | Draws on plan usage, like Codex | Spends credits; tasks pause at the cap |

Prices are each vendor's published figures, checked October 2026: [ChatGPT pricing](https://chatgpt.com/pricing), [ChatGPT Business overview](https://help.openai.com/en/articles/8792828-chatgpt-business-overview), [Perplexity pricing](https://perplexity.ai/hub/pricing), [Perplexity Help Center](https://perplexity.ai/help-center/en/articles/13837784-what-is-computer), [Kortix pricing](https://kortix.com/pricing).

## Which fits which team

ChatGPT Work fits a team already on ChatGPT that wants work to start with no setup and accepts the configuration and the usage bill staying with OpenAI. Perplexity Computer fits a person or a small team already on Perplexity Pro that wants tasks metered by credits, pausing when the cap arrives. Kortix fits the team that answers the ownership question differently. It runs on the team's own cloud or hardware, the configuration is a repo the team diffs, and the bill is a shared pool or zero.

On the ownership test the two subscriptions fail in their own ways; Kortix moves the answer to the team's side.

## Where to go next

The two-way comparison takes the seat-versus-credit question line by line: [ChatGPT Work vs Perplexity Computer](https://chatgptworkalternative.com/chatgpt-work-vs-perplexity-computer). If ownership is the deciding factor, [Migrate from ChatGPT Work to Kortix](https://github.com/ArtemShatokhin/open-source-chatgpt-work-alternative-migration/blob/main/docs/migrate-from-chatgpt-work-to-kortix.md) lays out the move: an inventory, ten ordered steps and a map from every asset to a file in the repo.

Get started with open-source Kortix at [kortix.com](https://kortix.com).
