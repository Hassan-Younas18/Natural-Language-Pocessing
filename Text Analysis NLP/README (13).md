# 📚 NLP Lab 1 — Introduction to Text Processing in Python

**Module:** ICP-4721 Natural Language Processing  
**Institution:** Bangor University, School of Computer Science and Engineering  
**Author:** Hassan Younas  
**Lecturer:** Bill Teahan  
**Academic Year:** 2025 / 2026

---

## Overview

This repository contains the full submission for Laboratory 1 of ICP-4721 Natural Language Processing. The lab investigates fundamental statistical properties of natural language text through corpus analysis in Python, covering Zipf's Law, Heap's Law, vocabulary growth, hapax legomena, and the zero-frequency problem.

---

## Repository Structure

```
nlp-lab1-text-processing/
│
├── NLP_Lab1.ipynb                  # Jupyter Notebook with all code and outputs
└── README.md
```

> **Note:** The five text corpora (random text, encrypted Brown Corpus, BBC News, Reddit, and French text) are not included in this repository as they contain manually collected data. All code to generate the random and encrypted corpora is included inside the notebook. Refer to the [Corpora Description](#corpora-description) section for details on how to recreate them.

---

## Corpora Description

| # | File | Description | Source |
|---|------|-------------|--------|
| 1 | `random_text.txt` | Randomly generated English-like words (no linguistic structure) | Python `random` + `string` libraries |
| 2 | `encrypted_Brown.txt` | Brown Corpus encrypted via a random substitution cipher | Brown Corpus (`Brown.txt`) |
| 3 | `News_Articles.txt` | ~100,000+ characters of formal English news text | BBC News (manually collected) |
| 4 | `Social_Media.txt` | ~100,000+ characters of informal English social media text | Reddit (manually collected) |
| 5 | `French_text.txt` | ~100,000+ characters of French-language news text | France 24 — French edition (manually collected) |

---

## Analysis Performed

### 1. Zipf's Law
Words ranked by descending frequency are plotted on a log–log scale. Natural language corpora produce a near-linear curve (slope ≈ −1), while random text produces a flat curve — confirming Zipfian distributions are a property of linguistic structure.

### 2. Heap's Law
Cumulative unique word types are plotted against cumulative word tokens. For typical English, vocabulary grows approximately as `V ≈ K · N^β` where `β ≈ 0.5`. Random text approaches `β ≈ 1`, reflecting no vocabulary saturation.

### 3. Types vs Tokens
Absolute vocabulary size is plotted against the running token count. All natural language corpora exhibit a concave (decelerating) growth curve; random text shows near-linear growth.

### 4. Word Length Grouping
Words are grouped by character length. Reveals noise in corpora (URLs, punctuation artefacts, encoding errors) and confirms the distribution of function vs content words across corpora.

### 5. Hapax Legomena (Sparse Data Analysis)
Computes the percentage of word types with frequency 1 (hapax legomena), frequency 2 (dis legomena), and frequency > 2. Quantifies the scale of the sparse data problem in each corpus.

| Corpus | Hapax (freq=1) | Dis (freq=2) | Frequent (freq>2) |
|--------|---------------|-------------|------------------|
| Random Text | ~96% | ~2% | ~2% |
| Encrypted Brown | ~49% | ~14% | ~37% |
| News Articles | ~46% | ~18% | ~35% |
| Social Media | ~45% | ~24% | ~31% |
| French Text | varies | varies | varies |

### 6. Zero Frequency (Missing Words) Analysis
Computes the percentage of vocabulary unique to each corpus in a pair. Demonstrates the domain shift problem — a model trained on one corpus will encounter a high proportion of unseen words from another.

---

## Requirements

```
Python 3.8+
matplotlib
collections (standard library)
re (standard library)
random (standard library)
string (standard library)
```

Install dependencies:

```bash
pip install matplotlib
```

---

## Usage

Clone the repository:

```bash
git clone https://github.com/your-username/nlp-lab1-text-processing.git
cd nlp-lab1-text-processing
```

Open the notebook in Jupyter:

```bash
jupyter notebook NLP_Lab1.ipynb
```

The notebook is self-contained and walks through all analyses in order — corpus generation, encryption, Zipf's Law, Heap's Law, Types vs Tokens, word grouping, hapax legomena, and zero frequency analysis — with inline plots and outputs at each step.

> **Before running:** Place your copies of `News_Articles.txt`, `Social_Media.txt`, `French_text.txt`, and `Brown.txt` in the same directory as the notebook. The random and encrypted corpora are generated automatically by the notebook itself.

---

## Key Findings

- **Statistical laws hold universally across natural language:** Zipf's Law and Heap's Law are consistent across English news, English social media, and French news — but break down entirely for random text.
- **Genre matters for NLP generalisation:** Despite both being English, BBC News and Reddit have measurably different Zipfian slopes, hapax rates, and vocabulary overlap, making cross-genre model transfer challenging.
- **The sparse data problem is pervasive:** Even in a 100,000-character corpus, over 45% of word types typically appear only once, necessitating smoothing techniques and large training datasets.
- **Text preprocessing is non-negotiable:** Group-word analysis revealed noise in every corpus — URLs, punctuation artefacts, HTML fragments — underscoring the need for robust preprocessing pipelines.

---

## Academic Integrity

All data collection, code implementation, debugging, and analysis in this project were completed independently by the author. An LLM (Claude by Anthropic) was used solely as a writing and formatting assistant for the lab report. All technical interpretations and findings are the author's own.

---

## References

- Zipf, G. K. (1949). *Human Behavior and the Principle of Least Effort.* Addison-Wesley Press.
- Heaps, H. S. (1978). *Information Retrieval: Computational and Theoretical Aspects.* Academic Press.
- Chen, S. F. (1996). *Building probabilistic models for natural language.* Ph.D. thesis, Harvard University.
- Python Documentation: [https://docs.python.org/3/](https://docs.python.org/3/)
- BBC News: [https://www.bbc.com/news](https://www.bbc.com/news)
- Reddit: [https://www.reddit.com](https://www.reddit.com)
- France 24 (French): [https://www.france24.com/fr/](https://www.france24.com/fr/)
