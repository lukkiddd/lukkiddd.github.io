---
title : All about Churn
notetype : feed
date : 19-02-2023
---


- [[Intervention to reduce churn]]
- Churn is hard to fight
	- Churn is hard to prevent
	- [[Churn is hard to predict]]
	- Reducing churn is a team effort
- Great Customer Metrics
	- Customers who use the product features more than five times a month churn at half the rate of customers who use it only once a month or less.
- [[Products with recurring user interactions]]


#### Chapter 2
- How to calculate churn/churn rate/retention rate
- What is the subscription database look like
- Net retention
	- = recurring revenues
	- = MRRretained account/MRRstart
	- MRR = Monthly reucrring revenues
	- Net retention combines the effects of churns, upsells and down sells*
	- Negative churn -- when the increase in revenue from upsells is greater than the combined negative effect of down sells and churns
	- **Impressive to report to investors**
- Standard account-based churn
	- uneffected by upsells, down sells and expiration of discounts
	- *outer join*
	- Use Standard account-based churn when every users pay with the same amount.
- Activity (event-based) churn for non-subscription products
	- Define of churn
		- Do not active for a time period
		- Active =
			- Do some certain specific events
			- Has minimum number of events
			- Purchases or has revenue generated from ads at some minimum amount
- Advanced churn: Monthly recurring revenue (MRR) churn
	- Use MRR churn when users has multiple pay variations
	- MRR Churn = (MRRchurned accounts + MRRdown sell) / MRRstart
- Standard Churn > MRR Churn > Net retention Churn
	- Accounts that pay more churn less.
- Churn rate conversion
	- Month to Year
		- Churn = 100% - (1 - churn_month) ^12
	- Year to Month
		- Churn = 100% - (1 - churn_year) ^1/12
	- Any p days period
		- Churn = 100% - (1 - c)^365/p
	- Measuring churn over a time window that is different from the typical subscription length can result in errors in the churn rate
- Seasonality
	- Handle seasonality using time-series analysis


#### Chapter 3
- Metric QA
	- How Metrics change over time
		- Missing data in some days
		- Extream value in some fields
		- % account that has metrics
- Event QA
	- How events change over time
		- Missing/Extream - by counts per day
		- event  per accounts
- Anomaly detection
- 3.9 - Selecting measurekent period
	- If an event is rare, use a longer period
	- Short-time period are more responsive to changes, less sensitive at picking up accounts with low event levels
	- For subscription with a fixed term like a month or a year, behavioral measurements should be similar in time scale to the term of the subscription
	- 