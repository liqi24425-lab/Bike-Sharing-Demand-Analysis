# Analysis of Bicycle Usage Volume: Capital Bikeshare 🚲

## 📌 Project Overview
This project investigates the impact of environmental conditions (weather) and temporal factors (seasonality, time of day) on hourly bike-sharing demand in Washington D.C. 

Using data from the Capital Bikeshare system, we developed a **Multiple Linear Regression model** to forecast rental volume, helping urban planners and operators optimize fleet allocation and green mobility infrastructure.

## 🛠️ Tools & Technologies
* **Language:** R (RMarkdown)
* **Libraries:** `dplyr`, `car`, `ggplot2`, `MASS`
* **Techniques:** * Multiple Linear Regression (OLS)
  * Feature Engineering (Cyclical Time Transformation)
  * Box-Cox Power Transformations
  * Sensitivity Analysis (Cook's Distance)
  * Interaction Modeling

## 📂 Dataset
* **Source:** [UCI Machine Learning Repository - Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset)
* **Origin:** Capital Bikeshare System, Washington D.C. (2011–2012)
* **Granularity:** Hourly records ($N \approx 17,000$)
* **Key Variables:** Rental Count (`cnt`), Temperature, Humidity, Windspeed, Season, Holiday, Working Day.

## 📊 Methodology & Key Features
1. **Cyclical Feature Engineering:** * Addressed the mathematical discontinuity of time (23:00 vs 00:00) by transforming the `hour` variable into continuous cyclical coordinates using Sine and Cosine functions.
   * *Formula:* $hr_{sin} = \sin(2\pi \cdot hr/24)$
2. **Interaction Modeling:** * **Weekday × Hour:** Modeled distinct traffic curves for "Commuter" days (double-peak) vs. "Leisure" weekends (single-peak).
   * **Season × Temperature:** Accounted for the varying impact of temperature on ridership across different seasons.
3. **Diagnostic Refinement:** * Applied a **Cube Root transformation** ($y^{1/3}$) to the response variable based on Box-Cox analysis.
   * Conducted a sensitivity analysis, removing ~5% of data (782 observations) flagged by Cook's Distance to improve model stability.

## 📈 Key Findings
* **Predictive Power:** The final model achieved an **Adjusted $R^2$ of 0.749**, explaining nearly 75% of the variance in hourly ridership.
* **Temporal Dynamics:** Daily usage patterns are statistically distinct between working days and weekends ($p < 0.001$).
* **Environmental Impact:** While adverse weather (high humidity/wind) universally reduces demand, the positive driver of temperature is context-dependent, varying significantly by season.

## ⚖️ Ethical Considerations
* **Data Trustworthiness:** Validated that data was collected via automated sensors (not simulated) with complete metadata.
* **Privacy:** Adhered to data minimization principles; the dataset contains only aggregate counts with no Personally Identifiable Information (PII) or individual trip routes.
* **License:** Usage authorized under Creative Commons Attribution 4.0 International (CC BY 4.0).

## 📄 Repository Structure
* `BikeShare_data_analysis.Rmd`: Source code for data cleaning, transformation, and regression modeling.
* `hour_cleaned_1.csv`: The processed dataset used for the final model.
* `Project_Report.pdf`: Final presentation of results and visualizations.

---
*Author: Qi Li* *Date: November 2025*
