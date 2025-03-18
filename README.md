# Bangalore House Price Analysis

### Table of Contents
-	[Project Overview](#project-overview)
-	[Data Source](#data-source)
-	[Tools](#tools)
-	[Data Preprocessing](#data-preprocessing)
-	[Tasks](#tasks)
-	[Insights](#insights)

### Project Overview

This project analyzes property prices in Bangalore using Exploratory Data Analysis (EDA) and outlier detection techniques. 
The focus is on examining price per square foot and applying various statistical methods to clean the data.
  
### Data Source
File: house_price.csv
Target Column: price_per_sqft

### Tools
The analysis was conducted using Python 3.x [Download here](#http://python.org/)
with the following libraries: 

-     Pandas
       
  - Installation: ‘pip install pandas’.
    
-	    NumPy
  
  - Installation:  ‘pip install numpy’.
    
-	   Matplotlib
  
  - Installation:  ‘pip install matplotlib’.
    
-	   Seaborn
  
  - Installation: ‘pip install seaborn’.

-   from scipy.stats import zscore,skew,normaltest

     - import multiple statistical functions from scipy.stats

### Data Preprocessing
In the initial data preparation, the following tasks were performed:
1. Loading data and inspecting the dataset.
2. Checking basic information (column types, number of rows, missing values, etc.).
3. Checking null values
4. Handling missing values.
5. Checking duplicate rows.
6. Datatype conversion.
7. Dropped unnecessary column size.
 

### Tasks
This step involved exploring data to answer the key questions such as:

#### Question 1: Exploratory Data Analysis (EDA)
            Steps Taken:
            -Checked data types, missing values, and duplicates.
            -Performed summary statistics to understand the data distribution.
            -Dropped unnecessary columns (e.g., size).
    
            Inference:
            -The dataset had no major missing values.
            -Extreme values were detected.

#### Question 2: Outlier Detection & Handling 
             Detect and remove outliers using:
            (a) Mean & Standard Deviation
            (b) Percentile Method
            (c) IQR (Interquartile Range)
            (d) Z-Score Method
            Handling Methods: Trimming, Capping, Imputation (Mean/Median)
            
            Steps Taken:
            Detected outliers using:
            -Mean & Standard Deviation
            -Percentile Method
            -IQR (Interquartile Range)
            -Z-Score Method
            Applied outlier handling techniques: trimming, capping, and imputation.
    
            Inference:
            (a) Mean & Standard Deviation:
            -Mean dropped from 8,132.64 to 6,821.89, showing that high outliers made the original 
             average higher .
            -Standard deviation decreased significantly from 111,232.90 to 4,988.48, meaning extreme 
             values were affecting the data.
            -Max value is still high (200,000) even after filtering, so the 3-sigma method didn’t remove 
             all outliers.
            -Lower bound came out negative (-325,566.06), which doesn’t make sense since prices can’t be negative.
     
            (b) Percentile Method:
            -Mean dropped from 8,132.64 to 6,551.17, showing that high outliers made the original average higher .
            -Standard deviation reduced significantly from 111,232.90 to 3278.24, 
            -Max value reduced from 12,000,000 to 15,600, meaning the 95th percentile filtering removed extreme outliers.
            -Min value increased from 267 to 3,150, so very low outliers were also removed.

            (c) IQR (Interquartile Range):
            -Mean dropped from 8,132.64 to 5,662.48, showing that high outliers made the original average higher .
            -Standard deviation reduced significantly from 111,232.90 to 1946.40, showing that extreme values were 
             affecting the data spread.
            -Max value decreased from 12,000,000 to 12,173, meaning the IQR method effectively removed extreme outliers.
            -Min value 267 remained unchanged, indicating that very low values were not considered outliers by this method.
            -Lower bound came out negative (-411.5), which isn't practical for price data, though no negative values exist 
             in the filtered data.
  
            (d) Z-Score Method:  
            -Mean dropped from 8,132.64 to 6,959.74, showing that extreme values were affecting the data spread.
            -Standard deviation reduced significantly from 111,232.90 to 8428.60, showing that extreme values were affecting 
             the data spread.
            -Max value decreased from 12,000,000 to 341831, so the Z-score method removed extreme outliers but still retained 
             some high values.
            -Min value (267) remained unchanged, meaning very low values were not considered outliers by this method.
       
 #### Question 3: Box Plot Analysis
            (a)Visualize outliers using a box plot.
            (b)Determine which method best removes outliers.
           
            Steps Taken:
            -Created box plots before and after outlier handling to visualize their impact.
            
            Inference:
           -IQR Method is the best choices for handling outliers.
           -It effectively removed extreme outliers, reducing max value from 12,000,000 to 15,600, making the dataset more realistic.
           -The mean (average) became more balanced, avoiding the skew caused by extreme values.
           -It kept 90% of the data intact, ensuring no major data loss.
 
#### Question 4: Normality Test & Transformation
            (a)Draw a histplot to check normality.
            (b)Check Skewness & Kurtosis before/after transformation.
            (c)Applying log transformations 

            Steps Taken:
            -Plotted histplot to check normality.
            -Measured Skewness & Kurtosis before and after transformation.
            -Applied log transformation to make the data more normally distributed.
  
             Inference:
             -The log transformation significantly reduces skewness and kurtosis, making the data closer to normal distribution.

#### Question 5: Correlation & Heatmap 
            (a)Compute correlation between numerical columns.
            (b)Plot a heatmap to visualize relationships.
   
            Steps Taken:
            -Computed correlation matrix for numerical columns.
            -Plotted a heatmap to visualize relationships.
   
            Inference:
            -Some features had strong positive/negative correlations, indicating multicollinearity.
            -Price per square foot showed weak correlation with some variables, suggesting external factors influence pricing.
   
#### Question 6: Scatter Plot Analysis 
           (a)Draw scatter plots between numerical variables.
           (b)Identify trends & relationships.
           
            Steps Taken:
            -Plotted scatter plots between numerical variables.
            -Identified trends and relationships visually.
            
            Inference:
            -Some variables had strong linear relationships, confirming findings from the correlation heatmap.


### Insights
#### Best Outlier Handling Method:
     - Based on skewness and normality tests, the IQR Method was the most effective because the data was not normally distributed.
     - It effectively removed extreme outliers, reducing max value from 12,000,000 to 15,600, making the dataset more realistic.
     - The mean (average) became more balanced, avoiding the skew caused by extreme values.
     - It kept 90% of the data intact, ensuring no major data loss.
     
#### Correlation Analysis:
     Some features showed strong positive/negative correlations, as visualized in the heatmap.
    
#### Normality Transformation:
     Log transformation improved skewness and kurtosis, making the distribution closer to normal.
