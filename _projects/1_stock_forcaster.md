---
layout: page
title: Quantitative Stock Forecasting Engine
description: LSTM & Attention-based model with real-capital validation
img: assets/img/stock/graph1.png
importance: 1
category: fun
---

**Role:** ML Researcher

This project focuses on the development and deployment of a specialized time-series forecasting engine designed to predict equity price volatility. Unlike purely theoretical academic projects, this system was **validated with real capital** in a live market environment. 

Working in a small team, we created a full-stack solution from raw data ingestion to signal generation—demonstrating the ability to bridge the gap between "test-set accuracy" and real-world performance.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/stock/mlpipeline.png" title="Data Pipeline" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/stock/mlarchitecture.png" title="LSTM Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: The custom ETL pipeline. Right: The LSTM/Attention model architecture.
</div>

### Real-World Performance
* **Quantitative Success:** The model achieved a **< 2% Mean Absolute Percentage Error (MAPE)** on the 40-day prediction window, a result considered exceptional by industry standards for mid-cap equities.
* **Capital Efficiency:** In a 2-month live-fire test, the strategy generated a **560% Return on Investment (ROI)**, scaling a test account from 300 to 2,000 dollars. Achieving this aggressive return, we trained the forecaster to predict 10 days in the future to execute quicker options trades instead of longer term holds.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/stock/graph1.png" title="40-Day Prediction Window" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/stock/graph2.png" title="40-Day Prediction Window" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Model Validation: The engine (blue dashed) tracking actual price movement (orange solid) over a 40-day forecast window. Note the model's ability to smooth out noise while capturing the macro trend.
</div>

### The Data Pipeline
To support the model, I engineered a robust data pipeline capable of handling noisy financial data.
1.  **Data Gathering:** Used yfinance to gather **10 years of daily time-series data** for 50+ target equities.
2.  **Cleaning:** Implemented automated cleaning protocols to handle missing ticks, stock splits, and dividends, ensuring data integrity before training.
3.  **Feature Engineering:** Enriched the dataset with **18 distinct predictive indicators** (technical and statistical) to expand the feature space for the neural network.
4.  **Normalization**: Normalized the dataset with a MinMax scaler from -1,1 to prevent higher weight on larger features.

### Technical Architecture
The core of the system is a custom deep learning model built with **TensorFlow** and **Keras**.
* **Custom Model Architecture:** I engineered a **custom Attention Layer subclass** rather than using off-the-shelf components, integrating it with **LSTM networks** to mathematically weigh the relevance of historical volatility against current price action.
* **Optimization & Training:** Implemented dynamic **Learning Rate Scheduling** and **Early Stopping** callbacks to optimize convergence and prevent overfitting on noise.
* **Feature Engineering:** The system aggregates over a decade of daily time-series data, generating **18 distinct predictive indicators** (including VWAP, Aroon, and Bollinger Bands) to enrich the feature space.