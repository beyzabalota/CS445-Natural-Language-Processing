# CS445 - Homework 2: Song Lyrics Classification

This repository contains my implementation for CS445 Homework 2 (Fall 2024-2025), where the objective was to classify song lyrics by artist using Natural Language Processing (NLP) techniques and classical machine learning models.

## Objective
The goal of this assignment was to:
- Build a **Naive Bayes classifier** from scratch using Bag-of-Words features.
- Apply **data preprocessing**, including cleaning, tokenization, stopword removal, and stemming.
- Use **TF-IDF** and **character n-grams** as features to train and compare multiple classification models (e.g., Logistic Regression, SVM).
- Evaluate performance using **accuracy** and **F1-score**, and visualize with **confusion matrices**.

## Dataset
- The dataset was provided in a `archive.zip` file that contained thousands of lyrics stored across multiple CSV files.
- Lyrics were labeled with corresponding **artist names**.
- Dataset was preprocessed and split into **train/dev/test** sets with a 70/15/15 ratio.

> **Note:** The dataset is not publicly available. If needed, request access through course materials.

## Models Used
- **Naive Bayes (custom implementation)**
- **Logistic Regression (TF-IDF, word n-grams)**
- **Support Vector Machine (TF-IDF, char n-grams)**

## Key Steps
1. Load and concatenate zip CSVs.
2. Clean missing/empty lyrics.
3. Explore most frequent artists (EDA).
4. Preprocess lyrics (lowercasing, punctuation removal, stopword filtering, stemming).
5. Implement classifiers and evaluate them on dev/test sets.

## Evaluation
Final evaluation was based on:
- Accuracy
- Weighted F1 Score
- Confusion matrices for model comparison
