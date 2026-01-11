drive LINK 
https://drive.google.com/drive/folders/1oRrcYnZ6zfUlHrbjydo_cxXzBPgTkPMU?usp=sharing
# 📘 COE025 – Natural Language Processing  
## Project 2: POS Tagging & Named Entity Recognition (NER) for Semantic Understanding

---



## 📌 Project Overview
This project is part of the **COE025: Natural Language Processing (Fall 2025–2026)** course.  
The objective of this project is to **build and evaluate systems for Part-of-Speech (POS) tagging and Named Entity Recognition (NER)** to achieve deeper **semantic understanding of movie scripts**.

By combining POS and NER, the system can understand both:
- **Syntactic structure** (verbs, nouns, adjectives)
- **Semantic roles** (people, locations, organizations, money, etc.)

---

## 💡 Project Idea
### POS + NER for Semantic Understanding
- **POS Tagging** helps identify grammatical roles  
  - Example: *“John runs into the room”* → *runs* = verb (action)
- **NER Tagging** detects named entities  
  - Example: *“John”* → B-PERSON (character)

This combination allows the model to interpret scripts similarly to a human reader.

---

## 📂 Datasets Used

### ✅ NER Dataset
- **Dataset:** ONTOPAD5 (HuggingFace)
- Contains B- and I- tags for entities
- Total of **36 NER labels**
- Split:
  - ~60k for training  
  - ~9k for validation  
  - ~9k for testing  

### ✅ POS Dataset
- **Dataset:** Universal Dependencies – English EWT
- Text source: blogs, reviews, emails, forums
- Contains **18 POS tags**

---

## 🧹 Dataset Preprocessing

### Common Steps
- Filtered uppercase lines and short utterances to remove:
  - Character names
  - Scene headers
- Tokenized text using regex-based tokenizer
- Preserved punctuation and contractions

---

## 🧠 POS Tagging Pipeline

### Models Implemented
1. **Hidden Markov Model (HMM)**
2. **Conditional Random Field (CRF)**
3. **BiLSTM**
4. **BERT (Token Classification)**

---

### 🔹 HMM (Hidden Markov Model)
- Uses emission and transition probabilities
- Decoding with Viterbi algorithm
- **Accuracy:** 88.5%
- Weak on rare tags (INTJ, SYM, X)

---

### 🔹 CRF
- Uses handcrafted features:
  - Capitalization
  - Suffixes
  - Neighboring words
- **Accuracy:** 94.3%
- Much better handling of rare tags than HMM

---

### 🔹 BiLSTM
- Learns contextual embeddings
- Requires indexed tokens and padded sequences
- **Accuracy:** 91.8%
- Good generalization but sensitive to rare tokens

---

### ✅ Best POS Model: **BERT**
- Uses WordPiece tokenization
- Aligns labels with subwords
- **Accuracy:** 97.4%
- Best overall POS performance

---

## 🏷 Named Entity Recognition (NER) Pipeline

### Models Implemented
1. **MEMM**
2. **Averaged Perceptron**
3. **BiGRU**
4. **BERT**

---

### 🔹 MEMM
- Uses handcrafted features and previous tag
- **Accuracy:** 93.5%
- Strong on frequent entities, weaker on rare ones

---

### 🔹 Averaged Perceptron
- Fast and lightweight baseline
- **Overall Accuracy:** 94.6%
- **Macro F1:** 0.55 (bias toward frequent classes)

---

### 🔹 BiGRU
- Sequence learning using GRU units
- **Accuracy:** 95.6%
- **Weighted F1:** 0.953
- Struggles with low-support entity types

---

### ✅ Best NER Model: **BERT**
- Handles contextual representation effectively
- **Token-level Accuracy:** 98.1%
- **Weighted F1:** 0.869
- Best overall performance across entity types

---

## 🌍 Multilingual Evaluation
The trained models were also evaluated on:
- **Spanish**
- **Arabic**

Results showed:
- Strong performance on POS tagging
- Slight degradation in NER for low-resource entities

---

## 📊 Model Comparison
- **Best POS Model:** BERT  
- **Best NER Model:** BERT  
- Traditional models perform well but struggle with rare patterns
- Neural and transformer models generalize better

---

## 🧠 Final Conclusion
This project demonstrates that combining **POS tagging and NER** significantly improves semantic understanding of text.  
Among all models tested:
- **BERT consistently achieved the best results** for both POS and NER tasks
- Traditional models remain useful baselines but are limited in complex scenarios

---

## 🛠 Tools & Technologies
- Python  
- PyTorch  
- HuggingFace Transformers  
- scikit-learn  
- spaCy  
- Universal Dependencies datasets  

---
