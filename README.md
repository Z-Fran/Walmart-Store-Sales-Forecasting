# Walmart-Store-Sales-Forecasting

## Part 1 Analysis and Preprocessing

### 1. Fina all variables
- Merge three dataframes into one by matching store id.

### 2. Clean data
- Deal with missing values
  - **Filling missing values** of markdowns with 0 is better than deleting them.
  - `0` is meaningful because it can presents there is no markdown on that date.

- Deal with outliers
  - Find outliers by **Boxplot** and **IQR** method.
  - Deal with outliers of unemployment by replacing with nearest values.

### 3. Feature Engineering
- Map `Type` and `IsHoiday` to numeric features.
- Split Date into Year, Month and Day so that it will be numeric.
- Use Dept and Size **create new meaningful features** according to correlation anlysis:
  - `Dept_num`: departments quantity of a store may affects sales.
  - `Size_per_dept`: average size of departments of a store may affects sales.

### 4. EDA with Visulization with Power BI
- Use pie charts to visualize the proportion of each Type, Year, Month, and IsHoliday.
    - the distribution of Year and Month are balanced
    - the distribution of Type and IsHoliday is not balanced, which may affect the model performance.
- Visualize sales varying with dates of a specific Dept of a specific Store by filtter of Power BI.
    - sales data has a contrary relationship with temperature.
    - sales data has not obvious relationship with fuel prices and unemployment.

### 5. Correlation analysis
-  Size(0.24), Dept(0.15) and Type(-0.18) have stonger correation with Weekly_Sales.
-  New feature Dept_num(0.16) and Size_per_dept (0.24) have stonger correation with Weekly_Sales.
-  The data of `Type=0` and `Type=1` are similar, but they are different from `Type=2`. We can try reclassifying them into two types. 

## Part 2 Training and Evaluation

### 1. Split dataset
- Use high correlation columns in part 1 correlation analysis
- Fix zero values of Weekly_Sales.
- Split dataset acoording to date. train:test = 4:1.
  
### 2. Train and Test models
- Train LinearRegression, KNN, RandomForest, and get scores on test dataset.

### 3. Evalution
- Compare MAE, MAPE, RMSE, R2 metrics.
  - Performance of KNN and RandomForest are similar and they are vey higher than LinearRegresiion

### 4. Emsemble Learning
- Use KNN and RandomForest to build a VotingRegressor which has a better Performance.

### 5. Visualize predicted data
- Using all columns to train have a better curve fitting
