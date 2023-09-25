# PWC Power BI Virtual work experience - Customer Churn Retention

![PwC Power BI Virtual Case Experience](https://user-images.githubusercontent.com/118357991/227788348-b988c4df-7923-46d6-8af7-102b8042f721.png)

## Table of Contents:

- [Problem Statement](https://github.com/DarvinciVincent/Customer_Churn_Retension_dashboard/edit/main/README.md#problem-statement-)
- [Datasource](https://github.com/DarvinciVincent/Customer_Churn_Retension_dashboard/edit/main/README.md#datasource-)
- [Data Preparation](https://github.com/DarvinciVincent/Customer_Churn_Retension_dashboard/edit/main/README.md#data-preparation)
- [Data Modeling](https://github.com/DarvinciVincent/Customer_Churn_Retension_dashboard/edit/main/README.md#data-modeling)
- [Data Analysis (DAX)](https://github.com/DarvinciVincent/Customer_Churn_Retension_dashboard/edit/main/README.md#data-analysis-dax)
- [Insights](https://github.com/DarvinciVincent/Customer_Churn_Retension_dashboard/edit/main/README.md#insights)
- [Recommendation](https://github.com/DarvinciVincent/Customer_Churn_Retension_dashboard/edit/main/README.md#recommendation)

## Problem Statement:

The purpose of this task is to:

- Define proper KPI's
- Create a dashboard for the retention manager reflecting the KPI's
- Write a short email to him (the engagement partner) explaining your findings, and include suggestions as to what needs to be changed
- Customers who left within the last month
- Services each customer has signed up for: phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies
- Customer account information: how long as a customer, contract, payment method, paperless billing, monthly charges, total charges and number of tickets opened in the categories administrative and technical
- Demographic info about customers – gender, age range, and if they have partners and dependents

## Datasource:

Dataset used for this task was presented by [Pwc](https://www.pwc.ch/en/careers-with-pwc/students/virtual-case-experience.html) and customer churn Retention dataset:

Dataset: [Customer Churn Retention](https://github.com/DarvinciVincent/Customer_Churn_Retension_dashboard/blob/main/02%20Churn-Dataset.xlsx)

## Data Preparation:

Completed the Data transformation in Power Query and the dataset loaded into Microsoft Power BI Desktop for modeling.

Customer Churn dataset is give table named:

- `Customer churn dataset` which has `23 columns and 7043 rows` of observation

Data Cleaning for the dataset was done in the power query editor as follows:

In the new table, one additional conditional columns were added using M-formula:

- loyalty = `SWITCH(TRUE(),'01 Churn-Dataset'[tenure]<=12,"< 1 year",'01 Churn-Dataset'[tenure]<=24,"< 2 years",'01 Churn-Dataset'[tenure]<=36,"< 3 years",'01 Churn-Dataset'[tenure]<=48,"< 4 years", '01 Churn-Dataset'[tenure]<=60,"< 5 years",'01 Churn-Dataset'[tenure]<=72,"< 6 years")`

- Removed Unnecessary columns 
- Removed Unnecessary rows
- Each of the columns in the table were validated to have the correct data type

## Data Modeling:

And then dataset was cleaned and transformed, it was ready to the data modeled.

- The `customer churn` tables as show below:

![Screenshot (39)](https://user-images.githubusercontent.com/118357991/227792100-51216842-8e72-4e48-b740-aab5d2f97541.png)

## Data Analysis (DAX):

Measures used in  all visualization are:

- Churn Rate = 
'DIVIDE(
    CALCULATE(COUNT('01 Churn-Dataset'[Churn]), '01 Churn-Dataset'[Churn] = "Yes"),
    CALCULATE(COUNT('01 Churn-Dataset'[Churn])),
    0)'

- Dependent % = 
'DIVIDE(
    CALCULATE(COUNT('01 Churn-Dataset'[Dependents]), '01 Churn-Dataset'[Dependents]="Yes",'01 Churn-Dataset'[Churn]="Yes"),
    CALCULATE(COUNT('01 Churn-Dataset'[Dependents]),'01 Churn-Dataset'[Churn]="Yes"),
    0)

- Churned Device Protection % = 
'DIVIDE(
    CALCULATE(COUNT('01 Churn-Dataset'[DeviceProtection]),'01 Churn-Dataset'[DeviceProtection] = "Yes", '01 Churn-Dataset'[Churn] = "Yes"), 
    CALCULATE(count('01 Churn-Dataset'[DeviceProtection]), '01 Churn-Dataset'[Churn] = "Yes"),
    0)'
  
- Churned Online Backup % = 
'DIVIDE(
    CALCULATE(COUNT('01 Churn-Dataset'[OnlineBackup]), '01 Churn-Dataset'[Churn] = "Yes", '01 Churn-Dataset'[OnlineBackup] = "Yes"),
    CALCULATE(COUNT('01 Churn-Dataset'[OnlineBackup]), '01 Churn-Dataset'[Churn] = "Yes"),
    0)'

- Churned Online Security % = 
'DIVIDE(
    CALCULATE(COUNT('01 Churn-Dataset'[OnlineSecurity]), '01 Churn-Dataset'[Churn] = "Yes", '01 Churn-Dataset'[OnlineSecurity] = "Yes"),
    CALCULATE(COUNT('01 Churn-Dataset'[OnlineSecurity]), '01 Churn-Dataset'[Churn] = "Yes"),
    0'

- Churned Phone Service % = 
'DIVIDE(
    CALCULATE(COUNT('01 Churn-Dataset'[PhoneService]), '01 Churn-Dataset'[PhoneService] = "Yes", '01 Churn-Dataset'[Churn] = "Yes"),
    CALCULATE(COUNT('01 Churn-Dataset'[PhoneService]), '01 Churn-Dataset'[Churn] = "Yes"),
    0)'

- Churned Streaming Movies % = 
'DIVIDE(
    CALCULATE(COUNT('01 Churn-Dataset'[StreamingMovies]), '01 Churn-Dataset'[Churn] = "Yes", '01 Churn-Dataset'[StreamingMovies] = "Yes"),
    CALCULATE(COUNT('01 Churn-Dataset'[StreamingMovies]), '01 Churn-Dataset'[Churn] = "Yes"),
    0)'

- Churned StreamingTV % = 
'DIVIDE(
    CALCULATE(COUNT('01 Churn-Dataset'[StreamingTV]), '01 Churn-Dataset'[Churn] = "Yes", '01 Churn-Dataset'[StreamingTV] = "Yes"),
    CALCULATE(COUNT('01 Churn-Dataset'[StreamingTV]), '01 Churn-Dataset'[Churn] = "Yes"),
    0)'
  
- Churned Tech Support % = 
'DIVIDE(
    CALCULATE(COUNT('01 Churn-Dataset'[TechSupport]), '01 Churn-Dataset'[Churn] = "Yes", '01 Churn-Dataset'[TechSupport] = "Yes"),
    CALCULATE(COUNT('01 Churn-Dataset'[TechSupport]), '01 Churn-Dataset'[Churn] = "Yes"),
    0)'

- Partner % = 
'DIVIDE(
    CALCULATE(COUNT('01 Churn-Dataset'[Partner]), '01 Churn-Dataset'[Partner]="Yes",'01 Churn-Dataset'[Churn]="Yes"),
    CALCULATE(COUNT('01 Churn-Dataset'[Partner]),'01 Churn-Dataset'[Churn]="Yes"),
    0)'

- Senior Citizen % = 
'DIVIDE(
    CALCULATE(COUNT('01 Churn-Dataset'[SeniorCitizen]), '01 Churn-Dataset'[SeniorCitizen]= 1,'01 Churn-Dataset'[Churn]="Yes"),
    CALCULATE(COUNT('01 Churn-Dataset'[SeniorCitizen]),'01 Churn-Dataset'[Churn]="Yes"),
    0)'

- Revenue = 'CALCULATE(SUM('01 Churn-Dataset'[TotalCharges]), '01 Churn-Dataset'[Churn] = "No")'

- TotalLost = 'sum('01 Churn-Dataset'[TotalCharges]) - [Revenue]'

- Y_Churn = 'CALCULATE(COUNT('01 Churn-Dataset'[Churn]), '01 Churn-Dataset'[Churn] = "Yes")'
  
## Insights:
1. Contract Length and Customer Tenure:<br>
• Customers on Two-Year contracts tend to have longer relationships with the company, while a significant number of customers on Month-to-Month contracts are relatively
new joiners.
2. Risk of Churn Among Recent Month-to-Month Customers:<br>
• The analysis suggests that the company is at risk of losing recently joined customers, especially those on Month-to-Month contracts.
3. Churn Statistics:<br>
• A total of 7,043 customers are at risk of churn, resulting in a churn rate of 27%.<br>
• The yearly charges amount to $16.06 million, while monthly charges sum up to $456.12 thousand.<br>
4. Ticket Support:<br>
• There were 2,955 technical support tickets and 3,632 administrative support tickets opened, indicating a notable level of customer support interaction.
5. Lack of Additional Services Among Churned Customers:<br>
• Most of the churned customers did not sign up for Online Security, Tech Support, or Phone Services, highlighting potential areas for improvement in service adoption.
6. Fiber Optic Services and Churn:<br>
• A significant portion (42%) of the churned customers were using Fiber Optic as their Internet Service, suggesting a potential issue with this service offering.

## Recommendation:
1. Encourage Longer Contracts:<br>
• Consider incentivizing customers to subscribe to One-Year and Two-Year contracts, as this can lead to better customer retention. Emphasize the cost savings associated with
longer contracts.
2. Discounts for Month-to-Month Customers:<br>
• Offer discounts or promotions to customers on Month-to-Month contracts to encourage them to commit to longer contract periods. This can help reduce churn among this segment.
3. Promote Additional Services:<br>
• Educate customers on the benefits of signing up for Online Security and Tech Support, as these services are essential for a seamless experience. Highlight the added value and peace of mind they provide.
4. Increase Sales Targets:<br>
• Increase the sales targets for One-Year and Two-Year contracts by 5% each to actively promote these options.<br>
• Encourage yearly automatic payments with a 5% annual increase to simplify billing for customers and improve revenue predictability

---













