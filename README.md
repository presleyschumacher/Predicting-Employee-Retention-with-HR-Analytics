# Predicting-Employee-Retention-with-HR-Analytics
The capstone project for my master's in data analytics degree.
>Combining 2 datasets from fake companies, the datasets will be combined, cleaned, explored, and trained by 4 classfication models to predict employee turnover and offer solutions for corrective steps in order to reduce turnover and increase employee development.

>The comprehensive report can be found on OverLeaf: [Schumacher_Overleaf_Report](https://www.overleaf.com/read/mfhmvbkvpcjf) 

## Import Packages


## Background

Employe turnover is the percentage of employees who leave an organization and are replaced by new employees. Employees can leave for a wide rane of reasons whether it be involuntary -- budget cuts or due to the restructuring of the organization -- or voluntary -- the employee found a better opportunity or is relocating. It's important for companies to track turnover because it can have significant negative impacts on a company. In 2021 the Work Institute's Report estimated that the cost of turnover for the average U.S. employee is aroung $15,000. Besides it being extremely costly for a company, it can affect the overall goals of the company, leads to lower morale, and results in the loss of fresh ideas, customer relationships, and expertise in specific areas.

## The Project

The main goal:
* Employ and compare 4 machine learning algorithims to identify the group of employees who are at the highest risk of leaving to implement solutions to improve employee satisfaction and enchance the retention rates.

## Process Flow:
![Process_Flow](https://user-images.githubusercontent.com/105391626/233816351-0b1e1d8b-9679-4ca9-940d-158b37ef7494.jpeg)

## The Data: Collecting, Cleaning, Exploring
#### Collecting
IBM Dataset: https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset
People Analytics. Starter Dataset: https://www.stevenshoemaker.me/datasets/starter

The following columns were copied from the IBM dataset into the People Analytics data to create a new dataset:
* Job Satisfaction
* Work Life Balance
* Years Sicne Last Promotion
* Performance

Data was added to the People Analytics datafame to enhance the dataset and explore how variables related to emotions and performance affect retention -- both things that the People Analytics dataset lacked.

#### Cleaning
Several steps were taken to clean the data. A brief process flow is as follows. Each step of the process flow are explained in detail in the full report.

![Cleaning_Process](https://user-images.githubusercontent.com/105391626/233816457-19ed02a5-0b84-41f9-8635-1a7b6359b8c7.jpeg)

The original dataset contained several categorial columns. All categorical columns were converted into numerical values so that the machine learning algorithms could achieve the highest accuracy during training and test. A table was created for these modifications for easy access and clear understanding of these variables throughout the analysis of this project and for future analysis. It is a large table so a PDF link has been included.

[Label Encoding_ Nominal Data.pdf](https://github.com/presleyschumacher/Predicting-Employee-Retention-with-HR-Analytics/files/11302704/Label.Encoding_.Nominal.Data.pdf)

#### Exploring

Using the seaborn package and matplotlib.pyplot charts were created of each feature to get a better understanding of the demographics of the company. 
* In doing so, it was discovered that the majority of the employees are active, male, white, work in the customer service department, and make between $67,799 - $88,267 annually.

Charts were also created of the demographics to compare the active vs inactive employees to get an early understanding of what may cause an employee to leave the company.

The chart below shows us that the analysis for turnover is necessary because turnover has been on the rise year over year.
![hires_terms](https://user-images.githubusercontent.com/105391626/233816843-ddd4468a-ea64-4930-99cc-223c09f48620.jpg)

During the exploratory data analysis process, it was discovered that 85% of the data belongs to active employees while nearly 15% belongs to inactive employees. This indicates that the classification is imbalanced, or has skewed class proportions.

![status](https://user-images.githubusercontent.com/105391626/233817042-657d071b-9319-44a2-ab01-3ce898b9d4cb.jpg)

## Model Training
#### Upsampling

Aiming to balance the distribution of labels, the minority class was upsampled using the resample method from the sklearn.utils library.
* In this project the majority class are the active employees and the miniority class are the inactive employees
* The feature variables were split from the target variable and labeled as X and Y respectively
* The miniority class was then resampled to have the same count as the majority class.
* The majority class wsd combined with the newly upsampled miniority class to create a new dataframe
* A new train and test set was created with the updated, upsampled data.

The upsampled Status Variable:
![status_up](https://user-images.githubusercontent.com/105391626/233817316-963f0e5a-280e-427c-b155-0a604c5c9cfc.jpg)

#### Feature Selection
* Feature selection was used to choose a subset of the features predicted to be the best indicators of our main goal -- predicting turnover -- to improve the clairity of learning results
* The feature selection method used was Fisher's Score
* SelectKBest method was imported from the sklearn.feature_selection library
* Years of Service is estimated to be the best predictor for employee turnover, by far

![Screen Shot 2023-04-22 at 10 06 30 PM](https://user-images.githubusercontent.com/105391626/233817508-f4616133-7f2b-40b5-9776-685e8e888f96.png)

## Model Validation
* 4 machine learning models were deployed and their classification reports and ROC AUC were compared to decide which model performed the best and, therefore, would be applied to determine the probability of turnover.
* The models used were logestic regression, decision tree classifier, random forest, and gaussian nb.
* The classification reports, ROC Curve, and further analysis can be found in the full report. Below is a box and whisker plot of the combined accuracy, precision, recall, and F1 scores to indicate which model performed the best.

![compare_ML](https://user-images.githubusercontent.com/105391626/233817763-34961249-62db-40a5-aa0e-5a2659e05b04.jpg)

* It was determined that Random Forest was the best performing model and would be used to make predictions.

## Model Predictions
* Random Forest was saved as a .pkl file using joblib then loaded and applied to the dataset to generate predicted probabilities of turnover.
* The mean() function was applied to turnover probability to determine the percentage of each attribute in the top 10 features that were identified earlier 
* To provide a high-level summary, the highest-ranking attrbute of the top 5 features were graphed. 
* The position feature had 2 attributes that were tied.

![Screen Shot 2023-04-22 at 10 21 24 PM](https://user-images.githubusercontent.com/105391626/233817953-c8d60e1d-55a0-4602-b4ac-90ac5f392fb8.png)

* Employees within their first year at the company are the most likely to leave. The company may want to re-evaluate its onboarding process to better integrate employees into the culture and provide opportunities for early career development through mentorship programs.

## Limitations
* The dataset lacked diversity  and representation which may have resulted in sampling bias skewing results
* The data may also lack in reliability and validity because it was composed of 2 fake datasets. Because of this, the findings may not be applicable to real-world scenarios.

#### Despite the limitations, the analysis still shows the importance of tracking and analyzing retention data in a company. This study  highlights the ways that machine learning algorithms can be used and serves as a valuable tool for HR departments and organizations looking to address employee turnover.
