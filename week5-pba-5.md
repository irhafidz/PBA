# Text Embeddings

- Mengubah teks → vektor angka (representasi padat / dense representation).
- Contoh: “gizi” → [0.12, -0.55, …, 0.89]

## Mengapa Embeddings lebih baik dari Keywords:

- Keywords: hanya cocok bila kata persis sama.
- Embeddings: menangkap makna semantik, meski kata berbeda.
- “program makanan” ≈ “inisiatif gizi” (vektornya mirip).

Referensi:
- Mikolov et al. (2013, NIPS) — Word2Vec. [https://arxiv.org/abs/1301.3781]
- Reimers & Gurevych (2019, EMNLP) — Sentence-BERT. [https://arxiv.org/abs/1908.10084]
