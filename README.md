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
The goal of model 2 was to predict ownership from individual demographic and household information. To begin, we chose several  variables that individuals have and do not have control of. The variables selected were Age, Race, Citizenship Status, Education Attainment, Class of Work, Marital Status, Number of own family members in the household, Number of families in the household, Group Quarter Status (Household vs Group Quarters), State, Year, Household Type (Married vs Single, etc), and Person Number in Sample Unit. To build this model we tested two types of models: logistic regression and decision tree. Both gave similar accuracy __ and __ respectively. We chose the decision tree which had a slightly higher accuracy and allowed for a more understandable model. The decision tree performed feature selection by only splitting on relevant features. To mitigate overfitting we only allowed for a maximum depth of the trees but did not limit the number of samples per split node. We did not consider the household weight which indicates how representative a household is of all households which could be included in further adaptations to decrease the bias of the model. We also ran this decision tree with the total household income and without, which gave some interesting results and will be discussed in further sections.

# Results 
## Model 2 
**Figure ?: Model 2 including Family Income Fearture**
<img width="1207" alt="Screenshot 2024-06-08 at 6 48 46 PM" src="https://github.com/twitte01/232R_GroupProject/assets/168356340/f2874083-ee2b-47cd-858f-19e749d491fe">

**Figure ?: Model 2 excluding Family Income Fearture**
<img width="1397" alt="Screenshot 2024-06-08 at 6 48 12 PM" src="https://github.com/twitte01/232R_GroupProject/assets/168356340/87d1dcd9-b5c6-42fe-8e9e-82cd7ec9f205">


This fitting graph shows as the complexity (depth of trees) increases, we do continue to see an increase in accuracy, however, it is trivial. We can see the best depth to pick is 2. After this, the marginal increase in accuracy is not worth it.

![alt text](image-1.png)


# Discussion 


# Conclusion 


# Collaboration 
- **Taylor Witte:**
- **Vitush Agarwal:**
- **Donal Yu:**
- **Parker Aman:**
- **Praveen Manimaran:**
