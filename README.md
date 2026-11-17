# Fine-tuning Gemma 3 (270M) for Persona-Grounded Dialogue

![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![Hugging Face](https://img.shields.io/badge/%F0%9F%A4%97-Transformers-yellow)
![PyTorch](https://img.shields.io/badge/PyTorch-2.x-EE4C2C)
[![License: MIT](https://img.shields.io/badge/license-MIT-green)](LICENSE)

Supervised fine-tuning of Google's **`gemma-3-270m`** causal language model on the
[**Cynaptics/persona-chat**](https://huggingface.co/datasets/Cynaptics/persona-chat)
dataset with the Hugging Face `Trainer`, so the model learns to continue conversations
in the voice of a given persona.

<table>
<tr><td><b>Validation perplexity</b></td><td><b>3.31</b></td></tr>
<tr><td>Base model</td><td><code>google/gemma-3-270m</code> (270M parameters)</td></tr>
<tr><td>Hardware</td><td>Single Colab/Kaggle T4 GPU</td></tr>
</table>

## Method

| Step | Details |
|---|---|
| **Data** | Each example's persona sentences and dialogue turns are joined into one sequence: `persona: … dialogue: …` |
| **Tokenisation** | Gemma tokenizer, truncated to 512 tokens |
| **Objective** | Causal LM (next-token prediction) via `DataCollatorForLanguageModeling(mlm=False)` |
| **Training** | 1 epoch, lr 2e-5, batch size 2 × 2 gradient-accumulation steps |
| **Evaluation** | Perplexity = exp(mean token-level cross-entropy) on held-out conversations (`Eval.ipynb`) |

## Contents

| File | Purpose |
|---|---|
| `Finetune_Cynaptics.ipynb` | Data loading, preprocessing, tokenization, training, saving the model |
| `Eval.ipynb` | Perplexity evaluation of the fine-tuned model |
| `requirements.txt` | Dependencies |

## Getting started

Gemma is a gated model, so first accept its licence on the
[model page](https://huggingface.co/google/gemma-3-270m) and create an access token.

```bash
git clone https://github.com/Victus0904/Fine-tuning-LLM.git
cd Fine-tuning-LLM
pip install -r requirements.txt

export HF_TOKEN=hf_...            # Windows PowerShell: $env:HF_TOKEN="hf_..."
jupyter notebook Finetune_Cynaptics.ipynb
```

A GPU is recommended (a free Colab or Kaggle T4 is enough). The fine-tuned weights are
written to `./my_finetuned_model`, and `Eval.ipynb` reads them from there.

## License

Code: [MIT](LICENSE). The Gemma weights are covered by the
[Gemma Terms of Use](https://ai.google.dev/gemma/terms).
