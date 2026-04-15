# Week 7: Language Modeling and Evaluation

Course Objectives (CPMK):
**CMPK01c:** Menerapkan pemodelan bahasa sederhana (C3)
**CMPK01g:** Membuat model pengolahan bahasa alami, mengevaluasi dan merekomendasikan perbaikannya (C2, C3, C4)

## 1. Introduction to Language Modeling (LM)
Secara sederhana, **Language Modeling** adalah tugas memprediksi kata berikutnya dalam suatu urutan kata. 
> *A Language Model (LM) computes the probability of a sentence or a sequence of words.*

### A. Konsep Probabilitas
Jika kita memiliki kalimat $W = w_1, w_2, ..., w_n$, maka model bahasa bertujuan menghitung $P(W)$.
* **Contoh:** Mana yang memiliki probabilitas lebih tinggi?
    * $P(\text{"I drink coffee"})$ **>** $P(\text{"I drink window"})$

### B. N-Gram Model (The Classical Way)
Sebelum era Deep Learning, kita menggunakan **N-gram**, yaitu urutan $n$ kata yang berdekatan.
* **Unigram:** Menghitung probabilitas kata secara independen.
* **Bigram:** Memprediksi kata berdasarkan satu kata sebelumnya $P(w_n | w_{n-1})$.

---

## 2. Transition to Large Language Models (LLM)
Dalam beberapa tahun terakhir, NLP bergeser ke **Neural Language Models** yang berskala raksasa (LLM) berbasis arsitektur **Transformer**.

### The Core Research: The Transformer
Hampir semua LLM modern (GPT, Llama, BERT) lahir dari satu riset kunci:
> **Vaswani, et al. (2017).** *"Attention Is All You Need"*. Riset ini memperkenalkan mekanisme **Self-Attention**, yang memungkinkan model fokus pada bagian kata yang paling relevan dalam satu konteks kalimat.

---

## 3. Evaluation Metrics & Essential Research
Mengevaluasi model bahasa memerlukan metrik yang berbeda dari klasifikasi biasa. Berikut adalah tabel acuan untuk mahasiswa:

| Metric / Benchmark | Fungsi Utama | Paper Referensi (Link) |
| :--- | :--- | :--- |
| **Perplexity (PPL)** | Mengukur seberapa baik model memprediksi sampel data (Intrinsic). | [Shannon (1948)](https://ieeexplore.ieee.org/document/6773024) |
| **BLEU Score** | Evaluasi kemiripan teks mesin dengan referensi manusia (Translation). | [Papineni et al. (2002)](https://aclanthology.org/P02-1040.pdf) |
| **ROUGE** | Mengukur *recall* pada ringkasan teks (Summarization). | [Lin (2004)](https://aclanthology.org/W04-1013.pdf) |
| **MMLU** | Benchmark pemahaman multi-tugas (STEM/Humaniora). | [Hendrycks et al. (2021)](https://arxiv.org/abs/2009.03300) |
| **Self-Attention** | Arsitektur dasar LLM (Transformer). | [Vaswani et al. (2017)](https://arxiv.org/abs/1706.03762) |

---
* **Human Evaluation:** Lakukan sampling (10-20%) untuk memvalidasi apakah interpretasi model terhadap keluhan pasien sudah sesuai dengan konteks layanan kesehatan di Indonesia.
* **Hallucination Rate:** Sangat krusial di Public Health agar model tidak mengarang fakta medis atau kebijakan BPJS.

---
