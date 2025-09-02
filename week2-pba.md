

###Pengumpulan Data dan Pembuatan Dataset untuk NLP 
**Metodologi, Pipeline, dan Aplikasi Praktis**  
  - Pengumpulan Data dan Dataset (CMPK01f)  
  - NLP pipeline data: alur dari ulasan aplikasi ke dataset terstruktur.  
---

### Tujuan Pembelajaran
- Memahami proses pengumpulan data untuk NLP (CMPK01f, C2).  
- Mengenal pipeline data: pengumpulan, pembersihan, prapemrosesan, anotasi.  
- Mengidentifikasi sumber data (misalnya, ulasan Google Play, media sosial).  
- Mempraktikkan pengumpulan dan prapemrosesan data ulasan TfL Go di Google Colab.  
- Menghubungkan pipeline data dengan aplikasi dunia nyata, termasuk konteks Indonesia.  

---

### Apa itu Pengumpulan Data untuk NLP?
- **Definisi**:  
  - Pengumpulan data adalah proses mengumpulkan teks atau ucapan dari sumber seperti media sosial, ulasan aplikasi, atau dokumen resmi untuk analisis NLP.  
- **Deskripsi**:  
  - Tujuan: Membuat dataset berkualitas tinggi untuk pelatihan model NLP.  
  - Jenis Data: Teks terstruktur (misalnya, database), semi-terstruktur (misalnya, JSON dari API), tak terstruktur (misalnya, ulasan pengguna).  
  - Contoh Indonesia: Mengumpulkan tweet tentang BPJS Kesehatan untuk analisis sentimen.  
