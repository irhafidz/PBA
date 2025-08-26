# WEEK 1: Pengantar Pemrograman Bahasa Alami – Dasar-Dasar Konseptual

**CMPK01a** (Memahami dasar-dasar konseptual dari pengolahan bahasa alami, C2) dan memperkenalkan konsep, metodologi, serta alat-alat utama NLP, dengan fokus pada teks Bahasa Indonesia. 
Materi mencakup definisi dan deskripsi dari sumber akademik (buku dan makalah ACL), studi kasus Google Colab menggunakan korpus Indonesia dari Hugging Face (`indonlu/smsa`), dan lima contoh pentingnya NLP dalam proyek pemerintahan global. Studi kasus diperluas dengan contoh dan analisis tambahan untuk teks Indonesia, menyoroti tantangan tokenisasi seperti slang dan afiksasi. Konten dirancang untuk mahasiswa sarjana dengan pengetahuan dasar Python dan diformat untuk integrasi ke GitHub.

### Slide 1: Judul (5 menit)
- **Judul**: Pengantar Pemrograman Bahasa Alami (Natural Language Processing)
- **Subjudul**: Dasar-Dasar Konseptual dan Aplikasi Praktis
- **Konten**:
  - Dosen: [Nama Anda]
  - Mata Kuliah: Pemrograman Bahasa Alami, ITS Surabaya
  - Pekan 1: Memahami Dasar-Dasar NLP
  - Tanggal: 26 Agustus 2025
- **Visual**: Gambar awan kata (word cloud) dari teks Bahasa Indonesia (misalnya, postingan media sosial).
- **Tujuan**: Menarik perhatian mahasiswa dan menetapkan konteks kuliah.

### Slide 2: Tujuan Pembelajaran (5 menit)
- **Konten**:
  - Memahami definisi, ruang lingkup, dan pentingnya NLP (CMPK01a, C2).
  - Mengenal konsep inti: tokenisasi, korpus, dan pipeline NLP.
  - Mengidentifikasi aplikasi dan tantangan NLP, khususnya dalam Bahasa Indonesia.
  - Mempersiapkan praktik langsung dengan tokenisasi di Google Colab menggunakan dataset Indonesia.
- **Kesesuaian CPMK**: CMPK01a (pemahaman konseptual NLP).
- **Visual**: Poin-poin dengan ikon untuk setiap tujuan.
- **Tujuan**: Menjelaskan apa yang akan dipelajari dan menghubungkannya dengan CPMK.

### Slide 3: Apa itu NLP? (10 menit)
- **Definisi**:
  - NLP adalah bidang ilmu komputer dan kecerdasan buatan yang memungkinkan komputer untuk memproses, memahami, dan menghasilkan bahasa manusia, terutama data teks tak terstruktur.
- **Deskripsi**:
  - Menggabungkan linguistik, ilmu komputer, dan pembelajaran mesin.
  - Berfokus pada bahasa alami (misalnya, Bahasa Indonesia, Inggris) dalam bentuk teks atau ucapan.
  - Tujuan: Memungkinkan interaksi manusia-komputer melalui bahasa (misalnya, chatbot, terjemahan).
  - Contoh Indonesia: Menganalisis sentimen tweet tentang kebijakan publik.
- **Sumber**: Jurafsky & Martin, *Speech and Language Processing* (edisi ke-3, 2023), Bab 1.
- **Visual**: Diagram NLP sebagai perpotongan linguistik, ilmu komputer, dan AI.
- **Tujuan**: Memberikan definisi akademik yang jelas dan relevan.

### Slide 4: Ruang Lingkup NLP (10 menit)
- **Konten**:
  - **Tugas NLP**: Klasifikasi teks, analisis sentimen, pengenalan entitas bernama (NER), terjemahan mesin, ringkasan teks.
  - **Aplikasi**: Mesin pencari, asisten virtual, analisis media sosial.
  - **Konteks Indonesia**: Memproses slang (misalnya, “gaul”), afiksasi (misalnya, “bermain” → “main”), dan code-switching (misalnya, Bahasa Indonesia dan Jawa).
  - **Contoh**: Mengklasifikasi ulasan produk di e-commerce Indonesia sebagai positif/negatif.
