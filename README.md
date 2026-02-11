# Custom Punkt Sentence Tokenizer

This repository contains a specialized **Punkt** model for sentence boundary detection. Unlike Transformer-based models, this tokenizer uses an unsupervised statistical approach, making it extremely lightweight and efficient for high-throughput NLP pipelines.


* **Architecture:** Unsupervised Statistical Boundary Detection (Punkt).
* **Format:** Serialized Python `.pickle`.
* **Language/Domain:** Luganda.

---

## 🚀 Usage

### Installation
You only need the `nltk` library and `requests` if loading remotely:
```bash
pip install nltk requests
