# Positioning Dory

This project is focused on data processing and estimating missing Received Signal Strength Indicator (RSSI) values for WiFi fingerprinting. Additionally, it includes a positioning algorithm to locate a target device named "Dory" based on the estimated RSSI values as the Final project for the IOT and Wireless Internet course (A.Y. 21/22) at Politecnico di Milano.

## Table of Contents
- [Introduction](#introduction)
- [Data Processing](#data-processing)
  - [Estimating Missing RSSI Values](#estimating-missing-rssi-values)
  - [Creating the Final Fingerprint Dataset](#creating-the-final-fingerprint-dataset)
- [Positioning Dory](#positioning-dory)
- [Files](#files)

## Introduction
WiFi fingerprinting is a technique used for indoor positioning systems. It involves collecting RSSI values from multiple access points at various locations in the target area to create a database of fingerprints. These fingerprints can be later used to determine the location of a target device by comparing its RSSI values with the pre-collected data.

## Data Processing
The data processing part involves estimating the missing RSSI values and creating the final fingerprint dataset.

### Estimating Missing RSSI Values
The missing RSSI values are estimated by interpolating the RSSI values for odd rows and columns. The process includes:
1. Creating even super row vectors for each row by combining the vectors of positions in that row.
2. Estimating odd super row vectors by averaging adjacent even super row vectors.
3. Extracting column super vectors by splitting the odd super row vectors.
4. Estimating RSSIs corresponding to odd super columns vectors by averaging adjacent column super vectors.

### Creating the Final Fingerprint Dataset
The final fingerprint dataset is created by converting the RSSI vector of positions with a dimensionality of 1x30 to vectors of 1x6. The choice of using max, mean, or min value for this transformation is controlled by the `max`, `mean`, or `min` flag respectively. The resulting dataset contains the estimated RSSI values and corresponding position coordinates.

## Positioning Dory
The positioning algorithm uses cosine similarity between Dory's RSSI vector and the fingerprint dataset to determine Dory's position. The cosine similarity calculates the cosine of the angle between two non-zero vectors and measures the similarity between them. The position with the highest similarity is considered as Dory's position.

## Files
- The processed final fingerprint dataset is stored in `final_estimated_fp_ds.csv` and can be downloaded.
- The intermediate fingerprint dataset after RSSI estimation is saved in `final_estimated_fp_ds_new.csv` and can be downloaded.

Please make sure you have the required libraries, such as pandas and numpy, installed in your Python environment to execute the code successfully. The code provided is designed to work in the Google Colab environment.
