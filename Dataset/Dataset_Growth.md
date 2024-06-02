# Dataset Growth: Efficiently Scaling Data Collection for Deep Learning

## Authors and Affiliations
- **Ziheng Qin** (National University of Singapore)
- **Zhaopan Xu** (National University of Singapore, Harbin Institute of Technology)
- **Yukun Zhou** (National University of Singapore)
- **Zangwei Zheng** (National University of Singapore)
- **Zebang Cheng** (Shenzhen Technology University)
- **Hao Tang** (ETH Zurich)
- **Lei Shang** (Alibaba Group)
- **Baigui Sun** (Alibaba Group)
- **Xiaojiang Peng** (Shenzhen Technology University)
- **Radu Timofte** (ETH Zurich)
- **Hongxun Yao** (Harbin Institute of Technology)
- **Kai Wang** (National University of Singapore)
- **Yang You** (National University of Singapore)

## Abstract
Efficiently handling the growing scale of deep learning data, especially from diverse sources with varying qualities, is challenging. Traditional methods of data cleaning and selection are not feasible at the current data scale. To address this, the authors propose InfoGrowth, an efficient online algorithm for data cleaning and selection, maintaining up-to-date datasets with cleanliness and diversity awareness. InfoGrowth improves data quality and efficiency for both single-modal and multi-modal tasks, providing a scalable solution for real-world data engines.

## Introduction
- Deep learning benefits significantly from the growing abundance of data, which also presents challenges in efficiently managing and utilizing these vast datasets.
- Traditional human-led data cleaning is no longer feasible due to the exponential growth of web data, which includes noise and redundancy.
- The proposed InfoGrowth algorithm aims to handle these issues by providing an efficient, scalable solution for maintaining clean and diverse datasets.

## Background and Related Works
### Deep Learning Datasets
- Datasets are foundational for training and validating deep learning models, ranging from early manually labeled datasets (e.g., MNIST, CIFAR10/100, ImageNet) to large-scale automatically labeled datasets (e.g., JFT).
- Multi-modal datasets, capturing rich information from various data types like images and text, have also evolved, with examples like COCO, Flickr30K, and LAION-5B.

### Web Scale Data Curation
- Various techniques have been proposed to reduce noise in web data, including soft-labeling, filtering, and recaptioning for multi-modal datasets and semi-supervised learning for single-modal datasets.
- However, these methods are typically offline and not scalable to the current data growth rate.

## How to Make a Dataset Grow
### Preliminaries
```
                    InfoGrowth Method Pipeline
                    ==========================

                      +-----------------------+
                      |   Data Stream Input   |
                      +-----------------------+
                                 |
                                 v
                    +---------------------------+
                    | Encoding (Using BLIP)     |
                    +---------------------------+
                                 |
                                 v
                      +----------------------+
                      |  Quality Estimation  |
                      +----------------------+
                                 |
                                 v
               +----------------------------------+
               | Noise Detection and Correction  |
               +----------------------------------+
                                 |
                                 v
                      +-------------------+
                      |  Gain Calculation |
                      +-------------------+
                                 |
                                 v
                          +------------+
                          |  Sampling  |
                          +------------+
                                 |
                                 v
                    +------------------------+
                    |  Updating the Dataset  |
                    +------------------------+

```
- **Multimodal Models**: The study leverages models like CLIP and BLIP, which use contrastive loss to predict relationships between images and text.
- **Submodular Function**: Utilized to estimate the information gain of selected samples, helping in efficiently adding informative samples to the dataset.
- **Online Approximate Near Neighbor Search Algorithm**: Employed to reduce the computational cost of neighborhood searches, essential for scalable data processing.

### Theoretical Analysis
- The paper interprets datasets from a Bayesian inference perspective, aiming to map data into an embedding space where embeddings are separable according to conditions (e.g., class labels).
- In this space, the algorithm detects out-of-distribution samples (noise) and redundant samples, estimating their quality for dataset growth.

### Overview of InfoGrowth
- **Pipeline**: The process involves encoding new data points, estimating their quality using a multimodal model, cleaning noisy data, and selecting informative samples based on calculated gains.
- **Algorithm**: Described in a step-by-step manner, highlighting how new data points are processed, cleaned, and added to the growing dataset.

### Detecting and Correcting Noisy Samples
- Utilizes a model predicting \(P(c|d)\) to clean data by filtering and recaptioning, employing cosine similarity to detect unmatched samples and improve data alignment.

### Gain Calculation
- Inspired by submodular functions, InfoGrowth uses neighborhood-based gain calculations to estimate the information gain of data pairs, facilitating efficient data selection.

### Selecting Informative Samples
- Two sampling strategies are proposed: static sampling for better diversity and dynamic sampling for computational efficiency, both leveraging calculated gain values for selection.

## Experiments
### Datasets and Implementation Details
- Evaluates InfoGrowth on multi-modal datasets like CC3M and single-modal datasets like ImageNet-1K.
- Implementation details include using MiniGPT-4 for data cleaning and parallel processing for efficiency.

### Evaluation on Multimodal Dataset
- Demonstrates InfoGrowth's effectiveness in improving data efficiency and performance in image-text retrieval tasks on MSCOCO and Flickr30K.

### Downstream Tasks
- Evaluates performance on tasks like Visual Question Answering (VQA), Visual Reasoning (NLVR2), and Image Captioning (COCO and NoCaps), showing competitive results with reduced data amounts.

### Evaluation on Single-modal Dataset
- Applies InfoGrowth to ImageNet-1K, demonstrating superior performance and reduced computational cost compared to traditional dataset compression methods.

### Ablation Studies
- Investigates the impact of different components (cleaner and sampler) and parameters (neighborhood size \(k\), mean calculation methods) on InfoGrowth's performance, confirming the importance of each component.

## Discussion
### Comprehensive Comparison with Other Methods
- Compares InfoGrowth with other data processing methods, highlighting its efficiency, scalability, and suitability for both single-modal and multi-modal tasks.

### Scaling to Even Larger Scale
- Discusses the potential for further scaling InfoGrowth to billion-scale data using distributed near-neighbor search algorithms.

### The Marginal Benefit of Data
- Analyzes the diminishing returns of adding more data, emphasizing the importance of data quality over quantity.

### Visualizations
- Provides examples of detected redundant and noisy samples, illustrating the effectiveness of InfoGrowth's data cleaning and selection process.

## Conclusion
InfoGrowth offers a novel, efficient solution for handling the growing data demands of deep learning, significantly improving data quality and efficiency for both multi-modal and single-modal tasks. Its scalable design ensures practical application in real-world data engines, contributing to the creation of high-quality large-scale datasets and sustainable AI development.

## Repository
For more information and access to the code and datasets used in this research, visit the [GitHub repository](https://github.com/NUS-HPC-AI-Lab/InfoGrowth).