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
