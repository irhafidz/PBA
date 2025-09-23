## TF-IDF, RAKE, Text Rank

🔑 Key Lesson: Different NLP Methods Tell Different Stories

#TF-IDF

- Focuses on word frequency & rarity.
- Great for identifying important terms like “triliun”, “anggaran”.
- But: misses multi-word phrases and deeper context.

# RAKE (Rapid Automatic Keyword Extraction)

- Finds multi-word phrases by removing stopwords and scoring co-occurrence.
- Captures more policy-relevant expressions like “anggaran program makan bergizi gratis”, “makanan basi”.
- But: purely statistical, doesn’t “understand” meaning.

# TextRank

- Graph-based: ranks sentences/phrases by importance.
- Captures contextual highlights, e.g. “Makanan basi jelas tidak layak untuk dikonsumsi anak”.
- Useful when you want summaries or key messages, not just terms.

📊 Why this matters in MBG (Makanan Bergizi Gratis) analysis

- TF-IDF → shows the numbers & policy focus (Rp 300 triliun, 82,9 juta orang).
- RAKE → reveals social & health concerns (makanan basi, dampak kesehatan anak).
- TextRank → highlights narratives & framing in media (“Makanan basi jelas tidak layak…”).

```python
# Install needed packages
!pip install rake-nltk sumy openpyxl

import nltk
from nltk.corpus import stopwords
from sklearn.feature_extraction.text import TfidfVectorizer
from rake_nltk import Rake
from sumy.parsers.plaintext import PlaintextParser
from sumy.nlp.tokenizers import Tokenizer
from sumy.summarizers.text_rank import TextRankSummarizer
import pandas as pd

# Download NLTK resources
nltk.download('punkt')
nltk.download('stopwords')

# --- 1. TF-IDF Setup ---
stop_words = stopwords.words("indonesian")
vectorizer = TfidfVectorizer(max_features=50, stop_words=stop_words)
X = vectorizer.fit_transform(df2["Konten"].fillna(""))
tfidf_feature_names = vectorizer.get_feature_names_out()

def extract_tfidf_keywords(doc_index, top_n=5):
    row = X[doc_index].toarray().flatten()
    top_indices = row.argsort()[::-1][:top_n]
    return [tfidf_feature_names[i] for i in top_indices if row[i] > 0]

# --- 2. RAKE Setup ---
r = Rake(stopwords=stop_words)

def extract_rake_keywords(text, top_n=5):
    if pd.isna(text):
        return []
    r.extract_keywords_from_text(text)
    return [phrase for score, phrase in r.get_ranked_phrases_with_scores()[:top_n]]

# --- 3. TextRank Setup ---
summarizer = TextRankSummarizer()

def extract_textrank_keywords(text, top_n=3):
    if pd.isna(text) or not isinstance(text, str):
        return []
    try:
        parser = PlaintextParser.from_string(text, Tokenizer("indonesian"))
    except LookupError:
        parser = PlaintextParser.from_string(text, Tokenizer("english"))
    summary = summarizer(parser.document, top_n)
    return [str(sentence) for sentence in summary]

# --- 4. Apply all methods to ALL documents ---
comparison_results = []
tfidf_results = []
rake_results = []
textrank_results = []

for idx in range(len(df2)):
    text = df2.loc[idx, "Konten"]
    title = df2.loc[idx, "Judul"]

    tfidf_kw = extract_tfidf_keywords(idx, top_n=5)
    rake_kw = extract_rake_keywords(text, top_n=5)
    textrank_kw = extract_textrank_keywords(text, top_n=3)

    comparison_results.append({
        "doc_id": idx,
        "title": title,
        "TF-IDF": tfidf_kw,
        "RAKE": rake_kw,
        "TextRank": textrank_kw
    })

    for kw in tfidf_kw:
        tfidf_results.append({"doc_id": idx, "title": title, "keyword": kw})
    for kw in rake_kw:
        rake_results.append({"doc_id": idx, "title": title, "keyword": kw})
    for kw in textrank_kw:
        textrank_results.append({"doc_id": idx, "title": title, "keyword": kw})

# DataFrames
df_comparison = pd.DataFrame(comparison_results)
df_tfidf = pd.DataFrame(tfidf_results)
df_rake = pd.DataFrame(rake_results)
df_textrank = pd.DataFrame(textrank_results)

# --- 5. Export to Excel with multiple sheets ---
output_file = "mbg_keywords_comparison.xlsx"
with pd.ExcelWriter(output_file, engine="openpyxl") as writer:
    df_tfidf.to_excel(writer, sheet_name="TF-IDF", index=False)
    df_rake.to_excel(writer, sheet_name="RAKE", index=False)
    df_textrank.to_excel(writer, sheet_name="TextRank", index=False)
    df_comparison.to_excel(writer, sheet_name="Comparison", index=False)

print(f"✅ Exported all results to {output_file}")

  ```
