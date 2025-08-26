# WEEK 1: Pengantar Pemrograman Bahasa Alami – Dasar-Dasar Konseptual
Irmasari Hafidz
irma@its.ac.id

**CMPK01a** (Memahami dasar-dasar konseptual dari pengolahan bahasa alami, C2) dan memperkenalkan konsep, metodologi, serta alat-alat utama NLP, dengan fokus pada teks Bahasa Indonesia. 

Materi mencakup definisi dan deskripsi dari sumber akademik (buku dan makalah ACL), studi kasus Google Colab menggunakan korpus Indonesia dari Hugging Face (`indonlu/smsa`), dan lima contoh pentingnya NLP dalam proyek pemerintahan global. Studi kasus diperluas dengan contoh dan analisis tambahan untuk teks Indonesia, menyoroti tantangan tokenisasi seperti slang dan afiksasi. Konten dirancang untuk mahasiswa sarjana dengan pengetahuan dasar Python dan diformat untuk integrasi ke GitHub.

### Tujuan Pembelajaran 
- **Konten**:
  - Memahami definisi, ruang lingkup, dan pentingnya NLP (CMPK01a, C2).
  - Mengenal konsep inti: tokenisasi, korpus, dan pipeline NLP.
  - Mengidentifikasi aplikasi dan tantangan NLP, khususnya dalam Bahasa Indonesia.
  - Mempersiapkan praktik langsung dengan tokenisasi di Google Colab menggunakan dataset Indonesia.
- **Kesesuaian CPMK**: CMPK01a (pemahaman konseptual NLP).

### Apa itu NLP? 
- **Definisi**:
  - NLP adalah bidang ilmu komputer dan kecerdasan buatan yang memungkinkan komputer untuk memproses, memahami, dan menghasilkan bahasa manusia, terutama data teks tak terstruktur.
  - Jurafsky & Martin, *Speech and Language Processing* (edisi ke-3, 2023), Chapter 1.
- **Deskripsi**:
  - Menggabungkan linguistik, ilmu komputer, dan pembelajaran mesin.
  - Berfokus pada bahasa alami (misalnya, Bahasa Indonesia, Inggris) dalam bentuk teks atau ucapan.
  - Tujuan: Memungkinkan interaksi manusia-komputer melalui bahasa (misalnya, chatbot, terjemahan).
  - Contoh Indonesia: Menganalisis sentimen tweet tentang kebijakan publik.

### Ruang Lingkup NLP 
- **Task/ Application/ Bahasa Indonesia context**:
  - **Tugas NLP**: Klasifikasi teks, analisis sentimen, pengenalan entitas bernama (NER), terjemahan mesin, ringkasan teks.
  - **Aplikasi**: Mesin pencari, asisten virtual, analisis media sosial.
  - **Konteks Indonesia**: Memproses slang (misalnya, “gaul”), afiksasi (misalnya, “bermain” → “main”), dan code-switching (misalnya, Bahasa Indonesia dan Jawa).
  - **Contoh**: Mengklasifikasi ulasan produk di e-commerce Indonesia sebagai positif/negatif.
- **Ref**: Cahyawijaya et al., “IndoNLU: Benchmark and Resources for Evaluating Indonesian NLP” (ACL 2020).

### Pipeline NLP 
- **Step by step NLP Pipelines**:
  - **Tahapan**:
    1. **Data**: Mengumpulkan teks (misalnya, berita, media sosial).
    2. **Pre-processing**: Tokenisasi, penghapusan stopword, stemming.
    3. **Ekstraksi Fitur**: Mengubah teks menjadi bentuk numerik (misalnya, Bag-of-Words, TF-IDF).
    4. **Pemodelan**: Membangun algoritma (misalnya, Naive Bayes, jaringan saraf).
    5. **Evaluasi**: Metrik seperti akurasi, presisi, recall.
  - **Indonesian Stopwords**: Sastrawi untuk stemming, IndoBERT untuk pemodelan.
  - **Contoh**: Pipeline untuk menganalisis sentimen ulasan film Indonesia.
- **Ref**: Jurafsky & Martin, Bab 2; Wilie et al., “IndoLEM: A Multi-Task Benchmark for Indonesian NLP” (ACL 2020).

