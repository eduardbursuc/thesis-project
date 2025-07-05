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

**Goal**: Evaluate if encoding URLs this way retains enough signal for accurate classification.

---

### 🧩 Feature-Based Bloom Encoding

- Extract structured features from URLs (e.g., length, presence of IP, HTTPS).
- Key each feature to avoid collisions (e.g., `URL_Length: u80`, `has_ip: i1`).
- Apply Bloom encoding on these keyed feature values.
- Feed resulting bit arrays into a deep learning model.

**Goal**: See how encoded structured features perform compared to clear feature vectors.

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

Only **3 base CSV files** are included in this repository for clarity and size.  
These are enough to reproduce all experiments and generate the full datasets via preprocessing notebooks.

The original dataset is open-source and can be downloaded here:  
🔗 [**Insert dataset link here**]

---

## 📚 Installation & Requirements

Install all dependencies via:

```bash
pip install -r requirements.txt
