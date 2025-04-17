---
layout: page
permalink: /data/
title: Data Resources
description: Explore datasets available for diabetic retinopathy and ophthalmological research.
nav: true
nav_order: 2
---

Below is a curated list of datasets available for research in diabetic retinopathy and ophthalmological analysis. These datasets cover a wide range of retinal imaging challenges, including multilabel classification, lesion segmentation, and disease progression analysis.

- A Brazilian Multilabel Ophthalmological Dataset: A multilabel dataset containing retinal images with annotations for various ophthalmological conditions.
  - [BRSET](https://physionet.org/content/brazilian-ophthalmological/1.0.1/)

- Messidor-1 & Messidor-2 Dataset: A widely used dataset for diabetic retinopathy detection and grading, containing fundus images.
  - [Messidor Dataset](https://www.adcis.net/en/third-party/messidor/)

- RFMiD Dataset: A large-scale dataset for retinal fundus disease classification, with multiple annotated diseases.
  - [RFMiD Dataset](https://ieee-dataport.org/open-access/retinal-fundus-multi-disease-image-dataset-rfmid)

- APOTS Dataset: A dataset focused on retinal optical tomography images, enabling the study of various retinal conditions.
  - [APTOS-2019 Dataset](https://www.kaggle.com/c/aptos2019-blindness-detection/overview)

- IDRiD Dataset: A comprehensive dataset for diabetic retinopathy lesion segmentation, disease grading, and severity assessment.
  - [IDRiD Dataset](https://idrid.grand-challenge.org/)

- MICCAI 2023 MMAC (Myopic Maculopathy Analysis Challenge): A dataset from the MICCAI 2023 challenge focused on myopic maculopathy segmentation and classification.
  - [MMAC Dataset](https://codalab.lisn.upsaclay.fr/competitions/12441)

- EyePACS Dataset: A large-scale dataset used in the Kaggle diabetic retinopathy detection competition, containing fundus images with severity labels.
  - *[EyePACS Dataset](https://www.kaggle.com/c/diabetic-retinopathy-detection/data)

- DRIVE Dataset (Digital Retinal Images for Vessel Extraction): A dataset focused on retinal vessel segmentation.
  - [DRIVE Dataset](https://drive.grand-challenge.org/)

- STARE Dataset: A dataset containing images for retinal disease diagnosis and vessel segmentation.
  - [STARE Dataset](https://cecas.clemson.edu/~ahoover/stare/)


Data Preprocessing

BRSET: Downloaded the data from the Physionet.org website.
The BRSET (Brazilian Retinography SET) dataset is a multilabel ophthalmological dataset containing high-resolution retinal fundus photographs. It includes labels for Diabetic Retinopathy (DR) severity based on the ICDR scale (0–4), where:
0 = No Retinopathy, 1 = Mild Non-Proliferative DR, 2 = Moderate Non-Proliferative DR, 3 = Severe Non-Proliferative DR, 4 = Proliferative DR.

We have used the dataset primarily for DR severity classification, which is a multiclass image classification problem.

1. We loaded the labels from the CSV file and ensured that the DR_ICDR column (containing DR grades) was treated as integers.
2. We resized each image to 128x128 pixels to standardize input dimensions 
3. All images were normalized to the range [0, 1] by dividing pixel values by 255
4. We converted categorical DR severity labels (0–4) into one-hot vectors, suitable for training with softmax output and categorical_crossentropy loss.

Dataset path:/mnt/projects/zhuangyo_project/a-brazilian-multilabel-ophthalmological-dataset-brset-1.0.1

RFMiD- Downloaded the dataset from the link as mentioned above.
RFMiD dataset has compressed .zip files that contain images and corresponding label CSVs. This preprocessing script unpacks those files, cleans up the directory structure.
1. Unzipping the dataset: The script scans for all the .zip files, which are then extracted into a temporary folder structure. The script also takes care of the nested folder.
2. Identifying the folder structure: As RFMiD has two datasets, All Classes Dataset and Challenge Dataset.
3. Organizing Image Subsets: Images are organized into three subsets Training Set, Validation Set, Testing Set. All images are moved to those structured folders.
4. Standardizing CSV files: All CSV files are renamed to training_label.csv, validation_labels.csv, testing_labels.csv, and they are moved under Groundtruths folder.

Dataset path: /mnt/projects/zhuangyo_project/data/RFMiD

Other dataset IDRiD, Messidor1, Messidor2 and MMAC are under the same path
/mnt/projects/zhuangyo_project/data/