# Sentiment Analysis using BERT

## Overview

This project implements a sentiment classification system using a pretrained BERT (Bidirectional Encoder Representations from Transformers) model. The model is fine-tuned on the IMDb movie reviews dataset to classify text as either positive or negative.

The objective of this project is to demonstrate a complete NLP pipeline including data preprocessing, model training, and evaluation using transformer-based architectures.

---

## Dataset

* **Name:** IMDb Movie Reviews Dataset
* **Source:** HuggingFace Datasets
* **Size:**

  * Training: 25,000 samples
  * Testing: 25,000 samples

Each sample contains:

* `text`: Movie review
* `label`:

  * 0 → Negative
  * 1 → Positive

---

## Model Architecture

The model is based on:

* **BERT Base (bert-base-uncased)**
* Pretrained transformer encoder with 12 layers
* Hidden size: 768
* Self-attention mechanism for contextual understanding

A classification head is added on top of BERT:

* Linear layer mapping 768 → 2 output classes

Pipeline:

```id="c0o6pn"
Text → Tokenizer → BERT Encoder → CLS Representation → Linear Classifier → Sentiment Output
```

---

## Implementation Details

### Tokenization

* Tokenizer: BertTokenizer
* Max sequence length: 256
* Padding: Fixed length
* Truncation enabled

### Training Configuration

* Optimizer: AdamW
* Learning Rate: 2e-5
* Batch Size: 8
* Epochs: Up to 10
* Loss Function: CrossEntropyLoss (handled internally)

### Device

* Trained on GPU (T4 / L4)
* CPU used for debugging

---

## Training Strategy

* The model is fine-tuned on the IMDb dataset
* Evaluation is performed after each epoch
* The best model is selected based on validation accuracy

---

## Requirements

```id="3mb1ha"
torch
transformers
datasets
scikit-learn
matplotlib
```

---

## Key Learnings

* Understanding transformer-based NLP models
* Tokenization and attention mechanisms
* Fine-tuning pretrained models
* Handling overfitting using validation performance
* Building an end-to-end NLP pipeline

---

## Conclusion

This project demonstrates how pretrained transformer models like BERT can be effectively fine-tuned for sentiment analysis tasks, achieving strong performance with minimal preprocessing. It reflects practical implementation aligned with modern NLP workflows.
