# credit_card_financial_report
OBJECTIVE - To develop two comprehensive credit card weekly dashboards that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

📊 Project Insights: Week 53 (31st Dec) 
WoW change:
Revenue increased by 28.8%
Total transaction amount increased by 35.04% week by week

Overview YTD:
Overall revenue: $57M
Total interest: $8M
Total transaction amount: $46M
Male customers' contribution: $31M, Female customers' contribution: $26M
Blue & Silver credit cards contribute to 93% of overall transactions
TX, NY & CA contribute to 68%
Overall activation rate: 57.5%
Overall delinquent rate: 6.06%

🔧 Tools and Techniques:
Data processing and cleaning

DAX queries for detailed analysis:

AgeGroup:
AgeGroup = SWITCH(TRUE(), 'public cust_detail'[customer_age] < 30, "20-30", 
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
 'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
 'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
 'public cust_detail'[customer_age] >= 60, "60+", "unknown" )

IncomeGroup:
IncomeGroup = SWITCH(TRUE(),
 'public cust_detail'[income] < 35000, "Low",
 'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] < 70000, "Med",
 'public cust_detail'[income] >= 70000, "High",
 "unknown"
)

Revenue Calculation:
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
Current_week_Revenue = CALCULATE(SUM('public cc_detail'[Revenue]), FILTER(ALL('public cc_detail'), 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))
Previous_week_Revenue = CALCULATE(SUM('public cc_detail'[Revenue]), FILTER(ALL('public cc_detail'), 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

📈 Insights and Recommendations:
Based on the data analysis, I have identified several key insights and recommendations to improve credit card operations:
Focus on marketing Blue & Silver credit cards as they contribute significantly to transactions.
Enhance customer engagement strategies in TX, NY, and CA to capitalize on their high contribution rates.
Develop targeted financial products and services for male customers, who contribute more to revenue.

'credit_card_transaction_report.pdf' and 'credit_card_customer_report.pdf' includes the main project dashboards.
CREDIT CARD weekly financial report.pdf - Includes Project Objective , DAX Queries and project Insights.

