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

World Happiness Dataset Variables 


Household Census Data
1. Household Variables: Geographic Variables
2. Household Variables: Technical Variables
3. Household Variables: Economic Variables
4. Household Variables: App,Mec,Other Variables
5. Household Variables: Household Comp Variables
 
Individual Census Data
1. Ind Variables: Household Variables
2. Ind Variables: Technical Variables
3. Ind Variables: Demographic Variables
4. Variables: Education Variables
5. Ind Variables: Employment & Income Variables
6. Ind Variables: Health Variables
 
Visualize distribution of all variables over whole dataset and years

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
