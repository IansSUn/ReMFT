# ReMFT
## Overview
ReMFT is a framework designed to enhance traffic flow forecasting by integrating multiscale temporal modeling with LLM-based semantic representation learning.  

The overall architecture of the framework is illustrated below.

![Alt Text](framework.png)
## Key components
### 1️⃣ Multiscale Time-Series Decomposition
The framework first performs multiscale decomposition on the original time series.
- The raw sequence is partitioned into multiple sub-sequences at different temporal resolutions.  
- This enables the model to capture temporal patterns across multiple time granularities.  
### 2️⃣ Multiscale Trend-Seasonality Mixing (MTSM)
We introduce the Multiscale Trend-Seasonality Mixing (MTSM) module to extract temporal components.  
For each sub-sequence:
- Trend component → captures long-term evolution  
- Seasonal component → captures periodic fluctuations

These components are then aggregated across scales using weighted fusion, allowing the model to jointly capture:
- Short-term dynamics  
- Long-term temporal dependencies
### 3️⃣ Multiscale Representation Integration
To further integrate information across scales:
- A Multi-Layer Perceptron (MLP) is applied  
- It combines representations from different temporal resolutions  

This improves:
- Representation capacity  
- Predictive robustness
### 4️⃣ LLM-based Semantic Representation
To enhance the model's understanding of latent semantics in time series:  
- We incorporate the embedding space of a pre-trained Large Language Model (LLM).  

Specifically:  
- The time series is divided into multiple temporal blocks, and 1D convolution is used to capture local features between adjacent blocks.  
- A multi-head cross-attention mechanism aligns the temporal feature blocks with the semantic space of the LLM, i.e., the pretrained token embeddings.
### 5️⃣ Cross-Attention Semantic Injection
A cross-attention mechanism is used to inject semantic-level information into the forecasting model.  

- In the Cross-Attention module, Q is derived from temporal feature blocks, while K/V are obtained from text prototypes.
- The cross-attention output is fed into a frozen LLM for deeper semantic modeling.
- The final hidden states are extracted and transformed through flattening and linear projection to produce the prediction sequence.
## Usage
1.Install the environment based on requirements.txt  
2.Download PEMS03.npz, PEMS04.npz, PEMS07.npz, PEMS08.npz and put them into ./data  
3.Download llama-7b, gpt-2, bert and put them into ./LLM  
4.run run.ipynb

