# Bank Client Churn Analysis 

![Picture8](https://github.com/user-attachments/assets/f297ee7c-a453-4f8e-a574-0b52f0798392)

## Table Of Contents
1. [Project Overview](#project-overview)
2. [Data Source](#data-source)
3.  [Data Cleaning Process](#data-cleaning-process)
4.  [Exploratory Data Analysis](#exploratory-data-analysis)
5.  [Data Analysis](#data-analysis) 
6.  [Results And Insights](#results-and-insights)
7.  [Recommendations](#recommendations)
8.  [Tools](#tools) 

### Project Overview
This project aims to provide actionable insights on the client churn of a bank over the past month. By analyzing different aspects of the data, we seek to identify trends, key factors influencing client churn, make data-backed recommendations, and assist the company in retaining more clients.

### Data Source
Bank Customer Churn: The dataset used for this project is Customer-Churn-Records.csv, the dataset contains information on the client's who've left the bank. This dataset was found on Kaggle: [click here](https://www.kaggle.com/datasets/radheshyamkollipara/bank-customer-churn)

### Data Cleaning Process
I first loaded the dataset into excel, then converted it from a csv to a xlsx file for better viewing. The next step was to remove duplicates and blanks, then I did some column formatting and ensured that the correct data types were used. The last step was to do a spell check on all the columns.

#### Before cleaning:

![Image](https://github.com/user-attachments/assets/020b17d6-45f1-4c62-b4e4-eaaf5bcf3246)


#### After cleaning:

![Image](https://github.com/user-attachments/assets/ccbe9c5f-4425-4e82-b687-d6cc4da46505)


### Exploratory Data Analysis
EDA involved exploring our dataset to answer these questions:
1. What are the genders and ages of the clients who've left the bank?
2. In which countries are we losing most of our clients, and in which countries are we retaining most of our clients?
3. What were the card types of the clients who've left the bank?
4. What percentage of the clients who've complained, eventually ended up leaving the bank?

### Data Analysis

#### Analysing Churn By Age And Gender
In order to figure this one out, I made use of the "Exited", "Age", and "Gender" columns. The issue is that the "Age" column had to be modified if we were going to have a visualization that would be pleasing to the eye, individuals had to be grouped into their age categories to avoid having a visualization that represented every individual age. To achieve this, I made use of the binning function in power BI to create 10 groups of similar ages.

![Image](https://github.com/user-attachments/assets/6aaf4b2f-0f26-4c89-9430-b71cb232bb19)

#### Analysing Churn By Client's Card Type
To answer this question, we needed two data points, "card type" and "total client churn", the issue is that we didn't have the total number of client's who've left in our dataset as it was, so to solve this problem, I made use of DAX in power BI to create a measure to filter through our column, select rows where value = 1 and sum up our total, this was achieved by using the CALCULATE(COUNT()) function.

```DAX
Number Of Clients Who Left The Bank = CALCULATE(COUNT(Customer_Churn_Records[Exited]), FILTER(Customer_Churn_Records, Customer_Churn_Records[Exited] = 1))
```

#### Analysing Percentage Of Complainant's Who Eventually Left
Last but not least, in order to get to the bottom of this question, a value couldn't simply be pulled from the dataset, so I again made use of Power BI's language 'DAX' to create a new measure. I then formatted the result to be displayed as a percentage.

```DAX
Complainant's Who Left = SUM(Customer_Churn_Records[Exited])/SUM(Customer_Churn_Records[Complain])
```

### Results And Insights
#### Client Churn By Age And Gender
- Across all age groups, female client churn is higher than male client churn, with females in their 40's being the highest.
- The age group with the highest client churn is 40-49. The age groups with the lowest churn are groups of clients aged 60 and older, and groups of clients aged 29 and younger. Age groups 30 and 50 aren't the highest or lowest, but we do have a significant number of clients in both age groups.

![Visual1](https://github.com/user-attachments/assets/5a8b21fb-d467-43c5-8e0e-8cd5508702e9)

#### Client Churn By Geography
- Our top two countries with the highest churn are Germany and France, having 814 and 811 client churn respectively.
- The country with the lowest churn is Spain, with 413 lost clients.

![Visual2](https://github.com/user-attachments/assets/b4f7c1d7-fb16-4458-b2e0-da4e71712bfe)

#### Client Churn By Card Type
- Card types with over 500 churned clients are the diamond, platinum, and silver cards.
- The card type with the lowest client churn is the gold card.

![Visual4](https://github.com/user-attachments/assets/14f00e36-edd6-4a89-94d7-d6a145e94499)

#### Percentage Of Compainant's Who Eventually Left The Bank
- 99% of the clients who've complained eventually ended up leaving the bank.

![Visual5](https://github.com/user-attachments/assets/c216e3e2-110b-4d47-b774-89559f23b897)

### Recommendations
- I recommend that the customer service department should conduct a survey for churned female clients to better understand their reasons for leaving the bank. This survey can help the company better understand if the issue is with customer service, pricing, a lack of desired features or something else.
- The company can then offer dedicated assistance for the issues which will be mentioned in the survey.
- I suggest that the marketing team considers designing loyalty programs that are beneficial to both genders, across all age groups, so that they have more reasons to stay with the bank.
- Another suggestion for the marketing team is to highlight features that speak to ease of use and convenience. As clients in their 40's have busy lives, they're most likely looking for services that help them on time saving. This would help the company retain more clients from the age group with the most churned clients.
- A suggestion for the service development team would be to re-examine the features and benefits of the diamond, platinum, and silver card types, and offer more competitive features.
- The company should provide training to the customer service department, as 99% of clients with complaints leaving indicates that customer service wasn't able to resolve these complaints while the clients were still with the bank. Training will lead to higher performance for the department, which will then translate to higher client retention.

### Tools
- Excel - Data Cleaning
- Power BI - Data Analysis And Visualizations


