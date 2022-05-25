# Covid_Comorbidities

**Selected Topic**

Covid 19

**Why we chose this topic**

By using machine learning, we can identify which factors increase the likelihood of a 'covid' death and predict which target groups will have the highest death rate. 
After identifying the at-risk target groups, we can identify best practices and precautions for their safety.

**Hypothesis**

Hypothesis: Individuals with comorbidities die more from covid than those with no known health issues

**Data source details**

The Data sources used in this project are acquired from the Centers for Disease Control and Prevention(CDC). Since CDC is the national public health agency of the United States it contains a large amount of research and data on Covid-19 available for the analysis of the project. 

 1. https://data.cdc.gov/Case-Surveillance/COVID-19-Case-Surveillance-Public-Use-Data/vbim-akqf (covid data)
 2. https://www.cdc.gov/nchs/covid19/mortality-overview.htm
 3. https://data.cdc.gov/NCHS/Conditions-Contributing-to-COVID-19-Deaths-by-Stat/hk9y-quqm
 
 **Database Construction**

  Our team used the Pandas library to clean and transform the raw data into a usable form for the analysis. We made sure all of the data types are accurate and appropriate. We dropped all null values, and unknowns because of the overabundance of data, and then dropped unnecessary columns. That whole process can be seen [here.](https://github.com/jeffblando/Covid_Comorbidities/blob/Databases_CH/Database/ETL_misc/Cleaned_Data_Machine_Learning_Model.ipynb) Once cleaned, we created a [schema/flow chart](https://github.com/jeffblando/Covid_Comorbidities/blob/Databases_CH/Database/SQL%20Schema/Database_schema.png) using QuickDB to see the connections and data sets visually so everything made sense. We imported the clean CSV files into SQL for easy queries and analysis. Once in SQL, we joined census county location and population data with individual covid case data [seen here.](https://github.com/jeffblando/Covid_Comorbidities/tree/main/Database/Database%20Images) The new table was exported to a CSV and used in the machine learning model. We cleaned another dataset that looked at the pre-existing conditions, by condition, connected dataframe in pandas directly to SQL using SQLalchemy, and ran a query [as seen here.](https://user-images.githubusercontent.com/92996865/170176033-9de4ee21-3033-4ac3-b7a6-f7f04bb71305.png)
 
 **DataSet** 

 Our team will use the Pandas library to clean and transform our data and export that data into CSV files. We will make sure all of the data types are accurate, drop null values, etc. Then we will create a schema/flow chart with the appropriate primary and secondary keys as well as their respective data types, and any connections that can be made between CSV files will become apparent. We will then import the clean CSV files into SQL for easy queries and analysis. Additional tables may be created with the SQL query tool depending on what needs to be analyzed.
 
### Database Integration

Data is stored in Postgres. We also creating tables. The 3 tables were cleaned county data, monthly data of Covid-19 death with contributing conditions, and deaths by age groups.
![Tablesquery](https://github.com/jeffblando/Covid_Comorbidities/blob/0388dd6d48fe8fe2a8e887940573f38c3dbf8722/Database/Database%20Images/3%20Tables%20and%20a%20query.png)

The tables were also joined so the data can now run through the machine learning model.
![join](https://github.com/jeffblando/Covid_Comorbidities/blob/0388dd6d48fe8fe2a8e887940573f38c3dbf8722/Database/Database%20Images/Join%20in%20SQL.png)

**Exploratory Data Analysis (EDA)**

After downloading the datasets from the CDC website, they were uploaded in the jupyter notebook. To understand the datasets, we first observed the size of it(numbers of rows and columns) and the type of variables. Then we cleaned the null values and removed unnecessary columns. Lastly, we identify the important variables by checking the relationships between each variables. These steps were taken so the potential biases are known and the accuracy of the machine learning model is not as negatively affected. The EDA process can be seen here in the following file. [EDA](https://github.com/jeffblando/Covid_Comorbidities/blob/d04c7815cedb3adebce8b7e593fd91f68c699cea/EDA.ipynb)

The image below is shows the relationships of the variables between COVID-19 death, Pneumonia death, and Influenza Death in one of our dataset.
![Pneumonia_Covid_death_corr](https://github.com/jeffblando/Covid_Comorbidities/blob/abd8a1735bfd4448f1fb7756c3140b3fd3d75c16/Images/Covid_influenza_corr.png)
From obeservation, we can see that there is a higher correlation of death for a person who have COVID-19 and Pneumonia.

## Machine Learning
To begin our machine learning investigation, and because the data is already labeled, we will use a supervised machine model to classify the results within our original dataset into two groups; deaths with comorbidities and deaths without comorbidities. 

There are many rich data sources that we have identified to support our research on this topic. For that reason, we will most likely only include the most complete data, thus eliminating any lines with null values to ensure the highest quality result.

To train the model, we will split the data into testing and training sets and analyze metrics of accuracy, precision, and recall to determine if our model is up to the standards of the test. We are aiming for over 95% accuracy in the preliminary phase and will seek more sophisticated ML modeling techniques if we are unable to achieve this through classification. In addition, we will opt for slightly higher sensitivity versus precision as we are dealing with health-related data that would likely encourage further testing should a positive result be determined.

As we refine our approach, we will delve deeper into the specific comorbidities that influence death rate and make predictions using our modeling techniques that can help to predict the likelihood of a covid death and which target groups may have the highest death rates. 


**Preliminary Data Preprocessing** 

Several of the columns in the individualized dataset needed to be converted to numerical columns that the machine learning model could use for its prediction. Other columns that didn't apply like `"case_month", "race", "ethnicity", "case_positive_specimen_interval", "case_onset_interval", "process", "exposure_yn", "current_status"` were dropped before loading into the ML model.


**Feature Engineering, Feature Selection + the Decision Making Process**

The first model that was constructed included the highest amount of columns. We wanted to look at the relationship between state, county, age, sex, hospitalization status, ICU status, and underlying conditions, and how those factors related to death.

Because our thesis was more directly related to underlying conditions and death, we revised the model to include only underlying conditions as a predictor of death. The results for this model were accurate but were not detailed enough to be useful (the model did not predict any 1s). 
	
Modifying from this learning, age was reintroduced as the third variable and predictor. The same results occurred here, where the model did not predict any 1s. For this reason, we are staying with our first model which looks at multiple variables to determine a death outcome. 

**Testing + Training**

To split the model, we used a 75% 25% split for testing and training.   

**Model Choice, Limitations + Benefits**

A supervised model was chosen for this exercise because we had the outcomes we were looking to predict. In doing so, we used SK learn as well as the decision tree classifier and a confusion matrix to analyze the results. 

The dataset we were using is largely disproportionate - as (happily) many more individuals who experienced Covid-19 survived rather than perished. We are happy to report on these facts, but it does pose a problem to our modeling as splitting the data could produce varied results. The recall was low in our model as well.

The benefits of this approach included ease and clarity of reporting. Accuracy was very high, but this was most likely due to the skewness of the data. 
![enter image description here](https://github.com/jeffblando/Covid_Comorbidities/blob/MachineLearning_KT/Images/S2%20ML%20Results.jpg?raw=true)



## Visualizations
### Dashboard
Tableau will be the primary technology used to create an interactive, visually appealing dashboard. The two main reasons Tableau will be our primary Dashboard technology are Tableau has no row limit & Tableau allows us to avoid static dashboards. No row limit allows us to upload and analyze the millions of rows of data we've gathered, without overly-long processing times. Typically, dashboards are shared through PDFs, making them static from the moment they're sent; however, Tableau allows us to share our dashboards and will automatically update them with any changes. 

[Storyboard](https://public.tableau.com/app/profile/giovanni.bottone/viz/Segment2StoryboardV1/Story1?publish=yes)

[Description of Tools & Interractivity](https://docs.google.com/presentation/d/1HLexLPKKv-I4AnZZq3R42-6RtVfnWUKWxupJI4ClcX0/edit#slide=id.p)


**Presentation**

[Analyis of pre-existing disease and death rates](https://docs.google.com/presentation/d/1i8Ry3hVTzgpDNV7zKgqXaR9tYIhOCbXmE6nfHRlGO4E/edit#slide=id.g12dc2ad45a7_0_0)


**Communication protocols**

 - The team has established a GitHub, with each team member owning a unique branch
 - A minimum of two weekly zoom collaborations have been established to track progress and discuss any potential issues, identify areas of need, and identify the next steps to meet our current deadline.   
 - Team roles have been clearly defined so each team member knows what they are expected to contribute. For this week, 
     - Triangle: Kristen
     - Square: Jeff
     - X: Giovanni
     - Circle: Aung, Chris
 - A slack channel has been established for daily communication on all project aspects.

**GitHub Management**
The GitHub repository shall be maintained by one team member every week. This member has the responsibility to monitor all commits from the local branches into the main branch. If conflicts arise, this team member will edit the documents and resolve them as needed.

## Technologies Used:
- SK Learn (Machine Learning Library)
- Pandas & Jupyter Notebook - (Machine Learning/Database)
- SQL (Database)
- Postgres (Database)
- Tableau (Visualization)