### NLP – Tokenisasi dan Korpus 
- **How to Tokenization x Corpus/ Corpora**:
  - **Tokenisasi**:
    - Definisi: Memecah teks menjadi unit-unit bermakna (token, misalnya, kata, tanda baca).
    - Pentingnya: Dasar untuk semua tugas NLP; menangani aturan bahasa spesifik (misalnya, afiks Indonesia).
    - Contoh: “Saya sedang bermain sepak bola” → [“Saya”, “sedang”, “bermain”, “sepak”, “bola”].
  - **Korpus**:
    - Definisi: Koleksi teks terstruktur (misalnya, Wikipedia, arsip berita).
    - Jenis: Monolingual (misalnya, Wikipedia Bahasa Indonesia), paralel (misalnya, terjemahan Inggris-Indonesia).
    - Pentingnya: Menyediakan data pelatihan untuk model NLP.
    - Contoh: Korpus IndoNLU untuk analisis sentimen media sosial.
- **Ref**: Bird et al., *Natural Language Processing with Python* (NLTK Book, 2009), Bab 1.


### Tantangan dalam NLP 
- **Challenge in NLP**:
  - **Ambiguitas**: Kata dengan makna ganda (misalnya, “bisa” sebagai “dapat” atau “racun”).
  - **Konteks**: Memahami maksud (misalnya, sarkasme dalam tweet Indonesia).
  - **Keragaman Bahasa**: Menangani afiksasi, slang, dan dialek daerah (misalnya, pengaruh Jawa).
  - **Kekurangan Data**: Dataset beranotasi terbatas untuk bahasa sumber daya rendah seperti Indonesia.
  - **Contoh**: Tokenisasi “gaul banget” sulit karena slang informal.
- **Ref**: Cahyawijaya et al., ACL 2020; Jurafsky & Martin, Bab 1.

### Tools for NLP 
- **various sources used in NLP coding**:
  - **Pustaka Python**: NLTK (NLP toolkit), spaCy (package in Python), Sastrawi (pre-processing, stopwords, etc. in Indonesian), Hugging Face (IndoBERT). Sastrawi untuk stemming/penghapusan stopword, IndoBERT untuk pemodelan.
  - **How to**: Instal Python, `pip install nltk spacy PySastrawi datasets`.
  - **Contoh**: Stemming “bermain” menjadi “main” dengan Sastrawi.
- **Sumber**: Bird et al., NLTK Book; Dokumentasi Hugging Face.

### Mengapa NLP Penting? Proyek Pemerintahan 
- **Examples**: Contoh NLP dalam inisiatif pemerintahan
  1. **Chatbot Smart Nation Singapura (GovTech)**:
     - **Deskripsi**: Gov.sg menggunakan chatbot berbasis NLP untuk menjawab pertanyaan warga tentang layanan publik (misalnya, pajak, kesehatan).
     - **Dampak**: Meningkatkan aksesibilitas, mengurangi beban administratif.
     - **NLP Tasks**: Pengenalan maksud, penjawaban pertanyaan.
     - **Contoh**: Menjawab “Bagaimana cara daftar vaksinasi?” dalam Bahasa Inggris/Melayu.
  2. **Platform Bhashini India**:
     - **Deskripsi**: Inisiatif pemerintah untuk terjemahan real-time di 22 bahasa India menggunakan model NLP.
     - **Dampak**: Menjembatani hambatan bahasa, mendukung inklusi digital.
     - **NLP Tasks**: Terjemahan mesin, NLP multibahasa.
     - **Contoh**: Menerjemahkan dokumen resmi dari Hindi ke Tamil.
  3. **Sistem eTranslation Uni Eropa**:
     - **Deskripsi**: Alat NLP UE menerjemahkan dokumen di 24 bahasa resmi untuk negara anggota.
     - **Dampak**: Meningkatkan komunikasi lintas batas, mengurangi biaya terjemahan.
     - **NLP Tasks**: Terjemahan mesin, pemrosesan dokumen.
     - **Contoh**: Menerjemahkan peraturan UE dari Inggris ke Prancis.
  4. **Analisis Teks Kesehatan Australia**:
     - **Deskripsi**: NLP digunakan untuk menganalisis umpan balik pasien dan laporan medis untuk kebijakan kesehatan masyarakat.
     - **Dampak**: Meningkatkan penyampaian layanan kesehatan melalui analisis sentimen dan deteksi tren.
     - **NLP Tasks**: Analisis sentimen, penambangan teks.
     - **Contoh**: Mengidentifikasi keluhan pasien tentang waktu tunggu rumah sakit.
       
