# The workshop tools with an OpenRouter key

## Youth AI Lab - Erasmus+ project

- **Partners:** L.A.B. (Aix-en-Provence), UAB (Barcelona), Perlatecnica (Naples), Digitale Wolven
  (Antwerp), CSC Vent des Îles (La Rochelle)
- **Need help?**
  - Read [Part 7 - When a request fails](#part-7---when-a-request-fails).
  - Look at, or open, an [issue](https://github.com/Youth-AI-Lab/yal-openrouter-guide/issues).
- **Working with young people?** Read
  [Part 8 - Data and young people](#part-8---data-and-young-people) first.

> **A recipe for the facilitator.** You open an OpenRouter account, buy credits, make one key per
> pair with a spending limit, and paste each key in `workshop-login`. Every tool of the workshops
> then runs without Claude. There is no new command: the key chooses.

This guide is for youth workers, facilitators and educators who run the
[workshops of the Youth AI Lab project](https://github.com/Youth-AI-Lab/yal-workshop-kit#the-series)
or use the [Open WebUI guide](https://github.com/Youth-AI-Lab/yal-openwebui-guide). It has no
Codespace of its own: you use it in the Codespace of a workshop, of the kit or of the Open WebUI
guide.

**With an Anthropic key**, you do not need this guide: follow
[SETUP.md](https://github.com/Youth-AI-Lab/yal-workshop-kit/blob/main/SETUP.md) of the kit, or
[Your Anthropic API key](https://github.com/Youth-AI-Lab/yal-openwebui-guide#your-anthropic-api-key)
in the Open WebUI guide. The two routes use the same commands.

---

## Goals

| Part | You will be able to... |
|---|---|
| **1. Choose** | Say what OpenRouter is, when to choose it, and what stays Anthropic only. |
| **2. The account** | Open an account, buy credits, and know the fee and the risk of auto top-up. |
| **3. One key per pair** | Make keys with a credit limit, and know what happens at the limit. |
| **4. One command** | Save a key with `workshop-login`, read each message, and choose a model. |
| **5. The tools** | Say which model each tool uses, and what differs from the Anthropic route. |
| **6. The models** | Read the table of 2026-11-01, and say why a room cannot rely on free models. |
| **7. When a request fails** | Recognise a 429, a 402 and a 503, and know what to do during a session. |
| **8. Data and young people** | Turn on what the warning asks, and say what no setting removes. |
| **9. Sources and status** | Check the sources, and see what was tested and what was not. |

---

## Part 1 - Choose your key

OpenRouter is a company that gives you one key for the models of many companies. You buy credits
from OpenRouter. It sends each question to a company that runs the model you chose.

| | Anthropic key | OpenRouter key |
|---|---|---|
| The key starts with | `sk-ant-` | `sk-or-` |
| Models | Claude | many companies; no Claude model by default |
| Engine of the chatbot | Claude Code, or OpenCode if you choose it | OpenCode, always |

Choose an **OpenRouter key** if you want the workshops without Claude, or want to try other models.
Choose an **Anthropic key** to follow the workshop pages as they are.

**What stays Anthropic only: Claude Code.** In the workshops it accepts Anthropic keys only. An
OpenRouter key always runs in OpenCode, a free and open-source program that runs the same chatbot
with the same commands.

> [!NOTE]
> The costs, the context gauge and the scores printed in the workshop pages were measured with
> Claude. They do not hold for this route. What was measured with OpenRouter is in
> [Part 6](#part-6---the-models-on-2026-11-01).

---

## Part 2 - The account

Do this part on your own, never with your screen projected.

1. **Decide who holds the account.** OpenRouter's [terms](https://openrouter.ai/terms) say: "You
   must be at least 18 years of age to use the Service." The holder is an adult. If you act for an
   organisation, you must have the authority to bind it. Its
   [data processing agreement](https://openrouter.ai/data-processing-agreement) then applies:
   through the terms on the Free and Standard plans, and as a signed copy on request from the
   Business plan.
2. **Create the account** on <https://openrouter.ai>.
3. **Buy credits** on the page **Credits**, before you make keys: the
   [pricing table](https://openrouter.ai/pricing) gives "Budgets & Spend Controls" to the Standard
   plan and above, not to the Free plan.
   - One purchase goes from 5 to 25,000 dollars.
   - The fee is 5.5 % on the Standard plan, and taxes are added. You pay it when you buy credits.
     Each request then costs the provider's list price.
   - Unused credits become non-refundable after 24 hours, except at termination or where the law
     requires it. Fees are never refunded. OpenRouter may expire credits 365 days after purchase.
4. **Think twice before auto top-up.** It buys credits without you. OpenRouter warns about it in its
   [documentation](https://openrouter.ai/docs/api_reference/authentication): "A key with no limit
   lets a leaked key or a runaway agent spend your entire balance, including any auto top-ups."
   Keep a credit limit on every key ([Part 3](#part-3---one-key-per-pair)). Auto top-up during a
   session: (not tested).

**What a session costs on this route: TO BE COMPLETED.** No full session was measured.
[Part 6](#part-6---the-models-on-2026-11-01) gives the costs that were.

---

## Part 3 - One key per pair

1. On the page **Keys**, choose **Create API Key**. Name it after the pair.
2. Under **Key limit**, set a **Credit limit**, in dollars. You choose how often it resets: daily,
   weekly, monthly, or never. OpenRouter recommends a limit on every key. You may also choose no
   limit: do not.
3. Copy the key. It starts with `sk-or-`.
4. Do it again for the next pair.

A key that OpenRouter creates for you during onboarding has a limit of 100 dollars and expires after
180 days. Lower that limit before a pair uses it, or make your own keys.

**At the limit.** OpenRouter writes: "Once a key has used its credit limit, requests with it are
rejected until you raise the limit on the key's page, or, for a daily, weekly, or monthly limit,
until the limit resets." The tools then print one of the messages of
[Part 7](#402-no-credits-or-a-limit). OpenRouter's page cites this case under both 402 and 403, so
you may see either. Reaching a real key limit: (not tested).

**Why the kit caps the length of an answer.** OpenCode reserves the longest possible answer at each
request. On 2026-11-01 a short question failed with this 402: "You requested up to 195288 tokens,
but can only afford 20387". For OpenRouter, the kit caps one step at 8,192 tokens (a token is a
piece of a word), so that a small limit does not stop a short question. This was checked on a fake
OpenRouter and in real runs, not with a small real balance.

---

## Part 4 - One command: `workshop-login`

In the terminal of the Codespace:

```bash
workshop-login
```

Paste the key of the pair, then press Enter. You see one `*` per character. The command tests the
key, then sends one very short request to the model. You must see:

```text
Key received: sk-or-v…abcd (73 characters). Testing it…
Key OK (OpenCode, OpenRouter, model openrouter/deepseek/deepseek-v4-flash). You can start: workshop bare
```

In the Open WebUI guide (class mode), you see this instead:

```text
Warning: with young people, turn on zero-data-retention models hosted in Europe.
Key OK (OpenRouter, model deepseek/deepseek-v4-flash). You can start: openwebui start
```

That warning is explained in [Part 8](#part-8---data-and-young-people).

### What each message means

| You see | It means | You do |
|---|---|---|
| `Key saved, but this OpenRouter account has no credits left. Add credits, or choose a free model: workshop-login --models free` | The account is empty, or this key is at its limit. | Add credits, or raise the limit. |
| `Key saved, but this key has reached its spending limit. Tell the facilitator.` | The key is at its limit. | Raise the limit on the key's page. |
| `Key saved, but no company can serve the model <name> while promising not to keep the questions. Choose another model: workshop-login --models openrouter` | Your rules leave no company for this model. | Choose another model. |
| `Key saved, but the quota of the model <name> is reached for now (HTTP 429). Try again later, or choose another model: workshop-login --models openrouter` | Too many requests, or a free quota used up. | See [429](#429-too-many-requests). |
| `Key saved, but the model <name> is busy (HTTP 503). Try again in a few minutes, or choose another model: workshop-login --models openrouter` | The model cannot answer now. | See [503](#503-busy-or-no-company). |
| `Key saved, but OpenRouter refuses it (HTTP 401). Check it with the facilitator.` | The key is wrong or disabled. | Make a new key. |
| `OpenRouter refuses this key (HTTP 401). Your earlier key is kept. Check it with the facilitator.` | Same, and the key saved before still works. | Make a new key. |
| `This is an OpenRouter key: Claude Code in the workshop needs an Anthropic key (sk-ant-…).` | You asked for `--engine claude`. | Type `workshop-login` alone. |
| `OpenRouter has no model <name> that can use tools.` | Wrong name, or a model without tools. | Read the close names under it. |

In the Open WebUI guide, some of these lines end with other words, written for one person alone.

### Choose another model

```bash
workshop-login --models           # the models of your key's provider that can use tools
workshop-login --models free      # the free ones
workshop-login --model mistralai/mistral-small-3.2-24b-instruct
```

With `--model`, press Enter alone at the question: it keeps the saved key. With a free model, the
last lines add `Free requests left today: <number>.`

A new key goes back to the default model, unless `--model` names one. An Anthropic key pasted after
an OpenRouter key also goes back to Claude Code, unless you chose OpenCode with `--engine`. If Open
WebUI is running, you see `Open WebUI keeps the old key until you type: openwebui start`.

---

## Part 5 - The tools

| Tool | With an Anthropic key | With an OpenRouter key |
|---|---|---|
| `workshop`, `replay` | Claude Code, `claude-sonnet-5-5` | OpenCode, `deepseek/deepseek-v4-flash`, or your `--model` |
| `score` (the judge) | `claude-haiku-5-5` | `deepseek/deepseek-v4-flash` |
| `openwebui`, kit mode (`replay RAG` included) | `claude-sonnet-5-5` | `deepseek/deepseek-v4-flash`, or your `--model` |
| `openwebui`, class mode | `claude-sonnet-5-5` and the cheaper `claude-haiku-5-5` | `deepseek/deepseek-v4-flash`, and `mistralai/mistral-small-3.2-24b-instruct` as second model |
| `./sorter compare` (workshop 6) | `claude-haiku-5-5` | `mistralai/mistral-small-3.2-24b-instruct` |

`./sorter claude` still works as another name for `./sorter compare`. With an OpenRouter key, it
does not call Claude.

**What differs from the Anthropic route:**

- With OpenCode, no shell command runs without asking. The chatbot searches with OpenCode's own
  `read`, `grep` and `glob` tools.
- `replay` runs in a copy of the kit without the test material.
- OpenRouter would send a question to any company that serves the model. The kit adds
  `data_collection: deny` to every request. This is not zero data retention
  ([Part 8](#step-1-zero-data-retention)).
- `replay` shows the cost when OpenCode knows the price of the model. `replay RAG` prints
  `cost: not shown by Open WebUI`.

---

## Part 6 - The models on 2026-11-01

These results are one day's measures, and the prices and quotas of OpenRouter change. A mode is one
stage of the chatbot in the workshops: `bare` is the model alone, A has its instructions, B all its
knowledge at once, C searches the documents, D adds outside tools, E adds a wiki. Modes bare, A, C,
D and E ran on 11 questions (22 points), and B on 3 (6 points).

| Model | bare | A | B | C | D | E | Empty or failed answers | What must be paid |
|---|---|---|---|---|---|---|---|---|
| `deepseek/deepseek-v4-flash` | 2/22 | 11/22 | 6/6 | 20/22 | 19/22 | 19/22 | 0 | credits |
| `mistralai/mistral-small-3.2-24b-instruct` | 10/22 | 8/22 | 4/6 | 16/22 | 14/22 | 14/22 | 0 | credits |
| `google/gemini-2.5-flash-lite` | 10/20 | 12/22 | 5/6 | 12/20 | 1/2 | 9/16 | 8 of 61 | credits |
| `google/gemma-4-26b-a4b-it:free` | 8/22 | 12/22 | stopped | stopped | stopped | stopped | 429 from C on | nothing, inside the quota |
| `cohere/north-mini-code:free` | stopped | stopped | stopped | stopped | stopped | stopped | 429 everywhere | nothing, inside the quota |

The scores come from a machine judge (`claude-haiku-5-5`) and from one run. No person checked them.
One score does not rank two models: on a second run of mode D, the same judge gave DeepSeek v4 Flash
22/22 instead of 19/22. A total below 22 means that fewer answers got a score. "Stopped" means that
`replay` stopped after three errors in a row: these two lines do not score the free models.

**Why these defaults.** DeepSeek v4 Flash is the chatbot and the judge. It is slower: 3 to 4.5
minutes for a `replay` of 11 questions in bare, C, D and E, against 30 to 50 seconds for Mistral
Small. Mistral Small is the sorter and the second model of class mode.

The second run of mode D took 2 min 43 and showed $0.02 for 11 answers. `score D --auto` then gave
21/22 with DeepSeek as judge, for $0.0008.

| As judge, against `claude-haiku-5-5` | Same score | 1 point apart | 2 points apart | No score | Cost reported |
|---|---|---|---|---|---|
| `deepseek/deepseek-v4-flash` | 150/180 (83 %) | 30 | 0 | 1 | $0.016 |
| `google/gemini-2.5-flash-lite` | 133/154 (86 %) | 20 | 1 | 27 | $0.039 |
| `mistralai/mistral-small-3.2-24b-instruct` | 135/181 (74 %) | 44 | 2 | 0 | TO BE COMPLETED |

| `./sorter compare`, 32 test messages, first run | Sorted right | Urgent messages missed | Time | Cost |
|---|---|---|---|---|
| `mistralai/mistral-small-3.2-24b-instruct` | 32/32 | 0 | 18 s | $0.0003 |
| `deepseek/deepseek-v4-flash` | 30/32 | 1 | 38 s | $0.0002 |
| `google/gemini-2.5-flash-lite` | stopped at 6 messages, account empty | - | - | - |

A second run of Mistral Small gave 32/32, 0 urgent messages missed, in 17 s, for $0.0003.

### Free models

**A room cannot rely on free models.** They were not measured as a room. OpenRouter's
[limits](https://openrouter.ai/docs/api_reference/limits):

- 20 requests a minute;
- 50 requests a day, or 1,000 a day once the account has bought at least 10 dollars of credits;
- "Making additional accounts or API keys will not affect your rate limits", so more keys give a
  room no more;
- failed attempts count in the daily cap, and a negative balance blocks free models.

In the table above, two free models running at the same time ran into 429. A retry of
`north-mini-code` alone failed too, with the day's quota already used up.

Then each ran alone in mode C, with 1,000 requests a day:

| Free model | Result | Requests |
|---|---|---|
| `cohere/north-mini-code:free` | 18/22 from the same judge, 3 min 04, 0 errors | 62 for one `replay C`, about 5.6 per question |
| `google/gemma-4-26b-a4b-it:free` | 3 questions in 429 within 10 s, stopped | not counted apart |

One `replay C` of `north-mini-code` uses more than the 50 requests of an account that has not
bought 10 dollars of credits. `Free requests left today` went from 935 to 873 over that run. Earlier
in the day, the counter showed no use for several models: the cause is not established. The 429 of
`gemma-4-26b-a4b-it:free` came from the company that runs it (`Provider returned error`).

For the data of free models, read [Part 8](#part-8---data-and-young-people) first. On 2026-11-01,
the pages of OpenRouter marked 8 of the 14 free models as training on data. Only one of the 14 kept
nothing.

Set aside: `inkling` and `inkling-small` (403 on any direct call, and terms that forbid children's
data), and `nemotron-3.5-super-vl:free` (no company can serve it under the rule of the kit).

---

## Part 7 - When a request fails

The steps below come from the messages of the tools and from OpenRouter's documentation. A real 429
in a session and a small real balance are (not tested).

### 429: too many requests

| Tool | On screen |
|---|---|
| `replay` | `ERROR: too many requests, or the quota of this key or of this model is used up (429: <details>). Wait a minute, then try again.` After three in a row: `Three errors in a row: stopping.` |
| `score` | `Judge unavailable: HTTP 429: <details>.` If OpenRouter asks for more than 60 seconds: `Judge stopped: OpenRouter asks to wait <n> seconds. You score alone for this run.` |
| `./sorter compare` | `<model> is busy (HTTP 429): <details>. Wait a minute and type ./sorter compare again.` |
| `workshop` | OpenCode's own screen (not tested) |
| Open WebUI | (not tested) |

During the session:

1. Look at the model name. It is in the line `Engine:` of the answers file.
2. **It ends with `:free`:** stop using it for this session. Trying again uses up the day's quota.
   Move the pair to a paid model, then press Enter alone at the question:

   ```bash
   workshop-login --model deepseek/deepseek-v4-flash
   ```

3. **It is a paid model:** wait a minute and type the same command again. If it does not pass,
   choose `mistralai/mistral-small-3.2-24b-instruct`.
4. **Many pairs at once:** let them start `replay` one after the other, or on a few questions:
   `replay D 8 11`.

### 402: no credits, or a limit

| Tool | On screen |
|---|---|
| `replay` | `ERROR: no credits left on this key (402: <details>). Add credits on the provider's website, or ask the facilitator.` |
| `score` | `Judge stopped: no credits left on this key (<details>). You score alone for this run.` |
| `./sorter compare` | `OpenRouter says this account has no credit left: <details>. Show this message to the facilitator.` |

A 402 can mean three things:

- **The account is empty.** On 2026-11-01, OpenRouter let 0.17 dollars of overdraft through, then
  answered 402. Add credits.
- **This key is at its limit.** Raise the limit on the key's page.
- **A small balance on a prepaid or recent account.** OpenRouter holds an estimated cost in advance,
  so a request can fail while the balance is still positive. Wait a minute and try again, and do
  not run many pairs at once on a small balance. This does not apply to free models.

If you see `this key or its account reached a spending limit (403: <details>)`, a budget stopped the
key: raise it on OpenRouter's website.

### 503: busy, or no company

| Tool | On screen |
|---|---|
| `replay` | `ERROR: the model is busy, or no company can serve it now (503: <details>). Try again later, or ask the facilitator.` |
| `./sorter compare` | `<model> is busy (HTTP 503): <details>. Wait a minute and type ./sorter compare again.` |
| `./sorter compare`, no company at all | `No company can run <model> for this test: <details>.`, followed by what to do |

Wait a few minutes. If it stays, choose another model with `workshop-login --model`. If you turned
on the settings of [Part 8](#part-8---data-and-young-people), they may leave no company for the
model: read the list of the model's companies on its page.

---

## Part 8 - Data and young people

> [!WARNING]
> **With young people, turn on zero-data-retention models hosted in Europe.**
>
> This is the rule of the Youth AI Lab project for this route. `workshop-login` in class mode prints
> it, and `openwebui` prints it with `in your OpenRouter settings` at the end.
>
> Those settings hold the first half only, and an ordinary account can turn it on there. "Hosted in
> Europe" is not a setting, and the commands of the kit cannot do it yet: see
> [step 2](#step-2-hosted-in-europe). Then read [what no setting removes](#what-no-setting-removes)
> before you open anything to young people.

The workshops are for adults. This part is for the moment a chatbot opens to young people, such as
in the class mode of the Open WebUI guide.

This is not legal advice. It says what the texts said on 2026-11-01. The organisation decides, with
its data protection contact. Nothing here means that this setup is allowed for your group.

### Step 1: zero data retention

OpenRouter's [definition](https://openrouter.ai/docs/guides/features/zdr): "Zero Data Retention
(ZDR) means that a provider will not store your data for any period of time." A company can promise
not to train on your data and still keep it, so these are two promises.

The rule of the kit, `data_collection: deny`, does not give you ZDR. On 2026-11-01, Gemini 2.5
Flash Lite answered with this rule on, and its one company is listed with 55 days of retention.

1. As the account holder, open the [privacy settings](https://openrouter.ai/settings/privacy).
2. Turn on the ZDR toggle of each model group: **Anthropic**, **OpenAI**, **Google**, **SpaceXAI**
   and **All other models**. DeepSeek and Mistral are not in the first four. "Enabling a scope
   restricts all your requests to ZDR endpoints for that model group." An endpoint is one company
   running one model in one place.
3. Choose **Zero retention only**. Without a choice, an ordinary account stays on **Safety retention
   allowed**: Google may then keep prompts its classifiers flag, for up to 90 days. OpenRouter warns
   that with **Zero retention only**, "Most Google models become unavailable."
4. Leave off the two options that keep your data: **Private Input & Output Logging**, and
   **OpenRouter Use of Inputs/Outputs** (a 1 % discount). Both are off by default. Section 6.2 of
   the terms attaches a licence to prompt logging that includes the right to "license or sell your
   User Content in anonymized form".
5. In the Codespace, type `workshop-login` and press Enter alone. You must see `Key OK`: a company
   can serve the model, and the line does not say which one. If you see
   `no company can serve the model`, choose another model.

Nothing in this guide was run with these settings on: (not tested).

ZDR has limits, even when it is on:

- OpenRouter's list "reflects the AI Model Provider's published or represented policy", and "does
  not constitute OpenRouter's guarantee of AI Model Provider compliance."
- It covers the routing of model requests, not plugins or tools such as web search. The kit keeps
  web search off in Open WebUI.
- OpenRouter does not count a cache in memory as retention.
- OpenRouter keeps metadata for each request (number of tokens, latency), and "samples a small
  number of prompts for categorization".

### Step 2: hosted in Europe

Europe is not a toggle. OpenRouter [writes](https://openrouter.ai/docs/guides/features/in-region-routing):
"There is no setting to turn on: once your account is on one of these plans, you choose the region
for each request by sending it to that region's base URL."

| What you want | Ordinary account (Standard) | Business plan |
|---|---|---|
| The ZDR settings of step 1 | yes | yes |
| Requests sent to `eu.openrouter.ai`, served only in Europe (EU and EEA, UK, Switzerland), with no fallback outside it | no | yes: self-serve, no contract, no minimum, a fee of 8 % on credits instead of 5.5 % |
| A European company named inside a request (`provider.only`) | the documentation sets no plan condition; (not tested) | not needed |
| A free model in Europe | none | none |

Naming a company in a request chooses where the model runs. It does not choose where OpenRouter
handles the request: only the European address does that.

> [!WARNING]
> **The commands of the kit cannot do step 2 yet.** They send every request to `openrouter.ai`,
> have no option for `eu.openrouter.ai`, and name no company. `workshop-login --model` chooses a
> model, not a place. TO BE COMPLETED.

**The model must change too:**

- **`deepseek/deepseek-v4-flash`, the default:** OpenRouter lists no company running it in Europe.
  Change it. Of its 17 companies, 12 are ZDR and 5 keep prompts. `deepseek/deepseek-v4-flash-0731`
  is a different model, served in Europe by Inceptron: (not tested).
- **`mistralai/mistral-small-3.2-24b-instruct`** is the one measured model that OpenRouter lists in
  Europe, run by Mistral (`mistral/eu`). Its window (how much the model can read at once) is smaller
  there: 32k tokens, against 128k to 256k at the three other companies, none listed in Europe. Our
  runs were not pinned to `mistral/eu`, so its scores in
  [Part 6](#part-6---the-models-on-2026-11-01) are not scores in Europe.
- **`google/gemini-2.5-flash-lite`:** OpenRouter lists no company running it in Europe, and none
  under ZDR.

On 2026-11-01, OpenRouter's public [list](https://eu.openrouter.ai/api/v1/endpoints/zdr) showed 87
ZDR endpoints (see step 1) in Europe, for 66 models with tools, from five companies: Mistral, Azure,
Amazon Bedrock, Google Vertex and Inceptron. The two Gemini chat models on that list use Safety
Retention. The region is OpenRouter's declaration: no call and no independent proof confirmed where
a model runs.

Even with `eu.openrouter.ai`, only prompts and answers stay in Europe. OpenRouter
[writes](https://openrouter.ai/docs/guides/features/sovereign-ai): "Account, billing, and other
operational records may be stored or processed in the US." OpenRouter, Inc. is a New York company,
and the EU-only addendum of its data processing agreement applies only if chosen in writing.

### What each company's terms say

These are each company's own terms for the product named. A route through OpenRouter can differ:
its pages declare a policy for each route, and its agreements with these companies are not public.

| Company and product | Minors | Training | Retention | Place |
|---|---|---|---|---|
| **DeepSeek**, its own services | "primarily intended for adults"; under 18 with a guardian's consent; no chatbot "designed to specifically appeal to or present a persona of any person under the age of 18" | may use inputs and outputs, de-identified; OpenRouter lists the direct route as training | as long as the account exists, no number of days | China |
| **Mistral**, API and Studio | no personal information of children under 13 or the age of digital consent; minors need "legally adequate consent from their parent or guardian" | no, with exceptions: opt-in, feedback, order form, Labs or Preview models | 30 rolling days, unless ZDR; OpenRouter lists no retention on `mistral/eu` | EU by default; temporary transfers possible, depending on the feature |
| **Google**, Gemini API and AI Studio | 18 or older, and see below | paid services: no; in the EEA, Switzerland and the UK, the same rules for free services | 55 days | "any country in which Google or its agents maintain facilities" |
| **Google**, Vertex | see below | not without the customer's permission | flagged prompts, up to 90 days | the `eu` address stays in EU member states |
| **Cohere**, free model of Part 6 | "not intended to be used by minors (children)"; its usage policy asks an application used by minors for added safety controls | trial keys: may be used for research and development | 30 days, unless flagged | Google Cloud, US-Central, in an undated FAQ |

The default model does not reach DeepSeek itself: OpenRouter lists 17 other companies for it, whose
own terms are not covered here. Check them company by company.

### What no setting removes

1. **OpenRouter's age rule.** The terms say: "You must be at least 18 years of age to use the
   Service." The [privacy policy](https://openrouter.ai/privacy) says: "This Site is offered and
   available to users who are 18 years of age or older." It has no exception for organisations or
   parental consent. Section 5.2 of the terms adds: "You will require that all of your Authorized
   Users and customers access and use the Service and Models only in accordance with this
   Agreement". No text says in so many words that an organisation may or may not offer a chatbot to
   minors, but together these clauses weigh against it. The question has to go to OpenRouter, in
   writing.
2. **Sensitive data.** The data processing agreement lists health, origin, religion and criminal
   records, among others, and says: "No processing of Sensitive Data or any special categories is
   intended". Any such processing needs an amendment. As we read it, a chatbot where a young person
   writes about their health or their situation falls outside this frame without one. The
   agreement names "End Customers" and never mentions minors.
3. **The planned screening for child abuse material.** The
   [announcement](https://openrouter.ai/blog/announcements/csam-screening/) of 27 October 2026 says:
   "CSAM screening will also apply to requests covered by OpenRouter's Zero Data Retention (ZDR)
   policy." The ZDR page adds: "Content flagged as potential CSAM may be retained for human review,
   reporting, and preservation where required by law." The start date is not established. As we
   read it, for a group of minors, a false alarm could lead to retention and to a person reading the
   text, even under ZDR. The announcement says: "A flag indicates suspected material; it is not
   itself a determination that the content is CSAM".
4. **Google's clause on under-18s.** The
   [Gemini API terms](https://ai.google.dev/gemini-api/terms) say you "will not use the Services as
   part of a website, application, or other service" that "is directed towards or is likely to be
   accessed by individuals under the age of 18." The
   [Google Cloud terms](https://cloud.google.com/terms/service-terms) say the same for generative AI
   services and their end users. Whether this reaches a customer of OpenRouter on the Vertex route
   is not established.

The facts of this part were collected by AI models and then checked by a second one, against the
raw pages. No lawyer read them. If your organisation says no, a model on its own machine sends
nothing to these companies: see the
[local AI guide](https://github.com/Youth-AI-Lab/yal-local-ai-guide).

---

## Part 9 - Sources and status

### Sources, read on 2026-11-01

- OpenRouter: [terms](https://openrouter.ai/terms), [privacy](https://openrouter.ai/privacy),
  [data processing agreement](https://openrouter.ai/data-processing-agreement),
  [pricing](https://openrouter.ai/pricing), [limits](https://openrouter.ai/docs/api_reference/limits),
  [API keys](https://openrouter.ai/docs/api_reference/authentication),
  [zero data retention](https://openrouter.ai/docs/guides/features/zdr),
  [in-region routing](https://openrouter.ai/docs/guides/features/in-region-routing),
  [sovereign AI](https://openrouter.ai/docs/guides/features/sovereign-ai),
  [data collection](https://openrouter.ai/docs/guides/privacy/data-collection),
  [provider logging](https://openrouter.ai/docs/guides/privacy/provider-logging),
  [screening announcement](https://openrouter.ai/blog/announcements/csam-screening/),
  [list of ZDR endpoints](https://openrouter.ai/api/v1/endpoints/zdr).
- DeepSeek: [terms of use](https://cdn.deepseek.com/policies/en-US/deepseek-terms-of-use.html),
  [privacy policy](https://cdn.deepseek.com/policies/en-US/deepseek-privacy-policy.html).
- Mistral: [commercial terms](https://legal.mistral.ai/terms/commercial-terms-of-service/),
  [privacy policy](https://legal.mistral.ai/terms/privacy-policy/),
  [where data is stored](https://help.mistral.ai/en/articles/347629-where-do-you-store-my-data-or-my-organization-s-data).
- Google: [Gemini API terms](https://ai.google.dev/gemini-api/terms),
  [usage policies](https://ai.google.dev/gemini-api/docs/usage-policies),
  [Google Cloud service terms](https://cloud.google.com/terms/service-terms),
  [abuse monitoring](https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/abuse-monitoring),
  [data residency](https://docs.cloud.google.com/gemini-enterprise-agent-platform/resources/data-residency).
- Cohere: [privacy](https://cohere.com/privacy), [usage policy](https://docs.cohere.com/docs/usage-policy),
  [data commitments](https://cohere.com/enterprise-data-commitments),
  [Trust Center](https://trustcenter.cohere.com/).

### What was tested

On 2026-11-01, with OpenCode 2.1.4, in a container of image 2026.10.42 with the new commands placed
in front, on a copy of the kit prepared by `workshop-start 5`:

- the scores, the judges and the sorter of [Part 6](#part-6---the-models-on-2026-11-01);
- on an account with credits, a key pasted with no option: `workshop-login`, the `summarize` skill
  with `deepseek/deepseek-v4-flash`, `replay D`, `score D --auto`, `./sorter compare`, then the two
  free models one at a time;
- Open WebUI v0.12.4 in kit mode, with Mistral Small through OpenRouter: `openwebui start` 250 s,
  `openwebui sizes` 885 s (2 cores, three other measures at the same time), `openwebui query` right,
  `replay RAG` 11 answers in 46 s, 0 ERROR, nothing in the error log;
- the cap of 8,192 tokens, on a fake OpenRouter and in the run with credits;
- Open WebUI in class mode, on a fake OpenRouter: it starts, it prints the warning, and the rule
  `data_collection: deny` reaches the fake OpenRouter.

The image number that carries these commands: TO BE COMPLETED.

### What was not tested

- A group. A real Codespace.
- `google/gemma-4-26b-a4b-it:free` at another moment: its 429 came from the company that runs it.
- The same scores replayed several times, to know how far a score moves.
- A small real balance, a real 429 in a session, a real key limit, auto top-up.
- Open WebUI in class mode with a real OpenRouter key, and Open WebUI with the default DeepSeek
  model.
- The ZDR settings, **Zero retention only**, `eu.openrouter.ai`, `provider.only`, the Business plan.
- A human reading of a sample of the scores.
- The cost of a full session.

---

## About

Part of the Youth AI Lab project (Erasmus+). Texts: CC BY-SA 4.0. Configuration files: EUPL-1.2. See
`REUSE.toml` and `LICENSES/`. OpenRouter, DeepSeek, Mistral, Google and Cohere are the names of
their owners, who have no link with this guide.
