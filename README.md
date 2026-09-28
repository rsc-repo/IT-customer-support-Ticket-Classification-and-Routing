# IT-customer-support-Ticket-Classification-and-Routing
Multi-class classification of incoming tickets into topics

# 🏛️ Smart Civic Issue Classifier & Routing Engine

An end-to-end NLP-based automated ticket classification and routing system for municipal and smart city administration. This application leverages a fine-tuned **DistilBERT** transformer model to classify citizen complaints into relevant municipal departments, predict priority levels, and display real-time predictions via an interactive **Gradio** web interface.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/YOUR_REPO_NAME/blob/main/notebooks/Smart_Civic_Classifier.ipynb)
[![Hugging Face Spaces](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Spaces-blue)](https://huggingface.co/spaces)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 📌 Project Overview
Cities receive thousands of non-emergency reports daily through portals like 311. Manually reading, categorizing, and routing these citizen tickets slows down resolution times and increases municipal overhead.

This project solves the problem by automating:
1. **Department Categorization:** Classifying issues into *Roads & Potholes*, *Garbage & Sanitation*, *Street Lighting*, *Water & Drainage*, or *Public Transport & Traffic*.
2. **Dynamic Priority Assignment:** Flagging emergency/urgent tickets using custom SLA heuristics (e.g., pipeline bursts, traffic signal failures).
3. **Interactive Support Dashboard:** Allowing city admins to test complaints live with confidence score breakdowns.

---

## 🏗️ System Architecture
[ Raw Citizen Complaint ]
│
▼
[ Preprocessing & Tokenization ]  (Regex PII Removal + DistilBertTokenizer)
│
▼
[ Fine-Tuned DistilBERT Model ]  (Multi-class Sequence Classification)
│
▼
[ Priority & Routing Engine ]   (Rules + Confidence Score Thresholding)
│
▼
[ Gradio UI / Admin Dashboard ] (Live Inference & Confidence Score Display)

---

## 📊 Dataset & Categories

The model is trained on municipal service request data mapped to 5 core civic categories:
* 🛣️ **Roads & Potholes** (Cave-ins, resurfacing, sidewalk damage)
* 🧹 **Garbage & Sanitation** (Overflowing dumpsters, uncollected waste)
* 💡 **Street Lighting** (Flickering lights, dark zones, broken bulbs)
* 💧 **Water Supply & Drainage** (Pipe bursts, sewage blockages, water cuts)
* 🚦 **Public Transport & Traffic** (Damaged bus stops, traffic light failures)

---

## 🛠️ Tech Stack & Libraries
* **Language:** Python 3.10+
* **Deep Learning Framework:** PyTorch
* **Transformers & NLP:** Hugging Face `transformers`, `datasets`, `accelerate`, `scikit-learn`
* **Model Architecture:** `distilbert-base-uncased`
* **User Interface:** Gradio

---

## 🚀 Quickstart (Run in Google Colab)

1. Click the **Open in Colab** badge at the top of this README.
2. Ensure GPU acceleration is active (**Runtime** ➔ **Change runtime type** ➔ **T4 GPU**).
3. Run all notebook cells sequentially.
4. Access the generated public Gradio URL to interact with the web interface.

---

## 📈 Evaluation & Results
* **Base Architecture:** `distilbert-base-uncased`
* **Training Epochs:** 2
* **Optimization:** AdamW with linear warmup, mixed precision (`fp16`) enabled on T4 GPU
* **Primary Metrics:** Accuracy, Macro Precision, Macro Recall, and Macro F1-Score

---

## 📄 License
Distributed under the MIT License. See `LICENSE` for more information.
