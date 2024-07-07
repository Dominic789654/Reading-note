### H2O: Heavy-Hitter Oracle for Efficient Generative Inference of Large Language Models

## Authors and Affiliations
- **Zhenyu Zhang** (University of Texas at Austin)
- **Ying Sheng** (Stanford University)
- **Tianyi Zhou** (University of California, San Diego)
- **Tianlong Chen** (University of Texas at Austin)
- **Lianmin Zheng** (University of California, Berkeley)
- **Ruisi Cai** (University of Texas at Austin)
- **Zhao Song** (Adobe Research)
- **Yuandong Tian** (Meta AI)
- **Christopher Ré** (Stanford University)
- **Clark Barrett** (Stanford University)
- **Zhangyang Wang** (University of Texas at Austin)
- **Beidi Chen** (Carnegie Mellon University)

## Abstract
H2O (Heavy-Hitter Oracle) is a KV cache eviction policy for large language models (LLMs) that dynamically balances recent and heavy-hitter (H2) tokens. H2O significantly reduces KV cache memory while maintaining model performance. The approach is based on the observation that a small portion of tokens contributes most to attention scores. H2O demonstrates up to 29× throughput improvement over leading inference systems like DeepSpeed Zero-Inference, Hugging Face Accelerate, and FlexGen, with up to 1.9× lower latency.

## Introduction
- **Context and Motivation**: Deploying LLMs for long-content generation is cost-prohibitive due to the KV cache size, which scales linearly with sequence length and batch size.
- **Heavy-Hitters (H2)**: A small set of tokens significantly impacts attention scores. Removing these tokens results in performance degradation.
- **H2O**: A KV cache eviction policy that retains H2 and recent tokens, formulated as a dynamic submodular problem, providing theoretical guarantees for efficiency.
![H2O Overview](../figs/h2o_1.png)

## Methodology
### Observations
1. **Sparsity**: Attention matrices are over 95% sparse during inference, suggesting potential for reducing KV cache size without accuracy loss.
2. **Heavy-Hitters**: Accumulated attention scores follow a power-law distribution, indicating the presence of critical tokens (H2).

### H2O Algorithm
- **Eviction Policy**: Retains recent tokens and H2 based on local attention scores.
- **Implementation**: Integrates H2O with FlexGen to support different cache eviction techniques.

### Algorithm Pseudo Code
```markdown
Algorithm 1: H2 Eviction Algorithm

1: procedure H2_EVICTION(Q,K ∈ Rn×d, k ∈ N)
2: Let k denote the budget size of cache
3: S0 ← ∅
4: for i = 1 to n do
5: if i ≤ k then
6: Si ← Si−1 ∪ {i}
7: else
8: Di ← (exp(Qi,∗(KSi−1,∗)⊤)− 1[i]\Si−1) · 1i
9: oi ← D−1i · (exp(Qi,∗(KSi−1,∗)⊤)− 1[i]\Si−1)
10: Fscore(T ) := ∑s∈T os
11: Gi ← Si−1 ∪ {i}
12: u ← argmaxv∈GiFscore(Si−1 ∪ {i}\{v})
13: Si ← (Si−1 ∪ {i})\{u}
14: end if
15: end for
16: end procedure
```

## Experiments
### Performance Evaluation
- **Models Evaluated**: OPT, LLaMA, GPT-NeoX.
- **Tasks**: COPA, MathQA, OpenBookQA, PiQA, RTE, Winogrande, XSUM, CNN/Daily Mail.
- **Results**: H2O matches the performance of full KV cache models while using only 20% of the cache. Achieves up to 29× throughput improvement and 1.9× lower latency compared to baseline inference systems.

### Memory Efficiency
- **Memory Reduction**: Up to 5-10× reduction in KV cache size without accuracy loss.
- **Enhanced Performance**: Improved performance over existing KV cache sparsification techniques.

## Conclusion
H2O effectively reduces KV cache memory usage in LLMs while maintaining high performance. By leveraging the properties of heavy-hitters, H2O achieves significant improvements in throughput and latency, making it a valuable approach for efficient LLM deployment.

## Repository
For more information and access to the code, visit the [GitHub repository](https://github.com/FMInference/H2O).