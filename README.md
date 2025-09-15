# Battery State Estimation: SOC and SOH Prediction

This project contains two Colab notebooks demonstrating the prediction of a battery's State of Charge (SOC) and State of Health (SOH) using different machine learning and filtering techniques.

---

## 1. State of Charge (SOC) Estimation (`SOC.ipynb`)

This notebook predicts the battery's current charge level (SOC).

### Key Features:
* **Methodology**: It employs and compares two different models for SOC prediction:
    1.  A **Long Short-Term Memory (LSTM)** neural network, which is well-suited for time-series data.
    2.  An **XGBoost** regressor, a powerful gradient-boosting model.
* **Target Variable Generation**: The initial SOC values (the "ground truth" for training) are calculated using the **Coulomb Counting** method.
* **Inputs**: The models use features like `Voltage`, `Current`, `Temperature`, `Capacity`, `WhAccu`, and `Cnt`.
* **Outcome**: The notebook trains both models, performs hyperparameter tuning, and compares their performance using Mean Squared Error (MSE), concluding with a visualization of the results.

---

## 2. State of Health (SOH) Estimation (`SOH (1).ipynb`)

This notebook estimates the battery's long-term health and degradation (SOH).

### Key Features:
* **Methodology**: It implements a **Kalman Filter** using PyTorch to estimate the SOH. The Kalman Filter is an optimal estimation algorithm that is effective for systems that change over time.
* **Data Handling**: The notebook first analyzes multiple battery datasets (`B0*.csv`) and selects a diverse set by checking the standard deviation of their SOH values before concatenating them for training.
* **Inputs**: The model uses features such as `terminal_voltage`, `terminal_current`, `temperature`, `cycle`, and `capacity`.
* **Outcome**: After training, the notebook evaluates the Kalman Filter's performance on a test set and displays a sequence of predicted SOH values against their actual counterparts.

---

### How to Use
1.  Open each `.ipynb` file in Google Colab.
2.  Ensure you have the required datasets uploaded to your Colab environment.
3.  Run the cells sequentially to see the data processing, model training, and evaluation steps.
