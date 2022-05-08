# Covid
**Pulling from multiple sources of data, this project aims to answer the question of:

Do individuals with comorbidities die more from covid than those with no known health issues?

**Selected Topic**

Covid

**Why we chose this topic**

By using machine learning, we can identify which factors increase the likelihood of a 'covid' death and predict which target groups will have the highest death rate. 
After identifying the at-risk target groups, we can identify best practices and precautions for their safety.


**Data source details**

 - https://data.cdc.gov/Case-Surveillance/COVID-19-Case-Surveillance-Public-Use-Data/vbim-akqf (covid data)
 - https://www.cdc.gov/nchs/covid19/mortality-overview.htm
 - https://data.cdc.gov/NCHS/Conditions-Contributing-to-COVID-19-Deaths-by-Stat/hk9y-quqm

**What we're looking to solve for**

 - Do individuals with comorbidities die more from covid than those with no known health issues?

**Communication protocols**

 - The team has established a GitHub, with each team member owning a unique branch
 - Twice weekly zoom collaborations have been set up to track progress 
 - Team roles have been clearly defined so each team member knows what they are expected to contribute. For this week, 
	 - Triangle: Kristen
	 - Square: Jeff
	 - X: Giovanni
	 - Circle: Aung, Chris
 - A slack channel has been established to share links and other ideas that come up between working sessions

# Machine Learning
To begin our machine learning investigation, and because the data is already labeled, we will use a supervised machine model to classify the results within our original dataset into two groups; deaths with comorbidities and deaths without comorbidities. To train the model, we will split the data into testing and training sets and analyze metrics of accuracy, precision, and recall in order to determine if our model is up to the standards of the test. We are aiming for over 99% accuracy in the preliminary phase, and will seek more sophisticated ML modeling techniques if we are unable to achieve this through classification. In addition, we will opt for slightly higher sensitivity versus precision as we are dealing with health related data that would likely encourage further testing should a positive result be determined.

As we refine our approach, we will delve deeper into the specific comorbidities that influcence death rate and make predictions using our modeling techniques that can help to predict the liklihood of a covid death and which target groups may have the hightest death rates. 



