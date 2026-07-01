# Computer-Vision-Project

Dental X-ray Synthetic Generation & Segmentation

The pipeline has two stages:

1. SYNgen_final.ipynb → generates synthetic ortho-panoramic X-ray images from real samples using a GAN and post-processing.
2. Segmentation_final.ipynb → trains segmentation models (U-Net and TransUNet) on real data, evaluates them, and tests generalization on the synthetic images produced by stage 1.


1) SYNgen_final.ipynb (Synthetic Data Generator)

Goal: Create a synthetic dataset to reduce the domain gap and augment training data.

Steps:

-GAN training/inference: trains two different Pix2Pix models to synthesize and generate dental X-rays images.

-Post-processing: histogram matching and domain adaptation techniques to improve realism.

-Outputs: generated images, saved into a folder for segmentation use.

2) Segmentation_final.ipynb (Training & Evaluation)

Goal: Train segmentation models on real data and evaluate them on both real and synthetic images.

Steps:

-Models: U-Net (MobileNetV2 backbone) and TransUNet.

-Dataset: supports different modes → real, synt, or mix (real + synthetic).

-Training: optimizer (AdamW), scheduler, AMP training.

-Evaluation: mIoU, Dice, per-class scores.

-Outputs: predictions and metrics report in a .txt file



Quickstart

Option A — Full pipeline

1. Run SYNgen_final.ipynb in Colab → generates the link of the synthetic images folder.
2. Copy the new generated link in Segmentation_final.ipynb.
3. Run Segmentation_final.ipynb → train on real, synthetic, or mixed dataset, and evaluate on both domains.

Option B — Segmentation only

1. Ensure the synthetic data hasn’t expired and exists.
2. Run Segmentation_final.ipynb.


Editable Parameters on 'Globals' section of both ipynb files

IMG_SIZE

LAMBDA_L1

LAMBDA_PERC

DATA_MODE

DATA_MODE_VAL

SYN_RATIO

MIX_STRATEGY

MIX_STRATEGY_VAL

batch size

epochs

LR