- **Sumber**: Cahyawijaya et al., “IndoNLU: Benchmark and Resources for Evaluating Indonesian NLP” (ACL 2020).
- **Visual**: Contoh tugas NLP (misalnya, analisis sentimen tweet Indonesia).
- **Tujuan**: Menunjukkan luasnya NLP dan relevansinya di Indonesia.

### Slide 5: Pipeline NLP (15 menit)
- **Konten**:
  - **Tahapan**:
    1. **Pengumpulan Data**: Mengumpulkan teks (misalnya, berita, media sosial).
    2. **Prapemrosesan**: Tokenisasi, penghapusan stopword, stemming.
    3. **Ekstraksi Fitur**: Mengubah teks menjadi bentuk numerik (misalnya, Bag-of-Words, TF-IDF).
    4. **Pemodelan**: Membangun algoritma (misalnya, Naive Bayes, jaringan saraf).
    5. **Evaluasi**: Metrik seperti akurasi, presisi, recall.
  - **Fokus Indonesia**: Alat seperti Sastrawi untuk stemming, IndoBERT untuk pemodelan.
  - **Contoh**: Pipeline untuk menganalisis sentimen ulasan film Indonesia.
- **Sumber**: Jurafsky & Martin, Bab 2; Wilie et al., “IndoLEM: A Multi-Task Benchmark for Indonesian NLP” (ACL 2020).
- **Visual**: Diagram alur pipeline NLP dengan contoh Indonesia.
- **Tujuan**: Menjelaskan proses end-to-end tugas NLP.

### Slide 6: Konsep Inti NLP – Tokenisasi dan Korpus (15 menit)
- **Konten**:
  - **Tokenisasi**:
    - Definisi: Memecah teks menjadi unit-unit bermakna (token, misalnya, kata, tanda baca).
    - Pentingnya: Dasar untuk semua tugas NLP; menangani aturan bahasa spesifik (misalnya, afiks Indonesia).
    - Contoh: “Saya sedang bermain sepak bola” → [“Saya”, “sedang”, “bermain”, “sepak”, “bola”].
  - **Korpus**:
    - Definisi: Koleksi teks terstruktur (misalnya, Wikipedia, arsip berita).
    - Jenis: Monolingual (misalnya, Wikipedia Bahasa Indonesia), paralel (misalnya, terjemahan Inggris-Indonesia).
    - Pentingnya: Menyediakan data pelatihan untuk model NLP.
    - Contoh: Korpus IndoNLU untuk analisis sentimen media sosial.
- **Sumber**: Bird et al., *Natural Language Processing with Python* (NLTK Book, 2009), Bab 1.
- **Visual**: Contoh tokenisasi teks Indonesia; cuplikan korpus IndoNLU.
- **Tujuan**: Memperkenalkan metode dasar pemrosesan teks.

### Slide 7: Tantangan dalam NLP (10 menit)
- **Konten**:
  - **Ambiguitas**: Kata dengan makna ganda (misalnya, “bisa” sebagai “dapat” atau “racun”).
  - **Konteks**: Memahami maksud (misalnya, sarkasme dalam tweet Indonesia).
  - **Keragaman Bahasa**: Menangani afiksasi, slang, dan dialek daerah (misalnya, pengaruh Jawa).
  - **Kekurangan Data**: Dataset beranotasi terbatas untuk bahasa sumber daya rendah seperti Indonesia.
  - **Contoh**: Tokenisasi “gaul banget” sulit karena slang informal.
- **Sumber**: Cahyawijaya et al., ACL 2020; Jurafsky & Martin, Bab 1.
- **Visual**: Contoh kalimat ambigu dalam Bahasa Indonesia.
- **Tujuan**: Menyoroti kompleksitas dunia nyata, terutama dalam NLP Indonesia.

