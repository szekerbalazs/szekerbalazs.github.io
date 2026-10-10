---
layout: page
title: Brain Age Prediction from MRI Features
description: Stacking ensemble regression
importance: 1
category: Coursework
---

The goal of this prediction challenge was to estimate a person's age from features extracted from brain MRI scans. Our model ranked 13th of 150 teams.

- **Preprocessing:** correlation-based feature selection, median imputation of missing values and standardisation.
- **Model:** a stacking ensemble of linear and ridge regression, k-nearest neighbours, random forest, gradient boosting, support vector regression and a Gaussian process (Matérn and rational quadratic kernels), combined by a linear meta-model.
- **Evaluation:** 5-fold cross-validation with the R² score.

[Code on GitHub](https://github.com/szekerbalazs/szekerbalazs/blob/main/BrainAgePrediction/BrainAgePrediction.ipynb)
