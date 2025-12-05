# CS445 - Homework 1: Custom Tokenizer

This repository contains the implementation of a custom tokenizer built as part of CS445 (Fall 2024) – **Information Retrieval** course at Sabancı University.

## Objective
The goal was to implement a rule-based tokenizer in Python that mimics or outperforms NLTK's `word_tokenize()` function when evaluated using Jaccard similarity. The tokenizer was designed to handle contractions, punctuation, hyphenated words, and casing.

## Key Steps
- Cleaned raw corpus by removing square bracket content and repeated symbols.
- Tokenized alphanumeric sequences, preserving hyphenated terms.
- Expanded common contractions (e.g., `"can't"` → `"cannot"`).
- Converted all tokens to lowercase and removed empty strings.
- Evaluated using NLTK’s `word_tokenize` and achieved a similarity score of **0.80**.

## Evaluation Corpus
Used the `product_reviews_2` dataset from the **NLTK** library as the main corpus.

## Report Summary
- Described tokenizer design decisions and challenges (e.g., punctuation handling, abbreviation splitting).
- Compared performance and advantages over NLTK’s default tokenizer.
- Suggested possible improvements like context-aware handling using ML models.

---

> **Note**: All code and analysis were completed individually as part of Homework 1, submitted on **20.10.2024**.

