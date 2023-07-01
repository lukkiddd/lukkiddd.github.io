---
title : BigQuery - Calculate DAU over MAU
notetype : feed
date : 18-05-2023
---


```sql
WITH engagement AS
(
	SELECT  event_date
			,user_id
	FROM engagement_table
), dau AS
(
	SELECT  event_date
	       ,COUNT(distinct user_id) AS count_dau
	FROM engagement
	GROUP BY  1
) , string_aggregate AS
(
	SELECT  event_date
	       ,STRING_AGG(DISTINCT user_id) AS users
	FROM engagement
	GROUP BY  1
) , rolling_7 AS
(
	SELECT  event_date
	       ,STRING_AGG(users) OVER(ORDER BY UNIX_DATE(event_date) RANGE BETWEEN 6 PRECEDING AND CURRENT ROW) users
	FROM string_aggregate
), wau AS
(
	SELECT  event_date
	       ,(SELECT  COUNT(DISTINCT id) FROM UNNEST (SPLIT(users)) AS id) count_wau
	FROM rolling_7
)


SELECT  *
       ,count_dau/count_wau AS stickiness
FROM dau
INNER JOIN wau USING (event_date)
```