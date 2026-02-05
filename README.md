# 🩺 Surgical-Llama-1B: Python Coding Specialist

[![Model on HF](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Model-blue)](https://huggingface.co/NEldin10/llama-3.2-1B-ft-v0.1-qlora-merged)
[![License: Llama 3.2](https://img.shields.io/badge/License-Llama%203.2-lightgrey)](https://ai.meta.com/llama/license/)

A fine-tuned **Llama 3.2 1B** model surgically optimized for high-accuracy Python code generation. This project demonstrates how a small (1B) model can achieve a **66.7% Pass@1** score on core algorithmic tasks through targeted SFT (Supervised Fine-Tuning).

## 🚀 The Result (Benchmark)

I benchmarked the model against the base Llama 3.2 1B across 6 surgical coding tasks. 

| Problem Category | Base Llama 1B | Surgical Llama (Fine-Tuned) | Status |
| :--- | :---: | :---: | :--- |
| **Math (GCD)** | 0% | 100% | ✅ PASS |
| **Logic (Palindrome)** | 0% | 100% | ✅ PASS |
| **Strings (Anagram)** | 0% | 100% | ✅ PASS |
| **Algorithms (Fibonacci)** | 0% | 100% | ✅ PASS |
| **Data (Flatten List)** | 0% | 0% | ❌ Recursion Limit |
| **System (Multiprocessing)** | 0% | 0% | ❌ Import Error |
| **TOTAL PASS@1** | **0.0%** | **66.7%** | **+66.7% Jump** |

## 🧠 Training Details
- **Base Model**: `meta-llama/Llama-3.2-1B`
- **Dataset**: `Vezora/Tested-22k-Python-Alpaca` (Filtered to 15k high-quality samples)
- **Method**: QLoRA (4-bit quantization)
- **Hardware**: Trained on [Insert your GPU, e.g., NVIDIA T4]
- **Epochs**: ~0.66 (500 Steps)

## 💻 How to Use

Since this is a **merged model**, you can use it just like a standard Llama model without needing the `peft` library.

```python
from transformers import AutoModelForCausalLM, AutoTokenizer

model_id = "NEldin10/llama-3.2-1B-ft-v0.1-qlora-merged"
tokenizer = AutoTokenizer.from_pretrained(model_id)
model = AutoModelForCausalLM.from_pretrained(model_id, device_map="auto")

prompt = "Write a Python function to check if a number is prime."
# Note: Use the Llama 3 Prompt Format for best results
