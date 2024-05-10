# 232R_GroupProject
UCSD Spring 2024 232R Big Data Analytics Using Spark Group Project 

**Project**: Examine US Happiness Trends with census data. 
Team Members: Taylor Witte, Donald Yu, Praveen Manimaran, Vitush Agarwal, Parker Aman

**Abstract**: 
This project aims to uncover trends in happiness across the United States by analyzing individual and household census data from the American Community Survey for the years 2012-2022, excluding 2020 due to the COVID-19 pandemic. Leveraging the power of the Spark framework and SDSC to manage large-scale datasets, pertinent features are selected from the comprehensive data. The analysis will utilize machine learning techniques provided by Spark's MLlib to explore relationships between demographic variables and reported happiness levels. The findings are expected to offer insights into how various factors influence happiness across different regions and demographic groups in the US. This study will provide an understanding of the determinants of happiness.

**Data Set**: 
This project will combine multiple datasets. 
Individual & household census data from the American Community Survey years 2012-2022 excluding 2020 due to the data being impacted by the COVID-19 pandemic. Due to the size of the data, we selected features from the entire dataset using IPUMS. The datasets can be found in this Google Drive (https://drive.google.com/drive/folders/1BgAn6uJvuALPtYoMj1vYInDOWKlxUyXX?usp=drive_link) and can be accessed following these instructions https://usa.ipums.org/usa/extract_instructions.shtml
Additionally, the World Happiness Report dataset from 2012-2022 excluding 2020 is being utilized to examine US happiness. 
Together the dataset contains over 10 million individuals and 81 variables. For ease of understanding we have categorized the variables. 

World Happiness Report Data 

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

Individual Census Data Variables

Number of Variables: 35
Number of Individuals: 10000426
Number of Households: 1394624

Technical Variables
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
Household Variables
* PERWT: (Person weight)
* FAMSIZE: (Number of own family members in household)
* GQ: (Group quarters status)
Demographic Variables
* SEX: (Sex) 
* AGE: (Age) 
* MARST: (Marital status) 
* RACE: (Race [general version]) 
* RACED: (Race [detailed version]) 
* CITIZEN: (Citizenship status)
Education Variables
* SCHOOL: (School attendance) 
* EDUC: (Educational attainment [general version]) 
* EDUCD: (Educational attainment [detailed version])
* SCHLTYPE: (Public or private school) 
Health Variables
* HCOVANY: (Any health insurance coverage) 
Employment & Income Variables
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

Household Census Variables 

Number of Variables: 31
Number of Individuals: 10002255
Number of Households: 1416026

Technical Variables
* YEAR
* SAMPLE: (IPUMS sample identifier)
* SERIAL: (Household serial number)
* CBSERIAL: (Original Census Bureau household serial number) 
* HHWT: (Household weight)
* HHTYPE: (Household Type) 
* CLUSTER: (Household cluster for variance estimation)
* CPI99: (CPI-U adjustment factor to 1999 dollars)
* STRATA: (Household strata for variance estimation)
Geographic Variables
* STATEICP: (State (ICPSR code)) State Identifier with digit codes.
* MET2023: (Metropolitan area (2023 delineations, identifiable areas only))
Economic Characteristics
* MOBLHOME: (Annual mobile home costs)
* TAXINCL: (Mortgage payment includes property taxes)
* INSINCL: (Mortgage payment includes property insurance)
* RENTGRS: (Monthly gross rent)
* CONDOFEE: (Monthly condominium fee)
* MOBLHOME: (Annual mobile home costs)
* HHINCOME: (Total household income)
* FOODSTMP: (Food stamp recipiency) 
* VALUEH: (House value)
Appliance, Mechanical, Other Variables
* COSTELEC: (Annual electricity cost)
* COSTGAS: (Annual gas cost)
* COSTWATR: (Annual water cost)
* COSTFUEL: (Annual home heating fuel cost) 
* CINETHH: (Access to internet) 
* VEHICLES: (Vehicles available)
Houshold Composition Variables
* GQ: (Group quarters status) 
* FARM: (Farm status) Farm status is a catagorical variable represented by digits. 
* OWNERSHP: (Ownership of dwelling (tenure) [general version]) 
* OWNERSHPD: (Ownership of dwelling (tenure) [detailed version]) 
* COUPLETYPE: (Householder couple type) 
* NFAMS: (Number of families in household)



**Preprocessing Methodology**

To generate the dataset an random sample of 1 million instance per year was generated. Variables were selected to be diverse enough to get a deep understanding of the US population and reflect the World Happiness Data varaibles but concise enough to be able to process. 
The distribution of all variables was examined to ensure the dataset was representative of the US population. 
For the household census dataset, each row repressnts an individuals but all variables were measured on a household level so the dataset was filtered to remove individuals within the same household to leave unique household instances. 
The World Happiness Report Dataset was filtered to only include US datapoints between the year of 2012-2022.
All monetary variables were normalized for inflation to the 2000 dollar values.
Further scaling of all variables will be dependent on the analysis that is being performed.
Any variables that were missing from too many individuals and/or households will be removed from further analysis. 

**Environment Setup**

pip install pyspark-dist-explore
