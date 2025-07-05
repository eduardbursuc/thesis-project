# 🛡️ Phishing URL Detection with Bloom Encoding

This repository contains all Jupyter notebooks used for experiments in my Bachelor thesis.

The project combines **deep learning** with **privacy-preserving techniques** to create an efficient phishing URL detection system. It specifically focuses on **Bloom encoding** — a novel method in this context — to anonymize sensitive URL data. The core goal is to **compare the detection performance between clear-text and encoded inputs** using deep learning models (CNN in this case).

---

## 🧠 Motivation

Phishing detection often requires analyzing sensitive web data. This project explores whether **privacy-enhancing encodings** — specifically Bloom filters — can preserve enough semantic value to support **deep learning-based classification**, without exposing original URLs.

This approach may offer practical applications in privacy-sensitive environments like healthcare, finance, and cybersecurity, where data masking is essential.

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
- Convert features into a keyed format (e.g., `URL_Length: u80`, `has_ip: i1`) to avoid value collisions.
- Apply Bloom encoding on these keyed feature values.
- Feed resulting bit arrays into a deep learning model.

**Goal**: See how encoded structured features perform compared to clear-text feature vectors.

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

- The dataset used in these experiments originally stems from this research paper: https://www.researchgate.net/publication/377343024_DEPHIDES_Deep_Learning_Based_Phishing_Detection_System
- The researchers created and evaluated a large dataset of roughly 5.2M samples to test different DL Models for phishing detection. As part of their project, they also provided both the large dataset but also a subset containing 10% (about 520k) of the samples as open source. I used this subset in my experiments.

- The original dataset is open-source and can be downloaded here:  
🔗 https://github.com/ebubekirbbr/dephides

---

## 📚 Installation & Requirements

Install all dependencies via:

```bash
pip install -r requirements.txt
```

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

📄 You can find the full thesis in [`/files/Bachelor_Thesis_Eduard_Bursuc-Pahome_FinalVersion.pdf`].

If referencing, feel free to cite it:

```
Eduard Bursuc-Pahome, *An Evaluation of Similarity-Preserving Bloom Encodings in URL-based Phishing Detection*, RWTH Aachen, 2024.
```

---

## 📌 Notes

- Bloom filters allow for lightweight, privacy-friendly encoding at the cost of some collisions.
- Input size `l` should ideally be large enough to balance 1s and 0s in the filter.
- Most experiments used power-of-two values for consistency (`128`, `256`, `512`, etc.).
- Feature keying (e.g., `has_ip: i1`) prevents collisions of semantically unrelated binary values.
- Q-gram size and hash count `k` are both tunable parameters and can affect performance.

---

## 📬 Contact

Feel free to reach out for questions or collaboration:

📧 eduard.bursuc2001@gmail.com  
🔗 [LinkedIn]([#](https://www.linkedin.com/in/eduard-bursuc-pahome-620682350/)) • [GitHub]([#](https://github.com/eduardbursuc))

---

## 📎 License

This project is made available for academic and non-commercial use.  
Please give proper credit if you use or adapt this work.

---
