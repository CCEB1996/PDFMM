# PDFMM: A Prompt-Driven FusionMamba Model for Accurate Skin Lesion Segmentation

This repository accompanies the manuscript **"PDFMM: A Prompt-Driven FusionMamba Model for Accurate Skin Lesion Segmentation"**, submitted to *Knowledge-Based Systems (KBS)*.

---

## 📢 Code Availability

> **The source code is not yet publicly available.**
>
> This paper is currently under peer review at *Knowledge-Based Systems*.  **The complete source code, training and evaluation scripts, configuration files, and pretrained weights will be open-sourced in this repository once the paper is accepted for publication.**
>
> We are committed to full reproducibility. Upon acceptance, this notice will be replaced with detailed installation, training, and inference instructions.

---

## Overview

Accurate segmentation of skin lesions in dermoscopic images is a prerequisite for computer-aided diagnosis and for the quantitative monitoring of skin cancer. The task is difficult because lesions show blurred boundaries, low contrast against the surrounding skin, and large variation in scale, shape, and colour, often compounded by hair and imaging artefacts.

**PDFMM (Prompt-Driven FusionMamba Model)** is a parameter-efficient framework that adapts the **SAM-Med2D** vision foundation model for skin lesion segmentation. It represents global lesion context and local boundary detail jointly within a single promptable encoder, achieving state-of-the-art accuracy while keeping the pretrained backbone frozen.

## Results

PDFMM is evaluated on three public dermoscopic benchmarks. On every benchmark it surpasses recent state-of-the-art methods, including recent adaptations of the Segment Anything Model, by at least **2.9 percentage points in Dice**.

| Dataset    | Role                | Dice (%) | IoU (%) |
|------------|---------------------|:--------:|:-------:|
| ISIC 2017  | Train / test        |  93.03   |  87.31  |
| ISIC 2018  | Train / test        |  94.25   |  89.33  |
| PH²        | External validation |  95.36   |  91.18  |

PH² is reserved entirely as an external test set: the model trained on ISIC 2018 is evaluated directly on the 200 PH² images **without any further adaptation**, demonstrating strong cross-dataset generalization.

## Datasets

All three datasets are publicly available from their original providers.

| Dataset    | Images | Train / Val / Test | Source |
|------------|:------:|:------------------:|--------|
| ISIC 2017  |  2750  |   2000 / 150 / 600 | International Skin Imaging Collaboration |
| ISIC 2018  |  2594  |  2076 / 259 / 259  | ISIC 2018 (Task 1) |
| PH²        |   200  |     0 / 0 / 200    | PH² Database |

All images are resized to **256 × 256** pixels for uniform batch training.

## Environment

The experiments were conducted under the following configuration (to be detailed with a full dependency list upon code release):

- Ubuntu 22.04
- Python + PyTorch 2.6.0
- Single NVIDIA A800 GPU (80 GB)
- Image encoder initialized from the **SAM-Med2D** backbone
- Optimizer: Adam, initial learning rate `1e-4`, cosine annealing schedule
- Up to 100 epochs; the checkpoint with the highest validation Dice is retained


## License

A license will be specified at the time of code release.

---

*This repository currently serves as a placeholder for the upcoming code release. Thank you for your interest in our work.*
