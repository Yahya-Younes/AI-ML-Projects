# AI-103 cheatsheet — "if the scenario says X, choose Y"

> Skim one domain right before you drill it in the [trainer](AI-103-trainer.html).
> Memorize the **trigger words** in the left column: most AI-103 questions are solved by spotting them.
> Exam: 120 min · pass 700/1000 · Python · case studies included.

| Domain | Weight |
|---|---|
| 1 · Plan and manage an Azure AI solution | 25–30% |
| 2 · Implement generative AI and agentic solutions | 30–35% |
| 3 · Implement computer vision solutions | 10–15% |
| 4 · Implement text analysis solutions | 10–15% |
| 5 · Implement information extraction solutions | 10–15% |

---

## Domain 1 · Plan and manage (25–30%)

### Choose the model

| Scenario trigger | Choose |
|---|---|
| Narrow task, huge volume, low latency, low cost | **Small language model** (e.g. Phi), fine-tuned if needed |
| Complex multi-step reasoning, quality over latency | **Reasoning model** (raise `reasoning_effort`) |
| Mix of easy and hard prompts, one endpoint, cut cost | **Model router** (Balanced / Cost / Quality mode, optional model subset) |
| Must see images / audio | **Multimodal model** |
| Offline, data must never leave the device | **Foundry Local** |
| Translate whole Office files keeping layout | **Translator document translation** (not a chat prompt) |

### Choose the deployment type

| Scenario trigger | Choose |
|---|---|
| Variable traffic, pay per token, no residency rule | **Global Standard** |
| EU/US data residency, pay per token | **Data Zone Standard** |
| Steady high volume, predictable latency | **Provisioned (PTU)** — Global or Data Zone |
| Big non-urgent job, results within 24 h, −50% cost | **Global Batch** / **Data Zone Batch** (if residency) |
| Short, cheap test of a fine-tuned model | **Developer** (no SLA) |
| Provisioned bursts must not fail | **Spillover** to a Standard deployment of the **same model + version, same resource** |

### Quotas and 429s

- Rate limit uses **prompt tokens + `max_tokens`** *before* processing → an oversized `max_tokens` causes 429s while metrics look low.
- RPM is checked over **1–10 s windows** → bursts trigger 429 even when TPM is fine. Smooth the traffic.
- Quota = **per subscription, per region, per model, per deployment type**. Free quota by lowering another deployment.
- Custom retry (tenacity)? Set the SDK's `max_retries=0`, exponential backoff with jitter, retry only `RateLimitError`.
- Prompt caching needs an **identical prefix ≥ 1,024 tokens** → put static instructions first, user input last.

### Security

| Requirement | Do this |
|---|---|
| No keys anywhere | **Managed identity** + `DefaultAzureCredential` + a data-plane role, **and** `disableLocalAuth = true` |
| Token scope for Foundry | `https://ai.azure.com/.default` |
| App only calls one published agent | **Foundry Agent Consumer** |
| Developer builds agents | **Foundry User** |
| Team lead publishes agents and can grant only the developer role | **Foundry Project Manager** |
| Deploy models but no data-plane access | **Foundry Account Owner** |
| See the Quota page | **Cognitive Services Usages Reader** at subscription scope |
| Private endpoint still resolves to a public IP | Missing **private DNS zone** linked to the VNet |
| Agent data (threads, files, vectors) in *your* resources | **Standard agent setup** (Cosmos DB + Storage + AI Search), private networking variant for "no public access" |
| GitHub Actions without stored secrets | **OIDC federated credential** + `id-token: write` + `azure/login` |
| Published agent loses access to a tool | Re-grant roles to the **new agent identity** created at publish time |

### Responsible AI and safety

| Risk | Control |
|---|---|
| User types "ignore your instructions…" | **Prompt Shields — user prompt attack** (on by default) |
| Hidden instructions in a document / web page / email / tool result | **Prompt Shields — document (indirect) attack** (**off** by default — turn it on) |
| Copyrighted lyrics or code in output | **Protected material detection** |
| Claims not supported by sources | **Groundedness detection** |
| Exact banned words | **Blocklist** |
| Measure attack success rate before launch | **AI Red Teaming Agent** (PyRIT) |
| Filter threshold "Low" | Blocks low, medium **and** high (strictest) |

### Monitor and operate

| Need | Choose |
|---|---|
| Per-step spans: model calls, tool calls, latency | **OpenTelemetry tracing → project's Application Insights** |
| Quality of live traffic over time, with alerts | **Continuous evaluation** rule (response-completed event) + dashboard |
| Block a merge if quality drops | **Evaluation gate in CI/CD** |
| Who created/deleted resources | Azure **Activity log** (control plane only) |
| Keep traces 2 years | Workspace-based App Insights on a Log Analytics workspace with that retention |

