# Venomous Snake Classification

A binary image classification project that distinguishes venomous and non-venomous snakes using Transfer Learning.

[![View Notebook](https://img.shields.io/badge/Notebook-nbviewer-orange)](https://nbviewer.org/github/akifayn/yilan-siniflandirma/blob/main/Zehirli_Yilan_Siniflandirma.ipynb)
[![Download Report](https://img.shields.io/badge/Report-PDF-red)](https://github.com/akifayn/yilan-siniflandirma/raw/main/Zehirli_Yilan_Siniflandirma_GUNCEL.pdf)

## Contributors

| Student ID | Name |
|------------|------|
| 214210040 | Muhammet Akif Ayan |
| 214210093 | Oguzhan Yalcin |
| 214210095 | Erkan Yigit |

## Project Overview

This project compares three Transfer Learning architectures for binary snake classification (Venomous vs Non-Venomous) using TensorFlow/Keras.

### Model Results

| Model | Epochs | Optimizer | Test Accuracy |
|-------|--------|-----------|---------------|
| ResNet50 | 44/50 | Adam | 56% |
| VGG16 | 16/50 | Adam | 79% |
| **MobileNetV2** | **50/50** | **Adam** | **87%** |

**Best model: MobileNetV2 — 87% test accuracy**

## Dataset

- **Training set:** 1,775 images (Non-Venomous: 715 / Venomous: 1,060)
- **Test set:** 269 images (Non-Venomous: 128 / Venomous: 141)
- **Image size:** 224x224x3

> The dataset is not included in this repository due to its size. Place the `Snake Images/` folder manually in the project directory.

## Installation

```bash
# Clone the repository
git clone https://github.com/akifayn/yilan-siniflandirma.git
cd yilan-siniflandirma

# Create virtual environment
python -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # Linux/Mac

# Install dependencies
pip install -r requirements.txt
```

## Usage

1. Place the `Snake Images/` folder in the project directory with the following structure:
```
Snake Images/
├── train/
│   ├── Non Venomous/
│   └── Venomous/
└── test/
    ├── Non Venomous/
    └── Venomous/
```
2. Open the notebook:
```bash
jupyter notebook Zehirli_Yilan_Siniflandirma.ipynb
```
3. Run cells in order

## Project Structure

```
yilan-siniflandirma/
├── Zehirli_Yilan_Siniflandirma.ipynb     # Main notebook
├── Zehirli_Yilan_Siniflandirma_GUNCEL.pdf  # Final training report
├── requirements.txt
└── README.md
```

## Technical Details

- **Framework:** TensorFlow / Keras
- **Task:** Binary classification (sigmoid output)
- **Data Augmentation:** Rotation, horizontal flip, zoom, width/height shift
- **Callbacks:** EarlyStopping + ReduceLROnPlateau
- **Class Balancing:** compute_class_weight (balanced)
- **Base Models:** ImageNet pretrained weights (frozen layers)