**PBA Gasal 2025/ project kelompok kalian!** 
Contoh project di:
- [Link Project PBA Gasal 2024](https://docs.google.com/spreadsheets/d/1CB4Pb1kA54bmvoUqc9I2GjEKJLkefq6FamTGJzilFyY/edit?gid=0#gid=0)
- [Link Project PBA Genap 2025](https://docs.google.com/spreadsheets/d/1CB4Pb1kA54bmvoUqc9I2GjEKJLkefq6FamTGJzilFyY/edit?gid=0#gid=0)

  **Analisis Sentimen BPJS Kesehatan Indonesia**:
  - **Deskripsi**: NLP diterapkan pada media sosial (misalnya, Twitter) untuk mengukur sentimen publik terhadap layanan BPJS Kesehatan.
  - **Dampak**: Memberikan masukan untuk perbaikan kebijakan asuransi kesehatan nasional.
  - **NLP Tasks**: Analisis sentimen, pemantauan media sosial.
  - **Contoh**: Mengklasifikasi tweet seperti “BPJS lambat banget!” sebagai negatif.


### Tokenisasi di Google Colab
- **Homework di rumah**:
  - **Tugas**: Melakukan tokenisasi teks Indonesia dari dataset IndoNLU SMSA.
  - **Tools**: Google Colab untuk aksesibilitas dan kolaborasi.
  - **Tujuan**: Mempraktikkan tokenisasi dan mengeksplorasi struktur dataset.
  - **Dataset**: `indonlu/smsa` (teks media sosial Indonesia).

- **How to**:
  - Buka Google Colab: [colab.research.google.com](https://colab.research.google.com).
  - Buat notebook baru, salin-tempel kode yang diberikan.
  - Instal pustaka yang diperlukan (misalnya, `datasets`, `nltk`, `PySastrawi`).
  - Analisis output tokenisasi dan diskusikan temuan.

## Studi Kasus Google Colab: Tokenisasi Teks Indonesia dengan Korpus IndoNLU

Studi kasus ini mencakup tokenisasi menggunakan dataset `indonlu/smsa` di Google Colab, dengan analisis tambahan untuk menangani tantangan teks Indonesia seperti slang dan afiksasi. 

### Colab
```python
!pip install datasets nltk PySastrawi
from datasets import load_dataset
import nltk
from nltk.tokenize import word_tokenize
from sastrawi.stemmer import StemmerFactory
nltk.download('punkt')

# dataset IndoNLU SMSA
dataset = load_dataset('indonlu/smsa', split='train')

# Konversi ke pandas untuk eksplorasi
import pandas as pd
df = dataset.to_pandas()

# Pilih beberapa contoh teks
sample_texts = df['text'][:3].tolist()  # Ambil 3 teks pertama
labels = df['label'][:3].tolist()  # Ambil label sentimen

# Inisialisasi stemmer Sastrawi
stemmer = StemmerFactory().create_stemmer()

# Tokenisasi dan analisis untuk setiap teks
for i, text in enumerate(sample_texts):
    print(f"\nContoh Teks {i+1} (Label: {labels[i]}):")
    print("Teks Asli:", text)
    
    # Tokenisasi
    tokens = word_tokenize(text)
    print("Token:", tokens)
    print("Jumlah Token:", len(tokens))
    print("Token Unik:", len(set(tokens)))
    
    # Stemming (opsional untuk analisis)
    stemmed_text = stemmer.stem(text)
    stemmed_tokens = word_tokenize(stemmed_text)
    print("Token setelah Stemming:", stemmed_tokens)
    print("Jumlah Token setelah Stemming:", len(stemmed_tokens))
    
    # Simpan token ke file
    with open(f'tokens_sample_{i+1}.txt', 'w', encoding='utf-8') as f:
        f.write('\n'.join(tokens))
    print(f"Token disimpan ke tokens_sample_{i+1}.txt")

# Analisis tambahan: Frekuensi kata
from collections import Counter
all_tokens = []
for text in sample_texts:
    all_tokens.extend(word_tokenize(text.lower()))
word_freq = Counter(all_tokens).most_common(10)
print("\n10 Kata Teratas:", word_freq)
