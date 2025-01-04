# Credit_Card_Financial_Dashboard
power bi dashboard

## Project Objective
The objective of this project is to develop a comprehensive Credit Card Weekly Dashboard that provides real-time insights into key performance metrics and trends. This dashboard enables stakeholders to monitor and analyze credit card operations effectively, facilitating data-driven decision-making and operational efficiency.



## Steps followed

### Step 1: Import Data to SQL Database

1. Prepare CSV file.
2. Create tables in SQL.
3. Import CSV file into SQL.

### Step 2: Write DAX Queries

 #### Creating Age Group Column
    
    AgeGroup = SWITCH(
        TRUE(),
        'ccdb cust_detail'[Customer_Age] < 30, "20-30",
        'ccdb cust_detail'[Customer_Age] >= 30 && 'ccdb cust_detail'[customer_age] < 40, "30-40",
        'ccdb cust_detail'[Customer_Age] >= 40 && 'ccdb cust_detail'[customer_age] < 50, "40-50",
        'ccdb cust_detail'[Customer_Age] >= 50 && 'ccdb cust_detail'[customer_age] < 60, "50-60",
        'ccdb cust_detail'[Customer_Age] >= 60, "60+",
        "unknown"
    )

 #### Creating IncomeGroup column
    
    IncomeGroup = SWITCH(
    TRUE(),
    'ccdb cust_detail'[income] < 35000, "Low",
    'ccdb cust_detail'[income] >= 35000 && 'ccdb cust_detail'[income] <70000, "Med",
    'ccdb cust_detail'[income] >= 70000, "High",
    "unknown"
    )

 #### Creating a Revenue column

    Revenue = 'ccdb cc_detail'[Annual_Fees] + 'ccdb cc_detail'[total_trans_amt] + 'ccdb cc_detail'[interest_earned]

   
 #### Calculating measure of 'current week revenue' 

    Current_week_Revenue = CALCULATE(
    SUM('ccdb cc_detail'[Revenue]),
    FILTER(
    ALL('ccdb cc_detail'),
    'ccdb cc_detail'[week_num2] = MAX('ccdb cc_detail'[week_num2])))


 #### Calculating measure of 'previous week revenue'

    Previous_week_Revenue = CALCULATE(
    SUM('ccdb cc_detail'[Revenue]),
    FILTER(
    ALL('ccdb cc_detail'),
    'ccdb cc_detail'[week_num2] = MAX('ccdb cc_detail'[week_num2])-1))

#### Calculating week over week revenue 

    wow_revenue = DIVIDE(([Current_week_Reveneue] - [Previous_week_Reveneue]),[Previous_week_Reveneue])
    


## Key Insights

![image alt](https://github.com/Baljeet942000/Credit_Card_Financial_Dashboard/blob/3104cd4998967b0583fe851eb08d944071a30ad0/credit_card_transaction_report.jpg)

# Credit Card Transaction Report

This report provides an analysis of credit card transactions, focusing on key performance metrics such as revenue, transaction methods, and customer segmentation.

## Key Insights

#### 1. **Overall Metrics**
- **Total Revenue:** 55M
- **Total Transactions:** 45M
- **Total Interest Earned:** 7.84M
- **Total Transaction Count:** 656K

#### 2. **Revenue by Card Category**
- **Blue Cards:** 
  - Revenue: 36.96M
  - Interest Earned: 6.49M
- **Silver Cards:** 
  - Revenue: 4.59M
  - Interest Earned: 812K
- **Gold Cards:** 
  - Revenue: 2.02M
  - Interest Earned: 374K
- **Platinum Cards:** 
  - Revenue: 953K
  - Interest Earned: 162K

#### 3. **Revenue by Transaction Method**
- **Swipe Transactions:** 35M
- **Chip Transactions:** 17M
- **Online Transactions:** 3M

#### 4. **Quarterly Performance**
- **Q1:**
  - Revenue: 14M
  - Transaction Count: 163.3K
- **Q2:**
  - Revenue: 13.8M
  - Transaction Count: 164.2K
- **Q3:**
  - Revenue: 14.2M
  - Transaction Count: 166.6K
- **Q4:**
  - Revenue: 13.3M
  - Transaction Count: 161.6K

#### 5. **Revenue by Expenditure Type**
- **Bills:** 14M
- **Entertainment:** 10M
- **Fuel and Grocery:** 9M each
- **Food:** 8M
- **Travel:** 6M

#### 6. **Revenue by Customer Segmentation**
- **By Education Type:**
  - Graduates contribute the highest revenue: 22M.
  - High School: 11M.
  - Post-Graduate: 3M, and Doctorate: 2M.
- **By Job Type:**
  - Businessmen contribute the highest revenue: 17M.
  - White-collar professionals: 10M.
  - Self-employed and Government workers: 8M each.
  - Retirees: 5M.

#### 7. **Revenue by Card Category**
- **Blue Cards:** 46M
- **Silver Cards:** 6M
- **Gold Cards:** 2M
- **Platinum Cards:** 1M

## Conclusion
This report highlights the dominance of Blue Cards in revenue generation and Swipe as the most preferred transaction method. It also provides valuable insights into customer behavior segmented by education, job type, and expenditure categories. These findings can guide strategies to maximize revenue and optimize service offerings.






   