### Slide 8: Alat dan Pustaka untuk NLP (10 menit)
- **Konten**:
  - **Pustaka Python**: NLTK (NLP umum), spaCy (pemrosesan cepat), Sastrawi (prapemrosesan Indonesia), Hugging Face (IndoBERT).
  - **Alat Khusus Indonesia**: Sastrawi untuk stemming/penghapusan stopword, IndoBERT untuk pemodelan.
  - **Pengaturan**: Instal Python, `pip install nltk spacy PySastrawi datasets`.
  - **Contoh**: Stemming “bermain” menjadi “main” dengan Sastrawi.
- **Sumber**: Bird et al., NLTK Book; Dokumentasi Hugging Face.
- **Visual**: Tangkapan layar output tokenisasi NLTK dan stemming Sastrawi.
- **Tujuan**: Memperkenalkan alat praktis untuk pembelajaran langsung.

### Slide 9: Mengapa NLP Penting? Proyek Pemerintahan Global (20 menit)
- **Konten**: Lima contoh dampak NLP dalam inisiatif pemerintahan:
  1. **Chatbot Smart Nation Singapura (GovTech)**:
     - **Deskripsi**: Gov.sg menggunakan chatbot berbasis NLP untuk menjawab pertanyaan warga tentang layanan publik (misalnya, pajak, kesehatan).
     - **Dampak**: Meningkatkan aksesibilitas, mengurangi beban administratif.
     - **Kasus Penggunaan**: Pengenalan maksud, penjawaban pertanyaan.
     - **Contoh**: Menjawab “Bagaimana cara daftar vaksinasi?” dalam Bahasa Inggris/Melayu.
  2. **Platform Bhashini India**:
     - **Deskripsi**: Inisiatif pemerintah untuk terjemahan real-time di 22 bahasa India menggunakan model NLP.
     - **Dampak**: Menjembatani hambatan bahasa, mendukung inklusi digital.
     - **Kasus Penggunaan**: Terjemahan mesin, NLP multibahasa.
     - **Contoh**: Menerjemahkan dokumen resmi dari Hindi ke Tamil.
  3. **Sistem eTranslation Uni Eropa**:
     - **Deskripsi**: Alat NLP UE menerjemahkan dokumen di 24 bahasa resmi untuk negara anggota.
     - **Dampak**: Meningkatkan komunikasi lintas batas, mengurangi biaya terjemahan.
     - **Kasus Penggunaan**: Terjemahan mesin, pemrosesan dokumen.
     - **Contoh**: Menerjemahkan peraturan UE dari Inggris ke Prancis.
  4. **Analisis Teks Kesehatan Australia**:
     - **Deskripsi**: NLP digunakan untuk menganalisis umpan balik pasien dan laporan medis untuk kebijakan kesehatan masyarakat.
     - **Dampak**: Meningkatkan penyampaian layanan kesehatan melalui analisis sentimen dan deteksi tren.
     - **Kasus Penggunaan**: Analisis sentimen, penambangan teks.
     - **Contoh**: Mengidentifikasi keluhan pasien tentang waktu tunggu rumah sakit.
  5. **Analisis Sentimen BPJS Kesehatan Indonesia**:
     - **Deskripsi**: NLP diterapkan pada media sosial (misalnya, Twitter) untuk mengukur sentimen publik terhadap layanan BPJS Kesehatan.
     - **Dampak**: Memberikan masukan untuk perbaikan kebijakan asuransi kesehatan nasional.
     - **Kasus Penggunaan**: Analisis sentimen, pemantauan media sosial.
     - **Contoh**: Mengklasifikasi tweet seperti “BPJS lambat banget!” sebagai negatif.
- **Sumber**: Sumber web tentang proyek NLP pemerintahan.
- **Visual**: Tangkapan layar antarmuka chatbot, terjemahan, atau dasbor sentimen.
- **Tujuan**: Menunjukkan dampak nyata NLP, terutama dalam tata kelola.

