# Week 7 PBA
Irmasari Hafidz
irma@its.ac.id

Example GColab (bu irma):
Week 7 PBA/ IndoBERT: [https://colab.research.google.com/drive/1Z17oVBlWmWpbJfiCvI-ARqpv5bGwBWYA?usp=sharing]/ harus punya akun huggingface/ ambil token di akun HF masing2

Ambil token di: [https://huggingface.co/settings/tokens]

## 🔹Part 1: What is NER?   
NER = Named Entity Recognition = finding names of people, organizations, places, dates, etc.

Example:
> “Barack Obama was born in Hawaii in 1961.”

**Entities →** `Barack Obama (PERSON)`, `Hawaii (LOCATION)`, `1961 (DATE)`


Real use cases:

- News summarization
- Resume screening
- Social media analysis
- Chatbots

<img src="https://github.com/irhafidz/PBA/blob/main/figure/img_2.png?raw=true" 
     alt="NER Visualization" 
     width="650">

Reference: https://www.johnsnowlabs.com/named-entity-recognition-ner-with-python-at-scale/

## 🔹 Part 2: Hands-on — Pretrained NER with spaCy / Hugging Face 
Objective: Run and explore NER models.

```python
!pip install spacy
import spacy

nlp = spacy.load("en_core_web_sm")
text = "Elon Musk founded SpaceX in California."
doc = nlp(text)

for ent in doc.ents:
    print(ent.text, ent.label_)

```
```python
Elon Musk PERSON
California GPE
```
> “Elon Musk founded SpaceX in California.”
> 
> Entities → `Elon Musk (PERSON)`, `SpaceX (ORG)`, `California (LOC)`

Discuss:
- What do labels like PERSON, ORG, GPE, DATE mean?
- How accurate is it?

```python
spacy.displacy.render(doc, style="ent", jupyter=True)
```
##💬 1. Optional Add-On: Indonesian NER using IndoBERT or spaCy-id

NER can work in Indonesian language, using pretrained models such as IndoBERT (Hugging Face) or spaCy-id (Indonesian NER pipeline).
use a pretrained model: (indobenchmark/indobert-base-p1 )[https://huggingface.co/indobenchmark/indobert-base-p1]

🧩 Example in Colab
```python
!pip install transformers datasets torch
```

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification
from transformers import pipeline

# Load IndoBERT fine-tuned for NER
model_name = "cahya/bert-base-indonesian-NER"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForTokenClassification.from_pretrained(model_name)

# Create pipeline
nlp_ner = pipeline("ner", model=model, tokenizer=tokenizer, aggregation_strategy="simple")

# Example Indonesian text
text = "Presiden Joko Widodo menghadiri acara di Jakarta bersama Menteri Keuangan Sri Mulyani."

# Run NER
entities = nlp_ner(text)
entities

```
🧭 2. Visualization of Entities (using displacy)

```python
from spacy import displacy

# Convert to spaCy-style
doc_data = {
    "text": text,
    "ents": [{"start": e["start"], "end": e["end"], "label": e["entity_group"]} for e in entities],
    "title": None,
}

# Visualize inline
displacy.render(doc_data, style="ent", manual=True, jupyter=True)

```
🇮🇩 3. Alternative: Using spaCy-id (Indonesian NER)
```python
!pip install spacy spacy-lookups-data
!python -m spacy download id_core_news_sm

import spacy
nlp = spacy.load("id_core_news_sm")

text = "Menteri Kesehatan Budi Gunadi Sadikin mengunjungi RSUP Dr. Sardjito di Yogyakarta."
doc = nlp(text)

for ent in doc.ents:
    print(ent.text, ent.label_)

spacy.displacy.render(doc, style="ent", jupyter=True)

```

📚 Lesson Learned
| Model                 | Description                                           | Strength                           |
| --------------------- | ----------------------------------------------------- | ---------------------------------- |
| **IndoBERT**          | Transformer-based model fine-tuned for Indonesian NER | High accuracy, modern architecture |
| **spaCy-id (legacy)** | Classical NLP pipeline with rules and limited data    | Fast, simple demo                  |

Visualization helps you see how NER models detect entities like PER (Person), ORG (Organization), and LOC (Location) in Bahasa Indonesia.

You can extend this by:
- Testing your own sentences: <<buat text3="">>
- Using domain-specific texts (e.g., halal, climate, education)
- Fine-tuning IndoBERT for custom entity labels 🎓
