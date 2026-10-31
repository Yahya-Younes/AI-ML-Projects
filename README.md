# 🎓 AI & Cloud Certification Study Hub

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](LICENSE)

**Free, complete, beginner-friendly guides to pass Microsoft Azure, Google Cloud and TensorFlow certifications** — each with a study plan in hours, a full course written for people starting from zero, a one-page cheatsheet, every official link, and an **interactive exam simulator** that runs in your browser.

> ⭐ If this helps you pass, star the repository so others can find it — and open an issue if you spot anything outdated.

---

## Choose your certification

| Certification | Level | Study time | Guide | Practice questions | ▶️ Practice now | Status (Oct 2026) |
|---|---|---|---|---|---|---|
| **AZ-900** · Microsoft Azure Fundamentals | Beginner | **~18 h** | [Guide](microsoft-azure/AZ-900/) | [40 + simulation](microsoft-azure/AZ-900/AZ-900-trainer.html) | [**Open trainer**](https://yahya-younes.github.io/ai-cloud-certification-hub/microsoft-azure/AZ-900/AZ-900-trainer.html) | ✅ Active (outline of 14 Jan 2026) |
| **AI-900 → AI-901** · Azure AI Fundamentals | Beginner | **~16 h** (+ ~8 h Foundry hands-on for AI-901) | [Guide](microsoft-azure/AI-900/) | [38 + simulation](microsoft-azure/AI-900/AI-900-trainer.html) | [**Open trainer**](https://yahya-younes.github.io/ai-cloud-certification-hub/microsoft-azure/AI-900/AI-900-trainer.html) | ⚠️ AI-900 retired 30 Jun 2026 → exam is now **AI-901** |
| **AI-103** · Azure AI Apps and Agents Developer Associate | Intermediate | **~55 h** | [Guide](microsoft-azure/AI-103/) · [Cheatsheet](microsoft-azure/AI-103/cheatsheet.md) · [**Personal planner**](https://yahya-younes.github.io/ai-cloud-certification-hub/microsoft-azure/AI-103/AI-103-planner.html) | [**190** + 4 case studies + 50-q simulation](microsoft-azure/AI-103/AI-103-trainer.html) | [**Open trainer**](https://yahya-younes.github.io/ai-cloud-certification-hub/microsoft-azure/AI-103/AI-103-trainer.html) | ✅ Active (replaces AI-102) |
| **Google Cloud Generative AI Leader** | Beginner (business) | **~15 h** | [Guide](google-cloud/generative-ai-leader/) | [51 + 50-q simulation](google-cloud/generative-ai-leader/GenAI-Leader-trainer.html) | [**Open trainer**](https://yahya-younes.github.io/ai-cloud-certification-hub/google-cloud/generative-ai-leader/GenAI-Leader-trainer.html) | ✅ Active |
| **TensorFlow Developer Certificate** | Intermediate (coding) | **~60 h** | [Guide + tested code templates](tensorflow/developer-certificate/) | [31 concept & code questions](tensorflow/developer-certificate/TensorFlow-trainer.html) | [**Open trainer**](https://yahya-younes.github.io/ai-cloud-certification-hub/tensorflow/developer-certificate/TensorFlow-trainer.html) | ⛔ Exam closed in 2024 — still the best structured deep-learning bootcamp |

## Repository layout

```
.
├── microsoft-azure/
│   ├── AZ-900/            guide · 40-question trainer
│   ├── AI-900/            guide (AI-900 → AI-901) · 38-question trainer
│   └── AI-103/            guide · cheatsheet · 190-question trainer with case studies · date-based study planner
├── google-cloud/
│   └── generative-ai-leader/   guide · 51-question trainer
└── tensorflow/
    └── developer-certificate/  guide with tested code templates · 31-question trainer
```

## Suggested roadmaps

```
Cloud & AI beginner      AZ-900 (18 h) ──► AI-901 (24 h) ──► AI-103 (55 h)
AI engineer on Azure     AI-901 (24 h) ──► AI-103 (55 h)
Business / product lead  Google Generative AI Leader (15 h) ──► AI-901 (24 h)
Deep-learning developer  TensorFlow Developer (60 h) ──► AI-103 (55 h)
```

## What every guide contains

1. **Exam facts** — format, duration, passing score, price, validity, current status.
2. **A day-by-day study plan with hours**, and a "done when you can…" check for each day.
3. **The full course**, domain by domain, written for beginners: analogies, tables, ⚠️ exam traps and ✅ self-checks.
4. **A one-page cheatsheet**: *"if the question says X, the answer is Y"*.
5. **Exam-day tactics.**
6. **All the official resources** — study guides, free practice assessments, exam sandboxes, labs, documentation.

## How to use the interactive trainers

The `*-trainer.html` files are self-contained web pages — no account, no install, no tracking.

1. Click **▶️ Open trainer** in the table above — it opens directly in your browser. (Offline? Open the trainer file on GitHub, click **Download raw file**, and double-click it.)
2. **Domain cards** → practice one domain with instant feedback and an explanation for every option.
3. **Exam simulation** → timed and weighted like the real exam, flag & review screen, scaled score out of 1000 (700 to pass).
4. **Weak skills / Retry missed** → drill your mistakes until every domain is green.
5. Your progress is saved **only in your browser**.


### How realistic are the questions?

The questions are **original** and written from the official skills outlines and documentation, in the **same formats, weighting and difficulty** as the real exams: scenario-based single and multiple choice, drop-down code completion, yes/no statement sets, ordering, and case studies. Each explanation says *why* every wrong option is wrong, which is what actually prepares you for new questions.

They are **not** copies of real exam questions: those are protected by the certification providers' non-disclosure agreements, and "dumps" are both a violation and a bad way to learn. For the closest thing to the real exam, combine these trainers with each provider's **free official practice assessment**, linked in every guide.

## Contributing

Certifications change every few months. If a service was renamed, a question is outdated or an explanation is unclear, [open an issue](https://github.com/Yahya-Younes/ai-cloud-certification-hub/issues/new/choose) or a pull request with a link to the official documentation — see [CONTRIBUTING.md](CONTRIBUTING.md).

## License

The guides, cheatsheets and practice questions are licensed under [**Creative Commons Attribution 4.0 (CC BY 4.0)**](LICENSE): share and adapt them freely, as long as you credit this repository.

<sub>Unofficial study material. Not affiliated with or endorsed by Microsoft, Google or the TensorFlow team. All trademarks belong to their owners.</sub>
