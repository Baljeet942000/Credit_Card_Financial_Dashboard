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

   
