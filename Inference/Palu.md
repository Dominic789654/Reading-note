Here's a summary of the paper titled **"Palu: Compressing KV-Cache with Low-Rank Projection"**:

---

# Palu: Compressing KV-Cache with Low-Rank Projection

**Authors**:  
Chi-Chih Chang\(^1\)*, Wei-Cheng Lin\(^1\)*, Chien-Yu Lin\(^2\)*, Chong-Yan Chen\(^1\), Yu-Fang Hu\(^1\), Pei-Shuo Wang\(^1\), Ning-Chi Huang\(^1\), Luis Ceze\(^2\), Kai-Chiang Wu\(^1\)  
\(^1\)National Yang Ming Chiao Tung University, \(^2\)University of Washington

\*These authors contributed equally to this work.

**Abstract**:  
This paper presents Palu, a novel KV-Cache compression framework that employs low-rank projection to reduce the size of the KV-Cache, a crucial component in large language models (LLMs). Unlike traditional methods that either quantize KV-Cache or sample it, Palu targets the hidden dimensions of KV tensors, which are often redundant. The framework involves decomposing linear layers into low-rank matrices, caching smaller intermediate states, and reconstructing full keys and values on-the-fly. Key contributions include medium-grained low-rank decomposition, an efficient rank search algorithm, low-rank-aware quantization, and matrix fusion optimized for GPU kernels. Experiments demonstrate that Palu can compress KV-Cache by over 91.25% while maintaining better accuracy compared to state-of-the-art methods. Additionally, Palu delivers up to a 1.61× end-to-end speedup for the attention module when compressing KV-Cache by 50%.

---

### 1. Introduction

- **Motivation**: KV-Cache is essential for speeding up LLM inference, but its size can grow rapidly, straining memory resources and slowing down inference. Existing compression techniques like quantization and token eviction do not fully exploit the hidden dimensions in KV tensors.

- **Objective**: Palu aims to reduce KV-Cache size through low-rank projection, which targets the hidden dimensions of KV tensors, achieving better compression and efficiency.

### 2. Methodology

- **Low-Rank Projection**: Palu decomposes key and value projection matrices into low-rank matrices, caching the latent representations instead of the original KV-Cache. This method reduces memory usage and minimizes runtime overhead.

- **Decomposition Techniques**:
  - **Multi-Head Low-Rank Decomposition (M-LRD)**: Per-head decomposition, but may lead to accuracy degradation.
  - **Joint-Head Low-Rank Decomposition (J-LRD)**: Decomposes all heads jointly, preserving common components but with higher computational cost.
  - **Group-Head Low-Rank Decomposition (G-LRD)**: Balances accuracy and computational cost by grouping heads and performing decomposition.

- **Rank Search Algorithm**: An efficient algorithm based on Fisher information is used to assign different ranks to matrices, optimizing compression without sacrificing accuracy.

- **Low-Rank-Aware Quantization**: Palu integrates a low-rank-aware quantization algorithm, utilizing the Walsh-Hadamard transform to eliminate outliers and improve quantization accuracy.

- **Matrix Fusion**: Offline fusion of matrices reduces runtime overhead during the reconstruction of KV-Cache.

### 3. Experiments

- **Models**: Evaluated on Llama2, Mistral, and Vicuna models.

- **Datasets**: WikiText-2, C4, and various long-context tasks from LongBench.

- **Results**: Palu achieves over 91.25% compression while maintaining similar or better accuracy compared to baseline methods. It also provides significant speedup in attention module processing, particularly in scenarios requiring extensive KV-Cache usage.

### 4. Conclusion

- **Contributions**:
  - Introduces a novel KV-Cache compression framework using low-rank projection.
  - Demonstrates significant memory reduction and inference speedup while maintaining accuracy.
  - Provides a flexible and efficient method for compressing KV-Cache in large-scale LLMs.

- **Future Work**: Exploration of Palu's performance on even larger models and integration with other efficiency techniques like token eviction.

**Code Availability**: The implementation of Palu is publicly available at [GitHub](https://github.com/shadowpa0327/Palu).

---

This summary captures the key aspects of the paper in a concise manner, reflecting the main contributions and findings of the work. Let me know if you need more details or have any other requests!