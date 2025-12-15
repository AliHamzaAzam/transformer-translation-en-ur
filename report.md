# Report: English-to-Urdu Machine Translation

## BLEU Score Implementation Choices

In this project, two different methods were used to calculate the BLEU score, each aligning with the specific goals of the two notebooks.

### `transformer_translation.ipynb`: The "From-Scratch" Approach

In the first notebook, the BLEU score was calculated using the `nltk.translate.bleu_score` library. This choice was deliberate and consistent with the notebook's overall philosophy of building the translation pipeline from the ground up.

*   **Educational Value**: Using `nltk` provides a more hands-on, foundational understanding of how BLEU scores are computed. It requires manual tokenization and careful formatting of the hypothesis and reference sentences, which is a valuable learning experience.
*   **Consistency**: Since the Transformer model in this notebook was built from scratch, using a more fundamental library like `nltk` for evaluation maintains a consistent, low-level approach throughout the entire pipeline.

### `transformer_translation_optimized.ipynb`: The "Optimized" Approach

In the second notebook, the `evaluate.load("sacrebleu")` library from Hugging Face was used. This is the current industry standard for evaluating machine translation models.

*   **Standardization and Reproducibility**: `sacrebleu` provides a standardized implementation of the BLEU score with its own built-in tokenization. This ensures that the results are consistent and directly comparable to those reported in other research papers and projects.
*   **Efficiency**: As part of the high-level Hugging Face ecosystem, `sacrebleu` integrates seamlessly with the pre-trained models and tokenizers used in the optimized notebook, making the evaluation process more streamlined and efficient.

By using both methods, this project not only demonstrates how to build and evaluate a translation model but also highlights the trade-offs between a foundational, educational approach and a high-level, optimized framework.