---

## Domain 2 · Generative AI and agents (30–35%)

### Build the app

- **Responses API:** continue a chat with `previous_response_id` (or a **conversation** object); `store=False` = nothing persisted; long jobs → `background=True` + poll.
- **Chat Completions:** stateless — resend the history every call.
- **Structured outputs:** `type: json_schema`, `strict: true`, every property in `required`, `additionalProperties: false`, optional = `["string","null"]`. (`json_object` only guarantees *valid JSON*.)
- **Project-level work** (agents, connections, evaluations) → `AIProjectClient`; **embeddings / lowest latency** → OpenAI client on `/openai/v1/`.
- **Reasoning models:** no `temperature`/`max_tokens`; use `max_completion_tokens` (includes reasoning tokens) and `reasoning_effort`; reasoning **summary** is the supported way to see "why".
- **Tuning:** change *temperature or top_p*, not both. Hard business rules belong in **code**, never only in the prompt.
- **Reflection loop** (draft → critique → revise) improves quality at the cost of latency.

### RAG — order matters

**Index time:** extract (layout/OCR) → **chunk** → **embed** → store chunk + vector.
**Query time:** embed the question (or let the **vectorizer** do it) → **hybrid** query (BM25 + vector, merged with **RRF**) → **semantic ranker** on the top 50 → put top chunks in the prompt → answer **with citations**.
Never embed a whole document as one vector. Exact codes (SKUs, part numbers) → add keyword search (hybrid).

### Pick the agent tool

| Need | Tool |
|---|---|
| Questions on files the user uploads in the chat | **File search** (vector store) |
| Compute statistics, draw a chart from a CSV | **Code interpreter** |
| Call a REST API with an OpenAPI spec | **OpenAPI tool** (managed identity auth, audience = the API) |
| Tools exposed by a remote MCP server | **MCP tool** + `allowed_tools` + `require_approval` (`always` / `never` / per-tool object) |
| Delegate to another company's agent | **A2A tool** |
| Async work through an Azure Functions queue | **Azure Functions tool** |
| Fill forms on a website, watch live | **Browser automation** |
| Drive a legacy desktop app from screenshots | **Computer use** (acknowledge `pending_safety_checks` with a human) |
| Public news with citations, no extra resource | **Web search** (data leaves the Azure compliance boundary) |
| Curated company content, many agents, user permissions enforced | **Foundry IQ knowledge base** |
| Remember user preferences across sessions | **Memory store** (needs chat + embedding deployments; TTL for retention) |

### Orchestrate agents (Microsoft Agent Framework)

| Pattern | Use when |
|---|---|
| **Sequential** | Fixed pipeline, each step uses the previous output |
| **Concurrent** | Independent opinions in parallel, then aggregate |
| **Handoff** | Specialist **takes over** the conversation |
| **Agent-as-tool** | Main agent **keeps ownership**, gets a result back |
| **Group chat** | Agents refine together in a shared conversation, orchestrator picks the speaker |
| **Magentic** | Manager plans, delegates, re-plans an open-ended task (`enable_plan_review` for human approval) |
| **Switch-case edges** | Deterministic routing by business rules after LLM extraction |

### Evaluate

| Question | Evaluator |
|---|---|
| Answer supported by the context? | **Groundedness** (LLM judge, 1–5) / **Groundedness Pro** (pass/fail, no judge model) |
| Answer addresses the question? | **Relevance** |
| Retrieved chunks relevant? | **Retrieval** |
| Missing info vs ground truth? | **Response Completeness** |
| Right tool + right parameters? | **Tool Call Accuracy** (or Tool Selection / Tool Input Accuracy) |
| Understood the user's goal? | **Intent Resolution** |
| Followed the system-message rules? | **Task Adherence** |
| Tool ran without technical error? | **Tool Call Success** |
| Group 400 failures by type | **Cluster analysis** |

---

## Domain 3 · Computer vision (10–15%)

