# Fine-tuning Gemma 3 (270M)

Supervised fine-tuning of Google's **`gemma-3-270m`** causal language model on the **Cynaptics** dataset,
using Hugging Face Transformers and PyTorch.

**Validation perplexity: 3.31**

## Contents

| File | Purpose |
|---|---|
| `Finetune_Cynaptics.ipynb` | Data loading, tokenization, training with the HF `Trainer`, saving checkpoints |
| `Eval.ipynb` | Evaluation and perplexity measurement |
| `requirements.txt` | Dependencies |

## Getting started

```bash
git clone https://github.com/Victus0904/Fine-tuning-LLM.git
cd Fine-tuning-LLM
pip install -r requirements.txt
jupyter notebook Finetune_Cynaptics.ipynb
```

A GPU (e.g. Colab T4) is recommended.
