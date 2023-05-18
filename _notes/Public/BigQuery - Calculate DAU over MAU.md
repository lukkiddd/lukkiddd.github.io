---
title : BigQuery - Calculate DAU over MAU
notetype : feed
date : 18-05-2023
---




```sql
WITH users AS
(
	SELECT  distinct user_id
	       ,event_date
	FROM `your_data`
	WHERE event_date > DATE_SUB(CURRENT_DATE(), INTERVAL 56 DAY)
)
SELECT  daily.event_date
       ,COUNT(distinct daily.user_id)   AS DAU
       ,COUNT(distinct weekly.user_id)  AS WAU
       ,COUNT(distinct monthly.user_id) AS MAU
FROM users daily
LEFT JOIN users weekly
ON weekly.event_date BETWEEN date_sub(daily.event_date, interval 7 day) AND daily.event_date
LEFT JOIN users monthly
ON monthly.event_date BETWEEN date_sub(daily.event_date, interval 28 day) AND daily.event_date
GROUP BY  daily.event_date
ORDER BY daily.event_date asc
```