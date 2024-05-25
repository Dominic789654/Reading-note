## Successful Language Model Evaluations

### Author: Jason Wei
[link](https://www.jasonwei.net/blog/evals)
#### Key Points

- **Importance of Evaluations**: Evaluation benchmarks ("evals") are crucial incentives for the research community. Many breakthroughs are closely linked to significant performance improvements on specific evals. A key role of team leads is to determine which eval to optimize.

- **Definition of a Successful Eval**: An eval is considered successful if it is used in breakthrough papers and is trusted within the community.

#### Successful Evals in the Past Five Years

1. **GLUE/SuperGLUE**: Used by almost all NLP papers in the pre-LLM era (e.g., BERT, T5).
2. **MMLU**: Favored by DeepMind and Google, used in almost all LLM papers.
3. **GSM8K**: Spurred LLMs for reasoning, used in every chain-of-thought paper.
4. **MATH**: Used in most LLM papers.
5. **HumanEval**: Classic eval for LLMs in coding.

#### Factors for a Successful Eval

1. **Promotion by Major Papers**: Successful evals are often promoted by significant papers, such as GLUE by BERT and MMLU by Gopher and Chinchilla.
2. **Significant and Understandable Scores**: Achieving superhuman performance or solving grade-school math problems is easily grasped and significant.
3. **Sufficient Number of Examples**: At least 1,000 examples to avoid noise and poor user experience.
4. **High Quality**: An eval with many mistakes loses researchers' trust.
5. **Simplicity and Ease of Use**: Overly complex or resource-intensive evals are less likely to be widely adopted.
6. **Meaningful Tasks**: Evals should measure central aspects of intelligence like language understanding or math.

#### Common Issues with Evals

- **Instability**: Insufficient examples or complex designs can lead to instability.
- **Low Quality**: Mistakes in the eval undermine its credibility.
- **Overly Complex**: Too many metrics or subsets make the eval hard to understand and use.
- **High Cost**: Evals that require significant resources and time are difficult to promote.
- **Meaningless Tasks**: Evals must be relevant to intelligence to be of interest to researchers.
- **Accurate Scoring**: Minimizing grading errors is crucial to maintaining researcher trust.
- **Performance Saturation**: Evals must provide long-term value and not become saturated too quickly.

#### Future of Evaluations

- **Human Pairwise Ratings**: Evals like LMSYS offer a general single-number metric but may have unclear measurements.
- **Model-Generated Evaluations**: Though finicky, they can be useful for quick experiments.
- **Domain-Specific Evals**: High-quality, domain-specific evals, while limited in audience, are still valuable.
- **Test Set Contamination**: Combining public and private test sets can balance ease of use with trustworthiness.

#### Conclusion

Evaluation benchmarks are vital for AI research and deserve more attention and investment. Good evals, with proper buy-in, serve as objective functions for AI researchers and have a powerful impact on the field.