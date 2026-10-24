# TensorFlow Developer Certificate — the complete revision guide

> ### ⚠️ Status: exam closed since 2024
> Google closed the TensorFlow Developer Certificate exam in 2024 (last purchase date: 30 April 2024) "while it evaluates the next step of the program". Certificates already earned stay valid for 3 years from the passing date.
> **Why keep this guide?** The skills it tests — building, training and debugging Keras models for vision, text and time series — are exactly what deep-learning interviews and projects ask for. Use it as a structured deep-learning bootcamp.

> **Who this is for:** Python developers who want practical deep learning with TensorFlow/Keras.
> **Time budget:** **~60 hours** over 5–6 weeks (the original recommendation was the 4-course DeepLearning.AI program plus practice).
> **Interactive practice:** [**▶️ Open the TensorFlow trainer in your browser**](https://yahya-younes.github.io/ai-cloud-certification-hub/tensorflow/developer-certificate/TensorFlow-trainer.html) (or download [`TensorFlow-trainer.html`](TensorFlow-trainer.html) to use it offline) — concept and code questions with explanations.

| Exam fact (when it was open) | Value |
|---|---|
| Format | **Hands-on coding**: build and train 5 models in PyCharm with a TensorFlow exam plugin, graded automatically on accuracy |
| Duration | 5 hours |
| Price | US $100 |
| Validity | 3 years |
| The 5 model categories | ① basic/regression model ② image classification (simple dataset) ③ image classification with CNNs on real-world images ④ natural language processing ⑤ time series / sequence forecasting |
| Official skills checklist | [Candidate handbook (PDF)](https://www.tensorflow.org/static/extras/cert/TF_Certificate_Candidate_Handbook.pdf) · [Certificate page](https://www.tensorflow.org/certificate) |

## The skills checklist (5 sections) and hours

| # | Section | Hours | Template below |
|---|---|---|---|
| 1 | TensorFlow developer skills (environment, debugging, saving models, reading docs) | 4 h | [§1](#1-developer-skills-4-h) |
| 2 | Building and training neural network models | 12 h | [§2](#2-neural-network-basics-12-h) |
| 3 | Image classification (CNNs, augmentation, transfer learning) | 16 h | [§3](#3-image-classification-16-h) |
| 4 | Natural language processing (tokenization, embeddings, RNN/LSTM/Conv1D) | 14 h | [§4](#4-natural-language-processing-14-h) |
| 5 | Time series, sequences and predictions | 10 h | [§5](#5-time-series-10-h) |
| — | Trainer + full mock (build all 5 models in 5 hours from scratch) | 4 h | [§6](#6-mock-exam-and-tactics) |

---

## 1. Developer skills (4 h)

- Know your versions: `import tensorflow as tf; print(tf.__version__)`. Keras is `tf.keras`.
- **Read the docs** for every layer you use ([tensorflow.org/api_docs](https://www.tensorflow.org/api_docs/python/tf)).
- **Shapes cause 80% of bugs.** Print `model.summary()` and the shape of one batch: `for x, y in ds.take(1): print(x.shape, y.shape)`.
- **Save and reload** a model:

```python
model.save("model.keras")                      # native Keras format
reloaded = tf.keras.models.load_model("model.keras")
```

- Keep models **reasonably small**: the grader has size and time limits. Prefer a few well-chosen layers over huge ones.
- Use **callbacks** to save time:

```python
callbacks = [
    tf.keras.callbacks.EarlyStopping(monitor="val_loss", patience=5, restore_best_weights=True),
    tf.keras.callbacks.ModelCheckpoint("best.keras", save_best_only=True),
]
```

## 2. Neural network basics (12 h)

### 2.1 The universal recipe

```python
model = tf.keras.Sequential([...])   # 1. architecture
model.compile(optimizer=..., loss=..., metrics=[...])   # 2. how to learn
model.fit(x, y, validation_data=..., epochs=..., callbacks=...)   # 3. learn
model.evaluate(...); model.predict(...)   # 4. check and use
```

### 2.2 Pick the output layer and loss — the table that decides most bugs

| Problem | Last layer | Loss | Labels look like |
|---|---|---|---|
| Regression (predict a number) | `Dense(1)` (no activation) | `mse` or `huber` (metric `mae`) | `3.7` |
| Binary classification | `Dense(1, activation="sigmoid")` | `binary_crossentropy` | `0` / `1` |
| Multiclass, **integer** labels | `Dense(n, activation="softmax")` | `sparse_categorical_crossentropy` | `3` |
| Multiclass, **one-hot** labels | `Dense(n, activation="softmax")` | `categorical_crossentropy` | `[0,0,0,1,0]` |

### 2.3 Template — regression on tabular data

```python
import numpy as np, tensorflow as tf

x = np.array([-1.0, 0.0, 1.0, 2.0, 3.0, 4.0], dtype=float)
y = 2 * x - 1                                   # the rule to learn: y = 2x - 1

model = tf.keras.Sequential([tf.keras.Input(shape=(1,)), tf.keras.layers.Dense(1)])
model.compile(optimizer="sgd", loss="mse")
model.fit(x, y, epochs=500, verbose=0)
print(model.predict(np.array([[10.0]])))        # ≈ 19
```

### 2.4 Fighting overfitting

| Symptom | Fix |
|---|---|
| Training accuracy ≫ validation accuracy | Data augmentation, `Dropout`, fewer parameters, early stopping, more data |
| Both accuracies low (underfitting) | Bigger model, more epochs, better features, higher learning rate |
| Loss explodes / NaN | Lower learning rate, normalize inputs |

**Normalize inputs**: pixels `/ 255.0`, tabular features standardized. **Learning-rate finder:** train with `LearningRateScheduler(lambda e: 1e-8 * 10 ** (e / 20))`, plot loss vs LR, pick the LR just before the loss becomes unstable.

## 3. Image classification (16 h)

### 3.1 Simple images (Fashion-MNIST style)

```python
(x_train, y_train), (x_test, y_test) = tf.keras.datasets.fashion_mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0          # normalize

model = tf.keras.Sequential([
    tf.keras.Input(shape=(28, 28, 1)),
    tf.keras.layers.Conv2D(32, 3, activation="relu"),
    tf.keras.layers.MaxPooling2D(),
    tf.keras.layers.Conv2D(64, 3, activation="relu"),
    tf.keras.layers.MaxPooling2D(),
    tf.keras.layers.Flatten(),
    tf.keras.layers.Dense(128, activation="relu"),
    tf.keras.layers.Dense(10, activation="softmax"),
])
model.compile(optimizer="adam", loss="sparse_categorical_crossentropy", metrics=["accuracy"])
model.fit(x_train[..., None], y_train, validation_data=(x_test[..., None], y_test), epochs=10)
```

- **Conv2D** learns filters (edges → shapes → objects). **MaxPooling2D** halves the size and keeps the strongest signals. **Flatten** turns feature maps into a vector for the dense layers.

### 3.2 Real-world images from folders, with augmentation

```python
train_ds = tf.keras.utils.image_dataset_from_directory(
    "data/train", image_size=(150, 150), batch_size=32, label_mode="binary")
val_ds = tf.keras.utils.image_dataset_from_directory(
    "data/validation", image_size=(150, 150), batch_size=32, label_mode="binary")

augment = tf.keras.Sequential([
    tf.keras.layers.RandomFlip("horizontal"),
    tf.keras.layers.RandomRotation(0.1),
    tf.keras.layers.RandomZoom(0.1),
])

model = tf.keras.Sequential([
    tf.keras.Input(shape=(150, 150, 3)),
    augment,                                   # active only during training
    tf.keras.layers.Rescaling(1.0 / 255),
    tf.keras.layers.Conv2D(32, 3, activation="relu"), tf.keras.layers.MaxPooling2D(),
    tf.keras.layers.Conv2D(64, 3, activation="relu"), tf.keras.layers.MaxPooling2D(),
    tf.keras.layers.Conv2D(128, 3, activation="relu"), tf.keras.layers.MaxPooling2D(),
    tf.keras.layers.Flatten(),
    tf.keras.layers.Dropout(0.5),
    tf.keras.layers.Dense(512, activation="relu"),
    tf.keras.layers.Dense(1, activation="sigmoid"),
])
model.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])
model.fit(train_ds, validation_data=val_ds, epochs=20,
          callbacks=[tf.keras.callbacks.EarlyStopping(patience=4, restore_best_weights=True)])
```

### 3.3 Transfer learning — the fastest route to high accuracy

```python
base = tf.keras.applications.MobileNetV2(input_shape=(160, 160, 3), include_top=False, weights="imagenet")
base.trainable = False                          # freeze the pretrained features

inputs = tf.keras.Input(shape=(160, 160, 3))
x = tf.keras.applications.mobilenet_v2.preprocess_input(inputs)
x = base(x, training=False)
x = tf.keras.layers.GlobalAveragePooling2D()(x)
x = tf.keras.layers.Dropout(0.2)(x)
outputs = tf.keras.layers.Dense(num_classes, activation="softmax")(x)
model = tf.keras.Model(inputs, outputs)
```

Then optionally **fine-tune**: unfreeze the top layers of `base` and train with a **much lower learning rate** (e.g. `1e-5`).

## 4. Natural language processing (14 h)

### 4.1 Text → numbers

1. **Tokenize** words into integers (vocabulary), handling unknown words (OOV).
2. **Pad/truncate** sequences to the same length.
3. **Embedding** layer turns each integer into a dense vector whose geometry captures meaning.

```python
vectorize = tf.keras.layers.TextVectorization(max_tokens=10_000, output_sequence_length=120)
vectorize.adapt(train_texts)                    # learn the vocabulary from training text only

model = tf.keras.Sequential([
    tf.keras.Input(shape=(1,), dtype=tf.string),
    vectorize,
    tf.keras.layers.Embedding(10_000, 16),
    tf.keras.layers.Bidirectional(tf.keras.layers.LSTM(32)),
    tf.keras.layers.Dense(24, activation="relu"),
    tf.keras.layers.Dense(1, activation="sigmoid"),   # e.g. sarcastic or not
])
model.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])
```

| Layer after the embedding | Strength |
|---|---|
| `GlobalAveragePooling1D` | Fastest baseline, ignores word order |
| `Conv1D` + pooling | Detects local phrases, fast |
| `LSTM` / `GRU` (often `Bidirectional`) | Captures order and long-range context |

**Overfitting is very common in NLP:** reduce vocabulary size and embedding dimension, add dropout, stop early.

### 4.2 Text generation (next-word prediction)

Build n-gram sequences from text, use the last word as the label (one-hot over the vocabulary), train an `Embedding → Bidirectional(LSTM) → Dense(vocab, softmax)` model with `categorical_crossentropy`, then predict one word at a time.

## 5. Time series (10 h)

### 5.1 Concepts

- **Trend**, **seasonality**, **noise**, **autocorrelation**. Split by **time** (train on the past, validate on the future — never shuffle before splitting).
- Baselines to beat: **naive forecast** (tomorrow = today) and **moving average**. Metric: **MAE**.

### 5.2 Windowed dataset — the function you must be able to write from memory

```python
def windowed_dataset(series, window_size, batch_size, shuffle_buffer):
    ds = tf.data.Dataset.from_tensor_slices(series)
    ds = ds.window(window_size + 1, shift=1, drop_remainder=True)
    ds = ds.flat_map(lambda w: w.batch(window_size + 1))
    ds = ds.shuffle(shuffle_buffer)
    ds = ds.map(lambda w: (w[:-1], w[-1]))          # features = past values, label = next value
    return ds.batch(batch_size).prefetch(1)
```

### 5.3 Model template (sunspots-style forecasting)

```python
model = tf.keras.Sequential([
    tf.keras.Input(shape=(window_size, 1)),
    tf.keras.layers.Conv1D(64, 3, padding="causal", activation="relu"),
    tf.keras.layers.LSTM(64, return_sequences=True),
    tf.keras.layers.LSTM(64),
    tf.keras.layers.Dense(30, activation="relu"),
    tf.keras.layers.Dense(1),
])
model.compile(optimizer=tf.keras.optimizers.Adam(1e-3), loss=tf.keras.losses.Huber(), metrics=["mae"])
```

Add a channel dimension to windows when using Conv1D/LSTM: `ds.map(lambda x, y: (tf.expand_dims(x, -1), y))`.
**Huber loss** is less sensitive to outliers than MSE — a good default for noisy series.

## 6. Mock exam and tactics

**Mock (4 h):** without looking at notes, build one model per category in a fresh environment:
① `y = 2x − 1` regression ② Fashion-MNIST ≥ 90% ③ horses-vs-humans or cats-vs-dogs with augmentation / transfer learning ④ sarcasm or IMDB sentiment ≥ 80% ⑤ sunspots or a synthetic series with MAE below the moving-average baseline.

**Tactics that passed the exam:**
- Read **each task's required input shape, output layer and metric** first; a wrong shape = zero points.
- Start with the **smallest model that could work**, submit it, then improve. Each category is graded independently.
- Use **EarlyStopping with `restore_best_weights=True`** so you never submit an overfitted epoch.
- Use transfer learning only if the task allows downloading weights.
- Keep a copy of the templates above in your head — they cover all five categories.

## 7. All the useful resources

| Resource | Link |
|---|---|
| Certificate page and candidate handbook | [tensorflow.org/certificate](https://www.tensorflow.org/certificate) |
| DeepLearning.AI TensorFlow Developer Professional Certificate (4 courses — the official prep) | [Coursera](https://www.coursera.org/professional-certificates/tensorflow-in-practice) |
| TensorFlow tutorials (images, text, time series) | [tensorflow.org/tutorials](https://www.tensorflow.org/tutorials) |
| Keras guides | [keras.io/guides](https://keras.io/guides/) |
| Next step: TensorFlow Advanced Techniques specialization (custom models, detection, segmentation) | [Coursera](https://www.coursera.org/specializations/tensorflow-advanced-techniques) |

---

<sub>Unofficial study material, not affiliated with or endorsed by Google or TensorFlow. Code templates use TensorFlow 2 / Keras APIs; check the docs for your installed version.</sub>
