# CS445 - Homework 3: POS Tagging with Hidden Markov Models (HMM)

This repository contains my implementation for CS445 Homework 3 (Fall 2024-2025), where the objective was to build a **Part-of-Speech (POS) Tagger** using the **Hidden Markov Model (HMM)** and the **Viterbi algorithm** from scratch.

## Objective

The main goals of this homework were to:

- Parse and preprocess datasets in CoNLL format.
- Filter and use specific POS tags (e.g., `"ADJ", "ADV", "NOUN", "VERB", "PUNCT"`).
- Train an HMM using **Maximum Likelihood Estimation (MLE)** for:
  - **Transition probabilities** between tags.
  - **Emission probabilities** of words given tags.
- Implement the **Viterbi algorithm** to predict tags on unseen sentences.
- Evaluate model performance using **Accuracy**, **F1-score**, and **Confusion Matrix**.
- Experiment with **smoothing techniques** to handle unseen words/tags and improve results.

## Dataset

- Format: `.conllu` files containing tokenized and tagged sentences.
- Two datasets were used:
  - `web.conllu`
  - `wiki.conllu`
- After merging both datasets, a total of **4851 sentences** were processed.
- Sentences were split into training and testing sets (80%/20%).

> **Tag filtering:** In some experiments, sentences were filtered to include only the tags: `"ADJ", "ADV", "NOUN", "VERB", "PUNCT"` for a simpler and more controlled POS tagging task.

## Implementation Overview

### 1. Data Preparation
- CoNLL-U file reader: parses the files and stores `(word, tag)` tuples grouped into sentences.
- POS filtering: keeps only desired POS tags per assignment instruction.

### 2. Train/Test Split
- Sentences are randomly shuffled and split (80% training / 20% test).
- Filtering is applied *before* splitting for the preprocessed model.

### 3. HMM Training
- **Transition matrix**: P(tag<sub>t</sub> | tag<sub>t-1</sub>)
- **Emission matrix**: P(word | tag)
- Vocabulary and tag statistics were collected using `defaultdict(Counter)`.

### 4. Viterbi Algorithm
- Implements dynamic programming with backpointers.
- Handles unknown words via:
  - Zero probability smoothing.
  - (Bonus) Laplace smoothing on rare/unseen transitions/emissions.

### 5. Evaluation
- Model was evaluated on test data using:
  - **Accuracy**
  - **Weighted F1 Score**
  - **Confusion Matrix** (with `seaborn.heatmap`)

## Results

### Filtered Tag List (`ADJ`, `ADV`, `NOUN`, `VERB`, `PUNCT`)
- Accuracy: **91.17%**
- F1 Score: **91.70%**

### All POS Tags (16+ total)
- Accuracy: **88.60%**
- F1 Score: **88.54%**

### With Bonus (Laplace Smoothing)
- Filtered Accuracy: **93.03%**
- Filtered F1 Score: **93.18%**
- All-Tag Accuracy: **90.53%**
- All-Tag F1 Score: **90.54%**

> Smoothing greatly improved predictions for rare/unseen words and transitions.

## 🔍 Visualizations

- Confusion matrices were generated using `seaborn.heatmap()` to observe common tag misclassifications.
- NOUN-VERB confusion was prominent in unfiltered models.

##  Key Files

- `web.conllu`: Contains CoNLL-formatted sentences with POS tags, used as part of the training data.

- `wiki.conllu`: Additional POS-tagged dataset similar in structure to `web.conllu`, merged with it to create a larger dataset.

- > **Note:**  

- > These files are **private** and **not publicly accessible** due to academic integrity and copyright policies.

## Observations & Improvements

- **Challenges:**
  - Handling unknown tokens in test data.
  - Keeping code modular and reusable across filtered and unfiltered datasets.
- **Limitations:**
  - First-order HMMs don’t use contextual information beyond one previous tag.
- **Future Work:**
  - Use bi-grams or neural sequence models (e.g., BiLSTM-CRF).
  - Experiment with unsupervised/semi-supervised POS tagging.


