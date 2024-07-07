### ChunkAttention: Efficient Self-Attention with Prefix-Aware KV Cache and Two-Phase Partition

## Authors and Affiliations
- **Lu Ye**
- **Ze Tao**
- **Yong Huang**
- **Yang Li**
- **Affiliation**: Microsoft
- **Emails**: {luye, zetao, yohuan, yali2}@microsoft.com

## Abstract
ChunkAttention is a novel self-attention module designed to optimize memory and computational efficiency for large language models (LLMs) in multi-tenant serving scenarios. By leveraging shared system prompts, it introduces a prefix-aware KV cache and a two-phase partition algorithm to enhance data locality and reduce redundancy. Experiments demonstrate that ChunkAttention achieves a 3.2-4.8× speedup in self-attention kernel performance with system prompt lengths ranging from 1024 to 4096 tokens.

## Introduction
- **Context and Motivation**: LLMs require significant memory for self-attention operations, especially with long sequences. System prompts, common in multi-tenant architectures, introduce redundancy in the KV cache.
- **ChunkAttention**: Detects and shares prompt prefixes across multiple requests, structuring KV cache into smaller chunks within an auxiliary prefix tree to enhance memory utilization and computational efficiency.

## Methodology
### Prefix-Aware KV Cache (PAKV)
- **Structure**: KV cache organized into a prefix tree, allowing shared prefixes to be stored and reused across sequences.
- **Operations**: Manages sequence joins, leaves, and token decoding dynamically, reducing memory waste.

### Two-Phase Partition (TPP)
1. **Chunk-First Phase**: Processes shared chunks with high data locality, performing batched self-attention operations.
2. **Sequence-First Phase**: Handles individual sequence-specific chunks, optimizing parallelization and cache locality.

### Algorithm Pseudo Code
```markdown
Algorithm 1: Self Attention: Chunk First (partition chunks)
Require: Q ∈ Rb×d (query), T (prefix tree)
Ensure: O ∈ Rb×d (attention output)
function ATTNCHUNKFIRST(Q, T )
    Get chunks C1, ..., Ck in T that are shared by multiple sequences
    O,m,n← 0, 0, 0
    for C← C1 to Ck do
        K(C), V (C)← key, value cache stored in C
        i, j← start index, end index of sequences covered by C
        O(C),m(C),n(C)← partial_attn(Q, K(C), V (C), i, j)
        Save partial attention result O(C),m(C),n(C) to memory
    end for
end function
```

## Experiments
### Microkernel Evaluation
- **Baselines**: Compared against Naive, xformers, FlashAttention, and PagedAttention implementations.
- **Performance**: ChunkAttention achieves significant latency reductions, especially with longer shared prefixes. Outperforms baselines by 2.8-3.2× with 1024-4096 shared tokens.

### End-to-End Evaluation
- **ChunkLlama**: Built on Huggingface Llama with ChunkAttention integrated.
- **Results**: Achieves 1.6-2.3× higher throughput compared to vLLM, with up to 90% reduction in KV cache memory usage when sharing long system prompts.

## Conclusion
ChunkAttention efficiently manages KV cache and accelerates self-attention for LLM inference by leveraging shared system prompts and optimizing data locality. The prefix-aware KV cache and two-phase partition algorithm significantly improve performance and memory efficiency without compromising accuracy.

## Repository
For more information and access to the code, visit the [GitHub repository](https://github.com/microsoft/chunk-attention).