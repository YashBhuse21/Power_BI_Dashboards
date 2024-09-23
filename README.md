# Financial Dashboard of Credit Card 

𝐏𝐫𝐨𝐣𝐞𝐜𝐭 𝐎𝐛𝐣𝐞𝐜𝐭𝐢𝐯𝐞:

To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

𝐒𝐭𝐞𝐩 𝟏: 𝐈𝐦𝐩𝐨𝐫𝐭 𝐝𝐚𝐭𝐚 𝐭𝐨 𝐒𝐐𝐋 𝐝𝐚𝐭𝐚𝐛𝐚𝐬𝐞:

1. Prepare csv file
2. Create tables in SQL
3. Import csv file into SQL

𝐒𝐭𝐞𝐩 𝟐: 𝐃𝐚𝐭𝐚 𝐩𝐫𝐞𝐩𝐚𝐫𝐚𝐭𝐢𝐨𝐧 𝐮𝐬𝐢𝐧𝐠 𝐃𝐀𝐗 𝐐𝐮𝐫𝐢𝐞𝐬 𝐢𝐧 𝐏𝐨𝐰𝐞𝐫 𝐁I

1. Create New Column using 'SWITCH' function for columns "AgeGroup & IncomeGroup"

- AgeGroup = SWITCH(
  TRUE(),
  'public cust_detail'[customer_age] < 30, "20-30",
  'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
  'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
  'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
  'public cust_detail'[customer_age] >= 60, "60+",
  "unknown"
   )

- IncomeGroup = SWITCH(
  TRUE(),
  'public cust_detail'[income] < 35000, "Low",
  'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
  'public cust_detail'[income] >= 70000, "High",
  "unknown"
   )

2. Create New column for 'Revenue' 
- Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

3. Create New Column using 'WEEKNUM' function 
- week_num2 = WEEKNUM('public cc_detail'[week_start_date])

4. Create New Measures
- Current_week_Reveneue = CALCULATE(
  SUM('public cc_detail'[Revenue]),
  FILTER(
  ALL('public cc_detail'),
  'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))

- Previous_week_Reveneue = CALCULATE(
  SUM('public cc_detail'[Revenue]),
  FILTER(
  ALL('public cc_detail'),
  'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

𝐒𝐭𝐞𝐩 𝟑: 𝐂𝐫𝐞𝐚𝐭𝐞 𝐚𝐧 𝐈𝐧𝐭𝐞𝐫𝐚𝐜𝐭𝐢𝐯𝐞  𝐃𝐚𝐬𝐡𝐛𝐨𝐚𝐫𝐝𝐬 𝐨𝐧 𝐏𝐨𝐰𝐞𝐫 𝐁𝐈

![Transaction_Report](https://github.com/user-attachments/assets/2c0366d6-4289-41b5-854d-782149f5f1f2)

![Customer_Report](https://github.com/user-attachments/assets/5b234e22-6994-4f91-8a35-be7944197661)


𝐏𝐫𝐨𝐣𝐞𝐜𝐭 𝐈𝐧𝐬𝐢𝐠𝐡𝐭𝐬: 𝐄𝐯𝐚𝐥𝐮𝐚𝐭𝐞 𝐟𝐨𝐫 𝐖𝐞𝐞𝐤 𝟓𝟑 (𝟑𝟏𝐬𝐭 𝐃𝐞𝐜)

1. 𝐖𝐞𝐞𝐤_𝐎𝐧_𝐖𝐞𝐞𝐤 𝐜𝐡𝐚𝐧𝐠𝐞:
- Revenue increased by 28.8%,
- Total Transaction Amt increased by 2.22% 
- Customer count increased by 1.74%

2. 𝐎𝐯𝐞𝐫𝐯𝐢𝐞𝐰 𝐘𝐞𝐚𝐫_𝐓𝐨_𝐃𝐚𝐭𝐞:
- Overall revenue is 57M
- Total interest is 8M
- Total transaction amount is 46M
- Male customers are contributing more in revenue 31M, female 26M
- Blue & Silver credit card are contributing to 93% of overall transactions
- TX, NY & CA is contributing to 68%
- Overall Activation rate is 57.5%
- Overall Delinquent rate is 6.06%

𝐂𝐨𝐧𝐜𝐥𝐮𝐬𝐢𝐨𝐧:
- Developed an interactive dashboard using transaction and customer data from a SQL database, 
  to provide real-time insights.
- Streamlined data processing & analysis to monitor key performance metrics and trends.
- Shared actionable insights with stakeholders based on dashboard findings to support decision- 
  making processes.












