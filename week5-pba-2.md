## 5.1 Lemma & Morphological Variations Search
```python
import re
import pandas as pd
import nltk
from collections import Counter

nltk.download("punkt")

# Define lemma roots
lemmas = ["racun", "basi", "korban", "kejang"]

# Regex patterns to catch variations of each lemma
patterns = {lemma: re.compile(rf"\b\w*{lemma}\w*\b", re.IGNORECASE) for lemma in lemmas}

# Function: extract sentences + matched variations
def find_variations(text, patterns):
    if pd.isna(text):
        return []
    found = []
    sentences = nltk.sent_tokenize(text)
    for sent in sentences:
        for lemma, pattern in patterns.items():
            matches = pattern.findall(sent)
            if matches:
                found.append((lemma, sent.strip(), matches))
    return found

# Apply to dataset
df2['lemma_sentences'] = df2['Konten'].apply(lambda x: find_variations(x, patterns))

# Flatten results for frequency summary
all_matches = []
for row in df2['lemma_sentences']:
    for lemma, sent, matches in row:
        all_matches.extend([(lemma, m.lower()) for m in matches])

# Count frequency per lemma root
lemma_counts = Counter([lemma for lemma, _ in all_matches])

# Count frequency per variation
variation_counts = Counter([match for _, match in all_matches])

# Convert to DataFrames for readability
df_lemma_summary = pd.DataFrame(lemma_counts.items(), columns=["lemma_root", "count"]).sort_values(by="count", ascending=False)
df_variation_summary = pd.DataFrame(variation_counts.items(), columns=["variation", "count"]).sort_values(by="count", ascending=False)

print("🔹 Frequency per Lemma Root:")
display(df_lemma_summary)

print("🔹 Frequency per Word Variation:")
display(df_variation_summary)

# Show sentences with matches (sample 5)
df_lemma_sentences = df2[df2['lemma_sentences'].str.len() > 0][['Judul', 'lemma_sentences']]
display(df_lemma_sentences.head(5))

```
#🔹 Frequency per Lemma Root:

|index|lemma\_root|count|
|---|---|---|
|1|racun|32|
|0|basi|17|
|2|korban|14|

# Step by step:
- Tokenize sentences from the Konten column using nltk.sent_tokenize.
- Search all lemma variations (racun, basi, korban, kejang) using regex patterns that catch prefixes/suffixes (e.g., keracunan, diracun, korban-korban, kejang-kejang).
- Collect matches as tuples (lemma, sentence, matched_words).
- Flatten and count results:

df_lemma_summary → frequency per lemma root.
df_variation_summary → frequency per actual word variation.

- Display sample sentences with their matched words for context.

# Lesson learned N-grams
5 → general n-gram extraction (e.g., ibu hamil, Rp 300 triliun).
5.1 → deeper lemma/morphological search (domain-specific keywords).

```python
import re
import pandas as pd
import nltk
from collections import Counter

nltk.download("punkt")

# Define lemma roots
lemmas = ["racun", "basi", "korban", "kejang"]

# Regex patterns to catch variations of each lemma
patterns = {lemma: re.compile(rf"\b\w*{lemma}\w*\b", re.IGNORECASE) for lemma in lemmas}

# Function: extract sentences + matched variations
def find_variations(text, patterns):
    if pd.isna(text):
        return []
    found = []
    sentences = nltk.sent_tokenize(text)
    for sent in sentences:
        for lemma, pattern in patterns.items():
            matches = pattern.findall(sent)
            if matches:
                found.append((lemma, sent.strip(), matches))
    return found

# Apply to dataset
df2['lemma_sentences'] = df2['Konten'].apply(lambda x: find_variations(x, patterns))

# --- 1) Lemma frequency summary ---
all_matches = []
for row in df2['lemma_sentences']:
    for lemma, sent, matches in row:
        all_matches.extend([(lemma, m.lower()) for m in matches])

lemma_counts = Counter([lemma for lemma, _ in all_matches])
df_lemma_summary = pd.DataFrame(
    lemma_counts.items(), columns=["lemma_root", "count"]
).sort_values(by="count", ascending=False)

# --- 2) Variation frequency summary ---
variation_counts = Counter([match for _, match in all_matches])
df_variation_summary = pd.DataFrame(
    variation_counts.items(), columns=["variation", "count"]
).sort_values(by="count", ascending=False)

# --- 3) Sentence-level matches ---
rows = []
for i, row in df2.iterrows():
    for lemma, sent, matches in row['lemma_sentences']:
        for m in matches:
            rows.append({
                "Judul": row['Judul'],
                "lemma_root": lemma,
                "match": m,
                "sentence": sent
            })

df_sentence_matches = pd.DataFrame(rows)


df_lemma_summary
df_variation_summary
df_sentence_matches

```
# df_lemma_summary
|index|lemma\_root|count|
|---|---|---|
|1|racun|32|
|0|basi|17|
|2|korban|14|

# df_variation_summary
|index|variation|count|
|---|---|---|
|1|keracunan|31|
|0|basi|16|
|2|korban|13|
|3|korbannya|1|
|4|berbasis|1|
|5|meracuni|1|

# df_sentence_matches.head()
|index|Judul|lemma\_root|match|sentence|
|---|---|---|---|---|
|0|Persiapan Makan Bergizi Gratis: Sudah Simulasi Pengiriman, Ada Puluhan Perusahaan Minat Terlibat|basi|basi|Salah satu opsi yang disiapkan adalah mengemas makanan dengan vakum agar bisa tahan lama, tidak basi\.|
|1|Keluhan Makanan Basi di Menu Makan Bergizi Gratis, Apa Dampaknya jika Dikonsumsi Anak?|basi|basi|Makanan yang seharusnya menjadi solusi gizi, justru menimbulkan keluhan akibat kualitas makanan yang buruk, salah satunya makanan basi\.|
|2|Keluhan Makanan Basi di Menu Makan Bergizi Gratis, Apa Dampaknya jika Dikonsumsi Anak?|basi|basi|Kasus makanan basi yang ditemukan dalam distribusi menu bergizi ini, memicu kekhawatiran tentang dampak kesehatan bagi anak-anak yang mengonsumsinya\.|
|3|Keluhan Makanan Basi di Menu Makan Bergizi Gratis, Apa Dampaknya jika Dikonsumsi Anak?|basi|basi|Menurut dokter dan Ahli Gizi Masyarakat DR\. dr\. Tan Shot Yen, M\.hum, makanan basi jelas tidak layak untuk dikonsumsi anak\.|
|4|Keluhan Makanan Basi di Menu Makan Bergizi Gratis, Apa Dampaknya jika Dikonsumsi Anak?|basi|basi|“Makanan basi itu bukan makanan yang layak untuk dimakan\.|
