# Luganda Punkt Sentence Tokenizer

This repository contains a specialized **Punkt** model for sentence boundary detection. Unlike Transformer-based models, this tokenizer uses an unsupervised statistical approach, making it extremely lightweight and efficient for high-throughput NLP pipelines.


* **Architecture:** Unsupervised Statistical Boundary Detection (Punkt).
* **Format:** Serialized Python `.json`.
* **Language/Domain:** Luganda.

---

## 🚀 Usage

### Installation
You only need the `nltk` library:
```bash
pip install nltk
```
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
