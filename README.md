# Socio-Economic Factors and GDP per Capita

### Table of Contents
1. [Installation](#installation)  
2. [Project Motivation](#motivation)  
3. [File Descriptions](#files)  
4. [Results](#results)  
5. [Licensing, Authors, and Acknowledgements](#licensing)  

---

## Installation <a name="installation"></a>

The analysis was developed with **Python 3.10**.  
Required libraries can be installed via `pip`:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn shap ipykernel
```

The code should run without issues on standard Python environments.  
SHAP is used for model interpretation.

---

## Project Motivation <a name="motivation"></a>

This project was created as part of the **Udacity Data Scientist Nanodegree**.  
The goal was to analyze **World Development Indicators (WDI)** data from the World Bank and answer two key business questions:

1. **Which socio-economic factors best explain differences in GDP per capita (based on a country example)?**  
   → Relevant for **governments** to identify where investments (e.g., education, health) are most effective.  

2. **To what extent can development indicators (e.g., health, education, demographics) be used to predict a country’s GDP per capita?**  
   → Relevant for the **World Bank** to support GDP estimates for countries with uncertain or missing data.  

3. **Which countries are under-/over-predicted (residual analysis) and what does that imply?**

---

## File Descriptions <a name="files"></a>

- `World_Development_Indicators_all_Countries_Data.csv`  
  → Dataset containing multiple socio-economic indicators for several countries.  

- `Udacity_Project_1.ipynb`  
  → End-to-end workflow according to CRISP-DM including:
  - Data preprocessing (reshaping, handling NaN, dropping multicollinear features)  
  - Exploratory analysis (correlations, heatmaps, histograms)  
  - Linear regression model with `scikit-learn`  
  - Model evaluation (R², RMSE, scatter plots)  
  - Model interpretation using **SHAP** (feature importance, waterfall plot)  

---

## Results <a name="results"></a>

- **Model performance:**  
  - R² (Train): ~0.83
  - R² (Test): ~0.81 
  - RMSE indicates solid generalization with no strong overfitting.  

- **Business insights:**  
  - GDP per capita differences are mainly explained by **demographic and employment-related factors**.  
  - Example for **Germany, 2023**:  
    1. *Population ages 0-14 (% of total population)*  
    2. *Self-employed, total (% of total employment)*  
    3. *Death rate, crude (per 1,000 people)*  
  - Many features follow a **lognormal distribution**, which justified using median imputation.  

- **Residual analysis:**
  - The model **underestimates very wealthy countries** such as *Switzerland, Ireland, Luxembourg, Norway*.  
  - It **misestimates unique economies** like *Djibouti, Maldives, Guyana*.  
  - **Negative predictions (e.g., Guyana 2022)** show a limitation of linear regression, since GDP cannot be negative.  
  - The model generalizes well in the **middle-income range**, but is unreliable at the **extremes**.  

- **Limitations:**  
  - Predictions are more reliable for countries with lower GDP per capita.  
  - Some negative predictions occurred, highlighting limitations of linear regression for this dataset.  

---

## Licensing, Authors, and Acknowledgements <a name="licensing"></a>

- **Data Source:** [World Bank – World Development Indicators](https://databank.worldbank.org/source/world-development-indicators)  
- **Author:** Achraf Ouald Chaib (Udacity Data Scientist Nanodegree Project)  
- **License:** This project is intended for educational purposes within the Udacity program. 
- **Acknowldegements:** Code snippets from Udacity and some texting and coding with help of ChatGPT by OpenAI.

Feel free to use the code for your own analyses!
