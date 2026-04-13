# Luganda Punkt Sentence Tokenizer
#[UPDATE]
THE NEW VERSION HAS BEEN TRAINED ON 3 million + sentences
The modal  will be available on our api, and huggingface 
This repository contains a specialized **Punkt** model for sentence boundary detection. Unlike Transformer-based models, this tokenizer uses an unsupervised statistical approach, making it extremely lightweight and efficient for high-throughput NLP pipelines.


* **Architecture:** Unsupervised Statistical Boundary Detection (Punkt).
* **Format:** `.json`.
* **Language/Domain:** Luganda.
* **Data:** Trained on 3 million+ sentences.

---

##  Real-World Use Cases
Sentence Boundary Detection (SBD) is the foundation of modern NLP. This model is designed for:

* **Machine Translation Pre-alignment:** Breaking large paragraphs into discrete sentences to ensure source and target texts are perfectly aligned before being fed into translation models.
* **Large-Scale Web Mining:** Processing massive datasets (e.g., Common Crawl) for LLM pre-training where the $O(n)$ efficiency of Punkt outperforms costly Transformer-based splitters.
* **Legal & Medical Analysis:** Handling dense texts saturated with abbreviations (e.g., "v.", "corp.", "approx.", "Dr.") that often break standard regex-based splitters.
* **Abstractive Summarization:** Ensuring precise sentence boundaries so that summarization algorithms can rank and extract information without truncating mid-clause.
* **Search Engine Indexing:** Improving the granularity of indexed text segments for more accurate snippet generation in search results.

##  Usage

### Installation
You only need the `nltk` library:
## Step 1
```bash
pip install nltk
```
---
## Step 2
```bash
git clone https://github.com/sage-pond/PunktTokenizer.git
```
---
## Step 3
```python
import json
from nltk.tokenize.punkt import PunktParameters, PunktSentenceTokenizer
with open('luganda.json', 'r') as f:
    data = json.load(f)
params = PunktParameters()
params.abbrev_types = set(data['abbrev_types'])
params.collocations = set(tuple(c) for c in data['collocations'])
params.sent_starters = set(data['sent_starters'])
params.ortho_context = data['ortho_context']

tokenizer = PunktSentenceTokenizer(params)
text = '''Emiti gy’obulo giyinza okulumbibwa ebiwuka eby’enjawulo omuli enseenene eziyitibwa codling moths, enseenene z’obulo n’enseenene. Okufuga ebiwuka bino, kikulu okulondoola emiti buli kiseera n’okukola amangu ddala ng’obubonero obulaga nti girimu ebiwuka. Kino kiyinza okuzingiramu okukozesa emitego gya pheromone, okusiiga eddagala eritta ebiwuka oba okukozesa ebisolo ebirya ebisolo eby’obutonde nga ladybugs. Era kikulu okukuuma obuyonjo obulungi mu nnimiro ng’oggyawo ebibala ebigudde n’okusala enku enfu.Biwuka ki ebitera okulumba emiti gy’obulo era nnyinza ntya okubifuga?
'''
print(tokenizer.tokenize(text))
```
