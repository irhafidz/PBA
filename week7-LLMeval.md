# Week 7: Language Modeling, Evaluation, & LLM Foundations

**CPMK:** CMPK01c (Penerapan Model Bahasa), CMPK01g (Evaluasi & Rekomendasi)

---

## 1. Core Architecture: Self-Attention
Self-Attention adalah mekanisme yang memungkinkan model memberikan "perhatian" lebih pada kata-kata yang relevan dalam satu konteks, terlepas dari jaraknya.



* **Query (Q):** Kata yang sedang diproses.
* **Key (K):** Kata-kata lain sebagai referensi.
* **Value (V):** Informasi yang diambil jika Q dan K cocok.
* **Context in ID:** Pada kalimat *"Obat ini manjur tapi mahal"*, model menghubungkan "mahal" kembali ke "Obat" menggunakan skor perhatian yang tinggi.

---

## 2. Modern Benchmarks: MMLU
**Massive Multitask Language Understanding (MMLU)** adalah "Ujian Nasional" bagi LLM.
* **Cakupan:** 57 subjek (STEM, Humaniora, Medis, dll).
* **Fungsi:** Menguji penalaran (reasoning) dan pengetahuan dunia model.
* **Indonesian Note:** Model dengan skor MMLU tinggi (seperti Llama 3 atau GPT-4) cenderung lebih baik dalam menangani tugas kompleks di Project A-30, meskipun perlu adaptasi bahasa.

---

## 3. Evaluation Metrics in Practice (Indonesian Context)

| Metric | Context (ID) | Do | Don't |
| :--- | :--- | :--- | :--- |
| **Perplexity** | Kefasihan gaya bahasa. | Bandingkan model pada korpus yang sama. | Bandingkan PPL antar dataset berbeda. |
| **ROUGE** | Ringkasan keluhan pasien. | Gunakan untuk cek keyword penting. | Abaikan variasi imbuhan (me-, di-, ke-an). |
| **BLEU** | Parafrase instruksi medis. | Gunakan untuk akurasi tekstual. | Gunakan untuk teks kreatif/opini. |

---

## 4. Practical Tips: Do's & Don'ts
* **DO:** Gunakan **F1-Score** untuk klasifikasi sentimen review BPJS.
* **DO:** Lakukan **Human Evaluation** (Sampling 10-20%) untuk cek halusinasi medis.
* **DON'T:** Percaya 100% pada skor otomatis; bahasa Indonesia memiliki nuansa (sarkasme/slang) yang sering luput dari metrik standar.

---
