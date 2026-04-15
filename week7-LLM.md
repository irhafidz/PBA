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

Secara matematis, sebuah Language Model (LM) adalah model yang mempelajari distribusi probabilitas dari urutan kata. Jika kita memiliki kalimat $S = (w_1, w_2, ..., w_n)$, model menghitung:

$$P(S) = \prod_{i=1}^{n} P(w_i | w_1, \dots, w_{i-1})$$

### Point Penting:
* **Next Token Prediction:** LLM tidak "memahami" kebenaran; ia memprediksi kata apa yang paling mungkin muncul secara statistik berdasarkan data training.
* **Context Window:** Seberapa banyak kata sebelumnya ($w_1, \dots, w_{i-1}$) yang bisa diingat oleh model untuk memprediksi kata berikutnya.

---

## 2. Transition to Large Language Models (LLM)
Dalam beberapa tahun terakhir, NLP bergeser ke **Neural Language Models** yang berskala raksasa (LLM) berbasis arsitektur **Transformer**.

### The Core Research: The Transformer / Arsitektur Utama: Self-Attention
LLM modern (GPT-4, Llama 3, IndoBERT) menggunakan mekanisme **Self-Attention** yang diperkenalkan dalam paper *“Attention Is All You Need”* (Vaswani et al., 2017).
Hampir semua LLM modern (GPT, Llama, BERT) lahir dari satu riset kunci:
> **Vaswani, et al. (2017).** *"Attention Is All You Need"*. Riset ini memperkenalkan mekanisme **Self-Attention**, yang memungkinkan model fokus pada bagian kata yang paling relevan dalam satu konteks kalimat.


### Mekanisme Q, K, V:
* **Query (Q):** "Apa yang sedang saya cari?" (Fokus saat ini).
* **Key (K):** "Informasi apa yang ditawarkan oleh kata lain?"
* **Value (V):** "Informasi penting apa yang harus saya ambil?"

> **Analogi:** Saat membaca review BPJS, mata kita secara otomatis menghubungkan kata *"lambat"* dengan kata *"pelayanan"*, bukan dengan kata *"gedung"*. Itulah kerja Self-Attention.

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




## more notes on Metrik Evaluasi: Cara Mengukur Performa 
Kapan menggunakan metrik tertentu.

| Metric | Nama Lengkap | Kegunaan Utama | Tip Praktis (Do's & Don'ts) |
| :--- | :--- | :--- | :--- |
| **PPL** | Perplexity | Mengukur kefasihan (fluency). | **Do:** Semakin rendah makin baik. **Don't:** Bandingkan PPL dari dataset yang berbeda genre. |
| **BLEU** | Bilingual Evaluation Understudy | Mengukur presisi kata. | **Do:** Gunakan untuk tugas translasi. **Don't:** Gunakan untuk tugas kreatif (opini/cerita). |
| **ROUGE** | Recall-Oriented Understudy | Mengukur kelengkapan info. | **Do:** Sangat cocok untuk **Summarization** (Project A-30). **Don't:** Abaikan stemming bahasa Indonesia. |
| **MMLU** | Massive Multitask Language Understanding | Benchmark kecerdasan umum. | **Do:** Gunakan
