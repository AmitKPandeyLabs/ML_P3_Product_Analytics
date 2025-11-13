# Conagra Predictive Analytics: Meat Substitute Market Strategy

<p align="left">
  <img src="https://img.shields.io/badge/Python-3.9%2B-blue.svg?style=for-the-badge&logo=python&logoColor=white" alt="Python Version">
  <img src="https://img.shields.io/badge/Pandas-2.0%2B-purple.svg?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas">
  <img src="https://img.shields.io/badge/Statsmodels-0.13%2B-yellow.svg?style=for-the-badge&logo=python&logoColor=white" alt="Statsmodels">
  <img src="https://img.shields.io/badge/Matplotlib-3.5%2B-green.svg?style=for-the-badge&logo=matplotlib&logoColor=white" alt="Matplotlib">
</p>

This repository contains an end-to-end predictive analytics project conducted for the Conagra Data Science Competition. The project analyzes the plant-based meat substitutes market to identify growth opportunities, model sales drivers, and provide data-driven strategies for Conagra's 'Gardein' brand.

## 🎯 Project Overview & Business Problem

The plant-based meat market is experiencing explosive growth, driven by health-conscious consumers, environmental concerns, and a rise in flexitarian diets. Conagra, with its 'Gardein' brand, is a key player but faces intense competition from brands like MorningStar Farms, Beyond Meat, and Impossible Foods.

This project aims to analyze proprietary sales and market data to unlock future growth potential for Conagra in this category. The primary goals are:
* **Analyze Market Trends:** Identify key market drivers, consumer demographics, and product insights within the meat substitute market.
* **Model Sales Drivers:** Use predictive modeling (Ordinary Least Squares regression) to understand and quantify the key factors that influence `Dollar_Sales`, focusing on price, product form, and geographical variations.
* **Provide Strategic Recommendations:** Deliver actionable, data-driven strategies for pricing optimization, product innovation, and targeted marketing focus to enhance Gardein's market share and profitability.

## 📊 Dataset

The primary dataset was a proprietary `df_merged2.pickle` file provided for the Conagra Data Science Competition. This comprehensive dataset contained detailed sales and product information across various brands and geographies. Key features included:
* **`Geography`**: The sales region (e.g., North-East, California, Mid-South, Great Lakes, South-East).
* **`Brand_Name`**: The manufacturer of the product, including major players like Gardein, Morningstar, Beyond Meat, Impossible, and Private Label brands.
* **`Form`**: The physical form factor of the product (e.g., Patties, Crumbles, Sausages, Nuggets, Links).
* **`Flavor_Scent`**: The flavor profile of the product (e.g., Original, BBQ, Italian, Spicy).
* **Sales Metrics**: `Dollar_Sales`, `Unit_Sales`, `Volume_Sales` (total sales, units sold, and volume in ounces/pounds).
* **Price Metrics**: `Price_per_Unit`, `Price_per_Ounce`, `Price_per_Volume` (various measures of product pricing).

The analysis was specifically focused on the top 5 brands by sales volume to ensure relevance and impact for Conagra's competitive landscape.

## ⚙️ Methodology

The project was executed in two main phases: a comprehensive Exploratory Data Analysis (EDA) to uncover market insights, followed by Predictive Modeling to quantify the impact of key variables on sales.

### 1. Exploratory Data Analysis (EDA)
EDA was performed to uncover insights into sales patterns, pricing strategies, consumer behavior, and market composition within the plant-based meat sector. Key analyses included:
* **Market Research Integration:** Insights from broader market research were incorporated, highlighting a projected market size of $4.8B by 2029, with primary consumers aged 18-44, and the growing importance of the flexitarian segment as a target market.
* **Regional Sales Analysis:** In-depth analysis was conducted to identify high-performing and underperforming regions, pinpointing key geographies with the highest growth potential and competitive opportunities.
* **Price Point Analysis:** Sales performance was rigorously analyzed across different price ranges (e.g., the competitive $7-9 and premium $13-16 brackets) to understand consumer price sensitivity and optimal pricing strategies.
* **Product & Flavor Insights:** Investigation into which product forms (e.g., patties, crumbles) and specific flavors were most significant in driving `Dollar_Sales` and `Unit_Sales`.
* **Competitive Landscape:** Analysis of competitors' market share, pricing strategies, and product portfolios to identify Gardein's strengths and weaknesses.

### 2. Predictive Modeling (Sales Driver Analysis)
To quantify the relationship between price, product form, geography, and sales, a **multivariate Ordinary Least Squares (OLS) regression model** was built using the `statsmodels` library.

The model aimed to predict `Dollar_Sales` based on key independent variables and their crucial interaction effects. A simplified version of the model formula used is:

```python
# OLS formula to model Dollar Sales, including interaction terms
formula = 'Dollar_Sales ~ Price_per_Unit + Price_per_Unit:C(Form) + Price_per_Unit:C(Geography):C(Form) + C(Form):C(Geography)'
model = smf.ols(formula, data=df_topbrands).fit()
```

