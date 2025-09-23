## Keyword Extraction (30 menit)
Keyword extraction ≠ keyword search.

Pendekatan utama:
- Statistical → TF-IDF, YAKE.
- Graph-based → RAKE.
- Embedding-based (BERT, Word2Vec, tapi opsional untuk kuliah ini).

Contoh cepat (tanpa coding):
Dari C11 → kata kunci: siswa, makan sehat bergizi, ayam goreng, porsi, Kodam, Presiden Prabowo.

# Using TF-IDF
```python
import pandas as pd
from sklearn.feature_extraction.text import TfidfVectorizer
from nltk.corpus import stopwords
import nltk

# Ensure stopwords are downloaded
nltk.download('stopwords')

# load dataset
#df2 used in here

# Get Indonesian stopwords
stop_words = set(stopwords.words('indonesian'))

# ekstrak TF-IDF
vectorizer = TfidfVectorizer(stop_words=list(stop_words), max_features=20)
X = vectorizer.fit_transform(df2["Konten"].dropna())
keywords = vectorizer.get_feature_names_out()

print("Kata kunci utama:", keywords)
```

# Using RAKE
```python
!pip install python-rake -q
!pip install rake-nltk

import RAKE

rake = RAKE.Rake(RAKE.SmartStopList())
text = df.loc[0, "Konten"]
keywords_rake = rake.run(text)
print(keywords_rake[:10])

```

# Diskusi: 
Dari artikel C11 → apakah frasa “pedas manis gitu” muncul sebagai kata kunci? Apakah ini relevan untuk analisis kebijakan?
Latihan: Bandingkan hasil RAKE & TF-IDF → mana lebih representatif?

Diskusi kelompok:
C01 (Anggaran & Implementasi) → fokus pada angka, target, SPPG.
C11 (Suara Masyarakat) → fokus pada rasa makanan, porsi, kepuasan siswa.
C06 (Ekonomi) → fokus pada lapangan kerja, pertumbuhan ekonomi.
Tugas mini: Buat tabel perbandingan kata kunci penting tiap kategori (Pelaksanaan, Suara, Ekonomi).

# Integrasi ke Kebijakan Publik
Bagaimana kata kunci membantu:

- Pemerintah → evaluasi implementasi.
- Media → framing isu (anggaran vs dampak sosial).
- Akademisi → riset kebijakan gizi.

## HOMEWORK Week 5
Tugas (Homework)

- Gunakan dataset MBG tambahan (5–10 artikel).
- Jalankan TF-IDF + RAKE.
- Tulis analisis 1 halaman: Bagaimana framing MBG di media berbeda-beda?
