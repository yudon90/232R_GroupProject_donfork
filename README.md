# 232R_GroupProject
UCSD Spring 2024 232R Big Data Analytics Using Spark Group Project 

**Project**: Examine US Happiness Trends with census data. 
Team Members: Taylor Witte, Donald Yu, Praveen Manimaran, Vitush Agarwal, Parker Aman

# Introduction 


# Methods 

## Data Exploration


## Preprocessing 


## Model 1


## Model 2
The goal of model 2 was to predict ownership from individual demographic and household information. To begin, we chose several  variables that individuals have and do not have control of. The variables selected were Age, Race, Citizenship Status, Education Attainment, Class of Work, Marital Status, Number of own family members in the household, Number of families in the household, Group Quarter Status (Household vs Group Quarters), State, Year, Household Type (Married vs Single, etc), and Person Number in Sample Unit. To build this model we tested two types of models: logical and decision tree. Both gave similar accuracy __ and __ respectively. We chose the decision tree which had a slightly higher accuracy and allowed for a more understandable model. The decision tree performed feature selection by only splitting on relevant features. To mitigate overfitting we only allowed for a maximum depth of the trees but did not limit the number of samples per split node. We did not consider the household weight which indicates how representative a household is of all households which could be included in further adaptations to decrease the bias of the model.

# Results 
## Model 2 
**Figure ?: Model 2 including Family Income Fearture**
<img width="1462" alt="Screenshot 2024-06-08 at 2 49 18 PM" src="https://github.com/twitte01/232R_GroupProject/assets/168356340/3612920a-e1cb-41c5-a89e-39b4406c4fad">

**Figure ?: Model 2 excluding Family Income Fearture**
<img width="1479" alt="Screenshot 2024-06-08 at 2 50 34 PM" src="https://github.com/twitte01/232R_GroupProject/assets/168356340/341a14f0-bab0-4b14-84a6-0ffd5023d72e">


# Discussion 


# Conclusion 


# Collaboration 
- **Taylor Witte:**
- **Vitush Agarwal:**
- **Donal Yu:**
- **Parker Aman:**
- **Praveen Manimaran:**
