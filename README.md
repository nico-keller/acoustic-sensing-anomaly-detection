# Acoustic Anomaly Detection

This repository contains the Jupyter Notebooks for the Bachelor's Thesis Accoustic Sensing for Anomaly Detection (Spectral-Temporal Anomaly Detection for Remote, High-altitude Hydro-power Plants).

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Data Preparation](#data-preparation)
3. [Models](#models)
4. [Usage](#usage)
5. [Requirements](#requirements)
6. [Directory Structure](#directory-structure)
7. [Contributing](#contributing)
8. [License](#license)

---

## Project Overview

This project aims to identify anomalies in machine sound recordings by:
- Generating Mel-spectrograms from raw `.wav` audio files,
- Splitting the spectrograms into overlapping frames,
- Training and evaluating various anomaly detection models.
- Additionally the EDA notebooks analyze the recordings in detail.

**Key Features:**
- End-to-end pipeline for data loading, preprocessing, feature extraction, model training, and evaluation.
- Multiple unsupervised models (K-means, One-Class SVM, Autoencoders) to learn normal machine behavior and flag anomalies.
- Visualization tools for raw waveforms, spectrograms, reconstruction errors, and confusion matrices.

---

## Models

1. **K-means Clustering (Unsupervised):**  
   - Trains on normal frames to learn a single cluster center.  
   - Distances to this center act as anomaly scores.

2. **One-Class SVM (Unsupervised):**  
   - Trained on normal data only.  
   - The decision function classifies outliers (anomalies).

3. **LSTM Autoencoder (Unsupervised):**  
   - Treats each frame as a sequence (time dimension = frame width, features = Mel frequency bins).  
   - High reconstruction error flags anomalies.
