---
layout: page
title: Heart-Rhythm Classification from ECG Data
description: CNN classifier for heart-rhythm anomalies. Ranked 14th of 131 participants.
importance: 2
category: Coursework
---

The goal of this challenge was to classify single-lead ECG recordings into four heart-rhythm classes. The model ranked 14th of 131 participants.

- **Preprocessing:** wavelet denoising with soft thresholding, median filtering to remove baseline drift, and padding or cropping all recordings to the same length.
- **Model:** a 1D convolutional network with batch normalisation and dropout, followed by two bidirectional LSTM layers and a fully connected classifier, implemented in PyTorch.
- **Training:** Adam with an exponentially decaying learning rate; the number of epochs was chosen on a stratified validation split using the F1 score, then the model was retrained on all data.

[Code on GitHub](https://github.com/szekerbalazs/szekerbalazs/blob/main/ECGAnalysis/ECGAnalysis.py)
