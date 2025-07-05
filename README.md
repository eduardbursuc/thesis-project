# 🛡️ Phishing URL Detection with Bloom Encoding

This repository contains all Jupyter notebooks used for experiments in my Bachelor thesis.

The project combines **deep learning** with **privacy-preserving techniques** to create an efficient phishing URL detection system. It specifically focuses on **Bloom encoding** — a novel method in this context — to anonymize sensitive URL data. The core goal is to **compare the detection performance between clear-text and encoded inputs** using deep learning models.

---

## 🔍 Project Overview

Two encoding strategies were explored and compared with their clear-text counterparts:

### 🌐 Q-Gram + Bloom Encoding

- Split each URL into overlapping Q-grams.
- Initialize a Bloom filter of size `l`.
- For each Q-gram:
  - Generate `k` hash values.
  - Map those positions in the Bloom filter to `1`.
- Feed the resulting bit array into a deep learning model.

**Goal**: Evaluate if encoding URLs this way retains enough information for accurate classification.

---

### 🧩 Feature-Based Bloom Encoding

- Extract structured features from URLs (e.g., length, presence of IP, HTTPS).
- Key each feature to avoid collisions (e.g., `URL_Length: u80`, `has_ip: i1`).
- Apply Bloom encoding on these keyed feature values.
- Feed resulting bit arrays into a deep learning model.

**Goal**: See how encoded structured features perform compared to clear feature vectors and the Q-Gram Approach. 

---

## 📁 Repository Structure

| File | Purpose |
|------|---------|
| `pre-process.ipynb` | Cleans data (removes duplicates, NaNs, illegal chars, truncates long URLs). |
| `feature_processing.ipynb` | Extracts binary and numerical features from each URL. Applies keys. |
| `bloom_encoder.ipynb` | Applies Bloom encoding for both Q-Gram and Feature-based datasets. |
| `cleartext_url.ipynb` | Model pipeline: Load → Train → Evaluate on raw URLs. |
| `encoded_url.ipynb` | Same as above, but on Q-Gram Bloom-encoded URLs. |
| `cleartext_feature.ipynb` | Model pipeline using raw structured features. |
| `encoded_feature.ipynb` | Model pipeline using Bloom-encoded feature vectors. |

---

## 🧪 Dataset Info

The dataset used in these experiments stems from a research paper from Jan. 2024 (Link: https://www.researchgate.net/publication/377343024_DEPHIDES_Deep_Learning_Based_Phishing_Detection_System).
The researchers used a huge dataset of over 5.8M samples to test different DL classifiers. They provided the huge dataset as open-source, but also created a subset of 10% (roughly 500k samples) which I used in my experiments.

The original dataset is open-source and can be downloaded here:  
🔗 (https://github.com/ebubekirbbr/dephides)

---

## 📚 Installation & Requirements

Install all dependencies via:

```bash
pip install -r requirements.txt

### Key Libraries Used

| Library | Purpose |
|--------|---------|
| `pandas`, `numpy`, `scipy` | Data processing and feature engineering |
| `matplotlib`, `seaborn` | Plotting and visualization |
| `sklearn` | Preprocessing, train/test splits |
| `tensorflow` | Deep learning models |
| `nltk`, `bitarray` | Bloom encoding (q-grams, bit manipulation) |
| Python standard libs | (`re`, `math`, `time`, `hmac`, `hashlib`, `urllib`, `ipaddress`) |

---

## 📄 Bachelor Thesis

This repository was created as part of my Bachelor thesis research.

📄 You can find the full thesis in [`/docs/thesis.pdf`](docs/thesis.pdf) *(once added)*.

If referencing, feel free to cite it:


