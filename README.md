# Pemrograman Bahasa Alami/ Gasal 2025

## Capaian Pembelajaran Mata Kuliah/ CPMK (Course Objectives)
*Capaian Pembelajaran Lulusan (CPL)* #01–#08:

- **CMPK01a**: Memahami dasar-dasar konseptual dari pengolahan bahasa alami (C2) – *Understand conceptual foundations of NLP* (CPL #01, #02).
- **CMPK01b**: Merancang skema encoding bahasa alami sederhana berdasarkan perhitungan (C2, P2) – *Design simple natural language encoding schemes* (CPL #01, #02, #03).
- **CMPK01c**: Menerapkan pemodelan bahasa sederhana (C3) – *Apply simple language modeling* (CPL #01, #02, #03, #04).
- **CMPK01d**: Mengidentifikasi teknik prapemrosesan bahasa yang tepat untuk task tertentu (C4) – *Identify appropriate preprocessing techniques for specific tasks* (CPL #01, #02, #03, #04).
- **CMPK01e**: Menerapkan teknik analisis data pada teks bahasa alami (C3) – *Apply data analysis techniques to natural language text* (CPL #01, #02, #03, #04).
- **CMPK01f**: Menerapkan langkah-langkah pembuatan data set bahasa alami (C3, P3) – *Apply steps to create natural language datasets* (CPL #01, #02, #03, #04).
- **CMPK01g**: Membuat model pengolahan bahasa alami, mengevaluasi dan merekomendasikan perbaikannya (C2, C3, C4) – *Build, evaluate, and recommend improvements for NLP models* (CPL #01, #02, #03, #04).

## Bahan Kajian (Course Content)
- Dasar-dasar konseptual dari pengolahan bahasa alami (Conceptual foundations of NLP).
- Dasar teori informasi dan kaitannya dengan bahasa alami (Information theory and its relation to natural language).
- Pemodelan bahasa dan evaluasinya (Language modeling and evaluation).
- Prapemrosesan teks bahasa alami (Text preprocessing).

## Syllabus Overview
- **Week 1**: Introduction to NLP and Conceptual Foundations (CMPK01a).
- **Week 2**: Data Collection and Dataset Creation (CMPK01f).
- **Week 3**: Web Scraping for NLP Data (CMPK01f).
- **Week 4**: Exploratory Data Analysis (EDA) for NLP (CMPK01e).
- **Week 5**: Preprocessing for Indonesian Text (CMPK01d).
- **Week 6**: TF-IDF and Encoding Schemes (CMPK01b).
- **Week 7**: Language Modeling and Evaluation (CMPK01c, CMPK01g).
- **Week 8**: Final Project and Model Improvement (CMPK01g).

## Week 1: Introduction to NLP – Conceptual Foundations and Tokenization
**Objective**: Understand NLP concepts and perform basic tokenization (CMPK01a).  
**Dataset**: NLTK’s Gutenberg corpus (English text for simplicity).  
**Data Collection Method**: Direct access to a prebuilt corpus via NLTK.  

### Code
```python
import nltk
from nltk.tokenize import word_tokenize

# Download NLTK data
nltk.download('gutenberg')
nltk.download('punkt')

# Load sample text from Gutenberg corpus
text = nltk.corpus.gutenberg.raw('austen-emma.txt')[:1000]  # First 1000 chars of Emma

# Tokenize the text
tokens = word_tokenize(text)

# Print first 20 tokens
print("First 20 tokens:", tokens[:20])

# Basic statistics
print("Total tokens:", len(tokens))
print("Unique tokens:", len(set(tokens)))
