# ReMFT
## Overview
ReMFT is a framework designed to enhance traffic flow forecasting by integrating multiscale temporal modeling with LLM-based semantic representation learning.  

The overall architecture of the framework is illustrated below.

![Alt Text](framework.png)
## Key components
### 1️⃣ Multiscale Time-Series Decomposition
The framework first performs multiscale decomposition on the original time series.
·The raw sequence is partitioned into multiple sub-sequences at different temporal resolutions.
·This enables the model to capture temporal patterns across multiple time granularities.
### 2️⃣ Multiscale Trend-Seasonality Mixing (MTSM)
We introduce the Multiscale Trend-Seasonality Mixing (MTSM) module to extract temporal components.
For each sub-sequence:
·Trend component → captures long-term evolution
·Seasonal component → captures periodic fluctuations
These components are then aggregated across scales using weighted fusion, allowing the model to jointly capture:
·Short-term dynamics
·Long-term temporal dependencies
## Usage
1.Install the environment based on requirements.txt  
2.Download PEMS03.npz, PEMS04.npz, PEMS07.npz, PEMS08.npz and put them into ./data  
3.Download llama-7b, gpt-2, bert and put them into ./LLM  
4.run run.ipynb

1️⃣ Multiscale Time-Series Decomposition
