# 📝 Text Embedding & Keyword Extraction Lecture Notebook

---

## 1. Introduction

### 🎯 Learning Objectives:
1. Memahami metode ekstraksi kata kunci (TF-IDF, TextRank, RAKE).
2. Menerapkan **N-gram extraction** (e.g., *ibu hamil*, *Rp 300 triliun*).
3. Membandingkan NLP: classical and modern NLP methods.
4. Apa itu **text embeddings** & keunggulan
5. Practice: MBA file data TA Mbak Celine.
   
### 📚 References
- Kavita Ganesan (2018). *Practical Guide to Keyword Extraction*  [[link](https://kavita-ganesan.com/python-keyword-extraction/#.W2TlD9hKhhE)]
- Mikolov et al. (2013). *Efficient Estimation of Word Representations in Vector Space*. NIPS.
- Devlin et al. (2019). *BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding*. NAACL.

---

## 2. Dataset Overview
We will use a dataset containing MBG-related articles stored in a CSV file. The dataset contains fields like:
- **ID**: Article code
- **Category**: e.g., Proyeksi, Implementasi
- **Source**: e.g., Kompas.com
- **Date**: Publication date
- **Title**: Article title
- **Content**: Full article text
- **Tone**: Manual sentiment annotation (e.g., Netral, Positif, Negatif)

---
