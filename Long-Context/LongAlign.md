# LongAlign: A Recipe for Long Context Alignment of Large Language Models

## Authors and Affiliations
- **Yushi Bai** (Tsinghua University)
- **Xin Lv** (Zhipu.AI)
- **Jiajie Zhang** (Tsinghua University)
- **Yuze He** (Tsinghua University)
- **Ji Qi** (Tsinghua University)
- **Lei Hou** (Tsinghua University)
- **Jie Tang** (Tsinghua University)
- **Yuxiao Dong** (Tsinghua University)
- **Juanzi Li** (Tsinghua University)

## Abstract
LongAlign is a recipe designed to extend large language models (LLMs) to handle long contexts effectively through instruction fine-tuning on lengthy input sequences. The approach includes creating a long instruction-following dataset using Self-Instruct, implementing packing and sorted batching strategies to optimize training efficiency, and introducing a loss weighting method to balance contributions across sequences. Additionally, LongAlign proposes LongBench-Chat, a benchmark for evaluating instruction-following capabilities on long contexts. The method outperforms existing recipes in long context tasks while maintaining proficiency in short, generic tasks.

## Introduction
- LLMs struggle with long-context tasks, which are essential for applications requiring the processing of lengthy texts.
- Existing methods mainly focus on context extension, but there is a lack of robust datasets and evaluation methods for long context alignment.
- LongAlign aims to address these issues by providing a comprehensive recipe for constructing long instruction-following datasets, efficient training methods, and reliable evaluation benchmarks.

## Key Components of LongAlign
### Data Construction
- **Dataset**: Constructed using Self-Instruct, covering a broad range of tasks from various long context sources.
- **Sources**: Includes books, academic papers, codes, and more.
- **Diversity**: Ensures data diversity to improve model generalization.

### Training Methods
- **Packing Strategy**: Packs sequences together up to the maximum length to optimize GPU usage and minimize idle time.
- **Loss Weighting**: Balances contributions to the loss across sequences of different lengths during training.
- **Sorted Batching**: Groups sequences of similar lengths to further reduce training inefficiencies.

### Evaluation Benchmark
- **LongBench-Chat**: A benchmark for evaluating LLMs on long-context instruction-following tasks, containing real-world queries ranging from 10k to 100k in length.
- **Evaluation Metrics**: Utilizes GPT-4 to score responses, ensuring a reliable assessment of long-context capabilities.

## Experiments and Results
- **Performance**: LongAlign shows up to 30% improvement over existing methods in handling long-context tasks.
- **Training Efficiency**: Packing and sorted batching strategies accelerate training by over 100% without compromising performance.
- **Data Influence**: The quantity and diversity of long instruction data significantly impact model performance, with more data leading to better long-context handling.

## Challenges and Future Directions
- **Scalability**: Future work should explore scalability to even larger models and longer context windows.
- **Evaluation**: Further studies are needed to validate the effectiveness of evaluation metrics and methods for long-context tasks.

## Conclusion
LongAlign provides a robust framework for aligning LLMs to handle long contexts through diverse data construction, efficient training methods, and comprehensive evaluation benchmarks. It significantly enhances the performance of LLMs in long-context tasks while maintaining their general capabilities.

## Repository
Code, data, and long-aligned models are available at [GitHub - LongAlign](https://github.com/THUDM/LongAlign).