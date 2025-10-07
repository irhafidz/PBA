# Week 7 PBA
Irmasari Hafidz
irma@its.ac.id

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
Discuss:
- What do labels like PERSON, ORG, GPE, DATE mean?
- How accurate is it?

  

