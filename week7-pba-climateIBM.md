# 🌍🩺 Climate-Health Named Entity Recognition (NER) Project

Dataset: IBM Research Climate-Change NER/ Hugging Face
Link: [https://huggingface.co/datasets/ibm-research/Climate-Change-NER/tree/main]

Download:
- en.train.txt (≈ 367 kB)
- en.val.txt (≈ 74.6 kB)
- en.test.txt (≈ 69.1 kB)

Ambil token di akun huggingface:
- https://huggingface.co/settings/tokens


### Setup
```python
!pip install datasets transformers spacy matplotlib
!python -m spacy download en_core_web_sm

```

## 📊 Dataset Exploration & Analysis Section

### 🔹 Load Dataset as DataFrame
```python
import pandas as pd
df_train = pd.DataFrame(dataset["train"])
df_test = pd.DataFrame(dataset["test"])
df_train.head(3)[["id", "text", "entities"]]
```
# ✅ Kelebihan Dataset

- Spesifik pada domain iklim – Fokus pada isu ilmiah dan lingkungan, tidak seperti dataset umum (mis. CoNLL-2003).
- Anotasi manual – Label diberikan oleh manusia, meningkatkan akurasi dan validitas ilmiah.
- Beragam entitas ilmiah – Memberikan peluang eksplorasi kategori nontradisional seperti hazards dan mitigations.
- Lisensi terbuka (ODC-By) – Dapat digunakan dan dimodifikasi untuk penelitian dan pendidikan.
- 
# ⚠️ Keterbatasan Dataset

- Jumlah data terbatas (534 abstrak) – Tidak cukup besar untuk melatih model baru dari nol.
- Bahasa Inggris – Tidak tersedia versi Bahasa Indonesia, perlu penerjemahan manual jika digunakan di konteks lokal.
- Konteks ilmiah – Bahasa teknis, kurang cocok langsung untuk data berita atau media sosial.
- Tidak mencakup domain kesehatan secara langsung – Namun bisa dikombinasikan dengan dataset kesehatan.
- Overlapping entities – Beberapa teks mengandung entitas tumpang tindih (mis. “heatwave mortality” dapat berarti hazard dan impact).
