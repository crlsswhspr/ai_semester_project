# UW-Madison GI Tract Image Segmentation

## Project Overview

This project focuses on automatic segmentation of gastrointestinal (GI) organs in MRI scans using deep learning.

The goal is to segment three organs:
- Large bowel
- Small bowel
- Stomach

Automated segmentation may help reduce manual annotation effort and support research into MRI-guided radiation therapy.

## Dataset

We use the [UW-Madison GI Tract Image Segmentation](https://www.kaggle.com/competitions/uw-madison-gi-tract-image-segmentation) dataset from Kaggle.

The training dataset contains MRI slices with ground-truth segmentation masks encoded using Run-Length Encoding (RLE).

## Methods

We compare two main approaches:

### 1. 2D U-Net Baseline
- Input: one MRI slice.
- Architecture: U-Net with a pretrained ResNet34 encoder.
- Loss function: Dice loss.

### 2. 2.5D U-Net
- Input: three neighboring MRI slices used as input channels.
- Architecture: U-Net with a pretrained ResNet34 encoder.
- Loss function: combined Dice and Binary Cross-Entropy (BCE).

We use five-fold cross-validation grouped by patient to reduce data leakage between training and validation sets.

## Evaluation

The primary evaluation metric is the Dice coefficient.

The notebook calculates Dice scores for:
- Large bowel
- Small bowel
- Stomach

Out-of-fold (OOF) predictions are used to compare the two approaches.

## Repository Contents

- `GI_Tract_Midterm.ipynb` — notebook containing data download, preprocessing, model training, and evaluation.
- `README.md` — project overview and instructions.

Training logs, model checkpoints, and OOF prediction files stored separately in Google Drive.

## Requirements

The notebook is designed for Google Colab and uses Python.

Main dependencies include:
- PyTorch
- pandas
- NumPy
- OpenCV
- Matplotlib
- Kaggle CLI

The notebook contains the required setup and import cells.

## How to Run

1. Open the notebook in Google Colab.
2. Select a GPU runtime if available.
3. Accept the rules of the Kaggle competition.
4. Add a Colab Secret named `KAGGLE_API_TOKEN` containing your Kaggle API token.
5. Enable access to that secret for the notebook.
6. Run the notebook cells in order to download the dataset, preprocess the data, train the models, and evaluate the predictions.

## Team

- Anastasiia Yosypiv
- Jiya Lal

AI Semester Project, Ukrainian Catholic University, 2026.
