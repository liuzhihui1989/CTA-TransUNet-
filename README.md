# CTA-TransUNet: Skin Lesion Segmentation

## Project Overview

This project implements the **CTA-TransUNet**, a skin lesion segmentation model based on **Cross-Axis Transformer Context Fusion (CTCF)** and **U-Net**, designed to precisely segment lesion areas from skin images. The model integrates Cross-Axis Transformer Context Fusion and Multi-Level Adaptive Feature Fusion, enabling it to capture multi-scale and contextual information, which significantly enhances segmentation accuracy.

## Installation Dependencies

To install all the required dependencies, use `requirements.txt`:

```bash
pip install -r requirements.txt
```

## Data Preparation

This project uses the publicly available datasets **ISIC 2016**, **ISIC 2017**, **ISIC 2018**, and **PH2**. Ensure that the datasets are organized in the following structure:

1. Download the ISIC datasets from [ISIC 2016/2017/2018 Dataset](https://challenge.isic-archive.com/data/) and place them into the corresponding folders: `datasets/ISIC2016`, `datasets/ISIC2017`, and `datasets/ISIC2018`.
2. Download the PH2 dataset from [PH2 Dataset](https://www.fc.up.pt/addi/ph2%20database.html) and place it in the `datasets/PH2` folder.

Once you have downloaded the data, you need to preprocess it using the following steps:

### 1. Resize the Dataset

To increase network training speed, you can use the `preprocess_resize_dataset.py` script to resize the dataset to your desired dimensions.

**How to use `preprocess_resize_dataset.py`:**

* When running the script, you need to specify the input dataset directory and the output directory.
* Use the `--size` parameter to specify the target dimensions (default is 576x576).

**Command line example:**

```bash
python preprocess_resize_dataset.py --input_dir data/ISIC/2016/images --output_dir data/ISIC/2016/resized_images --size 576,576
```

### 2. Split the Dataset

Use the `preprocess_split_dataset.py` script to specify training, validation, and test data, and store them in the `data` folder. The generated files will be used for training and testing the network.

**How to use `preprocess_split_dataset.py`:**

* When running the script, specify the input dataset directory and the output directory.
* You can adjust the proportions of training, validation, and test data (default is 70% training, 15% validation, 15% test).

**Command line example:**

```bash
python preprocess_split_dataset.py --input_dir data/ISIC/2016/images --output_dir data/ISIC/2016/split_data --train_ratio 0.7 --val_ratio 0.15 --test_ratio 0.15
```

## Train the Model

To start training the model, run the following command:

```bash
python main.py --train --lr 0.01 --epochs 100
```

## Evaluate the Model

To evaluate the model, run the following command:

```bash
python main.py --evaluate
```

---


