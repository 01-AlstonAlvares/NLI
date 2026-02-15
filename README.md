🧠 Sentence-BERT (SBERT) for Natural Language Inference

A from-scratch BERT model fine-tuned using a Siamese Sentence-BERT architecture for Natural Language Inference (NLI) with real-time web prediction.

✨ Project Overview

This repository presents a full pipeline implementation of:

🔧 Building BERT from scratch

🔁 Converting it into a Siamese SBERT architecture

📊 Training on large-scale datasets using streaming

🌐 Deploying a Flask web app for live inference

The system predicts the semantic relationship between two sentences:

Relationship	Meaning
Entailment	Hypothesis logically follows from premise
Neutral	No clear relationship
Contradiction	Hypothesis contradicts premise
🏗️ Architecture Highlights
🔹 BERT from Scratch

Implemented a full multi-layered Transformer Encoder including:

Multi-Head Self Attention

Scaled Dot-Product Attention

Positional Encoding

Feed-Forward Networks

Layer Normalization & Residual Connections

🔹 Siamese SBERT Structure

Two identical BERT encoders share weights:

Premise ──► BERT ──► Sentence Embedding (u)
Hypothesis ─► BERT ─► Sentence Embedding (v)
                      │
                      ▼
                Classification Layer


This enables efficient sentence similarity and NLI prediction.

🎯 Training Objective

Model is fine-tuned using a Softmax classification loss to predict:

Entailment | Neutral | Contradiction

📚 Dataset Credits & Sources

To maintain computational feasibility, 100,000 samples from each dataset were used.

Dataset	Purpose	Source
📖 Wikipedia (20220301.en)	BERT Pre-training subset	https://huggingface.co/datasets/wikipedia

🧪 SNLI (Stanford Natural Language Inference)	Siamese Fine-tuning	https://nlp.stanford.edu/projects/snli/
⚡ Streaming Data Processing

Wikipedia dataset (>20GB) is processed using HuggingFace Streaming Mode, allowing on-the-fly loading without large disk usage.

📊 Task 3 — Performance Report

Evaluation on 1,000 SNLI validation samples after 5 training epochs:

Class	Precision	Recall	F1-Score	Support
Entailment	0.76	0.76	0.76	331
Neutral	0.66	0.70	0.68	333
Contradiction	0.75	0.71	0.73	336
🏆 Overall Accuracy: 72%
🌐 Task 4 — Web Application

A simple Flask interface allows real-time NLI predictions.

💡 Features

Enter Premise and Hypothesis

Get instant classification result

Lightweight & local deployment

⚙️ How to Run Locally
1️⃣ Install Dependencies
pip install torch transformers datasets flask scikit-learn tqdm

2️⃣ Launch Application
python main.py

3️⃣ Open Web Interface

Visit 👉 http://127.0.0.1:5000

🚀 Key Achievements

✔️ Implemented BERT without prebuilt libraries

✔️ Built SBERT Siamese architecture

✔️ Used streaming for large-scale data handling

✔️ Achieved 72% accuracy on SNLI validation

✔️ Deployed an interactive inference web app

💡 Problem/ Limitations faced 

Throughout this project, the most significant challenge was managing the computational and storage overhead required for a 12-layer BERT architecture. We initially faced critical bottlenecks with disk space, as the full Wikipedia and SNLI archives exceed 20GB, necessitating a transition to streaming mode to handle data on-the-fly. Additionally, scaling the model to 12 layers significantly slowed training speeds and increased VRAM consumption, which required careful optimization of batch sizes to prevent "Out of Memory" errors on the GPU. Finally, resolving dataset noise in the validation set, specifically the presence of conflicting labels that caused value errors during performance reporting, proved to be a vital hurdle in achieving a clean classification report.

Web App

<img width="967" height="922" alt="Screenshot 2026-02-15 153203" src="https://github.com/user-attachments/assets/a96b1510-424d-403c-bb85-a42d09402b02" />
<img width="976" height="917" alt="Screenshot 2026-02-15 153210" src="https://github.com/user-attachments/assets/0931d4b0-7745-46ea-ad1f-5c0e2bda7ff8" />



👨‍💻 Author

Alston Alvares
