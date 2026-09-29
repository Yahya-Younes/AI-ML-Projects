# Advanced Computer Vision with TensorFlow

Graded programming assignments from **Course 3 of the DeepLearning.AI
"TensorFlow: Advanced Techniques" specialization** (Coursera).

| Week | Folder | Task | Dataset | Model |
|---|---|---|---|---|
| 1 | [`week-1-object-localization`](week-1-object-localization) | Predict a bounding box around a bird | [Caltech-UCSD Birds 2010](http://www.vision.caltech.edu/visipedia/CUB-200.html) (`tfds: caltech_birds2010`) | MobileNetV2 feature extractor + dense regression head, evaluated with IoU |
| 2 | [`week-2-object-detection`](week-2-object-detection) | Detect "zombies" from only 5 labelled training images | Course-provided images | RetinaNet (SSD ResNet50 FPN) fine-tuned with the TF2 Object Detection API and a custom eager training loop |
| 3 | [`week-3-image-segmentation`](week-3-image-segmentation) | Pixel-wise segmentation of handwritten digits | [M2NIST](https://www.kaggle.com/farhanhubble/multimnistm2nist) | Custom CNN encoder + FCN-8 decoder, evaluated with IoU and Dice score |
| 4 | — | Visualization & interpretability | — | Not uploaded yet |

## Running the notebooks

These notebooks were built for **Google Colab** with a GPU runtime:

1. Upload the notebook to Google Drive (or use *File → Open notebook → Upload* in Colab).
2. Select *Runtime → Change runtime type → GPU*.
3. Run the cells in order. Week 1 needs a Drive shortcut to the course data folder
   (instructions are in the notebook); Week 2 clones and installs the TensorFlow
   Object Detection API in the first cells.

Main libraries: `tensorflow`, `tensorflow_datasets`, `numpy`, `matplotlib`, `Pillow`,
`opencv-python` (week 1), `object_detection`, `imageio` (week 2), `scikit-learn` (week 3).
