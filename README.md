# Acoustic Anomaly Detection

This repository contains code and notebooks for detecting anomalies in acoustic data captured from industrial machines. The project focuses on preparing and analyzing Mel-spectrogram frames, then applying multiple models (unsupervised and supervised) to detect anomalous events.

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

**Key Features:**
- End-to-end pipeline for data loading, preprocessing, feature extraction, model training, and evaluation.
- Multiple unsupervised models (K-means, One-Class SVM, Autoencoders) to learn normal machine behavior and flag anomalies.
- Visualization tools for raw waveforms, spectrograms, reconstruction errors, and confusion matrices.

---

## Data Preparation

1. **Audio Loading:**  
   - The scripts load `.wav` files (normal vs. anomalous recordings) using [librosa](https://librosa.org/).

2. **Mel-Spectrogram Generation:**  
   - A Mel-spectrogram is created for each audio file, normalized to `[0, 1]`.

3. **Frame Slicing:**  
   - The spectrogram is split into overlapping frames based on a configurable frame length (e.g., 0.6 seconds) and overlap ratio.

4. **Train/Validation/Test Split:**  
   - The normal frames are split into train and validation sets.  
   - The test set contains both normal (held-out) and anomalous frames.

---

## Models

1. **K-means Clustering (Unsupervised):**  
   - Trains on normal frames to learn a single cluster center.  
   - Distances to this center act as anomaly scores.

2. **One-Class SVM (Unsupervised):**  
   - Trained on normal data only.  
   - The decision function classifies outliers (anomalies).

3. **Convolutional Autoencoder (Unsupervised):**  
   - Learns to reconstruct normal frames.  
   - High reconstruction error indicates an anomaly.

4. **LSTM Autoencoder (Unsupervised):**  
   - Treats each frame as a sequence (time dimension = frame width, features = Mel frequency bins).  
   - High reconstruction error flags anomalies.