### Slide 10: Tinjauan Studi Kasus – Tokenisasi di Google Colab (5 menit)
- **Konten**:
  - **Tugas**: Melakukan tokenisasi teks Indonesia dari dataset IndoNLU SMSA.
  - **Alat**: Google Colab untuk aksesibilitas dan kolaborasi.
  - **Tujuan**: Mempraktikkan tokenisasi dan mengeksplorasi struktur dataset.
  - **Dataset**: `indonlu/smsa` (teks media sosial Indonesia).
- **Visual**: Tangkapan layar antarmuka Colab.
- **Tujuan**: Transisi ke praktik langsung.

### Slide 11: Instruksi Praktik Langsung (10 menit)
- **Konten**:
  - Buka Google Colab: [colab.research.google.com](https://colab.research.google.com).
  - Buat notebook baru, salin-tempel kode yang diberikan.
  - Instal pustaka yang diperlukan (misalnya, `datasets`, `nltk`, `PySastrawi`).
  - Analisis output tokenisasi dan diskusikan temuan.
- **Visual**: Panduan langkah-demi-langkah pengaturan Colab.
- **Tujuan**: Mempersiapkan mahasiswa untuk studi kasus.

### Slide 12: Istirahat (10 menit)
- **Konten**: Jeda untuk pertanyaan dan diskusi.
- **Tujuan**: Memberi waktu bagi mahasiswa untuk mencerna konsep dan mengklarifikasi keraguan.

### Slide 13: Demo Studi Kasus – Penjelasan Langsung (20 menit)
- **Konten**:
  - Tunjukkan studi kasus Google Colab (kode di bawah).
  - Jelaskan setiap langkah: memuat dataset, tokenisasi, analisis output.
  - Soroti tantangan khusus Indonesia (misalnya, slang, afiksasi).
- **Visual**: Output Colab langsung atau tangkapan layar hasil tokenisasi.
- **Tujuan**: Menunjukkan aplikasi praktis konsep Pekan 1.

### Slide 14: Diskusi dan Tanya Jawab (15 menit)
- **Konten**:
  - Diskusikan tantangan tokenisasi (misalnya, menangani slang Indonesia).
  - Kaitkan dengan proyek pemerintahan (misalnya, analisis sentimen BPJS).
  - Dorong pertanyaan tentang konsep, alat, atau aplikasi NLP.
- **Visual**: Ruang terbuka untuk masukan mahasiswa.
- **Tujuan**: Memperkuat pembelajaran melalui interaksi.

### Slide 15: Ringkasan dan Langkah Berikutnya (5 menit)
- **Konten**:
  - Rekap: Definisi NLP, pipeline, tokenisasi, korpus, tantangan.
  - Pratinjau Pekan 2: Pengumpulan data dan pembuatan dataset (CMPK01f).
  - Tugas: Jelajahi Bab 1 NLTK Book, coba tokenisasi teks pendek Indonesia.
- **Visual**: Tabel ringkasan konsep utama.
- **Tujuan**: Mengonsolidasikan pembelajaran dan menetapkan ekspektasi.

## Studi Kasus Google Colab: Tokenisasi Teks Indonesia dengan Korpus IndoNLU

Studi kasus ini memperkenalkan mahasiswa pada tokenisasi menggunakan dataset `indonlu/smsa` di Google Colab, dengan analisis tambahan untuk menangani tantangan teks Indonesia seperti slang dan afiksasi. Ini selaras dengan CMPK01a dengan menerapkan konsep dasar NLP pada teks Indonesia.

### Kode Colab
```python
# Install pustaka yang diperlukan
!pip install datasets nltk PySastrawi

# Impor pustaka
from datasets import load_dataset
import nltk
from nltk.tokenize import word_tokenize
from sastrawi.stemmer import StemmerFactory
nltk.download('punkt')

# Muat dataset IndoNLU SMSA
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
