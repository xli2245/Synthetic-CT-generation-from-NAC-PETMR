# Synthetic-CT-generation-from-NAC-PETMR 
Simultaneous PET/MR scanners combine the high sensitivity of MR imaging with the functional imaging of PET. However, attenuation correction of breast PET/MR imaging is technically challenging. The purpose of this study is to establish a robust attenuation correction algorithm for breast PET/MR images that relies on deep learning (DL) to recreate the missing portions of the patient’s anatomy (truncation completion), as well as to provide bone information for attenuation correction from only the PET data. Three DL models, U-Net with mean absolute error loss (DL_MAE) model, U-Net with mean squared error loss (DL_MSE) model, and U-Net with perceptual loss (DL_Perceptual) model, were trained to predict synthetic CT images (sCT) for PET attenuation correction (AC) given non-attenuation corrected (NAC) PET (PET/MR) images as inputs. The DL and Dixon-based sCT reconstructed PET images were compared against those reconstructed from CT images by calculating the percent error of the standardized uptake value (SUV) and conducting Wilcoxon signed rank statistical tests. 
## Table of Contents
- [Setup](#setup)
- [Environment](#environment)
- [Perceptual Loss Framework](#perceptual-loss-framework)
  - [Discriminator](#discriminator)
  - [Generator](#generator)
  - [Prediction](#prediction)
## Setup
Clone this repo:
```
git clone [https://github.com/xli2245/CS839-sentiment-classification](https://github.com/xli2245/Synthetic-CT-generation-from-NAC-PETMR)
```
## Environment
This project is implemented using Keras.
1. create a conda environment
```
conda create -n tf2 python=3.7
conda activate tf2
```
2. install necessary packages
```
conda install -c anaconda keras-gpu=2.3.1
conda install -c anaconda tensorflow-gpu=1.14.0
conda install -c conda-forge nibabel
conda install -c conda-forge matplotlib=3.4.3
conda install -c anaconda scikit-learn
conda install -c anaconda scikit-image
```
## Perceptual Loss Framework
![Main framework](https://github.com/xli2245/Synthetic-CT-generation-from-NAC-PETMR/blob/main/main%20framework.png)
### Discriminator
The model training, validation and testing are performed using the [Monai Docker](https://hub.docker.com/r/projectmonai/monai).
### Generator
1.  Model training
```
python train.py
```
2. Model validation / testing
```
python predict.py
```
### Prediction
For the fin-bert and roberta-base pretrained model, the download links are provided under each folder. The downloaded pretrained models for the others like (BERT, DeBERTa ...) can be also be found in the google drive folder. The name is "model.tar.gz".

To unzip the model weight
```
tar -xvf ./model.tar.gz
mv ./model/* ./
rm -rf ./model
```


