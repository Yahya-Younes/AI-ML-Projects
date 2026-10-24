# AI-103 · Developing AI Apps and Agents on Azure — from zero to certified

> **Who this is for:** developers who want to build generative-AI apps, RAG systems and agents on Microsoft Foundry.
> **Time budget:** **~55 hours** over 5 weeks (≈ 2 h on weekdays + 5 h on weekends), or **~70 h** if you are new to Python or Azure.
> **Main tools in this folder:**
> - 🎯 [`AI-103-trainer.html`](AI-103-trainer.html) — **190 exam-style questions** with explanations, 4 case studies, domain drills, weak-skill tracking and a timed **50-question exam simulation** scored out of 1000.
> - 📄 [`cheatsheet.md`](cheatsheet.md) — one page per domain: "if the scenario says X, choose Y".

| Exam fact | Value |
|---|---|
| Certification | Microsoft Certified: **Azure AI Apps and Agents Developer Associate** |
| Duration | 120 minutes |
| Passing score | 700 / 1000 |
| Question types | Single and multiple choice, drop-down code completion, yes/no statements, ordering, **case studies** |
| Language of the code | Python (Foundry SDK, OpenAI SDK, Agent Framework) |
| Replaces | **AI-102** (Azure AI Engineer Associate), retired 30 June 2026 — AI-103 is centred on Microsoft Foundry, RAG and agents rather than individual AI services |
| Validity | 1 year; **free online renewal assessment** on Microsoft Learn every year |
| Official page | [AI-103 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ai-103) — skills measured as of 16 April 2026 |

## Before you start: are you a beginner?

| Your background | Do this first |
|---|---|
| Never used Azure | [AZ-900 guide](../AZ-900/) (~18 h) — subscriptions, identity, networking basics are assumed by AI-103 |
| Never studied AI concepts | [AI-900 guide](../AI-900/) (~16 h) — ML, vision, NLP and generative-AI vocabulary |
| Never written Python | 10 h of Python basics (functions, dicts, JSON, `pip`, virtual environments) |
| Comfortable with all three | Start below ⬇️ |

---

## The five domains

| # | Domain | Weight | Hours in the plan | What it really tests |
|---|---|---|---|---|
| 1 | Plan and manage an Azure AI solution | 25–30% | ~10 h | Choosing models & deployment types, quotas/429s, keyless security & RBAC, networking, CI/CD, monitoring, responsible AI |
| 2 | Implement generative AI and agentic solutions | 30–35% | ~16 h | Chat apps, Responses API, structured outputs, RAG, agents & tools (MCP, A2A, file search, code interpreter), multi-agent orchestration, evaluation, tracing |
| 3 | Implement computer vision solutions | 10–15% | ~2.5 h | Image generation/editing, video generation, multimodal understanding, Content Understanding, vision safety |
| 4 | Implement text analysis solutions | 10–15% | ~5 h | Azure Language, translation, speech, Voice Live, audio reasoning |
| 5 | Implement information extraction solutions | 10–15% | ~3.5 h | Azure AI Search ingestion, skillsets, hybrid/semantic search, Document Intelligence, Content Understanding, Foundry IQ |
| — | Practice: trainer drills, 3 practice gates, 2 exam simulations, reviews | — | ~18 h | |

> 💡 **Where the points are:** Domains 1 + 2 are **~60% of the exam**. If you are short on time, cut vision/speech videos, never cut agents, RAG, security or evaluation.

---

## The 5-week plan (~55 h)

Every study block follows the same loop, which is what makes the hours count:
**watch or read → do the lab (or read it carefully) → answer 5 trainer questions on that topic → log every miss.**

### Week 1 — Foundations (Domain 1) · ~10 h

