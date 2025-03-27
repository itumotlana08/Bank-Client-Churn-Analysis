# Bank Client Churn Analysis 

### Project Overview
This project aims to provide actionable insights on the client churn of a bank. By analyzing different aspects of the data, we seek to identify trends, key factors influencing client churn, make data-backed recommendations, and assist the company in retaining more clients.

### Data Source
Bank Customer Churn: The dataset used for this project is Customer-Churn-Records.csv, the dataset contains information on the client's who've left the bank. This dataset was found on [click here](https://www.kaggle.com/datasets/radheshyamkollipara/bank-customer-churn)

### Data Cleaning Process
I first loaded the dataset into excel, then converted it from a csv to a xlsx file for better viewing. The next step was to remove duplicates and blanks, then I did some column formatting and ensured that the correct data types were used. The last step was to do a thorough spell check on all the columns.

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

### Recommendations

### Tools
- Excel - Data Cleaning
- Power BI - Data Analysis And Visualizations

