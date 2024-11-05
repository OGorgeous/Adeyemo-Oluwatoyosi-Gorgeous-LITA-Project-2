# Adeyemo-Oluwatoyosi-Gorgeous-LITA-Project-2

## Project Title: _*Customer Segmentation for a Subscription Service*_

---
### Content
---
[Project Outline](#project-outline)

[Source Datasets](#source-datasets)

[Data Tools Used](#data-tools-used)

[Data Cleaning and Preparations](#data-cleaning-and-preparations)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Insight Visualization](#insight-visualization)

### Project Outline
---
  This Project is aimed at analysing customer data for a subscription service to identify segments and trends. The goal is to understand customer behaviour, track subscription types, and identify important trends in cancellations and renewals. These trends are to be displayed with beautiful dashboard.
  
  ### Source Datasets
---
  The data was provided by The Incubator Hub: Ladies in Tech Africa.
  
### Data Tools Used
---
  - Microsoft Excel [Download here](https://www.microsoft.com)
      1. *For Data cleaning*
      2. *For Analysis*
      3. *For summarizing the customers subscription pattern*
      4. *For Creating Aditional colunm*
      5. *For Creating Metrics that shows the calucation of the avareage subscription duration and the popular subscription*
  - SQL (Structured Query Language)
      1. *For Quering of data*
           
  - Power BI
      1. *For Data Visualisation*
      2. *For transform data to show the column quality, column distribution and column profile. This is to show if there is any error, blank cell or if the columns are valid.*
      3. *For creating new measure that calculate average subscription duration.*
      4. *Using conditional column to create additional column for canceled column*
      5. *Using Q&A to get the number of canceled subscription, the active subscription and the top subcription.

### Data Cleaning and Preparations
---
  In this aspect, which is cleaning and preparation of the dataset, the following was performed;
- Data Loading
- Data Inspection
- Removal of Duplicates
- Adding of necessary column (Subscription Duration Colunm)
- The column quality, distribution and profile were checked 
    
  ### Exploratory Data Analysis
  ---
Exploratory Data Analysis (EDA) is an interative process of analyzing and visualizing data to understand its fundamental structure, patterns, most importantly relationships.
  This involves the use of pivot tables and SQL commands to make an exploration of the data to answer questions about the data, such as;
  - The subcription patterns.
  - The top subscription type.
  - The region with the highest revenue.
  - The month with the highest revenue.
  - To find the total number of customers from each region.
  - To show the most popular subscription type by the number of customer.
  - To expose the customers who canceled their subscription within 6 months.
  - To calculate the average subscription duration for all cuatomers.
  - To show customers with subscriptions longer than 12 months.
  - To calculate total revenue by subscription type.
  - To exhibit the top 3 regions by subscription cancellations.

### Data Analysis
---
  These are some of the queries and formular used;
```EXCEL
=AVERAGE(I2:I33788)
```
```EXCEL
=COUNTIF(D:D,"Basic")
```
```SQL
Select Region,
	count(CustomerId) as Num_of_Customers
	from [dbo].[Customer Data set]
	group by Region
```
```SQL
Select SubscriptionType,
	count(CustomerId) as Num_of_Customers
	from [dbo].[Customer Data set]
	group by SubscriptionType
```
```SQL
Select [CustomerName],[Canceled],[SubscriptionStart]
	from [dbo].[Customer Data set]
	where [Canceled] = 0
	and MONTH([SubscriptionStart]) between 1 and 6
```
```SQL
Select count(CustomerId) as Num_of_Customers,
	avg([Subscription_Duration])
	as Average_Subscription_Duration
	from [dbo].[Customer Data set]
	where [SubscriptionEnd] is not null
```
```SQL
Select [CustomerName], [SubscriptionType], [SubscriptionStart], [SubscriptionEnd]
	from [dbo].[Customer Data set]
	where 
	datediff(month,[SubscriptionStart],[SubscriptionEnd])>=12
```
```SQL
Select [SubscriptionType],
	sum([Revenue]) as Total_Revenue
	from [dbo].[Customer Data set]
	group by [SubscriptionType]
```
```SQL
Select Top 3 [Region],[Canceled]
	from [dbo].[Customer Data set]
```
```SQL
Select sum
	(case when [Canceled] = 0
	then 1 else 0 end) as Active_Subscriptions,
	sum(case when [Canceled] = 1
	then 1 else 0 end) as Canceled_Subscriptions
	from [dbo].[Customer Data set]
```

### Insight Visualisation
---


### Conclusion
