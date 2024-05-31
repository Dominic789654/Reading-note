# LongBench: A Bilingual, Multitask Benchmark for Long Context Understanding

## Authors and Affiliations
- **Yushi Bai** (Tsinghua University)
- **Xin Lv** (Tsinghua University)
- **Jiajie Zhang** (Tsinghua University)
- **Hongchang Lyu** (Institute of Automation, Chinese Academy of Sciences)
- **Jiankai Tang** (Tsinghua University)
- **Zhidian Huang** (Tsinghua University)
- **Zhengxiao Du** (Tsinghua University)
- **Xiao Liu** (Tsinghua University)
- **Aohan Zeng** (Tsinghua University)
- **Lei Hou** (Tsinghua University)
- **Yuxiao Dong** (Tsinghua University)
- **Jie Tang** (Tsinghua University)
- **Juanzi Li** (Tsinghua University)

## Abstract
LongBench is the first bilingual, multitask benchmark designed for evaluating long-context understanding in large language models (LLMs). It comprises 21 datasets across 6 task categories in both English and Chinese. The benchmark addresses the need for models to handle texts extending thousands of tokens in length, with an average length of 6,711 words in English and 13,386 characters in Chinese. It includes tasks such as single-doc QA, multi-doc QA, summarization, few-shot learning, synthetic tasks, and code completion. LongBench provides a unified format for automatic evaluation and highlights the necessity for improved long-context capabilities in LLMs.

## Introduction
- LLMs have shown remarkable performance in NLP but are limited in handling long-context texts, essential for applications like books, reports, and codebases.
- Methods have been proposed to enhance long-context capabilities, but comprehensive benchmarks are lacking.
- LongBench addresses this gap by providing a rigorous evaluation framework for long-context understanding, incorporating 21 datasets across 6 task categories in both English and Chinese.

## Task Categories and Datasets
1. **Single-Document QA**
   - Includes datasets like NarrativeQA, Qasper, MultiFieldQA-en, and MultiFieldQA-zh.
   - Focuses on answering questions based on long documents from various fields.

2. **Multi-Document QA**
   - Features datasets such as HotpotQA, 2WikiMultihopQA, MuSiQue, and DuReader.
   - Requires models to extract and combine information from multiple documents.

3. **Summarization**
   - Utilizes datasets like GovReport, QMSum, MultiNews, and VCSUM.
   - Demands models to generate concise summaries from lengthy texts.

4. **Few-Shot Learning**
   - Includes TREC, TriviaQA, SAMSum, and LSHT.
   - Tests the models' ability to learn from a few examples provided within a long context.

5. **Synthetic Tasks**
   - Features PassageCount, PassageRetrieval-en, and PassageRetrieval-zh.
   - Designed to test specific scenarios and patterns in long-context understanding.

6. **Code Completion**
   - Includes LCC and RepoBench-P datasets.
   - Evaluates models' ability to complete code snippets based on preceding lines and cross-file information.

## Evaluation and Results
- Comprehensive evaluation of 8 models on LongBench, revealing insights into their long-context capabilities.
- Key findings include:
  1. Commercial models like GPT-3.5-Turbo-16k outperform open-source models but still face challenges with long contexts.
  2. Scaled positional embedding and fine-tuning on longer sequences significantly improve performance.
  3. Context compression techniques, such as retrieval, benefit models with weaker long-context abilities but lag behind stronger models.

## Challenges and Future Directions
- Identifies the need for enhanced evaluation metrics and methodologies for long-context tasks.
- Suggests future research directions, including better context compression techniques, improved memory mechanisms, and more robust benchmarks.

## Conclusion
- LongBench provides a comprehensive and rigorous framework for evaluating long-context understanding in LLMs.
- It enables a better understanding of the current models' capabilities and highlights areas for future improvement.

## Repository
A curated repository of relevant literature is available and continuously updated at [GitHub - long-llms-learning](https://github.com/Strivin0311/long-llms-learning).