| Block | Hours | Activity |
|---|---|---|
| 1 | 1 h | **Baseline:** run one exam simulation in the trainer with no notes. Write the score down — you'll compare later. Read the official skills outline once. |
| 2 | 1 h | Create a free Azure subscription and a Foundry project at [ai.azure.com](https://ai.azure.com). Deploy one chat model. |
| 3 | 2 h | Learn **deployment types** (Global/Data Zone/Regional × Standard/Provisioned/Batch, Developer) and **quotas** (TPM/RPM, 429 handling, retries, `max_tokens` trap). Docs: [Deployment types](https://learn.microsoft.com/en-us/azure/foundry/foundry-models/concepts/deployment-types), [Manage quota](https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/quota). |
| 4 | 2 h | **Security:** managed identity, `DefaultAzureCredential`, Foundry RBAC roles (User, Project Manager, Account Owner, Agent Consumer), `disableLocalAuth`, private endpoints + private DNS. Module: [Secure Microsoft Foundry environments](https://learn.microsoft.com/en-us/training/modules/azure-ai-foundry-secure-environment/). |
| 5 | 1 h | **CI/CD and evaluation gates** with GitHub Actions. Module: [Automate AI evaluations](https://learn.microsoft.com/en-us/training/modules/automated-evaluation-genaiops/). |
| 6 | 1.5 h | **Responsible AI:** content filters & severity, Prompt Shields (user vs document attacks), groundedness detection, blocklists, AI Red Teaming Agent. |
| 7 | 1.5 h | Trainer → **Domain 1** card. Read every explanation, even when you were right. |

### Week 2 — Generative apps and RAG (Domain 2, part 1) · ~9 h

| Block | Hours | Activity |
|---|---|---|
| 1 | 2 h | Lab: [Create a generative AI chat app](https://microsoftlearning.github.io/mslearn-ai-studio/Instructions/Exercises/03-foundry-sdk.html) — Chat Completions vs Responses API, keyless auth, conversation state, streaming, async. |
| 2 | 1 h | Lab: [Explore and compare models](https://microsoftlearning.github.io/mslearn-ai-studio/Instructions/Exercises/02-model-catalog-evaluation.html) — benchmarks and model evaluation. |
| 3 | 1.5 h | Structured outputs (`json_schema` + `strict`), function calling, prompt caching, reasoning models (`reasoning_effort`, `max_completion_tokens`), model router. |
| 4 | 2 h | **RAG end to end:** chunking, embeddings, vector/hybrid search, semantic ranker. Docs: [RAG overview](https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview), [Hybrid search](https://learn.microsoft.com/en-us/azure/search/hybrid-search-overview). |
| 5 | 1 h | Evaluation: Groundedness vs Relevance vs Retrieval vs Response Completeness; Groundedness Pro; cloud evaluations. Page: [Built-in evaluators](https://learn.microsoft.com/en-us/azure/foundry/concepts/built-in-evaluators). |
| 6 | 1.5 h | Trainer → **Domain 2** card (first pass). |

### Week 3 — Agents (Domain 2, part 2) · ~12 h

| Block | Hours | Activity |
|---|---|---|
| 1 | 1.5 h | Lab: [Build AI agents with the portal and VS Code](https://microsoftlearning.github.io/mslearn-ai-agents/Instructions/Exercises/01-build-agent-portal-and-vscode.html) |
| 2 | 1.5 h | Lab: [Use a custom function in an AI agent](https://microsoftlearning.github.io/mslearn-ai-agents/Instructions/Exercises/02-agent-custom-tools.html) |
| 3 | 1.5 h | Lab: [Extend agents with MCP tools](https://microsoftlearning.github.io/mslearn-ai-agents/Instructions/Exercises/03-mcp-integration.html) — `allowed_tools`, `require_approval`, `mcp_approval_request` |
| 4 | 1.5 h | Lab: [Integrate an agent with Foundry IQ](https://microsoftlearning.github.io/mslearn-ai-agents/Instructions/Exercises/04-integrate-agent-with-foundry-iq.html) — permission-aware knowledge bases |
| 5 | 1 h | Built-in tools: file search, code interpreter, web/Bing grounding (and its compliance boundary!), computer use vs browser automation, A2A, memory, standard vs basic agent setup. |
| 6 | 2 h | Labs: [Workflows](https://microsoftlearning.github.io/mslearn-ai-agents/Instructions/Exercises/06-build-workflow-ms-foundry.html), [Agent Framework](https://microsoftlearning.github.io/mslearn-ai-agents/Instructions/Exercises/07-agent-framework.html), [Multi-agent](https://microsoftlearning.github.io/mslearn-ai-agents/Instructions/Exercises/08-agent-framework-multi-agents.html) — sequential, concurrent, handoff, group chat, Magentic. |
| 7 | 1.5 h | Labs: [Trace your agent](https://microsoftlearning.github.io/mslearn-ai-agents/Instructions/Consolidated/D1-trace-your-agent.html), [Evaluate answer quality](https://microsoftlearning.github.io/mslearn-ai-agents/Instructions/Consolidated/D2-evaluate-answer-quality.html), [Red team your agent](https://microsoftlearning.github.io/mslearn-ai-agents/Instructions/Consolidated/D3-red-team-your-agent.html). |
| 8 | 1.5 h | Trainer → **New questions (set 2)** filtered by Domain 2 + **Retry missed**. |

> 🧪 **No GPU quota for agent labs?** New subscriptions sometimes have 0 quota for the newest models. Request a quota increase early (it's free), and in the meantime read the lab steps carefully and answer the trainer's questions on that topic.

### Week 4 — Vision, language, speech, extraction (Domains 3–5) · ~11 h

| Block | Hours | Activity |
|---|---|---|
| 1 | 2 h | **Knowledge mining:** indexers, skillsets, index projections, integrated vectorization, custom Web API skills, deletion detection, debug sessions. |
| 2 | 1.5 h | **Document Intelligence** (prebuilt vs custom template vs custom neural, classifiers, composed models, query fields) and **Content Understanding** (analyzers, field methods extract/classify/generate, prebuilt RAG analyzers). |
| 3 | 2.5 h | **Language & speech:** NER, PII redaction policies, Text Analytics for health, summarization, opinion mining, translation (sync vs batch document translation, Custom Translator), speech to text, SSML, custom speech, speech translation, **Voice Live**. |
| 4 | 2 h | **Vision:** image generation & editing (masks, reference images, `input_fidelity`), Sora video jobs & remix, vision chat (`detail: low/high`), Image Analysis 4.0, Content Safety for images, alt-text guidance. |
| 5 | 3 h | Trainer → **Domain 3, 4, 5** cards (unanswered first), including the Litware case study. |

> 🎬 **Video option:** the official *"AI-103: Develop AI apps and agents on Azure"* series on the Microsoft YouTube channels (a course preview + 26 episodes, roughly one per module). Watch at 1.25–1.5× and pause to do the matching lab.

### Week 5 — Exam mode · ~13 h

| Block | Hours | Activity | Go / no-go |
|---|---|---|---|
| 1 | 1.5 h | **Gate 1:** official Microsoft practice assessment (free, on the certification page) | ≥ 65% → continue; below → spend block 3 on your two weakest domains |
| 2 | 2 h | Trainer **exam simulation #1** in exam conditions (phone away, 100 min) | — |
| 3 | 2 h | Review every miss: explanation + Microsoft Learn link. Write each lesson as one line in your own cheatsheet. | — |
| 4 | 1.5 h | Trainer → **Weak skills** until every domain card is green | all domains ≥ 80% |
| 5 | 1.5 h | **Gate 2:** official practice assessment again | ≥ 75% |
| 6 | 2 h | Trainer **exam simulation #2** | **≥ 800 / 1000** |
| 7 | 1.5 h | **Gate 3:** official practice assessment + Retry missed | ≥ 85% → you're ready; below 75% or simulation < 700 → move the exam (free if > 24 h before) |
| 8 | 1 h | Day before: [cheatsheet](cheatsheet.md) only. No new material. Prepare ID and a quiet room (online proctoring), sleep early. | — |

### Rules that make the plan work

- **Never skip two days in a row.** A missed block moves to the next weekend, not onto tomorrow.
- **Log every wrong answer the same day.** One line: *"constraint word → right service"*.
- **From the last week on, no new material**: only the trainer, your notes and the cheatsheet.
- **You are ready when** the exam simulation is ≥ 800 *and* every domain card is green — not when you "feel" ready.

---

## How to use the trainer

1. Download [`AI-103-trainer.html`](AI-103-trainer.html) (click it, then the **Download raw file** button) and double-click it. It runs entirely in your browser: no account, no install, no tracking. Progress is saved in your browser only.
2. Click a **domain card** to practice with instant feedback, or **Exam simulation** for a timed, weighted 50-question exam.
3. Every answer shows **why** each option is right or wrong, and the **Microsoft Learn** page to read.

---

## All the official resources

| Resource | Link | Why use it |
|---|---|---|
| Certification page (schedule, free practice assessment, renewal) | [Azure AI Apps and Agents Developer Associate](https://learn.microsoft.com/en-us/credentials/certifications/azure-ai-apps-and-agents-developer-associate/) | The official practice assessment is the "gate" in Week 5 |
| Study guide (skills measured + change log) | [AI-103 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ai-103) | Every line of it is covered by at least one trainer question |
| Official labs — Foundry & generative AI | [MicrosoftLearning/mslearn-ai-studio](https://github.com/MicrosoftLearning/mslearn-ai-studio) | Chat apps, model catalog, evaluation |
| Official labs — agents | [MicrosoftLearning/mslearn-ai-agents](https://github.com/MicrosoftLearning/mslearn-ai-agents) | Agents, tools, MCP, Foundry IQ, workflows, multi-agent, tracing, red teaming |
| Official labs — vision, language, extraction | [mslearn-ai-vision](https://github.com/MicrosoftLearning/mslearn-ai-vision) · [mslearn-ai-language](https://github.com/MicrosoftLearning/mslearn-ai-language) · [mslearn-ai-information-extraction](https://github.com/MicrosoftLearning/mslearn-ai-information-extraction) | Domains 3–5 hands-on |
| Microsoft Foundry docs | [Foundry documentation](https://learn.microsoft.com/en-us/azure/foundry/) | Where every trainer explanation links to |
| Microsoft Agent Framework docs | [Agent Framework](https://learn.microsoft.com/en-us/agent-framework/) | Orchestration patterns (sequential, handoff, group chat, Magentic) |
| Azure AI Search docs | [Azure AI Search](https://learn.microsoft.com/en-us/azure/search/) | RAG, indexers, skillsets, hybrid & semantic search |
| Exam sandbox | [aka.ms/examdemo](https://aka.ms/examdemo) | Practice the case-study and drop-down interfaces |
| Exam duration and experience | [Exam duration](https://learn.microsoft.com/en-us/credentials/support/exam-duration-exam-experience) | Timing, accommodations, online proctoring rules |
| Foundry portal | [ai.azure.com](https://ai.azure.com) | Where you run every lab |

---

<sub>Unofficial study material written from the public AI-103 study guide and Microsoft Learn documentation. Not affiliated with or endorsed by Microsoft; the practice questions are original and are not real exam content. Azure changes quickly: when an explanation and Microsoft Learn disagree, trust Microsoft Learn — and please open an issue so it can be fixed.</sub>
