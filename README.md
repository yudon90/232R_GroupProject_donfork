# 232R_GroupProject
UCSD Spring 2024 232R Big Data Analytics Using Spark Group Project 

**Project**: Examine US Happiness Trends with census data. 
Team Members: Taylor Witte, Donald Yu, Praveen Manimaran, Vitush Agarwal, Parker Aman

## Abstract
This project aims to uncover trends in happiness across the United States by analyzing individual and household census data from the American Community Survey for the years 2012-2022, excluding 2020 due to the COVID-19 pandemic. Leveraging the power of the Spark framework and SDSC to manage large-scale datasets, pertinent features are selected from the comprehensive data. The analysis will utilize machine learning techniques provided by Spark's MLlib to explore relationships between demographic variables and reported happiness levels. The findings are expected to offer insights into how various factors influence happiness across different regions and demographic groups in the US. This study will provide an understanding of the determinants of happiness.

## Data Set
**Dataset Overview**
This project will combine multiple datasets. 
Individual & household census data from the American Community Survey years 2012-2022 excluding 2020 due to the data being impacted by the COVID-19 pandemic. Due to the size of the data, we selected features from the entire dataset using IPUMS. The datasets can be found in this Google Drive (https://drive.google.com/drive/folders/1BgAn6uJvuALPtYoMj1vYInDOWKlxUyXX?usp=drive_link) and can be accessed following these instructions https://usa.ipums.org/usa/extract_instructions.shtml
Additionally, the World Happiness Report dataset from 2012-2022 excluding 2020 is being utilized to examine US happiness. 
Together the dataset contains over 10 million individuals and 81 variables. For ease of understanding we have categorized the variables. 

### World Happiness Report Data

Number of Variables: 15
Number of Years: 10 

1. Country Name
2. Regional Indicator
3. Year
4. Happiness Index
5. Happiness Rank
6. Life Ladder
7. Log GDP Per Capita
8. Social Support
9. Healthy Life Expectancy At Birth
10. Freedom To Make Life Choices
11. Generosity
12. Perceptions Of Corruption
13. Positive Affect
14. Negative Affect
15. Confidence In National Government'

### Individual Census Data Variables

Number of Variables: 35
Number of Individuals: 10000426
Number of Households: 1394624

**Technical Variables**
* Year
* SAMPLE (IPUMS sample identifier)
* SERIAL (Household serial number)
* CBSERIAL: (Original Census Bureau household serial number)
* HHWT: (Household weight)
* PERNUM: (Person number in sample unit) 
* CBPERNUM: (Original Census Bureau Person number in sample unit)
* CLUSTER: (Household cluster for variance estimation) 
* CPI99: (CPI-U adjustment factor to 1999 dollars)
* STRATA: (Household strata for variance estimation)
**Household Variables**
* PERWT: (Person weight)
* FAMSIZE: (Number of own family members in household)
* GQ: (Group quarters status)
**Demographic Variables**
* SEX: (Sex) 
* AGE: (Age) 
* MARST: (Marital status) 
* RACE: (Race [general version]) 
* RACED: (Race [detailed version]) 
* CITIZEN: (Citizenship status)
**Education Variables**
* SCHOOL: (School attendance) 
* EDUC: (Educational attainment [general version]) 
* EDUCD: (Educational attainment [detailed version])
* SCHLTYPE: (Public or private school) 
**Health Variables**
* HCOVANY: (Any health insurance coverage) 
**Employment & Income Variables**
* EMPSTAT: (Employment status [general version]) 
* EMPSTATD: (Employment status [detailed version])
* CLASSWKR: (Class of worker [general version]) 
* CLASSWKRD: (Class of worker [detailed version]) 
* UHRSWORK: (Usual huours worked per week) 
* LOOKING: (Looking for work) 
* INCTOT: (Total personal income)
* FTOTINC: (Total family income)
* INCWELFR: (Welfare (public assistance) income)
* INCINVST: (Interest, dividend, and rental income)
* POVERTY: (Poverty status) 

### Household Census Variables

Number of Variables: 31
Number of Individuals: 10,002,255
Number of Households: 1,416,026

**Technical Variables**
* YEAR
* SAMPLE: (IPUMS sample identifier)
* SERIAL: (Household serial number)
* CBSERIAL: (Original Census Bureau household serial number) 
* HHWT: (Household weight)
* HHTYPE: (Household Type) 
* CLUSTER: (Household cluster for variance estimation)
* CPI99: (CPI-U adjustment factor to 1999 dollars)
* STRATA: (Household strata for variance estimation)
**Geographic Variables**
* STATEICP: (State (ICPSR code)) State Identifier with digit codes.
* MET2023: (Metropolitan area (2023 delineations, identifiable areas only))
**Economic Characteristics**
* MOBLHOME: (Annual mobile home costs)
* TAXINCL: (Mortgage payment includes property taxes)
* INSINCL: (Mortgage payment includes property insurance)
* RENTGRS: (Monthly gross rent)
* CONDOFEE: (Monthly condominium fee)
* MOBLHOME: (Annual mobile home costs)
* HHINCOME: (Total household income)
* FOODSTMP: (Food stamp recipiency) 
* VALUEH: (House value)
**Appliance, Mechanical, Other Variables**
* COSTELEC: (Annual electricity cost)
* COSTGAS: (Annual gas cost)
* COSTWATR: (Annual water cost)
* COSTFUEL: (Annual home heating fuel cost) 
* CINETHH: (Access to internet) 
* VEHICLES: (Vehicles available)
**Houshold Composition Variables**
* GQ: (Group quarters status) 
* FARM: (Farm status) Farm status is a catagorical variable represented by digits. 
* OWNERSHP: (Ownership of dwelling (tenure) [general version]) 
* OWNERSHPD: (Ownership of dwelling (tenure) [detailed version]) 
* COUPLETYPE: (Householder couple type) 
* NFAMS: (Number of families in household)



## Preprocessing Methodology

To generate the dataset a random sample of 1 million instances per year was generated. Variables were selected to be diverse enough to get a deep understanding of the US population and reflect the World Happiness Data variables but concise enough to be able to process. 
The distribution of all variables was examined to ensure the dataset was representative of the US population. 
For the household census dataset, each row represents an individuals but all variables were measured on a household level so the dataset was filtered to remove individuals within the same household to leave unique household instances. 
The World Happiness Report Dataset was filtered to only include US datapoints between the year of 2012-2022.
All monetary variables were normalized for inflation to the 2000 dollar values. 
Variables that were missing from too many individuals and/or households will be removed from further analysis. For some selected categorical variables, categories were combined such as household definitions for the Group Quarters variable. For clustering, all variables were normalized using the MinMax Scaler to a 0-1 scale. Each column was scaled individually. The MinMax normalization function was selected to preserve the true distribution of each variable. 


**Feature Expansion**

Created a FULLTIME column in the individual dataset that is a 1 if the individual works 40+ hours per week, and a 0 if otherwise. Also created a COSTUTIL column in the household dataset that sums up all of the utility costs.

## Models 

**K Means**

Ran the scaled/normalized household dataset through the kmeans clustering model with different values for k (2-10) and plotted the cost of features, so we can determine the best value for k.


For the K-Means on the individual dataset, Elbow Curve was used to get the k-value of 3. The Cluster Centers plot shows the average values of each feature for the three identified clusters. Each bar represents a feature, and its height reflects the mean value of that feature within the cluster. The features include demographic, socio-economic, and health-related variables. Notably, variables such as AINCTOT (total income), AFTOTINC (family total income), and POVERTY show significant differences across clusters, indicating that income and poverty status are key distinguishing factors among the clusters.

The silhouette score is 0.869, which is quite high. A high silhouette score close to 1 indicates that the clusters are well-defined and distinct from each other. The points within each cluster are very similar to each other and different from points in other clusters. The clustering model has successfully grouped the data points into clusters that have high internal similarity and low external similarity.

Based on the visualizations, KMeans appears to be a good model for clustering this dataset. The high silhouette score of 0.869 indicates that the clusters are well-defined and distinct from each other, with data points closer to their assigned cluster centers compared to other clusters. The PCA plot further supports this, showing clear separation between clusters in a two-dimensional space. The cluster centers plot reveals meaningful differences across several features, particularly income-related variables. Together, these findings suggest that KMeans effectively captures the underlying structure of the data, making it a suitable model for identifying and analyzing patterns within the dataset.

To model the household dataset, K-Means was used for clustering. An Elbow curve was used to get the k-value of 3. However, the clustering was unsuccessful with a silhouette score of 0.359. Since K-means was unsuccessful, a decision tree was built using the household data to predict ownership status: rented or owned. 

**Decision Trees**

A decision tree was built using the household data to predict ownership status: rented or owned. The dataset also contains group quarter house which reported N/A to the ownership question. This subset only represents 10% of the test dataset. Rented properties represented 26% of the test dataset. The decision tree achieved a test accuracy of 99.9% with only 3 variables: Group Quarter, Inflation Adjusted House Value, and Year. The Group Quarter variable was used to filter out group quarters. The remaining 90% of households' ownership status was determined based on house value and year.

## Evaluating Models and Comparing Test and Training Data (Fitting Graph)

It appears that the training and test errors decrease sharply from a max depth of 1 to 2. This indicates that a tree depth of 1 is too simple to capture the underlying patterns in the data. After increasing from a max depth of 2, both the training and test errors still remain very low, so this may suggest that increasing the depth beyond 2 does not significantly improve the model's performance on both training and test data. 

We also notice that the training and test errors overlap so closely in the fitting graph. 
There are some potential reasons for this:

1. Simplistic Data: The data might be very simple which makes it easy for even shallow trees to achieve high accuracy on both training and test sets.
2. Small Data Variability: If the training and test sets are very similar, the errors might overlap due to a lack of variability in the data.

Ways we can address #2 is to plot the distribution of features to see if there's significant overlap between training and test sets and we can address #1 by showing summary statistics using describe() in Spark. This will be done in the next step.

## Conclusion & Next Steps

We were very happy with the results from our first few models. Besides the clustering on the Household data, we saw some surprisingly good test errors. We plan on dropping some features from the household dataset and tuning a few parameters for the clustering model. We feel we can get better results, however we all had trouble accessing the SDSC computer. This made running the models locally very difficult. When we secure full access, we will make the appropriate changes to improve our findings. We also discussed a couple other models such as predicting individuals' salary and homeowning ability based on the census data using a random forest model. 

## Environment Setup

pip install pyspark-dist-explore
