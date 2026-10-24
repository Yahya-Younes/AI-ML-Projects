# AI / ML Projects

> Machine-learning and deep-learning work in Python – from linear regression written from
> scratch to TensorFlow object localization, detection and segmentation.

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white" alt="Jupyter">
  <img src="https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white" alt="TensorFlow">
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white" alt="scikit--learn">
  <img src="https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white" alt="NumPy">
  <img src="https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white" alt="pandas">
</p>

> ### 🎓 New: [Certification Study Hub](certifications/)
> Free zero-to-certified guides with study plans in hours, cheatsheets and interactive exam simulators for **AZ-900**, **AI-900/AI-901**, **AI-103**, **Google Cloud Generative AI Leader** and the **TensorFlow Developer Certificate**.

A collection of machine-learning and deep-learning work: personal projects and graded
course assignments, mostly in Python (NumPy, pandas, scikit-learn, TensorFlow/Keras).

### Highlights

- **Normal equation vs. scikit-learn** – multiple linear regression implemented with linear algebra, matching scikit-learn's coefficients exactly (R² ≈ 0.87).
- **Object localization** – bounding-box regression on Caltech Birds with a MobileNetV2 backbone, evaluated with IoU.
- **Few-shot object detection** – RetinaNet fine-tuned from only 5 labelled images with the TF2 Object Detection API and a custom training loop.
- **Semantic segmentation** – CNN encoder + FCN-8 decoder on M2NIST, evaluated with IoU and Dice score.

## Repository layout

```
.
├── certifications/                             # Study hub: guides, cheatsheets, exam simulators
│   ├── microsoft-azure/                       # AZ-900, AI-900/AI-901, AI-103
│   ├── google-cloud/                          # Generative AI Leader
│   └── tensorflow/                            # TensorFlow Developer Certificate
├── courses/
│   └── advanced-computer-vision-tensorflow/   # DeepLearning.AI TensorFlow course 3 assignments
│       ├── week-1-object-localization/        # Bounding-box regression (Caltech Birds, MobileNetV2)
│       ├── week-2-object-detection/           # Few-shot RetinaNet fine-tuning (TF Object Detection API)
│       ├── week-3-image-segmentation/         # FCN-8 segmentation of M2NIST digits
│       └── week-4/                            # placeholder (not uploaded yet)
├── projects/
│   ├── chest-disease-classification/          # Chest X-ray dataset (COVID-19 / normal / viral / bacterial pneumonia)
│   └── linear-regression-olympic-medals/      # Linear regression from scratch vs. scikit-learn
├── requirements.txt
└── README.md
```

## Contents

| Folder | Topic | Techniques | Status |
|---|---|---|---|
| [`projects/linear-regression-olympic-medals`](projects/linear-regression-olympic-medals) | Predict Olympic medal counts per team | Normal equation, R², scikit-learn `LinearRegression` | Complete |
| [`projects/chest-disease-classification`](projects/chest-disease-classification) | Classify chest X-rays into 4 classes | Image classification (CNN / transfer learning) | Dataset only – notebook not yet added |
| [`courses/advanced-computer-vision-tensorflow`](courses/advanced-computer-vision-tensorflow) | Localization, detection, segmentation | Transfer learning, RetinaNet, FCN-8, IoU / Dice | Weeks 1–3 complete |

## Getting started

```bash
git clone https://github.com/Yahya-Younes/AI-ML-Projects.git
cd AI-ML-Projects
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

The course notebooks were written for **Google Colab** (GPU runtime) and use
`google.colab` helpers, the TensorFlow Object Detection API and Coursera-hosted data.
Open them in Colab rather than running them locally — see each folder's README.

## Conventions

- Folder names are lowercase `kebab-case`.
- Each project has its own `README.md` describing the goal, data, and how to run it.
- Datasets live next to the notebook that uses them (chest X-rays in `data/`).
- Files were only moved/renamed during the reorganisation; nothing was deleted or edited.

---

## Author

**Yahya Younes** – AI & GenAI Engineer (LLM, RAG, model compression), Toulouse, France
[Portfolio](https://yahyayounes.com) · [LinkedIn](https://www.linkedin.com/in/yahyayounes/) · [GitHub](https://github.com/Yahya-Younes)
