# AI-900 · Microsoft Azure AI Fundamentals — from zero to certified

> ### ⚠️ Status: AI-900 retired on 30 June 2026 — it is replaced by **AI-901**
> The certification (*Microsoft Certified: Azure AI Fundamentals*) still exists, but its exam is now **AI-901**, with a new two-domain outline (skills measured as of 15 April 2026):
>
> | AI-901 domain | Weight | Where to study it in this repo |
> |---|---|---|
> | Identify AI concepts and capabilities (responsible AI, model components and configuration, AI workloads) | **40–45%** | §2, §3, §6 of this guide |
> | Implement AI solutions by using Microsoft Foundry (generative AI apps & agents, text & speech, vision & image generation, information extraction) | **55–60%** | §4–§6 of this guide **+** the hands-on parts of the [AI-103 guide](../AI-103/) (Weeks 2–4) |
>
> AI-901 expects **basic Python** (reading simple scripts) and more hands-on Foundry work than AI-900 did. Everything below still teaches the fundamentals both exams test; the AI-901 additions are the Foundry portal and SDK basics.
> Always confirm on the [official AI-901 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ai-901) — the status above comes from Microsoft's retirement notice as reported in October 2026.

> **Who this is for:** anyone curious about AI — students, managers, developers. No math and no coding required.
> **Time budget:** **~16 hours** over 2 weeks (about 1 hour a day).
> **Interactive practice:** [`AI-900-trainer.html`](AI-900-trainer.html) — download it and open it in your browser.
> **Recommended before:** nothing. **Recommended after:** [AI-103](../AI-103/) if you want to build AI apps and agents.

| Exam fact | Value |
|---|---|
| Format | ~40–60 questions, 45 minutes of answering time |
| Passing score | 700 / 1000 |
| Question types | Single choice, multiple choice, yes/no statements, drop-down, drag-and-drop matching |
| Prerequisites | None |
| Official page | [AI-900 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ai-900) — check it for the current skills outline before you start |

> ℹ️ **About product names.** Microsoft renames AI products often: *Azure AI Studio → Azure AI Foundry → Microsoft Foundry*; *Azure Cognitive Services → Azure AI services → Foundry Tools*. The concepts tested stay the same. This guide gives the current name and the older one so you recognize both in questions.

---

## Contents

