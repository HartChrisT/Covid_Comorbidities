# Covid_Comorbidities

**Selected Topic**

Covid 19

**Why we chose this topic**

By using machine learning, we can identify which factors increase the likelihood of a 'covid' death and predict which target groups will have the highest death rate. 
After identifying the at-risk target groups, we can identify best practices and precautions for their safety.

**Hypothesis**

Hypothesis: Individuals with comorbidities die more from covid than those with no known health issues

**Data source details**

The Data sources used in this project came from the Centers for Disease Control and Prevention(CDC). Since the CDC is the national public health agency of the United States of America, it contains a large amount of research and data on Covid-19 available for the analysis of the project. 

 1. https://data.cdc.gov/Case-Surveillance/COVID-19-Case-Surveillance-Public-Use-Data/vbim-akqf (covid data)
 2. https://www.cdc.gov/nchs/covid19/mortality-overview.htm
 3. https://data.cdc.gov/NCHS/Conditions-Contributing-to-COVID-19-Deaths-by-Stat/hk9y-quqm
 
 **Database Construction**

Our team used the Pandas library to clean and transform the raw data into a usable form for the analysis. We made sure all of the data types were accurate and appropriate. We dropped all null values and unknowns because of the overabundance of data. We then dropped unnecessary columns. That whole process can is shown [here.](https://github.com/jeffblando/Covid_Comorbidities/blob/Databases_CH/Database/ETL_misc/Cleaned_Data_Machine_Learning_Model.ipynb) Once cleaned, we created a [schema/flow chart](https://github.com/jeffblando/Covid_Comorbidities/blob/Databases_CH/Database/SQL%20Schema/Database_schema.png) 
Using QuickDB, the connections and data sets are shown visually, so everything made sense. We imported the clean CSV files into SQL for easy queries and analysis. Once in SQL, we joined census county location and population data with individual covid case data [seen here.](https://github.com/jeffblando/Covid_Comorbidities/tree/main/Database/Database%20Images) The new table was exported to a CSV and used in the machine learning model. We cleaned another dataset that looked at the pre-existing conditions, by condition. Connecting the dataframe in pandas directly to SQL using SQLalchemy, a query was run [as seen here.](https://user-images.githubusercontent.com/92996865/170176033-9de4ee21-3033-4ac3-b7a6-f7f04bb71305.png)

### Exploratory Data Analysis (EDA) ###

After downloading the datasets from the CDC website, they were uploaded to the jupyter notebook. To understand the datasets, we first observed the numbers of rows and columns and the type of variables. Then we cleaned the null values and removed unnecessary columns. Lastly, we identified the important variables by checking the relationships between each variable to limit the potential biases so that the accuracy of the machine learning model was not negatively affected. The EDA process can be seen here in the following file. [EDA](https://github.com/jeffblando/Covid_Comorbidities/blob/d04c7815cedb3adebce8b7e593fd91f68c699cea/EDA.ipynb). As observed in the image below, we can see that our dataset have 446687 rows and ten columns. 
![Size of the dataset](https://github.com/jeffblando/Covid_Comorbidities/blob/80703793b7eacfc69265d47b0eb3c28cc1ad3206/Images/Rows.png)


**Correlation Matrix** 

![corr_Corrl](https://github.com/jeffblando/Covid_Comorbidities/blob/012c567edf282072e0db8709d11a9ed308675826/Images/EDAnew.png)

The image above shows the relationships of the variables in our dataset. We ran a correlation matrix and displayed it as a heatmap to see if there was a linear association between the variables. The correlation coefficient of a -1 indicates a perfect negative linear correlation between two variables, a zero indicates no linear correlation between two variables, and a 1 indicates a perfect positive linear correlation between two variables.
As seen in the matrix, there is a positive relationship between the variables: death and people in the ICU and death and hospitalization. A higher relationship between the age group of 65+ with death is also observed. 

**PairPlot**

![PairPlot](https://github.com/jeffblando/Covid_Comorbidities/blob/4090674325e72191def410d2d0fb7f713a91c433/Images/Pairplot.png)

For the distributions of single variables and relationships between two variables, pair plots were used. Pair Plots are used to identify trends for further analysis. Diagonally, we can see histograms and distributional plots of single variables. These give us an estimate of the marginal distribution of each numerical feature in our dataframe. Other plots show relationships between two variables. Just as observed in our Correlation Matrix, in the scatter plots we can see some relationships between death and people who were in ICU, death and hospitalization, and a higher relationship for the age group of 65+ with death.  



## Machine Learning
To begin our machine learning investigation,we will use a supervised machine model to classify the results within our original dataset into two groups: deaths with comorbidities and deaths without comorbidities. 

There are many rich data sources that we have identified to support our research on this topic. For that reason, we will most likely only include the most complete data, thus eliminating any lines with null values to ensure the highest quality result.

To train the model, we will split the data into testing and training sets and analyze metrics of accuracy, precision, and recall to determine if our model is up to the standards of the test. We are aiming for over 95% accuracy in the preliminary phase and will seek more sophisticated ML modeling techniques if we are unable to achieve this through classification. In addition, we will opt for slightly higher sensitivity versus precision as we are dealing with health-related data that would likely encourage further testing should a positive result be determined.

As we refine our approach, we will delve deeper into the specific comorbidities that influence death rate and make predictions using our modeling techniques. These changes can help predict the likelihood of a covid death and which target groups may have the highest death rates. 


**Preliminary Data Preprocessing** 

Several of the columns in the individualized dataset needed to be converted to numerical columns that the machine learning model could use for its prediction. Other columns that didn't apply like `"case_month", "race", "ethnicity", "case_positive_specimen_interval", "case_onset_interval", "process", "exposure_yn", "current_status"` were dropped before loading into the ML model.


**Feature Engineering, Feature Selection + the Decision Making Process**

The first model that constructed included the highest amount of columns. We wanted to look at the relationship between age, sex, hospitalization status, ICU status, underlying conditions, and how those factors related to death.

After running the preliminary models, we found some inconsistencies with the data, such as ICU coming up as positive and hospitalization remaining negative. We removed these anomalies from the data set before processing. 

The final columns impacted the results per the correlations below:
![enter image description here](https://github.com/jeffblando/Covid_Comorbidities/blob/MachineLearning_KT/Images/FeatureSelection.jpg?raw=true)

**Testing + Training**

We used a 75% 25% split for testing and training To split the model.    

The SMOTEENN method was used to resample the data. Results of this resampling showed no significant improvement. 
![enter image description here](https://github.com/jeffblando/Covid_Comorbidities/blob/MachineLearning_KT/Images/SMOTEENNResample.jpg?raw=true)


**Model Choice, Limitations + Benefits**

The outcomes we were looking to predict required a supervised model for this exercise. We used SK learn, the decision tree classifier, and a confusion matrix to analyze the results. 

The dataset we were using was disproportionate - as (happily)many cases resulted in survivals rather than deaths. We are happy to report on these facts, but it does pose a problem to our modeling as splitting the data could produce varied results.

|Limitations  |Benefits  |
|--|--|
| Biased trees can be created if data is skewed |Reporting is easy to interpret  |
|Prone to overfitting| Ability to validate with statistical tests|



**Model Accuracy**

3rd Segment

![Figure](https://github.com/jeffblando/Covid_Comorbidities/blob/MachineLearning_KT/Images/Confusion%20Matrix%20Figure.jpg?raw=true))

![Resampled](https://github.com/jeffblando/Covid_Comorbidities/blob/MachineLearning_KT/Images/SMOTEENNResampleCM.jpg?raw=true)

![2nd Model, 3rd Segment](https://github.com/jeffblando/Covid_Comorbidities/blob/main/Images/ML%20Results%205.27.jpg?raw=true)

2nd Segment

![Segment 2 Submission](https://github.com/jeffblando/Covid_Comorbidities/blob/MachineLearning_KT/Images/S2%20ML%20Results.jpg?raw=true)



## Visualizations
### Dashboard
Tableau was the primary technology used to create an interactive, visually appealing dashboard. The two main reasons Tableau will be our primary Dashboard technology are Tableau has no row limit & Tableau allows us to avoid static dashboards. No row limit allows us to upload and analyze the millions of rows of data we've gathered, without overly-long processing times. Typically, dashboards are shared through PDFs, making them static from the moment they're sent; however, Tableau allows us to share our dashboards and will automatically update them with any changes. 

[Storyboard](https://public.tableau.com/app/profile/giovanni.bottone/viz/Group2Storyboard/Group2Storyboard?publish=yes)

[Description of Tools & Interractivity](https://docs.google.com/presentation/d/1HLexLPKKv-I4AnZZq3R42-6RtVfnWUKWxupJI4ClcX0/edit#slide=id.p)


**Presentation**

[Analyis of pre-existing disease and death rates](https://docs.google.com/presentation/d/1i8Ry3hVTzgpDNV7zKgqXaR9tYIhOCbXmE6nfHRlGO4E/edit#slide=id.g12dc2ad45a7_0_0)


## Technologies Used:
- SK Learn (Machine Learning Library)
- Pandas & Jupyter Notebook - (Machine Learning/Database)
- SQL (Database)
- Postgres (Database)
- Tableau (Visualization)
