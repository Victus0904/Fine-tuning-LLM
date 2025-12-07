# Fine-tuning-LLM
This repository contains code and experiments for fine-tuning a Large Language Model (LLM) using the **Cynaptics dataset**.  
The training was implemented in Python using [Hugging Face Transformers](https://huggingface.co/transformers/) and PyTorch.
Perplexity = 3.31

---

## 📌 Project Overview
- Fine-tuned a pretrained LLM for domain-specific tasks.
- Implemented with Hugging Face `Trainer` API.
- Supports saving, reloading, and pushing models to the Hugging Face Hub.

---

## 🚀 Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/victus0904/Fine-tuning-LLM.git
cd Fine-tuning-LLM
```
### 2. Install dependencies
```
pip install -r requirements.txt
```
### 3. Run training
```
jupyter notebook Finetune_Cynaptics.ipynb
```
