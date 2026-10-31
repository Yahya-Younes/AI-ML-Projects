# Google Cloud Generative AI Leader — from zero to certified

> **Who this is for:** managers, consultants, product owners and engineers who must *lead* generative-AI adoption. **No coding.**
> **Time budget:** **~15 hours** over 2 weeks.
> **Interactive practice:** [**▶️ Open the GenAI Leader trainer in your browser**](https://yahya-younes.github.io/ai-cloud-certification-hub/google-cloud/generative-ai-leader/GenAI-Leader-trainer.html) (or download [`GenAI-Leader-trainer.html`](GenAI-Leader-trainer.html) to use it offline).

| Exam fact | Value |
|---|---|
| Format | 50–60 multiple-choice / multiple-select questions |
| Duration | 90 minutes |
| Price | US $99 (plus tax) |
| Validity | 3 years |
| Delivery | Online-proctored or at a test center |
| Languages | English, Japanese |
| Prerequisites | None |
| Official page | [Generative AI Leader certification](https://cloud.google.com/learn/certification/generative-ai-leader) · [Official exam guide (PDF)](https://services.google.com/fh/files/misc/generative_ai_leader_exam_guide_english.pdf) |

> ℹ️ **Product names move fast at Google.** Example: *Agentspace* became part of **Gemini Enterprise**. The exam tests *which kind of tool solves which business problem*; this guide gives the current name and the older one where it changed. Check the official exam guide before your exam.

## The four sections

| # | Section | Weight | Hours |
|---|---|---|---|
| 1 | Fundamentals of generative AI | ~30% | 4 h |
| 2 | Google Cloud's generative AI offerings | ~35% | 5 h |
| 3 | Techniques to improve generative AI model output | ~20% | 2.5 h |
| 4 | Business strategies for a successful generative AI solution | ~15% | 1.5 h |
| — | Trainer drills, exam simulation, review | — | 2 h |

## Study plan (15 hours)

| Day | Hours | Do | Done when you can… |
|---|---|---|---|
| 1 | 2 h | §1.1–1.3 | place AI, ML, deep learning, gen AI and foundation models in one diagram |
| 2 | 2 h | §1.4–1.5 + trainer Section 1 | explain data quality, the ML lifecycle and model limitations |
| 3 | 2.5 h | §2.1–2.3 | pick the right Google product for a business need |
| 4 | 2.5 h | §2.4–2.5 + trainer Section 2 | explain Vertex AI's building blocks and Google's AI infrastructure |
| 5 | 2.5 h | §3 + trainer Section 3 | choose between prompting, grounding, RAG and fine-tuning |
| 6 | 1.5 h | §4 + trainer Section 4 | apply Google's AI Principles and SAIF to a scenario |
| 7 | 2 h | **Exam simulation** + review every miss + Google's official sample questions | 800+ in the simulation |

---

## 1. Fundamentals of generative AI (~30%)

### 1.1 The family tree

```
Artificial intelligence   — machines that mimic human intelligence
└── Machine learning      — systems learn patterns from data instead of explicit rules
    └── Deep learning     — ML with multi-layer neural networks
        └── Generative AI — deep learning that CREATES new content (text, images, code, audio, video)
            └── Foundation models — huge models pre-trained on broad data, adaptable to many tasks
                └── Large language models (LLMs) — foundation models specialized in language
```

- **Discriminative / predictive AI** classifies or predicts (*is this spam?*). **Generative AI** produces new content (*write a reply*).
- **Multimodal model** = understands and/or generates several data types (text, images, audio, video) — e.g. **Gemini**.
- **Prompt** = the input you give the model. **Token** = a chunk of text the model processes; limits and prices are counted in tokens. **Context window** = how many tokens a model can consider at once.

### 1.2 How models learn

| Approach | Data | Example |
|---|---|---|
| **Supervised learning** | Labeled examples | Predict churn from customers labeled churned / stayed |
| **Unsupervised learning** | No labels | Group customers into segments |
| **Reinforcement learning** | Rewards for actions | Optimize a robot's or an agent's decisions |
| **Self-supervised pre-training** | Raw text/images (the data provides its own labels, e.g. "next word") | How foundation models are trained |

### 1.3 Data — "garbage in, garbage out"

- **Structured** data: tables, rows and columns (databases, spreadsheets). **Unstructured**: text, images, audio, video — most enterprise data, and where gen AI shines.
- **Labeled vs unlabeled** data: labels cost time and money; foundation models reduce the need for them.
- **Data quality dimensions:** accuracy, completeness, consistency, relevance, timeliness, availability. Poor data → poor and biased outputs.

### 1.4 The ML lifecycle (and the Google tool at each step)

| Stage | What happens | Google Cloud examples |
|---|---|---|
| Data ingestion & preparation | Collect, clean, label, store | BigQuery, Cloud Storage, Dataflow |
| Model training / selection | Train, or pick a foundation model | Vertex AI (AutoML, custom training), Model Garden |
| Deployment | Serve the model | Vertex AI endpoints |
| Management & monitoring | Track drift, performance, cost | Vertex AI Model Monitoring, Model Registry |

### 1.5 Limitations you must be able to name

| Limitation | What it means | Mitigation |
|---|---|---|
| **Hallucination** | Confident but false output | Grounding, RAG, citations, human review |
| **Knowledge cutoff** | Model doesn't know recent events | Grounding with Google Search or your data |
| **Bias** | Unfair outputs inherited from training data | Diverse data, evaluation, human oversight |
| **Edge cases / ambiguity** | Unpredictable on unusual inputs | Testing, guardrails, clear prompts |
| **Data dependency** | Quality depends on input data | Data governance |

---

## 2. Google Cloud's generative AI offerings (~35%)

Think of it as **layers**, from ready-made to build-your-own:

```
Ready-to-use apps        Gemini app · Gemini for Google Workspace · NotebookLM
Enterprise AI workspace  Gemini Enterprise (formerly Agentspace): search, assistants & agents over company data
Build your own           Vertex AI: Model Garden · Vertex AI Studio · Agent Builder / Agent Engine · Vertex AI Search
Models                   Gemini (multimodal) · Imagen (images) · Veo (video) · Chirp (speech) · Gemma (open models)
Infrastructure           Google Cloud AI-optimized infrastructure: TPUs and GPUs
```

### 2.1 Ready-to-use products

| Product | Pick it when… |
|---|---|
| **Gemini app** | Individuals need a general AI assistant |
| **Gemini for Google Workspace** | Help writing in Docs/Gmail, summarizing in Meet, analyzing in Sheets — **inside the tools people already use** |
| **NotebookLM** | Research assistant **grounded only in the sources you upload** (summaries, Q&A, audio overviews) |
| **Gemini Enterprise** (formerly Agentspace) | Employees search and ask questions across **company data** (Drive, SharePoint, Jira…) and use or build **agents**, with enterprise security |

### 2.2 Vertex AI — Google Cloud's AI platform

| Component | Purpose |
|---|---|
| **Model Garden** | Catalog of Google, partner and open models (Gemini, Gemma, Llama, Mistral, …) to discover and deploy |
| **Vertex AI Studio** | Test and tune prompts and models in a UI |
| **AutoML** | Train custom models on your data without ML expertise |
| **Agent Builder / Agent Engine** | Build, deploy and manage agents (with tools, memory, grounding) |
| **Vertex AI Search** | Google-quality search and **RAG** over your enterprise data, out of the box |
| **Model Registry, Pipelines, Model Monitoring** | MLOps: version, automate and watch models |

### 2.3 Agents

An **agent** = model + instructions + **tools** + reasoning loop, acting toward a goal (e.g. *process a refund*). Types to recognize:

- **Conversational agents** (customer service — the *Customer Engagement Suite*),
- **Workflow / task agents** (automate multi-step processes),
- **Information / research agents** (find and synthesize knowledge).

Agents use **tools** such as extensions, functions, data stores and APIs. **Reasoning frameworks** like **ReAct** (reason + act) let them plan, call a tool, observe and repeat.

### 2.4 Google's models

| Model | For |
|---|---|
| **Gemini** | Multimodal reasoning over text, images, audio, video and code; long context |
| **Gemma** | Lightweight **open** models you can run yourself |
| **Imagen** | Image generation and editing |
| **Veo** | Video generation |
| **Chirp** | Speech recognition |

### 2.5 Infrastructure, security and responsibility

- **TPUs (Tensor Processing Units)** — Google's custom AI chips, used to train and serve Gemini; available on Google Cloud.
- **Secure AI Framework (SAIF)** — Google's framework for securing AI systems (secure foundations, detection & response, automated defenses, risk context).
- **Your data is not used to train Google's foundation models** when you use Google Cloud enterprise AI services — a common exam point about data privacy and governance.

---

## 3. Techniques to improve model output (~20%)

### 3.1 Prompt engineering

| Technique | What it is |
|---|---|
| **Zero-shot** | Just ask, no examples |
| **One-shot / few-shot** | Give one or a few examples of the desired output |
| **Role prompting** | "You are an experienced tax advisor…" |
| **Chain-of-thought** | Ask the model to reason step by step |
| **ReAct** | Reason, act with a tool, observe, repeat (agents) |
| **Prompt chaining** | Split a complex task into a sequence of prompts |

### 3.2 Sampling parameters

| Parameter | Effect |
|---|---|
| **Temperature** | Low = focused and repeatable; high = creative and varied |
| **Top-K** | Choose the next token among the K most likely |
| **Top-P** (nucleus) | Choose among tokens whose cumulative probability reaches P |
| **Output length (max tokens)** | Caps the response length (and cost) |
| **Safety settings** | Block harmful content categories at chosen thresholds |

### 3.3 Grounding, RAG or fine-tuning? — the decision every exam asks

| Need | Choose |
|---|---|
| Answers about **recent public events** | **Grounding with Google Search** |
| Answers from **company documents**, with citations | **RAG / grounding on enterprise data** (Vertex AI Search, RAG Engine) |
| A **consistent style, format or specialized behavior** the prompt can't achieve | **Fine-tuning** (supervised tuning) |
| Quick improvement, no data | **Better prompts** (few-shot, role, structure) |
| Correct facts that change often | **RAG**, *not* fine-tuning (fine-tuning bakes in a snapshot) |

**Human in the loop (HITL)** — keep people reviewing high-stakes outputs (medical, legal, financial). It's the go-to answer when "accuracy is critical".

---

## 4. Business strategies for a successful solution (~15%)

### 4.1 Pick the right use case

Good first gen-AI use cases are **high value, low risk, data available, measurable**: summarizing documents, drafting content, internal search, customer-service assistance.
Decide **build vs buy**: use a ready product (Workspace, Gemini Enterprise) when the need is common; build on **Vertex AI** when you need customization or integration.

### 4.2 Make adoption succeed

- Executive sponsorship, a clear **business goal and KPIs** (time saved, resolution rate, revenue, CSAT).
- **Change management**: training, champions, communication — people adoption is the #1 blocker.
- Start with a **pilot**, measure, then scale.

### 4.3 Responsible AI — Google's AI Principles

Google's AI Principles (updated in 2025) are organized around **bold innovation**, **responsible development and deployment**, and **collaborative progress**. The original 2018 version listed objectives that are still the vocabulary of most questions: be socially beneficial, avoid creating or reinforcing unfair bias, be built and tested for safety, be accountable to people, incorporate privacy design principles, uphold high standards of scientific excellence. In practice, the exam expects you to:

- check **fairness and bias**, **privacy** (data protection, consent), **security** (SAIF),
- ensure **transparency** and **explainability** where decisions affect people,
- keep **human oversight** and **accountability**.

---

## 5. One-page cheatsheet

| If the question says… | The answer is usually… |
|---|---|
| "help employees write emails and documents in tools they already use" | **Gemini for Google Workspace** |
| "research assistant grounded only in my uploaded sources" | **NotebookLM** |
| "employees search and use agents across all company data" | **Gemini Enterprise** (formerly Agentspace) |
| "choose and deploy a foundation model, including open models" | **Vertex AI Model Garden** |
| "experiment with prompts and tune a model in a UI" | **Vertex AI Studio** |
| "custom model on our data without ML expertise" | **AutoML** |
| "build and deploy an agent with tools" | **Vertex AI Agent Builder / Agent Engine** |
| "search and RAG over our documents out of the box" | **Vertex AI Search** |
| "lightweight open model to run ourselves" | **Gemma** |
| "custom chips to train and serve AI" | **TPUs** |
| "recent events / knowledge cutoff" | **Grounding with Google Search** |
| "answers from internal documents with citations" | **RAG / grounding on enterprise data** |
| "consistent brand voice or format" | **Fine-tuning** |
| "more creative output" | **Raise temperature** |
| "confident but false answer" | **Hallucination** → grounding + human review |
| "accuracy is critical (medical, legal)" | **Human in the loop** |
| "framework to secure AI systems" | **SAIF** |
| "content created by AI vs. predicting a label" | **Generative vs discriminative/predictive AI** |

## 6. All the official resources

| Resource | Link |
|---|---|
| Certification page (register, sample questions) | [cloud.google.com/learn/certification/generative-ai-leader](https://cloud.google.com/learn/certification/generative-ai-leader) |
| Official exam guide (PDF) | [Generative AI Leader exam guide](https://services.google.com/fh/files/misc/generative_ai_leader_exam_guide_english.pdf) |
| Free learning path | **"Generative AI Leader"** learning path on [Google Cloud Skills Boost](https://www.cloudskillsboost.google/) (5 short courses that mirror the exam sections) |
| Google's AI Principles | [ai.google/responsibility/principles](https://ai.google/responsibility/principles/) |
| Secure AI Framework (SAIF) | [safety.google/cybersecurity-advancements/saif](https://safety.google/cybersecurity-advancements/saif/) |
| Vertex AI documentation | [cloud.google.com/vertex-ai/docs](https://cloud.google.com/vertex-ai/docs) |
| Gemini for Google Workspace | [workspace.google.com/solutions/ai](https://workspace.google.com/solutions/ai/) |
| NotebookLM | [notebooklm.google](https://notebooklm.google/) |

---

<sub>Unofficial study material, not affiliated with or endorsed by Google. The practice questions are original, not real exam content. Product names change often: when this guide and Google's official exam guide disagree, trust Google.</sub>