| Need | Choose |
|---|---|
| New image from text | **Image generation** (`images.generate`; PNG/JPEG, `n` up to 10) |
| Change only part of an image | **Edit with a mask** (transparent pixels = editable) |
| Combine several reference photos faithfully | **Edit with several `image[]` inputs** + `input_fidelity="high"` |
| Video from text / first-frame image | **Sora** job: create → poll → download within 24 h |
| Small change to an approved video | **Remix** the completed video |
| Compare two photos in one answer | Both images in **one** user message to a multimodal model |
| Cheap coarse classification of many images | `detail: "low"` · read small text → `detail: "high"` |
| Image behind a private endpoint | Send it as **base64 data URL** |
| Caption / regions / OCR / smart crops | **Image Analysis 4.0** (`caption`, `denseCaptions`, `read`, `smartCrops`) |
| Your own fields from images/video/audio, no parser | **Content Understanding** analyzer (extract / classify / generate) |
| Hateful meme (image + caption) | **Content Safety multimodal** with OCR |
| Prove an image is AI-generated | **Content Credentials (C2PA)** — attached automatically |
| Instructions hidden in an image | Treat extracted text as **untrusted** + **Prompt Shields** + approval on sensitive tools |
| Alt text | Describe the **action** for icon buttons, ~150 characters, details in surrounding text, no "Image of…" |

---

## Domain 4 · Text and speech (10–15%)

| Scenario trigger | Choose |
|---|---|
| Standard entities at huge volume, low cost | **Azure Language NER** |
| Company-specific entities | **Custom NER** |
| Varied documents, many custom fields, strict JSON | **LLM + structured outputs** |
| Clinical notes, negation, FHIR output | **Text Analytics for health** |
| Sentiment per aspect ("breakfast bad, room good") | **Opinion mining** (`show_opinion_mining=True` → `mined_opinions`) |
| Readable redaction showing the entity type | PII redaction policy **`entityMask`** |
| Verbatim summary sentences with positions | **Extractive** summarization |
| Batch of files with layout | **Document translation** (async + Blob) · one file, no storage → **synchronous** document translation |
| Fixed brand terms | **Glossary** · domain-wide terminology → **Custom Translator** (pass the Category ID) |
| Offline audio archive | **Batch transcription** · who spoke when → **diarization** |
| Product names misrecognized | **Custom speech** (text data first, phrase lists) |
| Pause / speed / pronunciation in TTS | **SSML**: `break time`, `prosody rate`, `phoneme` → `speak_ssml_async` |
| Real-time spoken translation | **Speech translation** |
| Voice agent with noise and echo | **Voice Live**: `azure_semantic_vad_multilingual`, `server_echo_cancellation`, `azure_deep_noise_suppression` |
| Tone and hesitation in recordings | **Audio-capable multimodal model** (not transcription + sentiment) |

---

## Domain 5 · Information extraction (10–15%)

| Scenario trigger | Choose |
|---|---|
| Scheduled pull + enrichment, little code | **Indexer + skillset** |
| Chunk and embed automatically, embed queries at query time | **Integrated vectorization** (Text Split + embedding skill + **vectorizer**) |
| Each chunk = its own search document | **Index projections** |
| Tables and headings preserved, page citations | **Document Layout skill** / **Content Understanding skill** |
| Text inside embedded images | `imageAction: generateNormalizedImages` + **OCR** + **Text Merge** |
| Lookup in your own API during indexing | **Custom Web API skill** (same `recordId`s, max timeout 230 s) |
| Deleted blobs must leave the index | **Native blob soft delete** detection policy (before the first run) |
| Measure HNSW recall | Query with `exhaustive: true` |
| Debug one document's enrichment | **Debug session** |
| Varied invoices | Document Intelligence **prebuilt-invoice** · extra fields, no training → **queryFields** |
| Fixed layout form | **Custom template** · varied layouts → **custom neural** · mixed stream → **classifier + composed model** |
| Markdown + summary + chunks for RAG | Content Understanding **prebuilt-documentSearch** (video → **videoSearch**, calls → **audioSearch**) |
| Several agents, permission-aware retrieval with citations | **Foundry IQ** knowledge base (project identity needs **Search Index Data Reader**) |
| Lawyers see only their group's documents | **Security filter** on a filterable group-ID collection (`search.in`) |

---

## Exam-day tactics

1. **Underline the constraint words first**: *no keys*, *EU only*, *lowest cost*, *no custom code*, *human approval*, *exact codes*. Each one eliminates options.
2. When two answers both work, pick the one that is **purpose-built** and **managed** (prebuilt over custom, managed tool over your own code) — unless the scenario says otherwise.
3. **Case studies:** re-read the requirements list before *each* question; requirements are reused across questions.
4. **Security answers are almost never "store the key in Key Vault"** when the scenario says "no keys": the answer is managed identity + RBAC.
5. Partial credit exists for drop-downs and multi-part questions: **answer every part**.

<sub>Unofficial study material, not affiliated with or endorsed by Microsoft. When this sheet and Microsoft Learn disagree, trust Microsoft Learn.</sub>
