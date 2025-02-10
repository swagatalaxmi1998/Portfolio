# Overview
This project analyzes and predicts laptop prices using machine learning techniques. The dataset contains various specifications of laptops, such as screen size, RAM, weight, processor type, and more. The workflow is divided into three main sections:

* Data Cleaning
* Exploratory Data Analysis (EDA)
* Model Development

Loaded the dataset using `pd.read_csv(filepath, header=0)`.
Displayed the dataset's structure using `.info()` and .`head()`.

## Data cleaning
In this section, I have cleaned and preprocessed the dataset to prepare it for analysis. Data cleaning is used to convert data from an initial format to a format that may be better for analysis. In this analysis I have cleaned the raw data using python code in [Google collab](https://colab.research.google.com) platform. 

### Handling Missing Data
 * Identified missing values using `.isnull()`.
 * Calculated mean for missing values in the `Weight_kg` column using `.mean()`.
 * Filled missing `Weight_kg` values with the column's mean using `.replace(np.nan, avg_weight, inplace=True)`.
 * Replaced `Screen_Size_inch` parameter using `.idmax()`. 
 * Dropped irrelevant or highly missing columns using `.drop(columns=['Unnamed: 0'], inplace=True)`.
 * Changed "Weight_kg" and "Screen_Size_cm" data type from "Object" to "float" using `.astype("float")`.

### Normalization 🔧
"CPU_frequency" column in the dataset by dividing each value by the maximum value in that column using `df['CPU_frequency'] / df['CPU_frequency'].max()`.
Since CPU frequency can have a wide range (e.g., 1.2 GHz to 5.0 GHz), normalizing ensures that no single large value dominates the dataset.

### Feature Engineering
* Rounded the `Screen_Size_cm` column values to two decimal places using `np.round()`.
* Dummy variables were created using `pd.get_dummies` to label categories or categorical variables. This step of converting categorical to numerical variables will help in further regression analysis.

## Exploratory data analysis (EDA)
This phase involves understanding the dataset through statistical analysis and visualization using `seaborn`. After cleaning of data further naalysis was performed.

### Regression plot using `sns.regplot`
All the **continuous** parameters:`CPU_frequency`, `Screen_Size_inch` and `Weight_pounds` have been visualized using regression plot against `Price`. 
### Box plot using `sns.boxplot`
Similarly, **categorical** features: `Category`, `GPU`, `OS`, `CPU_core`, `RAM_GB`, `Storage_GB_SSD` have been visualized using box plots.
### Pivot Table Analysis  
Parameters `GPU`, `CPU_core`, and `Price` are grouped to make a pivot table and visualized using the `pcolor` plot.  
### Correlation Analysis  
- Calculated **Pearson Coefficient** and **p-values** for each parameter.  
- Identified the strongest factors influencing `Price`.  
- Analyzed the correlation strength of each feature.

### Results

- Comparison of correlation for these features against Price shows that `CPU_frequency` has a 36% positive correlation with the price of the laptops. 
- Increasing `CPU_core` (`3 → 5 → 7`) **raises price** across all `GPU` levels.  
- Higher `GPU` levels (`1 → 2 → 3`) **increase price**.  
- **High-end `GPU` + high `CPU_core` = highest cost**.
  
- Strongest positive correlations:  
  - `RAM` (**0.549**)  
  - `CPU_core` (**0.459**)  
  - `CPU_frequency` (**0.367**)  

## Model Development

### Techniques used 🧰
- Cross-validation
- Ridge Regression
- Grid search using `GridSearchCV`
- Standardized features using `StandardScaler().fit_transform(df[['RAM_Size', 'Weight_kg']]`
- 
### Simple linear regression
`CPU_frequency` was identified as the feature with the **lowest p-value**. A **simple linear regression** model was built using `LinearRegression().fit(X_train, y_train)` for `CPU_frequency` as the sole predictor.  

### Ridge regression 
- To improve predictive accuracy, a regression using multiple variables was then performed by incorporating: `RAM_GB`, `Storage_GB_SSD`, `CPU_core`, `OS`, `GPU`, and `Category` using `Ridge(alpha=1.0).fit(X_train, y_train)`.  
- Different values of `hyperparameter` alpha (0.001 to 1) to evaluate the model’s performance on training and test data.

### GridSearchCV
- Tested six different `alpha` values to find the optimal one.
- Best Ridge Regression model `BestRR` from a GridSearchCV `Grid1` process.

### Results
- `R²` score: **0.1344** → Only **13.44% of the variance** in `Price` is explained by `CPU_frequency`: only `CPU_frequency` is insufficient to predict `Price` accurately.
- Train Score (0.634) > Test Score (0.371) → Indicating overfitting at lower alpha values.
- Using `GridSearch`, the best alpha value explains 24.48% of the variance in `Price` using the selected features.

## Conslusion
This project demonstrates how regression models help analyze features like `RAM_GB`, `CPU_core`, and `Storage_GB_SSD` that influence laptop prices. While single-variable models were insufficient, multiple regression improved accuracy, demonstrating machine learning’s ability to handle complex data and optimize predictions. Further refinements could include advanced algorithms, incorporating additional features to improve model interpretability
