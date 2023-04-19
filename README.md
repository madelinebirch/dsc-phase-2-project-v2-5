# Phase 2 Project: Multiple Linear Regression 

### Model-informed recommendations for real estate

![Long and Foster](Images/Long_and_Foster.png)


## Business Understanding

Real estate company Long and Foster has expanded their operations to King County, Washington, and is interested in developing a predictive model that can estimate the sale price of a house. Being new to the area, they are not familiar with the housing landscape and need to better understand their market. By analyzing various factors such as the number of bedrooms, bathrooms, square footage of the house, location, and other important features, L&F aim to provide more accurate home sale price estimates to their clients and improve their business efficiency.

The modeling process will also help Long and Foster identify potential investment opportunities in the county by analyzing which features have the most significant impact on the sale price of a house. By using the results of the analysis, the company can make better decisions regarding their investments in the county.

The objective of this project is to create a multiple linear regression model that can predict the sale price of a house based on predictive factors and provide insights that can help Long and Foster improve their business operations.

## Data Understanding

For this project, we are using 'kc_house_data.csv', a public, tabular dataset lifted from from King County, WA's website (kingcounty.gov).

Our target variable is 'price', which records final sale price of King County homes. Columns serve as features (predictors) in this dataset. The dataset has been updated to include homes sold up until the year 2022.

### Summary of exploratory data analysis

There are 30,155 observations and 25 features in the dataset.

Numeric predictors are: 'id' (recordor observation number), 'date' (date sold), 'bedrooms' (no. bedrooms), 'bathrooms' (no. bathrooms), 'sqft_above'(square footage of home apart from basement), 'sqft_living'(square footage of living space in the home),'sqft_lot'(square footage of lot), 'sqft_garage'(square footage of garage), 'sqft_patio(square footage of outdoor patio),'floors'(number of floors, including levels, in the home), 'yr_built'(year home was built), 'yr_renovated'(if and when home was renovated), 'lat'(latitude coordinate), and 'long'(longitude coordinate).

Categorical predictors are: 'waterfront'(whether or not home is on a waterfront, eg. Puget Sound, Lake Washington, etc.), 'greenbelt'(whether or not home is near or adjacent to a green belt or natural land),'nuisance'(whether or not the home is near an airport, heavy traffic, or other notable nuisances), 'view'(quality of both nature and city views from the home), 'condition'(overall codified condition of the house as defined by (https://info.kingcounty.gov/assessor/esales/Glossary.aspx?type=r), 'grade'(overall grade of the house pertaining to construction and design), 'heat_source'(heat source type), and 'sewer_system'(sewer system type).

There are 32 null values in feature 'heat_source' and 14 in 'sewer_system'.

Target 'price' is fairly skewed.

![Raw Distribution of Price](Images/raw_dist_of_price.png)


## Data Preparation

### Identifying correlated features 

##### Heatmap of correlated variables

![Correlation Matrix](Images/Corr_Matrix.png)


##### Correlation matrix with respect to 'price'

![Correlation Matrix](Images/corr_with_price.png)

### Baseline model results:

Using the raw data from target 'price' and selected feature 'sqft_living', we create a simple baseline model.

The model's F-statistic is 17926.67, which indicates that the model is significant and that at least one of the predictor variables is useful for predicting the target variable (price). The p-value of 0.0 indicates that the model is statistically significant and that there is strong evidence that at least one of the predictors is related to the target variable.

The R-squared value of 0.3804 indicates that the model explains about 38% of the variance in the target variable. This means that there is still a lot of unexplained variation in the target variable that is not accounted for by the predictor variable (sqft_living).

The regression coefficient for sqft_living is 565.41, which means that for each additional square foot of living space, the sale price of the home increases by $565.41. The constant term of -92223.53 represents the estimated value of the target variable when the predictor variable is zero (i.e., when the living space is zero). However, this interpretation is not meaningful in this case since it is impossible for a home to have zero living space.

![Baseline QQ Plot](Images/qqplot_baseline_model.png)

