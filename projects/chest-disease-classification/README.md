# AI-Powered Chest Disease Detection and Classification

Goal: automatically classify chest X-ray images into one of four categories using a
deep-learning image classifier (e.g. a CNN or transfer learning from ResNet50), to help
triage respiratory diseases.

> **Status:** the dataset is included; the training notebook has not been added yet.

## Dataset

```
data/
├── train/   # 100 images per class (400 total)
│   ├── 0/
│   ├── 1/
│   ├── 2/
│   └── 3/
└── test/    # 10 images per class (40 total)
    ├── 0/ … 3/
```

| Label | Class | Example file names |
|---|---|---|
| `0` | COVID-19 | figures from COVID-19 case reports (`nejmoa2001191_f1-PA.jpeg`, …) |
| `1` | Normal | `IM-0182-0001.jpeg` |
| `2` | Viral pneumonia | `person268_virus_553.jpeg` |
| `3` | Bacterial pneumonia | `person3_bacteria_13.jpeg` |

The class folders are numeric so they can be loaded directly with
`tf.keras.utils.image_dataset_from_directory("data/train")` (or Keras'
`ImageDataGenerator.flow_from_directory`), which assigns labels in folder order.

Sources: the images are a subset of the public
[COVID-19 image data collection](https://github.com/ieee8023/covid-chestxray-dataset) and the
[Chest X-Ray Images (Pneumonia)](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia)
Kaggle dataset.

## Suggested approach

1. Load `data/train` with an 80/20 train/validation split, resize to 256×256, normalise.
2. Apply light augmentation (rotation, zoom, horizontal flip).
3. Fine-tune an ImageNet-pretrained backbone (e.g. ResNet50) with a small dense head
   and a 4-way softmax.
4. Evaluate on `data/test` with accuracy, a confusion matrix and a classification report.

## Disclaimer

For educational purposes only — not a medical device and not for clinical use.