This robust statistical model allowed us to:

  * Determine the precise impact of `Price_per_Unit` on `Dollar_Sales`, effectively calculating price elasticity across different segments.
  * Quantify how sales are influenced by individual `Form` types and `Geography` regions.
  * Analyze the crucial **interaction effects** between `Price_per_Unit`, `Form`, and `Geography` to provide highly specific and nuanced recommendations, such as optimal pricing for a specific product form in a particular region.

## 📈 Key Findings & Strategic Recommendations

The comprehensive analysis and predictive modeling yielded several actionable, data-driven insights and strategic recommendations for Conagra's 'Gardein' brand to capitalize on market opportunities and enhance its competitive position.

<p align="center">
<img src="assets/key_recommendations_summary.png" width="80%" alt="Summary of Key Recommendations">
</p>

1.  **Prioritize Product Form Innovation:** Product form (e.g., patties, sausages) was found to be a statistically significant driver of sales, often more impactful than specific flavors within certain price brackets. Investment in developing and promoting diverse, high-quality product forms is critical.
2.  **Focus on Key Growth Regions:** The **North-East, California, Mid-South, and Great Lakes** regions were identified as high-priority areas with strong market potential and favorable competitive dynamics. Tailored merchandising, localized promotions, and distribution optimization in these regions are likely to yield significant sales growth.
3.  **New Product Opportunity: Plant-Based Bacon:** A significant market gap and high-growth opportunity were identified in the **plant-based bacon** category. The vegan bacon market is projected to grow at a 6% CAGR, and Morning Star's existing bacon product is already ranked 6th in dollar sales, indicating strong, untapped consumer demand. This represents a prime target for Gardein innovation.
4.  **Strategic Price Positioning:** Gardein should strategically align its pricing and unit sizing for maximum competitiveness. The analysis suggests an **average price of $3.75** and an **average unit size of 5.5 Oz** as a competitive sweet spot that balances affordability with perceived value.
5.  **Enhance Flavor & Texture Profiles:** While form is critical, developing flavor and texture profiles that closely mimic traditional meat is crucial for broader consumer adoption, particularly for flexitarians, and for driving repeat purchases. Continuous R&D in this area will reinforce brand loyalty.

<p align="center">
<img src="assets/regional_sales_map.png" width="45%" alt="Regional Sales Analysis">
<img src="assets/price_range_analysis.png" width="45%" alt="Price Point Analysis">
</p>

## 📌 Conclusion

This project successfully transformed raw, proprietary sales data into a strategic growth blueprint for Conagra's 'Gardein' brand within the dynamic meat substitute market. By leveraging robust predictive analytics (OLS regression), we not only quantified the key drivers of sales but also identified a clear, actionable path forward. The comprehensive recommendations, encompassing product innovation (specifically plant-based bacon), targeted regional prioritization, and data-backed strategic pricing, empower Conagra to capture a larger share of this rapidly expanding and lucrative market segment.

## 🛠️ Tools & Technologies Used

  * **Python:** The core programming language for the entire project (version 3.9+).
  * **Pandas:** Essential for high-performance data manipulation, cleaning, filtering, and aggregation of large datasets.
  * **NumPy:** Utilized for efficient numerical operations and foundational data structures supporting Pandas.
  * **Statsmodels:** The primary library used for building, fitting, and evaluating the Ordinary Least Squares (OLS) regression models to understand sales drivers.
  * **Matplotlib / Seaborn:** Employed for generating insightful static and statistical visualizations, crucial for both the Exploratory Data Analysis (EDA) and the final report/presentation.
  * **Jupyter Notebook:** Served as the central environment for interactive data analysis, iterative model development, and presenting findings in a reproducible format.
  * **Microsoft Office (Word/PowerPoint):** Used for compiling the detailed final business report and delivering the strategic presentation.

## 🚀 How to Run This Project

1.  Clone this repository:
    ```sh
    git clone [https://github.com/AmitKPandeyLabs/YOUR_REPO_NAME.git](https://github.com/AmitKPandeyLabs/YOUR_REPO_NAME.git)
    ```
    (Replace `YOUR_REPO_NAME` with the actual name of this repository)
2.  Navigate to the project directory:
    ```sh
    cd YOUR_REPO_NAME
    ```
3.  Install the required dependencies:
    ```sh
    pip install -r requirements.txt
    ```
    *(You will need to create a `requirements.txt` file listing pandas, numpy, statsmodels, matplotlib, seaborn, jupyter, etc.)*
4.  Run the notebook:
      * `jupyter notebook FInalProject.ipynb`
5.  **Important Required Files:**
      * **Dataset:** This project relies entirely on a proprietary dataset (`df_merged2.pickle`) from the Conagra Data Science Competition. This file is not included in the repository and must be acquired separately to run the EDA, build the models, and reproduce the results presented. Please ensure it's placed in the appropriate project directory as referenced in the notebook.

## 📜 License

This project was completed as part of a data science competition. The analysis and code are intended for portfolio and demonstration purposes only. Please note that the dataset utilized (`df_merged2.pickle`) is proprietary to Conagra Brands and is not distributed with this repository.

## ✉️ Contact

  * **Amit K. Pandey**
  * **LinkedIn:** [Your LinkedIn Profile URL] (Add your actual LinkedIn URL here)
