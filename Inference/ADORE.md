### Efficient Sparse Attention needs Adaptive Token Release (ADORE)

## Authors and Affiliations
- **Chaoran Zhang**, **Lixin Zou**, **Zihao Li**, **Chenliang Li** (Wuhan University)
- **Dan Luo** (Lehigh University)
- **Min Tang** (Monash University)
- **Xiangyang Luo** (State Key Lab of Mathematical Engineering and Advanced Computing, China)

在数据集上训练了 1000 个 samples，可能这是带来效果提升的原因。不公平对比。

## Abstract
ADORE is a method to manage KV cache in large language models (LLMs) by adaptively releasing and rebuilding tokens with the highest top-K attention weights. This lightweight controller module enhances throughput by up to 221.8% compared to full attention, maintaining nearly identical performance in text quality.

## Introduction
- **Context**: LLMs are computationally intensive due to the management of key-value (KV) states, limiting their throughput.
- **Solution**: ADORE releases resources from caches and rebuilds necessary KV states, retaining tokens with the highest attention weights and rebuilding discarded but necessary tokens for future decoding.

## Methodology
### Efficient Sparse Transformer
- **Attention Calculation**: Uses scaled dot-product attention to determine key-value states.
- **Sparse Attention**: Selects top-K attention weights to approximate full attention.

### Adaptive Token Release
- **Controller Module**: Utilizes a GRU to predict the importance of tokens and manages the KV cache by retaining top-K tokens.

### KV States Rebuild
- **Rebuilding Mechanism**: Retrieves and rebuilds the top-R tokens with the highest importance, ensuring essential tokens are not lost.

### Matrix Slicing
- **Efficient Implementation**: Uses pre-prepared slicing matrices for rapid KV state management, reducing computational overhead.

## Experiments
### Datasets
- **Evaluation Tasks**: Natural language generation, stream generation, and natural language modeling on datasets like UltraChat, EverythingLM, Math, StreamEval, CNN Dailymail, and SAMSum.

### Performance Metrics
- **Results**: ADORE achieves the highest performance across all tasks, with significant improvements in BLEU, ROUGE, and BERT-F scores compared to baselines like full attention, window attention, and H2O.

### Ablation Studies
- **Influence of Attention Sparsity**: Demonstrates the importance of top-K values for model performance.
- **KV States Rebuild**: Shows the trade-off between performance and throughput when rebuilding different numbers of tokens.
- **Effectiveness of Controller Module**: Highlights the GRU's role in maintaining high accuracy and performance.

## Conclusion
ADORE efficiently manages KV states in LLMs, significantly enhancing throughput without compromising text quality. The method dynamically adjusts KV cache, ensuring optimal performance in long-context scenarios.

## Repository
For more information and access to the code, visit the [GitHub repository](https://github.com/WHUIR/ADORE).