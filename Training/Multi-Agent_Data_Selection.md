# Multi-Agent Collaboration for Data Selection: Improving LLM Pre-training Efficiency

**Source:** arXiv, 2410.08102
**Date:** 2024-10-12
**Keywords:** Multi-Agent, Data Selection, Pre-training, LLM

## Paper Overview

### Research Problem
During the pre-training process of Large Language Models (LLMs), how can we effectively select and utilize data to improve training efficiency?

### Main Contribution
This study proposes an innovative **multi-agent collaboration mechanism** that integrates different data selection strategies, significantly improving data utilization and model performance.

## Key Ideas

### Related Work

1. **Importance of Data Selection**
   - Traditional methods often operate independently without synergistic effects
   - Limits their effectiveness in practical applications

2. **Advantages of Multi-Agent Systems**
   - By treating multiple data selection methods as independent agents, training samples can be evaluated and prioritized more flexibly

### Proposed Method

1. **Multi-Agent Collaboration Framework**
   - Composed of multiple independent agents
   - Each agent responsible for specific types of data selection (quality, topic, or domain)
   - Central console for information sharing and decision-making

2. **Data Selection Process**
   - **Initialization Phase**: Offline annotation of entire dataset, with annotation information stored in each agent's memory
   - **Online Update Phase**: During training, updates each agent's memory and collaboration mechanism based on current model to optimize sample scoring
   - **Decision Making**: "Agent Console" aggregates feedback from all agents to calculate final scores and make data selection decisions

3. **Reward Signals and Dynamic Adjustment**
   - Treats loss as a reward signal
   - Guides each agent to update its strategy
   - Enables dynamic adjustment of scoring criteria based on current model performance

## Experimental Results

The method significantly improves data efficiency and accelerates convergence during LLM training. Across multiple language model benchmarks, compared with existing state-of-the-art methods, this method achieves an average improvement of **10.5%**.

| Selection Method | Problem Solving | Commonsense Reasoning | Reading Comprehension | Average |
|------------------|-----------------|----------------------|----------------------|---------|
| Random Sampling - 30B tokens | 31.1 | 32.9 | 43.1 | 34.2 |
| Multi-Agent Collaboration | **36.7 (+5.6%)** | **34.8 (+1.9%)** | **45.9 (+2.8%)** | **37.8 (+3.6%)** |

## Conclusion

This research demonstrates the significant potential of multi-agent collaboration mechanisms in LLM pre-training. By flexibly combining different data selection strategies, it not only improves data utilization but also significantly enhances model performance.

## Personal Takeaways

This study shows promising results for multi-agent collaboration in LLM training. The ability to dynamically adjust data selection based on model performance during training is particularly valuable. This approach could be extended to more practical application scenarios in the future.

For more details, visit the [paper link](https://arxiv.org/html/2410.08102)
