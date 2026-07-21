# Cats vs Dogs Image Classification

A binary image classification project using a Convolutional Neural
Network (CNN) to classify images as **Cat** or **Dog**.

## Dataset

The project uses the Microsoft Cats vs Dogs dataset. The images are
organized into two classes:

-   `Cat`
-   `Dog`

Before training, corrupted images were detected and removed.

## Preprocessing

-   Images resized to **224 × 224**
-   Pixel values rescaled to **0--1**
-   Training data augmentation:
    -   Rotation
    -   Shearing
    -   Width and height shifting
    -   Zooming

## Model

The CNN consists of:

-   3 convolutional layers
-   Max pooling layers
-   Batch normalization
-   A dense layer
-   Dropout (`0.4`)
-   A sigmoid output layer for binary classification

### Architecture

``` text
Input (224 × 224 × 3)
        ↓
Conv2D (32 filters, 3×3) + ReLU
        ↓
MaxPooling (2×2)
        ↓
Conv2D (64 filters, 3×3) + ReLU
        ↓
MaxPooling (2×2)
        ↓
Batch Normalization
        ↓
Conv2D (128 filters, 3×3) + ReLU
        ↓
MaxPooling (2×2)
        ↓
Flatten
        ↓
Dense (64) + ReLU
        ↓
Dropout (0.4)
        ↓
Dense (1) + Sigmoid
```

## Training

-   **Optimizer:** Adam
-   **Learning rate:** `0.001`
-   **Loss:** Binary Crossentropy
-   **Batch size:** `32`
-   **Maximum epochs:** `30`

Early stopping and model checkpointing were used to preserve the best
model weights.

## Results

The model achieved approximately:

-   **Accuracy:** 84.93%
-   **Cat F1-score:** 84.56%
-   **Dog F1-score:** 85.29%

The model was evaluated using:

-   Accuracy
-   Precision
-   Recall
-   F1-score
-   Confusion matrix

## Model Compression

The original `Model.h5` file was approximately **64 MB**.

To reduce the model size, the trained weights were converted from
`float32` to `float16` and saved as:

``` text
Model_float16.keras
```

This reduces the storage size of the model while preserving the trained
CNN architecture.

## Technologies

-   Python
-   TensorFlow / Keras
-   NumPy
-   Pandas
-   Matplotlib
-   Seaborn
-   Scikit-learn
-   Pillow

## Dataset

The dataset used in this project is the [Microsoft Cats vs Dogs Dataset]([https://www.microsoft.com/en-us/download/details.aspx?id=54765](https://download.microsoft.com/download/3/E/1/3E1C3F21-ECDB-4869-8368-6DEBA77B919F/kagglecatsanddogs_5340.zip))
