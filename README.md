# Anomaly Detection and Risk Scoring with GARCH-Based Volatility in Time-Series Analysis for VFV

## Project Overview
This project provides a robust framework for analyzing risk and detecting anomalies in stock data, specifically applied to the Vanguard S&P 500 Index ETF (VFV). Leveraging advanced time-series analysis and GARCH-based volatility modeling, the project aims to identify high-risk periods and potential fraudulent activity by examining volatility clusters, kurtosis, and custom risk scores.

## Key Objectives
1. **Anomaly Detection**: Identify unusual patterns in VFV time-series data using Isolation Forests.
2. **Risk Scoring**: Develop a custom risk score that incorporates price deviations (Z-score), volatility clustering, and high-risk flags.
3. **Volatility Modeling**: Use GARCH (Generalized Autoregressive Conditional Heteroskedasticity) models to predict time-varying volatility, enhancing risk assessment.
4. **Fraud Detection Insight**: Address the potential for high-risk activities and fraud by analyzing price fluctuations and volatility clustering.

## Methodology

### 1. Data Collection and Preparation
   - Data is retrieved using `yfinance` for VFV (Vanguard S&P 500 Index ETF).
   - The dataset includes columns for `price`, `volume`, and timestamp (`Date`), with additional columns derived for Z-score, rolling averages, and rolling kurtosis to aid in detecting anomalies.

### 2. Anomaly Detection
   - **Isolation Forest** is applied to identify outliers in price, volume, and Z-score, flagging unusual activity.
   - Anomalies are labeled for further risk scoring.

### 3. GARCH-Based Volatility Modeling
   - A GARCH(1,1) model is fitted to the returns series to capture conditional volatility.
   - The model’s output, `conditional_volatility`, highlights periods of heightened risk due to increased price fluctuations.

### 4. Custom Risk Scoring
   - A custom risk score is computed by combining Z-score, anomaly flags, and conditional volatility.
   - High kurtosis values are factored in to signal periods of extreme tail risk.
   - The risk score highlights periods of increased potential for loss or fraudulent activity.

### 5. Visualization
   - **Price and Anomaly Plot**: Visualizes price data with flagged anomalies.
   - **Conditional Volatility Overlay**: Plots GARCH-based conditional volatility on the price chart, highlighting high-risk periods.
   - **Risk Score Plot**: Displays the risk score over time, helping to visualize high-risk intervals.
   - **Additional Visualizations**: Include scatter plots and heatmaps to illustrate the relationship between conditional volatility and risk.

## Project Structure

- **data/**: Contains any data files required for the project (if applicable).
- **src/**: Source code files for each module (anomaly detection, GARCH modeling, risk scoring).
- **notebooks/**: Jupyter notebooks with step-by-step code, explanations, and visualizations.
- **README.md**: Project overview and instructions (this file).

## Requirements
- **Python 3.x**
- **Libraries**:
  - `yfinance`: Fetching historical stock data.
  - `numpy`, `pandas`: Data manipulation.
  - `matplotlib`, `seaborn`: Data visualization.
  - `scikit-learn`: Isolation Forest for anomaly detection.
  - `arch`: For GARCH modeling.
  - `statsmodels`: (Optional) For statistical analysis.

Install all dependencies with:
```bash
pip install -r requirements.txt

## Getting Started
1. **Data Collection**: Modify the `ticker` variable to specify the financial asset to analyze (default is `VFV.TO`).
2. **Run the Notebook**: Follow each section in the Jupyter notebook to replicate data preparation, anomaly detection, volatility modeling, and risk scoring.
3. **Visualization**: Each section includes visualizations to inspect the results of anomaly detection, volatility modeling, and risk scoring.

## Key Results
The project outputs a series of visualizations and metrics:
- **High-Risk Periods**: Highlighted time periods with elevated risk scores based on Z-score, volatility, and anomalies.
- **Volatility Clusters**: Periods of increased volatility captured by GARCH modeling.
- **Risk Alerts**: A detailed risk score for each time period, factoring in kurtosis, anomalies, and volatility.

## Future Improvements
Consider integrating:
- **Tail Risk Analysis**: Using Extreme Value Theory to further quantify tail risks.
- **Market Correlations**: Compare VFV volatility with major indices to detect correlated risks.
- **Sentiment Analysis**: Integrate financial news sentiment to provide a forward-looking risk assessment.

## License
This project is licensed under the MIT License.

## Acknowledgments
Special thanks to open-source contributors of `yfinance`, `arch`, and `scikit-learn`, whose libraries made this analysis possible.
