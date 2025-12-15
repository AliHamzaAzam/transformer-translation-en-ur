# English-to-Urdu Machine Translation

A Transformer-based machine translation model for English-to-Urdu translation, implementing the architecture from "Attention is All You Need" (Vaswani et al., 2017).

## Features

- Custom Transformer encoder-decoder architecture built from scratch
- Training on ~28K parallel English-Urdu sentence pairs
- BLEU and METEOR score evaluation
- Noam learning rate scheduler with warmup
- Gradient clipping and early stopping
- Checkpoint saving and model persistence

## Project Structure

```
transformer_translation/
├── transformer_translation.ipynb           # Main notebook (from-scratch implementation)
├── transformer_translation_optimized.ipynb # Fine-tuning with pre-trained model
├── requirements.txt                        # Dependencies for main notebook
├── requirements_optimized.txt              # Dependencies for optimized notebook
├── report.md                               # BLEU implementation notes
├── data/                                   # Parallel corpus data
│   ├── english-corpus.txt
│   └── urdu-corpus.txt
├── checkpoints/                            # Saved model checkpoints
├── checkpoints_optimized/                  # Checkpoints for optimized model
└── results/                                # Evaluation results and plots
    ├── evaluation_results.json
    ├── training_history.json
    ├── training_loss.png
    └── training_analysis.png
```

## Installation

```bash
# For the from-scratch implementation
pip install -r requirements.txt

# For the optimized fine-tuning approach
pip install -r requirements_optimized.txt
```

## Dataset

Download the following parallel corpus datasets:

- [Parallel Corpus for English-Urdu (Kaggle)](https://www.kaggle.com/datasets/zainuddin123/parallel-corpus-for-english-urdu-language)

Place the data files in the `data/` directory.

## Usage

### From-Scratch Implementation

Open `transformer_translation.ipynb` and run cells sequentially. The notebook includes:

1. Data preprocessing and vocabulary building
2. Custom Transformer model implementation
3. Training loop with progress tracking
4. BLEU/METEOR evaluation
5. Sample translation inference

### Optimized Fine-Tuning

Open `transformer_translation_optimized.ipynb` for a faster approach using pre-trained models:

- Fine-tunes `Helsinki-NLP/opus-mt-en-ur` model
- Uses Hugging Face Transformers and Datasets
- Implements gradient checkpointing for memory efficiency

## Model Architecture

| Parameter | Value |
|-----------|-------|
| Architecture | Transformer (Encoder-Decoder) |
| Encoder/Decoder Layers | 4 |
| Attention Heads | 8 |
| d_model | 512 |
| Feedforward Dimension | 2048 |
| Dropout | 0.3 |
| Vocabulary Size | 10,000 (each language) |

## Training Configuration

| Parameter | Value |
|-----------|-------|
| Batch Size | 16 |
| Gradient Accumulation | 4 steps |
| Learning Rate | 5e-6 |
| Warmup Steps | 1,000 |
| Max Epochs | 100 |
| Early Stopping Patience | 3 epochs |

## Results

Evaluated on 2,821 test sentence pairs:

| Metric | Score |
|--------|-------|
| BLEU-1 | 0.592 |
| BLEU-2 | 0.477 |
| BLEU-3 | 0.395 |
| BLEU-4 | 0.329 |
| Corpus BLEU-4 | 0.342 |
| METEOR | 0.558 |

## License

This project is licensed under the [MIT License](LICENSE).
