# Automotive Feedback using NLP
Semantic Clustering of Automotive Feedback using Sentence-BERT and HDBSCAN

---

## 📘 Overview

This is an end-to-end NLP pipeline that automatically cleans, embeds, clusters, and labels automotive customer and workshop feedback.

The goal is to group similar issue descriptions (e.g., “steering leather peeling” and “steering leather discolored”) into meaningful clusters without manual labeling, enabling faster root-cause analysis and issue tracking.

---

## ⚙️ Workflow

### Preprocessing → Embeddings → Clustering → Labeling → Output

### 1️⃣ Preprocessing

Converts text to lowercase

Removes punctuation and typos

Normalizes whitespace

### 2️⃣ Embeddings

Uses Sentence-BERT (all-MiniLM-L6-v2) to transform text into semantic vectors.

### 3️⃣ Clustering

Uses HDBSCAN to automatically detect the number of clusters.

Handles noisy data and outliers gracefully.

### 4️⃣ Cluster Labeling

Option 1: Keyword extraction with KeyBERT

Option 2: Summarization with BART-large-CNN

Option 3: Domain-specific model WG-BERT for Warranty & Goodwill text.

### 5️⃣ Output

Generates a CSV file with:
| feedback_id | cleaned_text | cluster_id | cluster_label |
| ----------- | ------------ | ---------- | ------------- |

---

## 🧠 Example Use Case

Input feedback samples:
"Steering wheel leather peeling"
"ABS sensor failed"
"Seatbelt fraying near buckle"

After processing:
| Cluster | Label                  | Example Feedback                                                |
| ------- | ---------------------- | --------------------------------------------------------------- |
| 0       | Steering Leather Issue | "Steering leather discolored", "Steering wheel leather peeling" |
| 1       | ABS Sensor Failure     | "ABS sensor malfunction", "ABS light on"                        |
| 2       | Seatbelt Wear          | "Seatbelt fraying", "Seatbelt torn"                             |

---

## 🧰 Tech Stack

Python 3.10+

Sentence-BERT (all-MiniLM-L6-v2)

HDBSCAN

KeyBERT / Hugging Face Transformers

pandas, scikit-learn, re, numpy

---

## 🚀 How to Run
### 1. Clone the Repository
  ```bash
git clone https://github.com/yourusername/AutoSense-NLP.git
cd AutoSense-NLP
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Notebook / Script
```bash
jupyter notebook text_processing.ipynb
```
 or 

```bash
 python main.py
```

---

## 📊 Scalability

This approach can easily scale with larger datasets and improved models:

Replace Sentence-BERT with mpnet-base-v2 or OpenAI embeddings

Use GPT-based summarization for better cluster labeling

Integrate into an API for automated feedback analysis

---

## 🏁 Results

✅ Automatically groups similar feedback into homogeneous clusters.

✅ Produces short, meaningful cluster labels.

✅ Works across multiple automotive domains (e.g., body, electrical, mechanical).

