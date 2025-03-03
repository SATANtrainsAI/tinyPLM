# tinyPLM

A tiny Protein Language Model (PLM) trained from scratch.  
We demonstrate how to load protein sequences from a FASTA file, tokenize them, train a GPT-style model using PyTorch, and generate new protein sequences.  

---
## Project Overview

- **Tokenizer**: Converts protein sequences into numerical tokens using a predefined vocabulary (`token_dict`).
- **Dataset**: An `IterableDataset` (`ProteinIterableDataset`) that streams sequences from a (large) FASTA file, suitable for memory-efficient training.
- **Model**: A GPT-style transformer (`GPT` class) with:
  - Absolute Positional embeddings
  - Multiple transformer blocks
  - Optional Latent attention for parameter effeciency (lora_dim)
- **Training**: 
  - Implements distributed training with PyTorch’s `DistributedDataParallel` (DDP)
  - Applies automatic mixed precision (AMP) for faster training in float16/bfloat16 modes (configurable)
- **Generation**: Demonstrates how to generate new protein sequences with specific constraints (temperature, top-k, n-gram blocking, repetition penalty). Also Blasting the generated protein and predicting the structre using ESMFold and visualizing it using PyMol
- **Pre-Trained Model**: You can download the pretrained nano model (202 M parameters) in the following link: https://drive.google.com/file/d/1-NBpPG3J1KIMMqCU-L_Y3ItRdo4mUqsG/view?usp=sharing
- **Play!**: You can use the following colab notebook to play with the model to generate and blast your own sequences, predict and visiualize the structure: https://colab.research.google.com/drive/1N2drnUl5M5w35k4GW368XqPIG6BvGpmT?usp=sharing 
---

## Requirements

- Python 3.8+
- [PyTorch](https://pytorch.org/) (with CUDA if you want GPU acceleration)
- (Optional) Additional libraries for distributed training (e.g., `nccl` backend)

---
