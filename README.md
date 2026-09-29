# AI / ML Projects

A collection of machine-learning and deep-learning work: personal projects and graded
course assignments, mostly in Python (NumPy, pandas, scikit-learn, TensorFlow/Keras).

## Repository layout

```
.
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
