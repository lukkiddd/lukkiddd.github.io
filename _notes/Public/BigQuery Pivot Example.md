---
title : BigQuery Pivot
notetype : feed
date : 2023-08-23
---

How to pivot multiple columns in BigQuery

```
SELECT  *
FROM
(
	SELECT  date, event_name, user_id, count(*) as transactions
	FROM TABLE
	WHERE event_name IN ('impression', 'click')
	GROUP BY  1
	         ,2
			 ,3
) PIVOT(
	COUNT(distinct user_id) AS login_users,
	SUM(transactions) AS total_txn]
	FOR event_name IN ( 'impression', 'click' )
)
```