- Jurafsky, D., & Martin, J. H. (2023). *Speech and Language Processing* (edisi ke-3, draf), Bab 2. [https://web.stanford.edu/~jurafsky/slp3/](https://web.stanford.edu/~jurafsky/slp3/)  

---

### Pipeline Data untuk NLP
- **Tahapan Pipeline Data**:  
  1. **Identifikasi Sumber**: Memilih sumber data (misalnya, Google Play, Twitter, Wikipedia).  
  2. **Pengumpulan Data**: Menggunakan API, web scraping, atau dataset publik.  
  3. **Pembersihan Data**: Menghapus duplikat, teks tidak relevan, atau kebisingan (misalnya, emoji, tanda baca berlebih).  
  4. **Prapemrosesan**: Tokenisasi, penghapusan stopword, stemming/lemmatisasi.  
  5. **Anotasi**: Memberi label data (misalnya, sentimen positif/negatif).  
  6. **Penyimpanan**: Menyimpan dataset dalam format terstruktur (misalnya, CSV, JSON).  
- **Fokus Indonesia**: Menangani slang (misalnya, “nggak”), afiksasi (misalnya, “bermain” → “main”), dan code-switching.  
- **Contoh**: Pipeline untuk ulasan TfL Go (pengumpulan via scraping → prapemrosesan → analisis sentimen).  
- **Referensi**: Bird, S., et al. (2009). *Natural Language Processing with Python* (NLTK Book), Bab 3. [https://www.nltk.org/book/](https://www.nltk.org/book/)  

---

### Sumber Data untuk NLP
- **Jenis Sumber Data**:  
  - **Media Sosial**: Twitter, Instagram (contoh: tweet Indonesia tentang transportasi).  
  - **Ulasan Pengguna**: Google Play, App Store (contoh: ulasan TfL Go).  
  - **Korpus Publik**: Wikipedia, IndoNLU, dataset Hugging Face.  
  - **Dokumen Resmi**: Laporan pemerintah, berita (contoh: berita Kompas).  
- **Metode Pengumpulan**:  
  - **API**: Twitter API, Google Play Scraper.  
  - **Web Scraping**: Menggunakan pustaka seperti `BeautifulSoup` atau `Scrapy`.  
  - **Dataset Publik**: Hugging Face, Kaggle.  
- **Konteks Indonesia**: Dataset IndoNLU, Wikipedia Bahasa Indonesia.  
- **Referensi**: Cahyawijaya, S., et al. (2020). “IndoNLU: Benchmark and Resources for Evaluating Indonesian NLP.” *Proceedings of the 1st Conference of the Asia-Pacific Chapter of the ACL*. [https://aclanthology.org/2020.aacl-main.85/](https://aclanthology.org/2020.aacl-main.85/)  

---

### Tantangan dalam Pengumpulan Data
- **Data Noisy**: Emoji, tanda baca berlebih, ejaan tidak standar (misalnya, “nggak” vs. “tidak”).  
- **Privasi dan Etika**: Menghormati privasi pengguna (misalnya, ulasan anonim di Google Play).  
- **Kekurangan Data**: Bahasa sumber daya rendah seperti Indonesia memiliki dataset terbatas.  
- **Bias Data**: Ulasan cenderung negatif (misalnya, pengguna TfL Go lebih sering mengeluh).  
- **Contoh**: Ulasan TfL Go seperti “App ini lambat banget!” mengandung slang dan sentimen negatif.  
- **Referensi**: Jurafsky & Martin, Bab 2; Bender, E. M., et al. (2021). “On the Dangers of Stochastic Parrots.” *Proceedings of the 2021 ACM Conference on Fairness, Accountability, and Transparency*. [https://dl.acm.org/doi/10.1145/3442188.3445922](https://dl.acm.org/doi/10.1145/3442188.3445922)  

---

### Metodologi Pipeline Data (TfL Go Case Study)
- Pipeline data untuk ulasan TfL Go di Google Play.  
- **Metodologi** (berdasarkan literatur akademik):  
  1. **Pengumpulan**: Menggunakan pustaka `google-play-scraper` untuk mengambil ulasan.  
  2. **Pembersihan**: Menghapus emoji, duplikat, dan teks non-relevan.  
  3. **Prapemrosesan**: Tokenisasi, penghapusan stopword, stemming (mengadaptasi untuk slang).  
  4. **Anotasi**: Memberi label sentimen (positif, negatif, netral) secara manual atau otomatis.  
  5. **Analisis**: Menghitung frekuensi kata, visualisasi sentimen.  
- **Referensi**:  
  - Jurafsky & Martin (2023), Bab 2: Pipeline data dan prapemrosesan teks.  
  - Liu, B. (2012). *Sentiment Analysis and Opinion Mining*. Morgan & Claypool Publishers, Bab 3. [https://www.morganclaypool.com/doi/abs/10.2200/S00416ED1V01Y201204DMK004](https://www.morganclaypool.com/doi/abs/10.2200/S00416ED1V01Y201204DMK004)  

---

### Pengumpulan dan Prapemrosesan Data: what tools?
- **Python**:  
  - `google-play-scraper`: Mengambil ulasan dari Google Play.  
  - `pandas`: Mengelola dataset dalam format tabel.  
  - `nltk`, `Sastrawi`: Tokenisasi, stemming untuk teks Indonesia.  
  - `emoji`: Menghapus atau mengkodekan emoji.  
- **Pengaturan**: Instal Python, `pip install google-play-scraper pandas nltk PySastrawi emoji`.  
- **Contoh**: Prapemrosesan ulasan TfL Go seperti “This app is AMAZING!”.  
- **Referensi**: Bird et al., NLTK Book, Bab 3; Dokumentasi Hugging Face.  

---

### Aplikasi Pipeline Data dalam Proyek Pemerintahan
Lima contoh penerapan pipeline data dalam proyek pemerintahan:  
1. **TfL Go Sentiment Analysis (UK)**:  
   - **Deskripsi**: Mengumpulkan ulasan TfL Go untuk menganalisis sentimen pengguna.  
   - **Pipeline**: Scraping → Pembersihan → Tokenisasi → Analisis sentimen.  
   - **Dampak**: Meningkatkan pengalaman pengguna aplikasi transportasi.  
   - **Contoh**: Ulasan “Fantastic app!” diklasifikasi sebagai positif.  [Transport for London](https://play.google.com/store/apps/details?id=uk.gov.tfl.gotfl&hl=en_GB)
2. **Indonesia’s BPJS Kesehatan Social Media Monitoring**:
   Google COlab (IH) di [link berikut](https://colab.research.google.com/drive/1F67OUFULNBBTTe-DgMHo5e7a8J2sjZgy#scrollTo=lkr3a1TRC6h-) 
   - **Deskripsi**: Mengumpulkan tweet untuk analisis sentimen layanan BPJS.  
   - **Pipeline**: Twitter API → Pembersihan slang → Analisis sentimen.  
   - **Dampak**: Memberikan masukan untuk kebijakan kesehatan.  
   - **Contoh**: Tweet “BPJS lambat banget!” diklasifikasi negatif.  
- **Referensi**: Informasi proyek pemerintahan dari sumber web.  [Mobile JKN di Google Apps](https://play.google.com/store/apps/details?id=app.bpjs.mobile&hl=id&pli=1))

---

### Week 2: Praktikum: Ulasan TfL Go di Google Colab
- **Tugas**: Mengumpulkan dan memproses ulasan TfL Go dari Google Play.  
- **Alat**: Google Colab, `google-play-scraper`.  
- **Tujuan**: Mempraktikkan pipeline data (pengumpulan → prapemrosesan → analisis).  
- **Dataset**: Ulasan TfL Go (teks multibahasa, fokus Inggris).  
- Buka [Google Colab](https://colab.research.google.com).  
- Buat notebook baru, salin-tempel kode studi kasus.  
- Instal pustaka: `google-play-scraper`, `pandas`, `nltk`, `PySastrawi`, `emoji`.  
- Analisis output: ulasan, token, frekuensi kata, visualisasi sentimen.  



---



### Recap Week 2: 
- **Rekap**: Pengumpulan data, pipeline data, prapemrosesan, tantangan.  
- **Pratinjau Pekan 3**: Ekstraksi fitur dan representasi teks (CMPK01g).  
- **Tugas Membaca**:  
  - Baca Bab 3 NLTK Book.  
  - Coba kumpulkan 10 ulasan aplikasi lokal (misalnya, Gojek) dan lakukan tokenisasi.  

---
