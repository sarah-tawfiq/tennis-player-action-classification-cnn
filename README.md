# 🎾 Tennis Player Action Classification using CNN

##  Project Description

This project is an end-to-end image classification system that identifies the tennis action performed by a player in an image.

The model classifies images into four different categories:

- Backhand
- Forehand
- Ready Position
- Serve

A Convolutional Neural Network (CNN) was built and trained completely from scratch using TensorFlow/Keras, without using any pre-trained models or transfer learning.

The project was implemented using **Google Colab**.

---

##  Dataset

- **Dataset:** Tennis Player Actions Dataset
- **Source:** [Tennis Player Actions Dataset - Kaggle](https://www.kaggle.com/datasets/orvile/tennis-player-actions-dataset)
- **Total Images:** 2,000
- **Number of Classes:** 4
- **Images per Class:** 500

### Classes

- Backhand
- Forehand
- Ready Position
- Serve

> **Note:** The original dataset contains pose annotation files, but they were not used in this project. Only the image folders were used because this project focuses strictly on image classification.

---

## Data Preprocessing

The following preprocessing steps were applied:

- Images were resized to **150 × 150 pixels**.
- Pixel values were normalized using **Rescaling (1/255)**.
- The dataset was split into:
  - **80% Training**
  - **20% Validation**
- Images were loaded using TensorFlow's `image_dataset_from_directory`.
- The training dataset was shuffled and optimized using caching and prefetching.
- Data augmentation was applied to improve model generalization.

### Data Augmentation

The following augmentation techniques were used:

- Random Horizontal Flip
- Random Rotation
- Random Zoom

---

##  Installation

Clone the repository:

```bash
git clone https://github.com/YourUsername/Tennis-Player-Action-Classification-CNN.git
cd Tennis-Player-Action-Classification-CNN
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

The notebook was developed and executed using **Google Colab**.

---

## Requirements

The main libraries used in this project are:

- TensorFlow
- NumPy
- OpenCV
- Matplotlib
- Seaborn
- Scikit-learn

All required dependencies are listed in:

```text
requirements.txt
```

---

## Model Architecture

The CNN model was built completely from scratch.

```text
Input Image (150 × 150 × 3)
        ↓
Rescaling (1/255)
        ↓
Conv2D (32 filters, 3×3) + ReLU
        ↓
MaxPooling2D
        ↓
Conv2D (64 filters, 3×3) + ReLU
        ↓
MaxPooling2D
        ↓
Conv2D (128 filters, 3×3) + ReLU
        ↓
MaxPooling2D
        ↓
Flatten
        ↓
Dense (128) + ReLU
        ↓
Dropout (0.5)
        ↓
Dense (4) + Softmax
```

### Training Configuration

| Parameter | Value |
|-----------|-------|
| Optimizer | Adam |
| Loss Function | Sparse Categorical Crossentropy |
| Metric | Accuracy |
| Batch Size | 32 |
| Image Size | 150 × 150 |
| Maximum Epochs | 50 |
| Early Stopping | Enabled |

Early Stopping was used to prevent overfitting by monitoring the validation loss.

---

## 📊 Results

The model was trained for a maximum of **50 epochs** with Early Stopping enabled.

Training stopped at **Epoch 17**, and the best model weights were restored from **Epoch 14** based on the validation loss.

### Best Model Performance

| Metric | Value |
|--------|------:|
| Validation Accuracy | **87.00%** |
| Validation Loss | **0.4258** |

The highest validation accuracy observed during training was **88.00%** at Epoch 17. However, the final saved model uses the weights from **Epoch 14**, because Early Stopping was monitoring `val_loss`.

The notebook includes the following evaluation results:

- Training and Validation Accuracy curves
- Training and Validation Loss curves
- Confusion Matrix
- Classification Report

---

##  Prediction

After training, the saved CNN model can be used to predict the tennis action in a new image.

The model returns:

- Predicted class
- Prediction confidence

Possible predictions are:

```text
Backhand
Forehand
Ready Position
Serve
```

A sample prediction was performed using an image from the **Serve** class.

---

## Saved Model

The trained model was saved in Keras format:

```text
saved_model/tennis_model.keras
```

The model can be loaded using:

```python
model = tf.keras.models.load_model(
    "saved_model/tennis_model.keras"
)
```

---

##  Project Structure

```text
Tennis-Player-Action-Classification-CNN/
│
├── dataset/
│
├── notebook.ipynb
│
├── README.md
│
├── report.pdf
│
├── requirements.txt
│
├── saved_model/
│   └── tennis_model.keras
│
└── predictions/
```

---


## Author

**Sarah Tawfiq**

## Instructor

**Mohamed Waleed**
