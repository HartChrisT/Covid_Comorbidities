
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

 Our team used the pandas library to clean and transform the raw data into a usable form for analysis. We made sure all of the data types are accurate, appropriate, and dropped all null values. We created a schema/flow chart using QuickDB to make database connections and data types easily apparent. We imported the clean CSV files into SQL for easy queries and analysis. Once in SQL, we joined census county data with individual covid case data to add more features to the machine learning model. The new table was exported to a csv and used in the machine learning model.
 
 **DataSet** 


Data used in this project are acquired from Centers for Disease Control and Prevention(CDC) and the dataset chosen for the analysis are from csv documents found on the CDC website, "Provisonal Covid-19 Deaths by Sex and Age" and "United States COVID-19 Cases and Deaths by State over Time". The dataset mentioned can be found in the following link: https://data.cdc.gov/browse?&page=1

**Covid-19 Comorbidities Prediction*

**Machine Learning**

To begin our machine learning investigation, and because the data is already labeled, we will use a supervised machine model to classify the results within our original dataset into two groups; deaths with comorbidities and deaths without comorbidities. 

There are many rich data sources that we have identified to support our research on this topic. For that reason, we will most likely only include the most complete data, thus eliminating any lines with null values to ensure the highest quality result.

To train the model, we will split the data into testing and training sets and analyze metrics of accuracy, precision, and recall to determine if our model is up to the standards of the test. We are aiming for over 99% accuracy in the preliminary phase and will seek more sophisticated ML modeling techniques if we are unable to achieve this through classification. In addition, we will opt for slightly higher sensitivity versus precision as we are dealing with health-related data that would likely encourage further testing should a positive result be determined.

As we refine our approach, we will delve deeper into the specific comorbidities that influence death rate and make predictions using our modeling techniques that can help to predict the likelihood of a covid death and which target groups may have the highest death rates. 

