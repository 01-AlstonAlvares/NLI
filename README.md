# 🧠 Sentence-BERT (SBERT) for Natural Language Inference

A from-scratch **BERT model** fine-tuned using a **Siamese Sentence-BERT architecture** for **Natural Language Inference (NLI)** with real-time web prediction.

---

## ✨ Project Overview

This repository presents a full pipeline implementation of:

* 🔧 Building BERT from scratch
* 🔁 Converting it into a Siamese SBERT architecture
* 📊 Training on large-scale datasets using streaming
* 🌐 Deploying a Flask web app for live inference

The system predicts the semantic relationship between two sentences:

| Relationship      | Meaning                                   |
| ----------------- | ----------------------------------------- |
| **Entailment**    | Hypothesis logically follows from premise |
| **Neutral**       | No clear relationship                     |
| **Contradiction** | Hypothesis contradicts premise            |

---

## 🏗️ Architecture Highlights

### 🔹 BERT from Scratch

Implemented a full multi-layered Transformer Encoder including:

* Multi-Head Self Attention
* Scaled Dot-Product Attention
* Positional Encoding
* Feed-Forward Networks
* Layer Normalization & Residual Connections

### 🔹 Siamese SBERT Structure

Two identical BERT encoders share weights:

```
Premise ──► BERT ──► Sentence Embedding (u)
Hypothesis ─► BERT ─► Sentence Embedding (v)
                      │
                      ▼
                Classification Layer
```

This enables efficient sentence similarity and NLI prediction.

---

## 🎯 Training Objective

Model is fine-tuned using a **Softmax classification loss** to predict:

```
Entailment | Neutral | Contradiction
```

---

## 📚 Dataset Credits & Sources

To maintain computational feasibility, **100,000 samples** from each dataset were used.

| Dataset                                       | Purpose                  | Source                                                                                 |
| --------------------------------------------- | ------------------------ | -------------------------------------------------------------------------------------- |
| 📖 Wikipedia (20220301.en)                    | BERT Pre-training subset | [https://huggingface.co/datasets/wikipedia](https://huggingface.co/datasets/wikipedia) |
| 🧪 SNLI (Stanford Natural Language Inference) | Siamese Fine-tuning      | [https://nlp.stanford.edu/projects/snli/](https://nlp.stanford.edu/projects/snli/)     |

### ⚡ Streaming Data Processing

Wikipedia dataset (>20GB) is processed using **HuggingFace Streaming Mode**, allowing on-the-fly loading without large disk usage.

---

## 📊 Performance Report

Evaluation on **1,000 SNLI validation samples** after **5 training epochs**:

| Class            | Precision | Recall | F1-Score | Support |
| ---------------- | --------- | ------ | -------- | ------- |
| Entailment       | 0.76      | 0.76   | 0.76     | 331     |
| Neutral          | 0.66      | 0.70   | 0.68     | 333     |
| Contradiction    | 0.75      | 0.71   | 0.73     | 336     |
| **Accuracy**     |           |        | **0.72** | 1000    |
| **Macro Avg**    | 0.73      | 0.72   | 0.72     | 1000    |
| **Weighted Avg** | 0.73      | 0.72   | 0.72     | 1000    |

🏆 **Overall Accuracy: 72%**

---

## 🌐 Web Application

A simple **Flask interface** allows real-time NLI predictions.

### 💡 Features

* Enter Premise and Hypothesis
* Get instant classification result
* Lightweight & local deployment

---

## ⚙️ How to Run Locally

### 1️⃣ Install Dependencies

```
pip install torch transformers datasets flask scikit-learn tqdm
```

### 2️⃣ Launch Application

```
python main.py
```

### 3️⃣ Open Web Interface

Visit 👉 [http://127.0.0.1:5000](http://127.0.0.1:5000)

---

## 🚀 Key Achievements

✔️ Implemented BERT without prebuilt libraries
✔️ Built SBERT Siamese architecture
✔️ Used streaming for large-scale data handling
✔️ Achieved 72% accuracy on SNLI validation
✔️ Deployed an interactive inference web app

---

## ⚠️ Problems / Limitations Faced

The most significant challenge was managing the **computational and storage overhead** required for a deep BERT architecture.

* Full Wikipedia + SNLI datasets exceed **20GB**, requiring a shift to **streaming mode**.
* Scaling to deeper layers increased **training time and VRAM usage**.
* Batch sizes had to be tuned carefully to avoid **GPU Out-of-Memory errors**.
* Dataset noise and conflicting labels in validation caused errors during performance reporting and required cleaning.

---

## 🖥️ Web App Screenshots

![Web App Screenshot](https://github.com/user-attachments/assets/a96b1510-424d-403c-bb85-a42d09402b02)

![Web App Screenshot](https://github.com/user-attachments/assets/0931d4b0-7745-46ea-ad1f-5c0e2bda7ff8)

---

## 👨‍💻

**Alston Alvares (st126488)**