1. [Study plan (16 h)](#1-study-plan-16-hours)
2. [AI workloads and responsible AI (15–20%)](#2-ai-workloads-and-responsible-ai-1520)
3. [Machine learning fundamentals (15–20%)](#3-machine-learning-fundamentals-1520)
4. [Computer vision (15–20%)](#4-computer-vision-1520)
5. [Natural language processing (15–20%)](#5-natural-language-processing-1520)
6. [Generative AI (20–25%)](#6-generative-ai-2025)
7. [One-page cheatsheet](#7-one-page-cheatsheet)
8. [Exam-day tactics](#8-exam-day-tactics)
9. [All the official resources](#9-all-the-official-resources)

---

## 1. Study plan (16 hours)

| Day | Hours | What you do | Done when you can… |
|---|---|---|---|
| 1 | 1.5 h | §2 — AI workloads + the 6 responsible-AI principles | name a principle from a one-line scenario |
| 2 | 2 h | §3.1–3.3 — regression, classification, clustering, deep learning | pick the ML type from a business question |
| 3 | 1.5 h | §3.4–3.5 — training, validation, metrics, Azure Machine Learning | explain overfitting and read a confusion matrix |
| 4 | 1 h | Trainer: Domains 1 and 2 | 80%+ on both |
| 5 | 2 h | §4 — computer vision + try image analysis in the Foundry portal | choose between classification, detection, OCR, face |
| 6 | 2 h | §5 — NLP, speech, translation + try language detection in the portal | map a scenario to the right language feature |
| 7 | 2.5 h | §6 — generative AI, LLMs, prompts, RAG, copilots, agents, responsible generative AI | explain tokens, embeddings, grounding and content filters |
| 8 | 1.5 h | Trainer: Domains 3, 4, 5 + **Weak skills** | every domain green |
| 9 | 1.5 h | **Exam simulation** + Microsoft's free practice assessment | 800+ in the simulation, 80%+ on the official assessment |
| 10 | 0.5 h | Cheatsheet only | — book the exam |

> 💡 **Free resources:** the [Microsoft Learn AI-900 learning path](https://learn.microsoft.com/en-us/credentials/certifications/azure-ai-fundamentals/) and its free **practice assessment**. A free Azure account lets you try every service in the [Microsoft Foundry portal](https://ai.azure.com) without writing code.

---

## 2. AI workloads and responsible AI (15–20%)

### 2.1 The kinds of AI you must recognize

| Workload | It lets software… | Example |
|---|---|---|
| **Machine learning** | learn patterns from data to predict | Predict house prices |
| **Computer vision** | see and interpret images and video | Detect defects on a production line |
| **Natural language processing (NLP)** | understand and produce text and speech | Analyze the sentiment of reviews |
| **Document intelligence** | extract fields from forms and documents | Read totals from invoices |
| **Knowledge mining** | extract insights from large amounts of unstructured content and make it searchable | Search across 100,000 contracts |
| **Generative AI** | *create* new content: text, code, images | Draft an email, a chatbot answer |
| **Anomaly detection** | spot unusual patterns | Flag a suspicious credit-card payment |

### 2.2 The 6 principles of responsible AI (Microsoft) — learn them by heart

Mnemonic: **"FRP-ITA"** — *Fair Rules Protect, Including Transparency & Accountability.*

| Principle | Question it asks | Scenario that triggers it |
|---|---|---|
| **Fairness** | Does it treat all people equally? | A loan model rejects more women than men with the same profile |
| **Reliability & safety** | Does it work as intended, even in unusual conditions? | A self-driving car must be tested in fog and snow |
| **Privacy & security** | Is personal data protected? | Customer data used for training must be secured and consented |
| **Inclusiveness** | Does it empower everyone, including people with disabilities? | A voice app must also work for users with speech impairments |
| **Transparency** | Can people understand how it works and its limits? | Tell users they are talking to an AI and why it decided |
| **Accountability** | Are humans responsible for it? | A governance board reviews AI decisions |

> ⚠️ **Exam trap:** *Transparency* = people **understand** the system. *Accountability* = **people are responsible** for it. They are often swapped in wrong answers.

---

## 3. Machine learning fundamentals (15–20%)

### 3.1 The vocabulary

- **Features** = the inputs (size of a house, number of rooms). **Label** = what you predict (price).
- **Training** = showing the algorithm many examples so it learns a **model**. **Inferencing** = using the model to predict on new data.

### 3.2 Types of machine learning

```
Machine learning
├── Supervised  (data HAS labels)
│   ├── Regression       → predict a NUMBER          (price, temperature, sales)
│   └── Classification   → predict a CATEGORY        (spam / not spam, which disease)
│       ├── binary       (2 classes)
│       └── multiclass   (3+ classes)
└── Unsupervised (data has NO labels)
    └── Clustering       → find GROUPS of similar items (customer segments)
```

**Trick to never fail:** look at the *output*. A number → **regression**. A category known in advance → **classification**. Groups you don't know in advance → **clustering**.

**Deep learning** uses **artificial neural networks** with many layers, inspired by the brain. It powers vision, speech and language models. The **Transformer** architecture (with *attention*) is the basis of modern large language models.

### 3.3 Training and evaluating a model

1. **Split the data:** a **training set** to learn and a **validation/test set** the model never saw, to check it generalizes.
2. **Overfitting** = the model memorized the training data and fails on new data.
3. **Metrics:**

| Model type | Metrics to recognize |
|---|---|
| Regression | **MAE**, **RMSE** (errors — lower is better), **R²** (coefficient of determination — closer to 1 is better) |
| Classification | **Accuracy**, **precision**, **recall**, **F1**, **confusion matrix** (true/false positives/negatives), **AUC** |
| Clustering | Distance between items and their cluster center |

- **Precision:** of everything I flagged as positive, how much was right? **Recall:** of all real positives, how many did I find?

### 3.4 Azure Machine Learning

| Capability | What it does |
|---|---|
| **Azure Machine Learning workspace** | Central place for data, experiments, models and deployments |
| **Automated ML (AutoML)** | Tries many algorithms and settings automatically and picks the best model — **no data-science expertise needed** |
| **Designer** | Build ML pipelines with **drag-and-drop**, no code |
| **Notebooks / SDK** | Code-first data science |
| **Endpoints** | Deploy a model as a web service for real-time or batch predictions |
| **Responsible AI dashboard** | Explain models, analyze errors, assess fairness |

---

## 4. Computer vision (15–20%)

### 4.1 The tasks

| Task | Output | Example |
|---|---|---|
| **Image classification** | One label for the whole image | "This is a cat" |
| **Object detection** | Labels **+ bounding boxes** for each object | "3 cars at these coordinates" |
| **Semantic segmentation** | A label for **each pixel** | Mark the exact shape of a tumor |
| **OCR (optical character recognition)** | Text read from images | Read a license plate or a scanned page |
| **Image analysis / captioning / tagging** | Description and tags of the image | "A person riding a bike on a street" |
| **Facial detection & analysis** | Location and attributes of faces | Blur faces in photos |

### 4.2 Azure services (current name ⟵ old name)

| Service | Use it for |
|---|---|
| **Azure AI Vision** (Image Analysis) | Captions, tags, objects, OCR (Read), smart cropping |
| **Azure AI Face** | Detect faces and analyze attributes. Identification/verification is a **Limited Access** feature (responsible-AI approval) |
| **Custom vision models** | Train on *your own* image categories when prebuilt tags aren't enough |
| **Azure AI Document Intelligence** ⟵ *Form Recognizer* | Extract fields from invoices, receipts, IDs, forms (prebuilt or custom models) |
| **Azure AI Content Understanding** | Turn documents, images, audio and video into structured fields using generative AI |

> ⚠️ **Exam trap:** *"where are the objects?"* → **detection** (boxes). *"what is this image?"* → **classification**. *"read the text"* → **OCR**. *"fields from an invoice"* → **Document Intelligence**, not plain OCR.

---

## 5. Natural language processing (15–20%)

### 5.1 Text analysis — Azure AI Language

| Feature | Output | Example |
|---|---|---|
| **Language detection** | Language name + confidence | "This review is in French" |
| **Sentiment analysis** | Positive / neutral / negative + scores | Rate customer reviews |
| **Opinion mining** | Sentiment per aspect | "battery: negative, screen: positive" |
| **Key phrase extraction** | Main talking points | "delivery delay", "refund" |
| **Named entity recognition (NER)** | People, places, organizations, dates… | "Paris" = Location |
| **Entity linking** | Links an entity to a knowledge base (Wikipedia) | "Mars" the planet vs. the brand |
| **PII detection** | Finds and redacts personal data | Mask phone numbers |
| **Summarization** | Short version of a long text | Summarize a report |
| **Conversational language understanding (CLU)** ⟵ *LUIS* | **Intent** + **entities** from what a user says | "Book a flight to Rome" → intent *BookFlight*, entity *Rome* |
| **Question answering** | Answers from a knowledge base (FAQ) | Support FAQ bot |

### 5.2 Speech — Azure AI Speech

| Feature | Direction |
|---|---|
| **Speech to text** (speech recognition) | 🎤 → 📝 (meeting transcription, captions) |
| **Text to speech** (speech synthesis) | 📝 → 🔊 (read content aloud, neural voices) |
| **Speech translation** | 🎤 language A → 📝/🔊 language B, in real time |
| **Speaker recognition** | Who is speaking |

### 5.3 Translation — Azure AI Translator

- **Text translation** — real-time text between 100+ languages.
- **Document translation** — whole documents keeping their formatting.
- **Custom Translator** — adapt translation to your domain's vocabulary.

> ✅ **Check yourself:** A chatbot must understand that *"I want to cancel my order"* means *CancelOrder*. Which feature? → **Conversational language understanding (CLU)**.

---

## 6. Generative AI (20–25%)

### 6.1 How it works, in plain words

- A **large language model (LLM)** is a deep-learning model (Transformer) trained on huge amounts of text to **predict the next token**.
- A **token** is a piece of a word (~4 characters of English). Prices and limits are counted in tokens.
- **Embeddings** turn text into vectors of numbers; similar meanings → close vectors. Used for **semantic search**.
- A **prompt** is the instruction you give. The **system message** sets the model's role and rules; the **user message** is the request.
- **Temperature** controls creativity: low = focused and repeatable, high = varied.

### 6.2 Making answers better

| Technique | What it does | When |
|---|---|---|
| **Prompt engineering** | Clear instructions, examples (**few-shot**), output format | Always first |
| **Grounding / RAG** (retrieval-augmented generation) | Retrieve relevant **company documents** and add them to the prompt, so answers use *your* data and cite it | The model must answer about private or recent data |
| **Fine-tuning** | Further train a model on your examples | Consistent style or specialized format at scale |

> ⚠️ **Exam trap:** "answer questions using the company's own documents" → **RAG / grounding**, *not* training a new model.

### 6.3 Copilots and agents

- A **copilot** is an AI assistant built into an app to help a user with a task (e.g. Microsoft 365 Copilot, GitHub Copilot).
- An **AI agent** goes further: it can **use tools** (search, call APIs, run code) and take actions to reach a goal, often over several steps.

### 6.4 Azure services for generative AI

| Service | Use |
|---|---|
| **Microsoft Foundry** ⟵ *Azure AI Foundry / Azure AI Studio* | Portal + SDK to build generative AI apps and agents: model catalog, playgrounds, prompt testing, evaluation, safety |
| **Azure OpenAI in Foundry Models** | OpenAI models (GPT for text/code, image generation, embeddings) with Azure security and compliance |
| **Model catalog** | Thousands of models from Microsoft, OpenAI, Meta, Mistral, and more |
| **Foundry Agent Service** | Build and run agents that use tools |
| **Azure AI Content Safety** | Detect harmful content (hate, sexual, violence, self-harm) with severity levels; **Prompt Shields** detect jailbreak attempts |

### 6.5 Responsible generative AI — the 4 stages Microsoft teaches

1. **Identify** potential harms (e.g. offensive or false content).
2. **Measure** them (test prompts, evaluations).
3. **Mitigate** at several layers: **model** (choose the right one) → **safety system** (content filters) → **system message & grounding** → **user experience** (disclose AI, limit inputs).
4. **Operate** responsibly (monitoring, incident response, phased rollout).

**Hallucination** = a confident but wrong answer. Main mitigations: **grounding (RAG)**, asking for **citations**, lower temperature, and **human review** for high-stakes uses.

---

## 7. One-page cheatsheet

| If the question says… | The answer is usually… |
|---|---|
| "predict a number" (price, sales, temperature) | **Regression** |
| "predict a category" (yes/no, which type) | **Classification** |
| "group customers without predefined labels" | **Clustering** |
| "build the best model without data-science skills" | **Automated ML** |
| "drag-and-drop pipeline, no code" | **Azure ML designer** |
| "model works on training data but not on new data" | **Overfitting** |
| "locate objects with boxes" | **Object detection** |
| "label every pixel" | **Semantic segmentation** |
| "read printed or handwritten text in an image" | **OCR** (Azure AI Vision Read) |
| "extract fields from invoices or receipts" | **Document Intelligence** |
| "is this review positive or negative?" | **Sentiment analysis** |
| "what language is this?" | **Language detection** |
| "names of people, places, organizations" | **Named entity recognition** |
| "user intent from an utterance" | **Conversational language understanding** |
| "convert speech to text" / "read text aloud" | **Speech to text** / **Text to speech** |
| "translate documents keeping the layout" | **Document translation** |
| "chatbot answers from company documents" | **RAG / grounding** |
| "control randomness of generated text" | **Temperature** |
| "vector representation of meaning" | **Embeddings** |
| "block harmful or violent generated content" | **Azure AI Content Safety / content filters** |
| "loan model disadvantages a group" | **Fairness** |
| "users must know they talk to an AI" | **Transparency** |
| "humans are answerable for the AI's decisions" | **Accountability** |
| "works for people with disabilities" | **Inclusiveness** |

## 8. Exam-day tactics

- Match the **output** described in the scenario (number, category, box, text, intent) to the task — most questions are solved this way.
- Prefer the **prebuilt, managed** service unless the question says the categories are *specific to the company* (then: custom model).
- Responsible-AI questions are worth easy points: learn the 6 principles until you can name them in 10 seconds.
- Never leave a question blank — there is no penalty for guessing.

---

## 9. All the official resources

| Resource | Link | Why use it |
|---|---|---|
| Certification page (schedule exam, practice assessment) | [Azure AI Fundamentals](https://learn.microsoft.com/en-us/credentials/certifications/azure-ai-fundamentals/) | Free official practice assessment — closest thing to the real questions |
| AI-901 study guide (current skills outline) | [Study guide AI-901](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ai-901) | The exact list of what can be asked |
| AI-900 study guide (archived outline) | [Study guide AI-900](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ai-900) | If you hold a voucher for the old exam |
| Exam sandbox | [aka.ms/examdemo](https://aka.ms/examdemo) | Try the real exam interface and every question type before the day |
| Exam duration and experience | [Exam duration](https://learn.microsoft.com/en-us/credentials/support/exam-duration-exam-experience) | Time per exam, accommodations, online vs test center |
| Microsoft Foundry portal | [ai.azure.com](https://ai.azure.com) | Try every service by clicking, no code needed |
| Free Azure account | [azure.microsoft.com/free](https://azure.microsoft.com/free/) | Credits for hands-on practice |
| Microsoft Virtual Training Days | [events.microsoft.com/mvtd](https://events.microsoft.com/en-us/mvtd) | Free live training, often with a **free exam voucher** |
| Fundamentals certifications never expire | — | No renewal needed for AI-900/AI-901 |

---

<sub>Unofficial study material, not affiliated with or endorsed by Microsoft. Product names and exam outlines change: when this guide and Microsoft Learn disagree, trust Microsoft Learn. Found a mistake? Open an issue or a pull request.</sub>
