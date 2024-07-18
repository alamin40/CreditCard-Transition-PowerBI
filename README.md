# Credit Card Financial Dashboard

## Project Objective
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

## Tutorial Video Content
1. Project Objective
2. Data from SQL
3. Data Processing & DAX
4. Dashboard & Insights
5. Export & Share Project

## Download Data
The project data can be downloaded from this github.


## Import Data to SQL Database
To set up the project, follow these steps:
1. Prepare the CSV file.
2. Create tables in SQL.
3. Import the CSV file into SQL.

Note: Find all SQL queries & project data in the GitHub repository.

## DAX Queries
The project includes several DAX queries to process and analyze the data:

### Age Group
```DAX
AgeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[customer_age] < 30, "20-30",
    'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
    'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
    'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
    'public cust_detail'[customer_age] >= 60, "60+",
    "unknown"
)

IncomeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[income] < 35000, "Low",
    'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] < 70000, "Med",
    'public cust_detail'[income] >= 70000, "High",
    "unknown"
)

week_num2 = WEEKNUM('public cc_detail'[week_start_date])

Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
Current_week_Revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])
    )
)
Previous_week_Revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]) - 1
    )
)


### Overview YTD:
- Overall revenue is $57M
- Total interest is $8M
- Total transaction amount is $46M
- Male customers are contributing more to revenue ($31M) compared to female customers ($26M)
- Blue & Silver credit cards are contributing to 93% of overall transactions
- TX, NY & CA are contributing to 68% of the revenue
- Overall Activation rate is 57.5%
- Overall Delinquent rate is 6.06%

*Note: You can add more insights as needed.*

## Adding to Resume

**Credit Card Financial Dashboard using Power BI:**
- Developed an interactive dashboard using transaction and customer data from a SQL database to provide real-time insights.
- Streamlined data processing & analysis to monitor key performance metrics and trends.
- Shared actionable insights with stakeholders based on dashboard findings to support decision-making processes.

## License
This project is licensed under the MIT License. See the LICENSE file for more details.

## Contact
For any queries, please contact MD AL AMIN at alamin23523@gmail.com
