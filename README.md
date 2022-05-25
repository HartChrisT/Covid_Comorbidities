
# Covid_Comorbidities

**Pulling from multiple sources of data, this project aims to answer the question of:**
Do individuals with comorbidities die more from covid than those with no known health issues?


## Hypothesis
Hypothesis: Individuals with comorbidities die more from covid than those with no known health issues.


## Technologies
A brief description of the technologies we're using: 
- SK Learn (Machine Learning Library)
- Pandas & J'upyter Notebook' - (Machine Learning/Database)
- SQL (Database)
- Postgres (Database)
- Tableau (Visualization)


### Data Cleaning and Analysis
Pandas will be used to clean the data and perform an exploratory analysis. Further analysis will be completed using Python.

### Database Storage
Mongo is the database we intend to use, and we will integrate Flask to display the data.

### Machine Learning
SKLearn, Pandas & J'upyter Notebook are the ML technologies we'll be using to create a classifier. Our training and testing setup is ___. 

### Dashboard
Tableau will be the primary technology used to create an interactive, visually appealing dashboard. The two main reasons Tableau will be our primary Dashboard technology are Tableau has no row limit & Tableau allows us to avoid static dashboards. No row limit allows us to upload and analyze the millions of rows of data we've gathered, without overly-long processing times. Typically, dashboards are shared through PDF's, making them static from the moment they're sent; however, Tableau allows us to share our dashboards and will automatically update them with any changes. 

# Covid Research

**Pulling from multiple sources of data, this project aims to answer the question of:**

Do individuals with comorbidities die more from covid than those with no known health issues?

**Selected Topic**

Covid

**Why we chose this topic**

By using machine learning, we can identify which factors increase the likelihood of a 'covid' death and predict which target groups will have the highest death rate. 
After identifying the at-risk target groups, we can identify best practices and precautions for their safety.

**Hypothesis**

Hypothesis: Individuals with comorbidities die more from covid than those with no known health issues


**Data source details**

 - https://data.cdc.gov/Case-Surveillance/COVID-19-Case-Surveillance-Public-Use-Data/vbim-akqf (covid data)
 - https://www.cdc.gov/nchs/covid19/mortality-overview.htm
 - https://data.cdc.gov/NCHS/Conditions-Contributing-to-COVID-19-Deaths-by-Stat/hk9y-quqm

**What we're looking to solve for**

 - After determining if individuals with comorbidities die more from covid than those with no known health issues, we have the potential to identify higher-risk individuals who may need additional medications to lower their risk of death from Covid.

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

**Database Construction**

 Our team will use the pandas library to clean and transform our data and export that data into CSV files. We will make sure all of the data types are accurate, drop null values, etc. Then we will create a schema/flow chart with the appropriate primary and secondary keys as well as their respective data types, and any connections that can be made between CSV files will become apparent. We will then import the clean CSV files into SQL for easy queries and analysis. Additional tables may be created with the SQL query tool depending on what needs to be analyzed.
 
 **DataSet** 


Data used in this project are acquired from Centers for Disease Control and Prevention(CDC) and the dataset chosen for the analysis are from csv documents found on the CDC website, "Provisonal Covid-19 Deaths by Sex and Age" and "United States COVID-19 Cases and Deaths by State over Time". The dataset mentioned can be found in the following link: https://data.cdc.gov/browse?&page=1

**Covid-19 Comorbidities Prediction*


## Machine Learning

*Segment 2*

**Preliminary Data Preprocessing** 

Several of the columns in the individualized dataset needed to be converted to numerical columns that the machine learning model could use for its prediction. Other columns that didn't apply like `"case_month", "race", "ethnicity", "case_positive_specimen_interval", "case_onset_interval", "process", "exposure_yn", "current_status"` were dropped before loading into the ML model.


**Feature Engineering, Feature Selection + the Decision Making Process**

The first model that was constructed included the highest amount of columns. We wanted to look at the relationship between state, county, age, sex, hospitalization status, ICU status, and underlying conditions, and how those factors related to a death.

Because our thesis was more directly related to underlying conditions and death, we revised the model to include only underlying conditions as a predictor of death. The results for this model were accurate, but were not detailed enough to be useful (the model did not predict any 1s). 
	
Modifying from this learning, age was reintroduced as the third variable and predictor. The same results occurred here, where the model did not predict any 1s. For this reason, we are staying with our first model that looks at multiple variables to determine a death outcome. 

**Testing + Training**

To split the model, we used a 75% 25% split for testing and training.   

**Model Choice, Limitations + Benefits**

A supervised model was chosen for this exercise because we had the outcomes we were looking to predict. In doing so, we used SK learn as well as the decision tree classifier and a confusion matrix to analyze the results. 

The dataset we were using is largely disproportionate - as (happily) many cases resulted in survivals rather than deaths. We are happy to report on these facts, but it does pose a problem to our modeling as splitting the data could produce varied results. Recall was low in our model as well.

Benefits of this approach included ease and clarity of reporting. Accuracy was very high, but this was most likely due to the skewedness of the data. 

![enter image description here](https://github.com/jeffblando/Covid_Comorbidities/blob/MachineLearning_KT/Images/S2%20ML%20Results.jpg?raw=true)

*Segment 1*


To begin our machine learning investigation, and because the data is already labeled, we will use a supervised machine model to classify the results within our original dataset into two groups; deaths with comorbidities and deaths without comorbidities. 

There are many rich data sources that we have identified to support our research on this topic. For that reason, we will most likely only include the most complete data, thus eliminating any lines with null values to ensure the highest quality result.

To train the model, we will split the data into testing and training sets and analyze metrics of accuracy, precision, and recall to determine if our model is up to the standards of the test. We are aiming for over 95% accuracy in the preliminary phase and will seek more sophisticated ML modeling techniques if we are unable to achieve this through classification. In addition, we will opt for slightly higher sensitivity versus precision as we are dealing with health-related data that would likely encourage further testing should a positive result be determined.

As we refine our approach, we will delve deeper into the specific comorbidities that influence death rate and make predictions using our modeling techniques that can help to predict the likelihood of a covid death and which target groups may have the highest death rates. 

**Visualizations**

[Covid vs Pneumonia vs Influenza](https://public.tableau.com/app/profile/giovanni.bottone/viz/Segment2DeathComparison/Total_Covid_deaths_by_gender?publish=yes)
