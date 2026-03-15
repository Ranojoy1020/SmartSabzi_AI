# SmartSabzi AI -- Vegetable Recognition Model (V1)

SmartSabzi AI is an on-device vegetable recognition system designed for
small and medium vegetable vendors.\
The goal is to assist vendors in quickly identifying vegetables using a
mobile camera, reducing billing time and human errors.

This model is optimized for: - Offline-first usage - Low-to-mid range
Android devices - 1--2 second inference time - 10--15 vegetable classes
(V1 scope)

------------------------------------------------------------------------

## 📌 Project Objectives

-   Perform on-device image classification using TensorFlow Lite
-   Suggest top predicted vegetable with confidence score
-   Allow manual override (AI is assistive, not authoritative)
-   Maintain lightweight model size (\<10MB recommended)

------------------------------------------------------------------------

## 📂 Project Structure

    smartsabzi-ai/
    │
    ├── data/
    │   ├── raw/
    │   ├── processed/
    │   ├── train/
    │   ├── val/
    │   └── test/
    │
    ├── notebooks/
    │
    ├── src/
    │   ├── config.py
    │   ├── data_loader.py
    │   ├── augmentations.py
    │   ├── model.py
    │   ├── train.py
    │   ├── evaluate.py
    │   └── export_tflite.py
    │
    ├── models/
    │   ├── checkpoints/
    │   ├── final/
    │   └── tflite/
    │
    ├── logs/
    ├── requirements.txt
    ├── README.md
    └── .gitignore

------------------------------------------------------------------------

## 🥕 Supported Vegetables (V1 Example)

-   Tomato
-   Onion
-   Potato
-   Brinjal
-   Cabbage
-   Cauliflower
-   Carrot
-   Capsicum
-   Cucumber
-   Bottle Gourd
-   Bitter Gourd
-   Spinach
-   Green Chili
-   Garlic
-   Ginger

(Recommended: Do not exceed 15 classes in V1.)

------------------------------------------------------------------------

## 🧠 Model Architecture

-   Base Model: MobileNetV2 (Pretrained on ImageNet)
-   Input Size: 224x224
-   Transfer Learning (Frozen base layers initially)
-   Softmax Output Layer
-   Optimized and Quantized for TensorFlow Lite

------------------------------------------------------------------------

## 🗂 Dataset Guidelines

Recommended per class: - Minimum: 300--800 images - Ideal: 1000+ images

Data should include: - Different lighting conditions - Real market
backgrounds - Various angles - Partial occlusions - Different maturity
stages

Split Strategy: - 70% Training - 15% Validation - 15% Testing

------------------------------------------------------------------------

## ⚙️ Installation

Create a virtual environment and install dependencies:

``` bash
python -m venv venv
source venv/bin/activate   # Linux / Mac
venv\Scripts\activate      # Windows

pip install -r requirements.txt
```

------------------------------------------------------------------------

## 🚀 Training the Model

Run:

``` bash
python src/train.py
```

The best model checkpoint will be saved inside:

    models/checkpoints/

Final selected model:

    models/final/

------------------------------------------------------------------------

## 📊 Evaluating the Model

``` bash
python src/evaluate.py
```

This will output: - Test accuracy - Confusion matrix - Per-class
performance

------------------------------------------------------------------------

## 📱 Exporting to TensorFlow Lite

``` bash
python src/export_tflite.py
```

Output file:

    models/tflite/vegetable_model_v1.tflite

This file is integrated into the Android application.

------------------------------------------------------------------------

## 📈 Performance Targets (V1)

-   Validation Accuracy: 85--92%
-   Real-world Accuracy: 75--85%
-   Inference Time: \< 1 second (target)
-   Model Size: \< 10MB

------------------------------------------------------------------------

## 🔄 Continuous Improvement Strategy

1.  Deploy to vendor
2.  Collect misclassified samples
3.  Add to dataset
4.  Retrain model
5.  Release improved version

Model versions should be tracked clearly (v1, v1.1, v2, etc.).

------------------------------------------------------------------------

## ⚠️ Important Notes

-   AI predictions must always allow manual override.
-   Do not increase classes without sufficient dataset size.
-   Always test quantized TFLite model before production release.
-   Never train directly on raw images without cleaning.

------------------------------------------------------------------------

## 📌 Version

SmartSabzi AI -- V1\
Designed for offline-first vegetable vendor assistance.
