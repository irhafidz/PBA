# 📝 PBA Week 5: Text Embedding & Keyword Extraction

---

## 1. Introduction

### 🎯 Learning Objectives:
1. Memahami metode ekstraksi kata kunci (TF-IDF, TextRank, RAKE).
2. Menerapkan **N-gram extraction** (e.g., *ibu hamil*, *Rp 300 triliun*).
3. Membandingkan NLP: classical and modern NLP methods.
4. Apa itu **text embeddings** & keunggulan
5. Practice: MBA file data TA Mbak Celine.
   
### 📚 References
- Kavita Ganesan (2018). *Practical Guide to Keyword Extraction*  [[link](https://kavita-ganesan.com/python-keyword-extraction/#.W2TlD9hKhhE)]
- Mikolov et al. (2013). *Efficient Estimation of Word Representations in Vector Space*. NIPS.
- Devlin et al. (2019). *BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding*. NAACL.

---

## 2. Dataset Overview
We will use a dataset containing MBG-related articles stored in a CSV file. The dataset contains fields like:
- **ID**: Article code
- **Category**: e.g., Proyeksi, Implementasi
- **Source**: e.g., Kompas.com
- **Date**: Publication date
- **Title**: Article title
- **Content**: Full article text
- **Tone**: Manual sentiment annotation (e.g., Netral, Positif, Negatif)

---

## 📘 Structured Lecture Notebook 

**1. Introduction** 
MBG (Makanan Bergizi Gratis)  news/articles.
Learning objectives: keyword extraction, n-gram analysis, embeddings, clustering, visualization.

**2. Load Dataset** 
Read CSV (artikel_manual_celine.csv).
Inspect fields (title, content, tone, etc.).

```python
from google.colab import files
import pandas as pd
import io

# Upload the Excel file
uploaded = files.upload()

# Get the filename automatically
filename = list(uploaded.keys())[0]

# Read two sheets into two separate DataFrames
df1 = pd.read_excel(io.BytesIO(uploaded[filename]), sheet_name="Case")
df2 = pd.read_excel(io.BytesIO(uploaded[filename]), sheet_name="Main")

# Preview
print("Sheet1 Shape:", df1.shape)
print("Sheet2 Shape:", df2.shape)

display(df1.head())
display(df2.head())
```

**3. Preprocessing** 
Clean text (lowercase, remove punctuation, stopwords).
Tokenization.

```python
### 🔧 Implementation
import re
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

nltk.download('punkt')
nltk.download('stopwords')
nltk.download('punkt_tab')

# Example: use only first article for demonstration
text = df2['Konten'][0]

# Lowercase
text = text.lower()

# Remove punctuation & numbers
text = re.sub(r'[^a-zA-Z\s]', '', text)

# Tokenization
tokens = word_tokenize(text)

# Remove stopwords
stop_words = set(stopwords.words('indonesian'))
filtered_tokens = [w for w in tokens if w not in stop_words]

print("Original Text (shortened):", df2['Konten'][0][:300])
print("\nProcessed Tokens:", filtered_tokens[:30])

```

**4. Keyword Extraction with TF-IDF**
Compare per-article vs. across dataset.

```python
from sklearn.feature_extraction.text import TfidfVectorizer
import pandas as pd
import re
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

nltk.download('punkt')
nltk.download('stopwords')

# Example: Apply TF-IDF on the 'Content' column of your dataset
# (replace 'Content' with your actual column name if different)
documents = df2['Konten'].astype(str).tolist()

# Get Indonesian stopwords
stop_words = set(stopwords.words('indonesian'))

# Initialize TF-IDF Vectorizer
vectorizer = TfidfVectorizer(max_features=20, ngram_range=(1,2), stop_words=list(stop_words))
tfidf_matrix = vectorizer.fit_transform(documents)

# Get feature names and scores
feature_names = vectorizer.get_feature_names_out()
dense = tfidf_matrix.todense()
denselist = dense.tolist()

# Create a DataFrame of TF-IDF scores
tfidf_df = pd.DataFrame(denselist, columns=feature_names)

print("Top TF-IDF Features across all documents:")
print(tfidf_df.sum().sort_values(ascending=False).head(20))
```


```python
Top TF-IDF Features across all documents:
program           8.753301
mbg               8.383029
makanan           7.513167
anak              7.448690
makan             6.094812
bergizi           5.378527
sekolah           5.013915
gizi              4.743646
gratis            4.673093
makan bergizi     4.375018
siswa             4.058666
bergizi gratis    4.018241
anggaran          3.883868
juta              3.474604
000               3.401372
triliun           3.290931
pemerintah        3.163490
indonesia         2.931050
pendidikan        2.139346
guru              1.134060
dtype: float64
```


**5. N-gram Analysis**
Extract bigrams/trigrams like “ibu hamil”, “Rp 300 triliun”.
Why n-grams matter in policy/news context.

📝Apa itu N-grams?
Unigram: single word → "makanan", "gratis".
Bigram: 2 consecutive words → "ibu hamil", "makanan basi".
Trigram: 3 consecutive words → "Rp 300 triliun", "program makanan gratis".

📊Why it matters? In policy/news, single words lose meaning.
"ibu" vs. "ibu hamil" → very different context.
"Rp" vs. "Rp 300 triliun" → magnitude of funding is lost if split.
N-grams capture context & semantics better.

Useful in:
Policy evaluation: track mentions of budget figures.
Public health news: phrases like "stunting anak", "ibu menyusui".

```python
import pandas as pd
from sklearn.feature_extraction.text import CountVectorizer
from nltk.corpus import stopwords # Import stopwords

# Take the 'content' column for analysis
texts = df2['Konten'].dropna().tolist()

# Get Indonesian stopwords
stop_words = set(stopwords.words('indonesian'))

# Create CountVectorizer for bigrams & trigrams
vectorizer = CountVectorizer(ngram_range=(2,3), stop_words=list(stop_words), max_features=10)
X = vectorizer.fit_transform(texts)

# Get top bigrams/trigrams
ngrams = vectorizer.get_feature_names_out()
counts = X.sum(axis=0).A1
ngram_freq = pd.DataFrame({'ngram': ngrams, 'count': counts}).sort_values(by='count', ascending=False)

ngram_freq
```

|index|ngram|count|
|---|---|---|
|4|makan bergizi|98|
|1|bergizi gratis|93|
|5|makan bergizi gratis|85|
|7|program makan|54|
|0|anak anak|47|
|8|program makan bergizi|47|
|9|program mbg|37|
|3|gratis mbg|31|
|2|bergizi gratis mbg|31|
|6|penerima manfaat|27|

🔍 Discussion 

"ibu hamil" and "ibu menyusui" appear → specific policy target groups.
"Rp 300 triliun" → captures budget discourse in MBG policy.
"makanan basi" → captures negative feedback/complaints.

➡️ N-grams help us understand narratives and focus points in media coverage, which would be lost with single-word analysis.
