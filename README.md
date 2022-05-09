# Covid
**Pulling from multiple sources of data, this project aims to answer the question of:**

Do individuals with comorbidities die more from covid than those with no known health issues?

**Selected Topic**

Covid

**Why we chose this topic**

By using machine learning, we can identify which factors increase the likelihood of a 'covid' death and predict which target groups will have the highest death rate. 
After identifying the at-risk target groups, we can identify best practices and precautions for their safety.

**Hypothesis**

Main Hypothesis: Individuals with comorbidities die more from covid than those with no known health issues

Alternative Hypothesis: Individuals with comorbidities do not die more from covid than those with no known health issues

Null hypothesis: There isn't enough evidence to support individuals with comorbidities die more or less than those with no known health issues

**Data source details**

 - https://data.cdc.gov/Case-Surveillance/COVID-19-Case-Surveillance-Public-Use-Data/vbim-akqf (covid data)
 - https://www.cdc.gov/nchs/covid19/mortality-overview.htm
 - https://data.cdc.gov/NCHS/Conditions-Contributing-to-COVID-19-Deaths-by-Stat/hk9y-quqm

**What we're looking to solve for**

 - After determining if individuals with comorbidities die more from covid than those with no known health issues, we have the potential to identify higher risk individuals who may need additional medications to lower their risk of death from Covid.

**Communication protocols**

 - The team has established a GitHub, with each team member owning a unique branch
 - A minimum of two weekly zoom collaborations have been established to track progress and discuss anypotential issues, identify areas of need, and identify the next     steps to meet our current deadline.   
 - Team roles have been clearly defined so each team member knows what they are expected to contribute. For this week, 
	 - Triangle: Kristen
	 - Square: Jeff
	 - X: Giovanni
	 - Circle: Aung, Chris
 - A slack channel has been established for daily communication on all project aspects.

**GitHub Management**
The GitHub repository shall be maintained by by one team member. This member has the responsibilty to monitor all commits to from local branches into the main branch. If conflicts arise, this team member will edit the docuents and resolve them.

**Database Construction**

 Our team will use the pandas library to clean and transform our data and export that data into csv files. We will make sure all of the data types are accurate, drop null values, etc. Then we will create a schema/flow chart with the appropriate primary and secondary keys as well as their respective data types, and any connections that can be made between csv files will become apparent. We will then import the clean csv files into SQL for easy querries and analysis. Aditional tables may be created with the SQL querry tool depending on what needs to be analyzed.


**Machine Learning**

To begin our machine learning investigation, and because the data is already labeled, we will use a supervised machine model to classify the results within our original dataset into two groups; deaths with comorbidities and deaths without comorbidities. 

There are many rich data sources that we have identified to support our research in this topic. For that reason, we will most likely only include the most complete data, thus eliminating any lines with null values to ensure the highest quality result.

To train the model, we will split the data into testing and training sets and analyze metrics of accuracy, precision, and recall in order to determine if our model is up to the standards of the test. We are aiming for over 99% accuracy in the preliminary phase, and will seek more sophisticated ML modeling techniques if we are unable to achieve this through classification. In addition, we will opt for slightly higher sensitivity versus precision as we are dealing with health related data that would likely encourage further testing should a positive result be determined.

As we refine our approach, we will delve deeper into the specific comorbidities that influcence death rate and make predictions using our modeling techniques that can help to predict the liklihood of a covid death and which target groups may have the hightest death rates. 

