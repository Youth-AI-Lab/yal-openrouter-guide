# The workshop tools with an OpenRouter key

## Youth AI Lab - Erasmus+ project

- **Partners:** L.A.B. (Aix-en-Provence), UAB (Barcelona), Perlatecnica (Naples), Digitale Wolven
  (Antwerp), CSC Vent des Îles (La Rochelle)
- **Need help?**
  - Read [Part 7 - When a request fails](#part-7---when-a-request-fails).
  - Look at, or open, an [issue](https://github.com/Youth-AI-Lab/yal-openrouter-guide/issues).
- **Working with young people?** Read
  [Part 8 - Data and young people](#part-8---data-and-young-people) first.

> **A recipe for the facilitator. Time: TO BE COMPLETED (no person has followed it yet).** You open
> an OpenRouter account, buy credits, make one key per pair with a spending limit, and paste each key
> in `workshop-login`. Every tool of the workshops then runs without Claude.

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

### Prerequisites

- An adult who holds the OpenRouter account and has a way to pay ([Part 2](#part-2---the-account)).
- A Codespace of a workshop, of the kit or of the Open WebUI guide, already open:
  [SETUP.md](https://github.com/Youth-AI-Lab/yal-workshop-kit/blob/main/SETUP.md) of the kit says how.
  No Codespace? See the [dev containers guide](https://github.com/Youth-AI-Lab/yal-devcontainer-guide).
- Before any session with young people: your organisation's data protection contact
  ([Part 8](#part-8---data-and-young-people)).

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

`openwebui` has two modes in these pages. **Kit mode** is the one of the workshops: each pair has its
own Open WebUI, with no accounts. **Class mode** is the one of the
[Open WebUI guide](https://github.com/Youth-AI-Lab/yal-openwebui-guide): one facilitator opens one
Open WebUI to a group, with accounts.

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
   - One purchase goes from $5 to $25,000.
   - The fee is 5.5 % on the Standard plan, and taxes are added. You pay it when you buy credits.
     Each request then costs the provider's list price.
   - Unused credits become non-refundable after 24 hours, except at termination or where the law
     requires it. Fees are never refunded. OpenRouter may expire credits 365 days after purchase.
4. **Leave auto top-up off.** It buys credits without you. OpenRouter warns about it in its
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
5. Give each pair its key in private, in a direct message or on paper. Never show a key on the
   projected screen.
6. After your last session with these pairs, delete each key on the
   [key settings page](https://openrouter.ai/settings/keys). A key with a limit that never resets
   stays usable until then: the limit protects the money, not the access. Deleting a key: (not
   tested).

A key that OpenRouter creates for you during onboarding has a limit of $100 and expires after
180 days. Lower that limit before a pair uses it, or make your own keys.

**At the limit.** OpenRouter writes: "Once a key has used its credit limit, requests with it are
rejected until you raise the limit on the key's page, or, for a daily, weekly, or monthly limit,
until the limit resets." The tools then print one of the messages of
[Part 7](#402-no-credits-or-a-limit). OpenRouter's page cites this case under both 402 and 403, so
you may see either. Reaching a real key limit: (not tested).

**Why the kit caps the length of an answer.** OpenCode reserves the longest possible answer at each
request. On 2026-11-01 a request to summarize a long document failed with this 402: "You requested
up to 195288 tokens, but can only afford 20387". For OpenRouter, the kit caps one step at 8,192 tokens (a token is a
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
Warning: with young people, turn on zero-data-retention models hosted in Europe: workshop-login --europe
Key OK (OpenRouter, model deepseek/deepseek-v4-flash). You can start: openwebui start
```

That warning is explained in [Part 8](#part-8---data-and-young-people).

### What each message means

| You see | It means | You do |
|---|---|---|
| `--europe needs an OpenRouter key (sk-or-…). This is an Anthropic key. Nothing saved.` | You typed `--europe` and pasted an Anthropic key. | Paste the OpenRouter key. |
| `Key saved, but this OpenRouter account has no credits left. Add credits, or choose a free model: workshop-login --models free` | The account is empty, or this key is at its limit. | Add credits, or raise the limit. |
| `Key saved, but this key has reached its spending limit. Tell the facilitator.` | The key is at its limit. | Raise the limit on the key's page. |
| `Key saved, but no company can serve the model <name> under the workshop's data rule. Choose another model: workshop-login --models openrouter` | Your rules leave no company for this model. | Choose another model. |
| `Key saved, but Mistral does not serve the model <name> in Europe with zero data retention. Choose another model, for example: workshop-login --model <name>` | You turned on `--europe`, and this model has no such company. | Type the command it gives. |
| `OpenCode is already open and keeps the old data rule: close it and start it again. A replay stops by itself before its next question.` | You changed `--europe` while OpenCode was running. | Close that chatbot, then start it again. |
| `Your data rule changed during this replay (workshop-login --europe or --no-europe). The next question was not sent.` | Same, during a `replay`. The question in progress finished under the old rule. | Type the same `replay` again. |
| `Open WebUI keeps the old data rule until you type: openwebui start` | You changed `--europe` while Open WebUI was running. | Type `openwebui start`. |
| `Your data rule changed since Open WebUI started (workshop-login --europe).` | Same, and you typed another `openwebui` command. | Type `openwebui start`, then the command again. |
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

What is already running keeps the old model. Close the chatbot and start it again, or type
`openwebui start`. No line tells you this when only the model changes.

A new key goes back to the default model, unless `--model` names one. An Anthropic key pasted after
an OpenRouter key also goes back to Claude Code, unless you chose OpenCode with `--engine`. If Open
WebUI is running, you see `Open WebUI keeps the old key until you type: openwebui start`.

### The commands of this guide

| Command | What it does |
|---|---|
| `workshop-login` | Saves a key and tests it. Enter alone keeps the saved key. |
| `workshop-login --models` | Lists the models of your key's provider that can use tools. |
| `workshop-login --models free` | Lists the free ones. |
| `workshop-login --model <name>` | Chooses the chatbot's model. It does not change the judge or the sorter. |
| `workshop-login --europe` | Turns on the rule of [Part 8](#required-hosted-in-europe). |
| `workshop-login --no-europe` | Removes that rule. Never during a session with young people. |

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
does not call Claude. With `workshop-login --europe`, every line of the last column is Mistral Small
by default ([Part 8](#required-hosted-in-europe)).

**What differs from the Anthropic route:**

- With OpenCode, no shell command runs without asking. The chatbot searches with OpenCode's own
  `read`, `grep` and `glob` tools.
- `replay` runs in a copy of the kit without the test material.
- OpenRouter would send a question to any company that serves the model. The kit adds
  `data_collection: deny` to every request, which leaves out companies that may collect the data or
  train on it. Some of the others keep the questions
  ([Part 8](#what-zero-data-retention-means)).
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
| `google/gemini-2.5-flash-lite` | 10/20 | 12/22 | 5/6 | 12/20 | 1/2 | 9/16 | 8 of 51 | credits |
| `google/gemma-4-26b-a4b-it:free` | 8/22 | 12/22 | stopped | stopped | stopped | stopped | 429 from C on | nothing, inside the quota |
| `cohere/north-mini-code:free` | stopped | stopped | stopped | stopped | stopped | stopped | 429 on 17 of 18 answers | nothing, inside the quota |

The scores come from a machine judge (`claude-haiku-5-5`) and from one run. No person checked them.
One score does not rank two models: on a second run of mode D, the same judge gave DeepSeek v4 Flash
22/22 instead of 19/22. A total below 22 means that fewer answers got a score. "Stopped" means that
`replay` stopped after three errors in a row: these two lines do not score the free models.

| Model | Price in/out, per million tokens | Window | Companies under ZDR (see [Part 8](#what-zero-data-retention-means)) | In Europe |
|---|---|---|---|---|
| `deepseek/deepseek-v4-flash` | about $0.09/$0.18 | 1M | 12 of 17 | none |
| `mistralai/mistral-small-3.2-24b-instruct` | $0.075/$0.20 at the cheapest company, $0.10/$0.30 in Europe | 128k to 256k, 32k in Europe | 4 of 4 | 1 |
| `google/gemini-2.5-flash-lite` | $0.10/$0.40 | 1M | 0 of 1 (55 days) | none |
| `google/gemma-4-26b-a4b-it:free` | free | 262k | 0 of 1 (55 days) | none |
| `cohere/north-mini-code:free` | free | 256k | 0 of 1 (30 days) | none |

The window is how much the model can read at once. These are OpenRouter's figures on 2026-11-01.

**Why these defaults.** DeepSeek v4 Flash scored highest in modes C, D and E with no failed answer,
and as judge it left one answer without a score, against 27 for Gemini 2.5 Flash Lite. That is one
run: a tendency, not a ranking. The cost is time: 3 to 4.5 minutes for a `replay` of 11 questions in
bare, C, D and E, against 32 to 53 seconds for Mistral Small. Mistral Small sorted all 32 test
messages and missed no urgent one, so it is the sorter. It is also the second model of class mode.

The second run of mode D took 2 min 43 and showed $0.02 for 11 answers. `score D --auto` then gave
21/22 with DeepSeek as judge, for $0.0008.

The next table shows how often each candidate gave the same score as `claude-haiku-5-5`. This model
is only the yardstick of these measures: the route of this guide does not use it.

| As judge, against `claude-haiku-5-5` | Same score | 1 point apart | 2 points apart | No score | Cost reported |
|---|---|---|---|---|---|
| `deepseek/deepseek-v4-flash` | 150/180 (83 %) | 30 | 0 | 1 | $0.016 |
| `google/gemini-2.5-flash-lite` | 133/154 (86 %) | 20 | 1 | 27 | $0.039 |
| `mistralai/mistral-small-3.2-24b-instruct` | 135/181 (75 %) | 44 | 2 | 0 | TO BE COMPLETED |

The next table shows `./sorter compare` with each model, on the 32 test messages of workshop 6.

| `./sorter compare`, 32 test messages, first run | Sorted right | Urgent messages missed | Time | Cost |
|---|---|---|---|---|
| `mistralai/mistral-small-3.2-24b-instruct` | 32/32 | 0 | 18 s | $0.0003 |
| `deepseek/deepseek-v4-flash` | 30/32 | 1 | 38 s | $0.0002 |
| `google/gemini-2.5-flash-lite` | stopped at 6 messages: `Provider returned error`, cause not established | - | - | - |

A second run of Mistral Small gave 32/32, 0 urgent messages missed, in 17 s, for $0.0003.

### Free models

**A room cannot rely on free models.** They were not measured as a room. OpenRouter's
[limits](https://openrouter.ai/docs/api_reference/limits):

- 20 requests a minute;
- 50 requests a day, or 1,000 a day once the account has bought at least $10 of credits (a day is a
  UTC day);
- "Making additional accounts or API keys will not affect your rate limits", so more keys give a
  room no more. The same sentence goes on: "We do however have different rate limits for different
  models";
- failed attempts count in the daily cap, and a negative balance blocks free models.

In the table above, two free models running at the same time ran into 429. A retry of
`north-mini-code` alone failed too, with the day's quota already used up.

Then each ran alone in mode C, with 1,000 requests a day:

| Free model | Result | Requests |
|---|---|---|
| `cohere/north-mini-code:free` | 18/22 from the same judge, 3 min 04, 0 errors | 60 to 62 for one `replay C`, about 5.5 per question |
| `google/gemma-4-26b-a4b-it:free` | 3 questions in 429 within 10 s, stopped | not counted apart |

One `replay C` of `north-mini-code` uses more than the 50 requests of an account that has not
bought $10 of credits. Do not rely on the counter `Free requests left today` during a session
([Part 9](#notes-on-the-measures)). The 429 of `gemma-4-26b-a4b-it:free` came from the company that
runs it (`Provider returned error`).

For the data of free models, read [Part 8](#part-8---data-and-young-people) first. On 2026-11-01,
the pages of OpenRouter marked 8 of the 14 free models as training on data. Only one of the 14 kept
nothing.

Set aside: `inkling` and `inkling-small` (403 on any direct call, and terms that forbid children's
data), and `nemotron-3.5-super-vl:free` (no company can serve it under the rule of the kit).

### Paid models

The [limits](https://openrouter.ai/docs/api_reference/limits) page, read on 2026-11-01, describes
OpenRouter's rate limits as "free-model request caps and DDoS protection". It says that the paid
variant of a model "has no platform-level request cap". So a 429 on a paid model should come from
the company that runs it, not from OpenRouter. A real 429 on a paid model: (not tested).

With `workshop-login --europe`, one company serves Mistral Small and there is no second choice. A 429
from Mistral reaches the group directly ([Part 7](#429-too-many-requests)).

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

OpenCode tries a 429 or a 503 again by itself before it shows the error, so the screen can look
stuck. This took 82 to 93 s on a fake OpenRouter. In a real run, three 429s came within 10 s: the
wait varies.

With `workshop` or Open WebUI, if nothing comes, wait a minute and try again. If it stays, the
facilitator changes the model with the steps below.

During the session:

1. Look at the model name. After a `replay`, it is in the line `Engine:` of the answers file.
   Otherwise, type `workshop-login` and press Enter alone: the last line names it.
2. **It ends with `:free`:** stop using it for this session. Trying again uses up the day's quota.
   Move the pair to a paid model, then press Enter alone at the question:

   ```bash
   workshop-login --model deepseek/deepseek-v4-flash
   ```

3. **It is a paid model:** wait a minute and type the same command again. If it does not pass,
   choose `mistralai/mistral-small-3.2-24b-instruct` with `workshop-login --model`.
4. **`--europe` is on:** wait a minute and try again. No other model is the fallback. Do not type
   `--no-europe` during a session with young people.
5. **Many pairs at once:** let them start `replay` one after the other, or on a few questions:
   `replay D 8 11`.

After a change of model, close the chatbot and start it again, or type `openwebui start`. `--model`
does not change the judge or the sorter: with `score` or `./sorter compare`, wait a minute and try
again.

### 402: no credits, or a limit

| Tool | On screen |
|---|---|
| `replay` | `ERROR: no credits left on this key (402: <details>). Add credits on the provider's website, or ask the facilitator.` |
| `score` | `Judge stopped: no credits left on this key (<details>). You score alone for this run.` |
| `./sorter compare` | `OpenRouter says this account has no credit left: <details>. Show this message to the facilitator.` |

A 402 can mean three things:

- **The account is empty.** On 2026-11-01, OpenRouter let $0.17 of overdraft through, then
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
model: read the list of the model's companies on its page. With `--europe` on and young people, do
not change the model: wait, or stop the chatbot for this session.

---

## Part 8 - Data and young people

> [!WARNING]
> **With young people and OpenRouter, type `workshop-login --europe`.**
>
> Requests then go only to Mistral, hosted in Europe, with zero data retention. The default model
> is Mistral Small. This is the rule of the Youth AI Lab project for this route. In class mode,
> `workshop-login`, `openwebui start` and `openwebui share open` print it until it is on.
>
> **Keep Mistral Small.** `--europe` allows Mistral alone. Other companies run models in Europe, but
> the terms of Amazon and Azure were not read, and Google's may exclude this use
> ([item 4](#what-no-setting-removes)). Mistral's were read, and they ask for parental consent
> ([item 5](#what-no-setting-removes)).
>
> It does not keep everything in Europe ([what it covers](#required-hosted-in-europe)), and it does
> not lift [what no setting removes](#what-no-setting-removes). Read both before you open anything
> to young people.

The workshops are for adults. This part is for the moment a chatbot opens to young people, such as
in the class mode of the Open WebUI guide.

This is not legal advice. It says what the texts said on 2026-11-01. The organisation decides, with
its data protection contact. Nothing here means that this setup is allowed for your group.

### What zero data retention means

OpenRouter's [definition](https://openrouter.ai/docs/guides/features/zdr): "Zero Data Retention
(ZDR) means that a provider will not store your data for any period of time." A company can promise
not to train on your data and still keep it.

The rule the kit always sends, `data_collection: deny`, does not give you ZDR. It only leaves out
companies that may collect the data or train on it. On 2026-11-01, Gemini 2.5 Flash Lite and
`google/gemma-4-26b-a4b-it:free` answered with this rule on, and the one company of each is listed
with 55 days of retention.

ZDR has limits, even when it is on:

- OpenRouter's list "reflects the AI Model Provider's published or represented policy", and "does
  not constitute OpenRouter's guarantee of AI Model Provider compliance."
- It covers the questions sent to a model, not add-ons such as web search. The kit keeps web search
  off in Open WebUI.
- OpenRouter does not count a cache in memory as retention.
- For each request, OpenRouter keeps the number of tokens and the time taken, and "samples a small
  number of prompts for categorization" (a prompt is a text sent to a model).

### Required: hosted in Europe

```bash
workshop-login --europe
```

Press Enter alone to keep the saved key. In class mode, you must see:

```text
Key OK (OpenRouter, model mistralai/mistral-small-3.2-24b-instruct, hosted in Europe). You can start: openwebui start
```

In the kit, you must see:

```text
Key OK (OpenCode, OpenRouter, model openrouter/mistralai/mistral-small-3.2-24b-instruct, hosted in Europe). You can start: workshop bare
```

**Before `openwebui share open`:** type `openwebui start`. The line `Warning: with young people...`
must be gone. If you still see it, the rule is off.

From then on, `workshop`, `replay`, `score`, `openwebui` and `./sorter` send this with each request:
one European endpoint (`mistral/eu`), zero data retention, no second choice. An endpoint is one
company running one model in one place. If it cannot serve the model, the request fails. The real run below
used `openwebui` in kit mode: class mode with `--europe` is (not tested).

> [!WARNING]
> **`--europe` chooses where the model runs, not where OpenRouter handles the request.** OpenRouter
> itself may handle a request elsewhere. The kit still sends every request to `openrouter.ai`, and
> has no option for `eu.openrouter.ai`. Accounts, billing and security logs may stay in the US in
> all cases.

| What you want | Ordinary account (Standard) | Business plan |
|---|---|---|
| A European company named inside each request: `workshop-login --europe` | yes: OpenRouter accepted it, see below | not needed |
| Requests sent to `eu.openrouter.ai`, handled and served only in Europe (EU and EEA, UK, Switzerland), with no fallback outside it | no: the pricing table gives it to the Business and Enterprise plans | yes: you turn it on yourself, no contract, no minimum, a fee of 8 % on credits instead of 5.5 %; not supported by the commands of the kit |
| A free model in Europe | none | none |

For the European address, OpenRouter [writes](https://openrouter.ai/docs/guides/features/in-region-routing):
"There is no setting to turn on: once your account is on one of these plans, you choose the region
for each request by sending it to that region's base URL." Even there, only prompts and answers stay
in Europe. OpenRouter [writes](https://openrouter.ai/docs/guides/features/sovereign-ai): "Account,
billing, and other operational records may be stored or processed in the US." OpenRouter, Inc. is a
New York company, and the EU-only addendum of its data processing agreement applies only if chosen
in writing.

**What was measured.** On 2026-11-01, on an ordinary account with no Business plan, one tiny real
request to `openrouter.ai`, model Mistral Small, naming `mistral/eu` alone, got HTTP 200, and
OpenRouter named Mistral as the company. A request to `eu.openrouter.ai` answered 403 with
`error code: 1010`, which does not say why. The same day, a real run through
`workshop-login --europe` covered OpenCode in modes C and D (4 questions), `score`,
`./sorter compare` and Open WebUI in kit mode (2 questions). 60 requests were answered. All 60
carried the rule, and OpenRouter named Mistral as the company on all 60. The sorter got 32 of 32
right, with no emergency missed. The whole run cost $0.0065. DeepSeek v4 Flash, which has no such
company, was refused. The replies named Mistral, and no region. The place comes from OpenRouter's
list: no call and no independent proof confirmed where a model runs.

**What changes when it is on:**

- **The model.** You move to `mistralai/mistral-small-3.2-24b-instruct`. Without young people, `--model`
  can name another model. If that one has no such company, the command says so.
- **The window** (how much the model can read at once). Mistral Small has 32k tokens at `mistral/eu`,
  against 128k to 256k at the three other companies, none listed in Europe. OpenRouter's list of
  models says 256,000 for this model, so `--europe` saves the size from the list of its companies.
  A class-mode chatbot with a long conversation in this window: (not tested).
- **Mode B.** Mode B sends the whole kit at once. That is about 100k tokens on Claude's gauge, and
  no count exists for Mistral. In the real run, OpenCode failed before the model's first word. The
  commands refuse mode B for any model with too small a window, with `--europe` or without it:

  ```text
  Mode B sends the whole kit at once, and this model reads 32,768 tokens at most.
  This mode cannot run with it. Skip mode B and go on with the next part of today's page.
  ```

  So with Mistral Small, skip mode B: the pages of workshops 2 and 3 say what to do. A European model
  with a larger window would pass this check, but none was tried in mode B (not tested).
- **The scores.** Our runs were not pinned to `mistral/eu`, so its scores in
  [Part 6](#part-6---the-models-on-2026-11-01) are not scores in Europe.
- **The judge.** The usual judge has no company in Europe, so `score` uses Mistral Small, unless
  `WORKSHOP_JUDGE_MODEL` names another model. It gave the same note as `claude-haiku-5-5` on 135 of
  181 notes (75 %), against 150 of 180 (83 %) for the usual judge.
- **The cost shown.** The saved price comes from OpenRouter's list of models. Mistral Small costs
  $0.10/$0.30 per million tokens (in/out) at `mistral/eu`, against $0.075/$0.20 at the cheapest
  company, so OpenCode can show too low a cost.
- **What is already running keeps the old rule.** OpenCode and Open WebUI read the rule when they
  start. The command prints a line if one of them is running: close the chatbot and start it again,
  or type `openwebui start`. A `replay` stops by itself before its next question, but the question
  in progress finishes under the old rule. So turn it on first, then start the rest.

It stays with your later logins. `workshop-login --no-europe` removes it, and so does a key of
another provider.

**The other models of Part 6:**

- **`deepseek/deepseek-v4-flash`, the default:** OpenRouter lists no company running it in Europe.
  Of its 17 companies, 12 are ZDR. 5 keep the questions, for a time OpenRouter does not give:
  StreamLake, Baidu, GMICloud, AtlasCloud and Alibaba.
- **`google/gemini-2.5-flash-lite`:** OpenRouter lists no company running it in Europe, and none
  under ZDR.

OpenRouter's European list has a fifth company, Inceptron. `--europe` leaves it out: its tags do not
say Europe ([Part 9](#notes-on-the-measures)).

### Optional: the same rule for the whole account

You do not need this step. `workshop-login --europe` already asks for ZDR in each request of the kit.
These settings hold ZDR for the whole account, whatever tool uses the key. Nothing in this guide was
run with them on.

1. As the account holder, open the [privacy settings](https://openrouter.ai/settings/privacy).
2. Turn on the ZDR toggle of each model group: **Anthropic**, **OpenAI**, **Google**, **SpaceXAI**
   and **All other models**. DeepSeek and Mistral are not in the first four. "Enabling a scope
   restricts all your requests to ZDR endpoints for that model group."
3. Choose **Zero retention only**. Without a choice, an ordinary account stays on **Safety retention
   allowed**: Google may then keep questions that its automatic filters flag, for up to 90 days.
   OpenRouter warns that with **Zero retention only**, "Most Google models become unavailable."
4. Do not opt in to the two options that keep your data: **Private Input & Output Logging**, and
   **OpenRouter Use of Inputs/Outputs** (a 1 % discount). OpenRouter stores your prompts only if you
   opt in, or if they are flagged as potential child abuse material. Section 6.2 of the terms
   attaches a licence to prompt logging that includes the right to "license or sell your User
   Content in anonymized form".
5. In the Codespace, type `workshop-login` and press Enter alone. You must see `Key OK`: a company
   can serve the model, and the line does not say which one. If you see
   `no company can serve the model`, choose another model.

### What each company's terms say

These are each company's own terms for the product named. A route through OpenRouter can differ:
its pages declare a policy for each route, and its agreements with these companies are not public.

| Company and product | Minors | Training | Retention | Place |
|---|---|---|---|---|
| **DeepSeek**, its own services | "primarily intended for adults"; under 18 with a guardian's consent; no chatbot "designed to specifically appeal to or present a persona of any person under the age of 18" | may use inputs and outputs, de-identified; OpenRouter lists the direct route as training | as long as the account exists, no number of days | China |
| **Mistral**, API and Studio | no personal information of children under 13 or the age of digital consent; minors need "legally adequate consent from their parent or guardian" | no, unless you agree to it; feedback, an order form, and Labs or Preview models are exceptions | 30 rolling days, unless ZDR; OpenRouter lists no retention on `mistral/eu` | EU by default; temporary transfers possible, depending on the feature |
| **Google**, Gemini API and AI Studio | 18 or older, and see below | paid services: no; in the EEA, Switzerland and the UK, the same rules for free services | 55 days | "any country in which Google or its agents maintain facilities" |
| **Google**, Vertex | see below | not without the customer's permission | flagged prompts, up to 90 days | the `eu` address stays in EU member states |
| **Cohere**, free model of Part 6 | "not intended to be used by minors (children)"; its usage policy asks an application used by minors for added safety controls | trial keys: may be used for research and development | 30 days, unless flagged | Google Cloud, US-Central, in an undated FAQ |

The default model does not reach DeepSeek itself. OpenRouter lists 17 other companies for it:

- under ZDR: Relace, DeepInfra, Venice, DigitalOcean, Fireworks, SiliconFlow, Crusoe, Parasail,
  Mancer 2, Azure (in the US), Cloudflare and Wafer;
- keeping the questions: StreamLake, Baidu, GMICloud, AtlasCloud and Alibaba.

**The terms of these 17 companies were not read.** So the default route is for adults only, with invented or public questions.

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
5. **Mistral's clause on minors.** Mistral is the company of the route for young people. Its
   [commercial terms](https://legal.mistral.ai/terms/commercial-terms-of-service/) forbid you to
   "include any personal information of children under 13 or the applicable age of digital consent
   as Customer Data or allow minors to use the Mistral AI Products without legally adequate consent
   from their parent or guardian". The young people of this project are 12 to 15, so this applies to
   them directly. As we read it: no personal information of a child under the age of digital consent
   goes in the chatbot, and you get written parental consent before any minor uses it. Whether this
   text reaches a customer of OpenRouter is not established: follow it anyway.

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
  [list of ZDR endpoints](https://openrouter.ai/api/v1/endpoints/zdr), and the same
  [list for Europe](https://eu.openrouter.ai/api/v1/endpoints/zdr).
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
  `replay RAG` 11 answers in 44 s, 0 ERROR, nothing in the error log;
- the cap of 8,192 tokens, on a fake OpenRouter and in the run with credits;
- Open WebUI in class mode, on a fake OpenRouter, without `--europe`: it starts, it prints the warning, and the rule
  `data_collection: deny` reaches the fake OpenRouter;
- `workshop-login --europe`, on a fake OpenRouter: the routing in every request of `workshop` and
  `replay`, the window of 32k, and a change of rule during a `replay`;
- on an ordinary account, one tiny request to `openrouter.ai` with the same routing, `mistral/eu`
  alone: HTTP 200, answered by Mistral. A request to `eu.openrouter.ai` answered 403 with
  `error code: 1010`;
- a real run through `workshop-login --europe` on 2026-11-01, with a logging relay: 60 answered
  requests carried the rule and named Mistral (OpenCode, `score`, `./sorter compare`, Open WebUI in
  kit mode), and DeepSeek v4 Flash was refused. The refusal of mode B before any request was tested
  on a fake OpenRouter only.

The image number that carries these commands: TO BE COMPLETED.

### Notes on the measures

- `Free requests left today` went from 935 to 873 around the `replay C` of `north-mini-code`. That
  count includes one or two tests of `workshop-login`, hence 60 to 62 requests.
- Earlier in the day, the same counter showed no use for several models. The cause is not
  established.
- On 2026-11-01, OpenRouter's public [list for Europe](https://eu.openrouter.ai/api/v1/endpoints/zdr)
  showed 87 ZDR endpoints for 76 models. 77 of these endpoints, for 66 models, can use tools. They
  come from five companies: Mistral, Azure, Amazon Bedrock, Google Vertex and Inceptron.
- `--europe` names `mistral/eu` alone: the terms of Mistral are the ones read for this route. So it
  refuses a model served in Europe by another company, such as `deepseek/deepseek-v4-flash-0731`
  at Inceptron: (not tested).
- Prices and windows of the model table come from OpenRouter's list on 2026-11-01. The price of
  DeepSeek v4 Flash was printed with two decimals, hence "about".

### What was not tested

- A group. A real Codespace.
- The screens of OpenRouter's website in Parts 2, 3 and 8. No person has followed them with this
  guide, which has no screenshots. Most names come from OpenRouter's documentation. **Create API
  Key** and **Key limit** do not: check them on the screen.
- Giving keys to pairs, deleting a key.
- `google/gemma-4-26b-a4b-it:free` at another moment: its 429 came from the company that runs it.
- The same scores replayed several times, to know how far a score moves.
- A small real balance, a real 429 in a session, a real key limit, auto top-up.
- Open WebUI in class mode with a real OpenRouter key, and Open WebUI with the default DeepSeek
  model.
- The ZDR settings, **Zero retention only**, `eu.openrouter.ai` with the Business plan.
- A whole session after `workshop-login --europe` with a real key, and the four other European
  endpoints.
- Class mode with `--europe` (real or fake), and a class-mode chatbot in a 32k window.
- Mode B with a European model of a larger window, and a workshop 2 that skips mode B with a group.
- A question typed in an OpenCode screen opened before the rule changed. The line that warns of it
  was seen, on a fake OpenRouter.
- A human reading of a sample of the scores.
- The cost of a full session.

---

## About

Part of the Youth AI Lab project (Erasmus+). Texts: CC BY-SA 4.0. Configuration files: EUPL-1.2. See
`REUSE.toml` and `LICENSES/`. OpenRouter, DeepSeek, Mistral, Google and Cohere are the names of
their owners, who have no link with this guide.
