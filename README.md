# *Diabetes Prediction Data Analysis* 
![WhatsApp Image 2025-03-18 at 18 12 35_7ce44ea3](https://github.com/user-attachments/assets/3629ad38-ef9c-4cf2-835a-5eeb1811fe4c)


## *Introduction*  
Diabetes is a chronic health condition affecting millions worldwide. Understanding its risk factors can help in early detection and prevention. This project analyzes a diabetes dataset to explore the relationships between various health indicators and diabetes outcomes. The analysis includes data cleaning, exploratory data analysis (EDA), and visualizations to uncover key insights.

## *Dataset*  
The dataset used in this analysis contains health-related attributes such as:  

- *Pregnancies* – Number of times a patient has been pregnant  
- *Glucose* – Blood glucose concentration (mg/dL)  
- *Blood Pressure* – Diastolic blood pressure (mm Hg)  
- *Skin Thickness* – Triceps skin fold thickness (mm)  
- *Insulin* – Serum insulin level (μU/ml)  
- *BMI* – Body mass index (kg/m²)  
- *Diabetes Pedigree Function* – A function that scores the likelihood of diabetes based on family history  
- *Age* – Age of the patient  
- *Outcome* – 0 (No diabetes) or 1 (Diabetes present)  

The dataset is sourced from the [Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database).

---

## *Data Cleaning Steps*  
To ensure data quality and accuracy, the following preprocessing steps were performed:  

1. *Handling Missing Values*  
   - Checked for missing or incorrect values (e.g., zero values in glucose, blood pressure, skin thickness, insulin, and BMI).  
   - Replaced zeros with NaN where a zero was not a valid value.  
   - Filled missing values using the median of respective columns.  

2. *Checking for Duplicates*  
   - Verified if any duplicate rows existed and removed them if necessary.  

3. *Feature Scaling & Encoding*  
   - Standardized numerical features where necessary to improve analysis and visualization.



## *Snapshot of the Cleaned Data*  
Below is a preview of the cleaned dataset 
![WhatsApp Image 2025-03-18 at 11 14 32_0777def2](https://github.com/user-attachments/assets/99d1918e-5560-4490-9a59-0b9384a35d5a)


## *Exploratory Data Analysis (EDA)*  
We used different visualizations to understand the dataset better:  

### *1. Distributions to Represent Dataset*  
- *Histogram:* Shows the distribution of numerical features.
- ![image](https://github.com/user-attachments/assets/cc737d6f-6150-4bf4-8a40-a8f5fa93c03e)
- Each histogram shows the distribution of values for a specific feature in the diabetes dataset. Here’s what they reveal:



*Glucose Distribution*
	•	The histogram likely shows a right-skewed distribution (more values on the lower end).
	•	Higher glucose levels are seen in some individuals, which suggests that some have diabetes.
	•	The peak around 100 mg/dL likely represents normal fasting glucose levels.

🔎 Insight: People with higher glucose levels are more likely to have diabetes.



*Blood Pressure Distribution*
	•	Likely bell-shaped (normal distribution) around 70–80 mmHg.
	•	Some individuals have very low values, which might be due to missing values imputed earlier.

🔎 Insight: Blood pressure is generally balanced, but extremely low values might need further investigation.



*BMI (Body Mass Index) Distribution*
	•	Typically right-skewed, meaning higher BMI values are more frequent.
	•	A significant portion of individuals have a BMI > 25, which is considered overweight/obese.

🔎 Insight: Higher BMI is a risk factor for diabetes.



*Age Distribution*
	•	Likely right-skewed, meaning most people in the dataset are younger.
	•	The dataset includes a wide range of ages, but more people are between 20–50 years old.

🔎 Insight: Diabetes affects people of all ages, but older individuals are more at risk.



* Insulin Distribution*
	•	This histogram often shows a peak near zero due to missing/imputed values.
	•	Some individuals have extremely high insulin levels, indicating insulin resistance.

🔎 Insight: Insulin levels are inconsistent. More analysis is needed to determine its role in diabetes risk.



*Skin Thickness Distribution*
	•	Likely right-skewed, meaning most people have lower skin thickness values.
	•	Some individuals have very high values, possibly indicating obesity-related factors.

🔎 Insight: Skin thickness may correlate with BMI and fat distribution, which impacts diabetes risk.
Overall Interpretation:
	•	Glucose and BMI are key factors in diabetes risk.
	•	Older individuals and those with high insulin levels are more likely to be diabetic.
	•	Blood pressure and skin thickness vary, but they might contribute indirectly.
  
- *Pairplot:* Displays scatter plots of numerical features categorized by diabetes outcome.
- ![image](https://github.com/user-attachments/assets/513c5387-fabc-465b-88bd-79233455bed8)
- The pairplot is a powerful visualization that shows the relationships between numerical features in your dataset while coloring data points based on the Outcome (Diabetes = 1, No Diabetes = 0).



What Each Part of the Pairplot Means:
	1.	Scatter Plots (Lower Triangle)
	•	Each scatter plot shows how two features relate to each other.
	•	If there’s a clear separation between the two classes (diabetic vs. non-diabetic), it means the feature combination is useful for prediction.
	•	Example: A strong trend between Glucose and Outcome means glucose is an important diabetes indicator.
	2.	KDE (Kernel Density Estimate) Diagonal Plots
	•	The diagonal shows KDE plots, which are smooth versions of histograms for individual features.
	•	The difference in KDE peaks between diabetic (1) and non-diabetic (0) groups shows how well that feature separates the two classes.
	•	Example: If diabetics have a higher glucose peak than non-diabetics, glucose is a strong predictor.
	3.	Corner=True
	•	This removes duplicate scatter plots, making the visualization cleaner.



Key Insights from the Pairplot

🔹 Glucose vs. Outcome
	•	If diabetic cases (red/orange) cluster at higher glucose levels, then glucose is a strong indicator of diabetes.

🔹 BMI vs. Outcome
	•	If diabetics generally have a higher BMI, it suggests that obesity is a risk factor for diabetes.

🔹 Age vs. Outcome
	•	If diabetics tend to be older, then age may be a contributing factor.

🔹 Glucose vs. BMI, Insulin vs. BMI, etc.
	•	If these pairs show a clear pattern or trend, it means these features are interrelated in determining diabetes risk.



Final Interpretation:
	•	Features like Glucose, BMI, and Age likely show clear differences between diabetic and non-diabetic individuals.
	•	If clusters overlap heavily (e.g., for Blood Pressure), that feature may not be a strong predictor.
	•	The pairplot helps visually confirm which features are most useful for detecting diabetes

- *Boxplot:*  
  - Compares feature distributions.
  - ![image](https://github.com/user-attachments/assets/728046c0-9bde-4184-b41a-e051b8897845)
  - Interpreting the Boxplot: “Glucose Levels by Diabetes Outcome”

This boxplot compares glucose levels between individuals with diabetes (Outcome = 1) and those without diabetes (Outcome = 0).



What the Boxplot Reveals:

1. Median Glucose Level (Middle Line in the Box)
	•	If the median glucose level for Outcome = 1 (diabetic) is significantly higher than for Outcome = 0 (non-diabetic), it confirms that higher glucose levels are associated with diabetes.
	•	Typically, diabetics have a median glucose level well above 126 mg/dL, which is the medical threshold for diabetes.

2. Interquartile Range (IQR - The Box)
	•	The box represents the middle 50% of glucose values in each group.
	•	If the diabetic group (Outcome = 1) has a higher and more spread-out IQR, it suggests that diabetics have more variation in glucose levels.

3. Whiskers (Lines Extending from the Box)
	•	The whiskers show how widely glucose levels vary.
	•	If the diabetic group has a wider range and extends much higher, it means some diabetics have extremely high glucose levels.
	•	The non-diabetic group (Outcome = 0) will likely have a narrower range, mostly below 126 mg/dL.

4. Outliers (Dots Outside the Whiskers)
	•	Outliers represent individuals with exceptionally high glucose levels.
	•	If there are many outliers in the diabetic group, it shows that some diabetics have extreme hyperglycemia.



Key Insights from the Plot:

✅ Diabetics (Outcome = 1) have significantly higher glucose levels on average than non-diabetics (Outcome = 0).
✅ The box for diabetics is shifted higher, meaning that most people with diabetes have glucose levels above normal thresholds.
✅ If there is little overlap between the two groups, glucose is a strong predictor of diabetes.
 
  
  - Analyzes the impact of BMI on diabetes risk.
  - ![image](https://github.com/user-attachments/assets/81a7ecd7-fa22-41a9-a0df-33ad20765467)
  - nterpreting the Boxplot: “BMI Distribution by Diabetes Outcome”

The boxplot you created compares BMI levels between diabetic (Outcome = 1) and non-diabetic (Outcome = 0) individuals.



What the Boxplot Shows:
	1.	Median (Middle Line in the Box):
	•	Shows the average BMI for each group.
	•	If the median BMI for diabetics (Outcome = 1) is higher than for non-diabetics (Outcome = 0), it suggests that higher BMI is linked to diabetes.
	2.	Interquartile Range (IQR) - The Box:
	•	The box represents the middle 50% of BMI values for each group.
	•	If the diabetic group’s IQR is higher and shifted right, it means most diabetics have a higher BMI range.
	3.	Whiskers (Lines Extending from Box):
	•	These show the spread of BMI values in each group.
	•	Longer whiskers indicate greater variability in BMI.
	4.	Outliers (Dots Outside the Whiskers):
	•	Any dots outside the whiskers represent unusually high or low BMI values.
	•	If many high BMI outliers are in the diabetic group, it suggests that obesity plays a role in diabetes risk.



Key Insights from the Plot:

📌 Higher BMI is likely linked to diabetes if the diabetic group has a higher median and IQR than the non-diabetic group.
📌 If the distributions overlap a lot, BMI alone may not be enough to predict diabetes but still contributes.
📌 Outliers (extremely high BMI values) in the diabetic group might suggest that obesity is a major risk factor.

Would you like me to generate this boxplot using your data and interpret the actual results? 🚀

- *Countplot:* Shows the number of people with and without diabetes.
- ![image](https://github.com/user-attachments/assets/1da66604-3513-442e-866e-a3394fcef117)
- Interpreting the Countplot: “Diabetes Cases Distribution”

This countplot shows the number of individuals in each category of Outcome:
	•	0 (“No Diabetes”) – Individuals without diabetes (Green).
	•	1 (“Diabetes”) – Individuals with diabetes (Red).



What the Countplot Reveals:
	1.	Class Imbalance
	•	If the bars are unequal in height, there is a difference in the number of diabetic vs. non-diabetic cases.
	•	If the “No Diabetes” bar is much taller, then the dataset contains more non-diabetic individuals than diabetics.
	•	If the bars are balanced, then the dataset has a nearly equal number of diabetic and non-diabetic cases.
	2.	Potential Bias in Data
	•	If the dataset is heavily skewed towards one class (e.g., far more non-diabetic cases), machine learning models trained on this data may struggle to predict diabetes correctly.
	•	Solution: If the imbalance is too large, techniques like oversampling, undersampling, or weighting can be used to improve predictive accuracy.
	3.	Dataset Representativeness
	•	If the diabetic group is too small, it might not represent real-world diabetes cases accurately.
	•	A more balanced dataset is generally better for predictive modeling.



Key Insights from the Plot:

📌 If more people are non-diabetic, the dataset may be imbalanced, affecting model predictions.
📌 If both bars are similar in height, it means we have a well-distributed dataset.
📌 Diabetes cases are lower in number (in most datasets), but still significant.

- *Violin Plot:* Displays the distribution of age by diabetes outcome.
- ![image](https://github.com/user-attachments/assets/af6cb63f-2a41-4b7c-9519-a76713c551ee)
- This violin plot shows how age is distributed for people with and without diabetes (Outcome). It combines aspects of a boxplot and a KDE (Kernel Density Estimation) plot, making it useful for spotting differences in distribution.



Key Elements of the Violin Plot:
	1.	Shape & Width (Density Estimation)
	•	The wider sections show where most data points are concentrated.
	•	If the diabetic group (Outcome = 1) is wider at older ages, it means diabetes is more common in older individuals.
	2.	Median & Quartiles (Inner Quartile Lines)
	•	The inner white lines show the median and quartiles (like a boxplot).
	•	If the median age for diabetics is higher than for non-diabetics, it suggests that diabetes is more common among older individuals.
	3.	Split=True (Comparison Between Groups)
	•	The plot is split into two mirrored distributions for Outcome = 0 (non-diabetic) and Outcome = 1 (diabetic).
	•	If the diabetic distribution is more concentrated at older ages, it confirms that age is a significant factor in diabetes risk.



What This Plot Likely Shows:

✅ Diabetes is more common in older individuals (if the diabetic side is wider at older ages).
✅ The median age for diabetics may be higher than for non-diabetics.
✅ Younger individuals have lower diabetes risk (if the non-diabetic group is wider at younger ages).



Final Insights:

📌 If the diabetic group’s distribution shifts toward older ages, age is a significant risk factor for diabetes.
📌 If both groups have similar distributions, age alone may not be a strong indicator.
📌 If there are outliers (long tails), it means some young individuals also develop diabetes, though it’s less common.

- *Heatmap:* Shows correlations between features.
- ![image](https://github.com/user-attachments/assets/20092b42-7d78-437f-9e72-1514a14e3804)
- This heatmap visualizes the correlation between different features in your dataset. Correlation measures how strongly two variables are related (from -1 to +1):
	•	+1 → Strong positive correlation (When one increases, the other increases).
	•	0 → No correlation (No relationship between variables).
	•	-1 → Strong negative correlation (When one increases, the other decreases).

The annot=True parameter ensures that the correlation values are displayed inside the heatmap.



Key Things to Look for in the Heatmap:

1. High Positive Correlations (Closer to +1)

🔹 Glucose vs. Outcome → Likely high correlation (diabetics tend to have higher glucose levels).
🔹 BMI vs. Outcome → If BMI is positively correlated, it suggests that obesity is a risk factor for diabetes.
🔹 Age vs. Outcome → If age has a moderate correlation, older individuals are more likely to have diabetes.

2. High Negative Correlations (Closer to -1)

🔹 If any feature has a strong negative correlation with Outcome, it means that higher values of that feature decrease diabetes risk (rare in medical datasets like this).

3. Strong Feature Relationships (Non-Outcome Correlations)

🔹 Glucose & Insulin → A strong positive correlation suggests that higher glucose levels lead to increased insulin production.
🔹 BMI & Skin Thickness → If positively correlated, it suggests that individuals with higher BMI also have higher skin thickness measurements.
🔹 Blood Pressure & Age → Older individuals typically have higher blood pressure.



Final Insights:

📌 Glucose is likely the strongest predictor of diabetes (Outcome).
📌 BMI and Age might also be significant predictors.
📌 Some features (like Blood Pressure) may have weak or no correlation with diabetes.
📌 If two features are highly correlated (e.g., Insulin & Glucose), one might be redundant in modeling.
  

### *2. Insights from EDA*  
- *Glucose Levels and Diabetes:* Higher glucose levels are strongly associated with diabetes.  
- *BMI Impact:* Individuals with a higher BMI tend to have a higher risk of diabetes.  
- *Age Factor:* Older individuals have a higher probability of being diagnosed with diabetes.  
- *Feature Correlations:*  
  - Glucose has the highest correlation with diabetes.  
  - BMI and age also play significant roles in predicting diabetes risk.  

## *Conclusion*  
After performing Exploratory Data Analysis (EDA) on the diabetes dataset, we observed key patterns and relationships between various health indicators and diabetes risk:

1️⃣ Glucose levels have the strongest correlation with diabetes, confirming that high glucose is a major risk factor.
2️⃣ BMI and Age also show a positive relationship with diabetes, indicating that obesity and older age increase diabetes risk.
3️⃣ The heatmap revealed strong relationships between some features, such as Glucose & Insulin, suggesting potential redundancies in predictive modeling.
4️⃣ The boxplots and violin plots showed clear differences in feature distributions between diabetic and non-diabetic individuals, particularly in Glucose and BMI.
5️⃣ The countplot highlighted a class imbalance, with fewer diabetic cases than non-diabetic cases, which is important to consider when building predictive models.

🛠 Next Steps:

✅ Handle missing data properly to improve model performance.
✅ Balance the dataset (if needed) to ensure fair model predictions.
✅ Build and test machine learning models to predict diabetes based on these insights.

## *Recommendations*  
- *Medical Monitoring:* Regular health check-ups, focusing on glucose and BMI.  
- *Diet and Exercise:* Promoting healthy eating habits and physical activity.  
- *Further Research:* Using machine learning models to enhance prediction accuracy.  
This is just an example of how your recommendations will look like
