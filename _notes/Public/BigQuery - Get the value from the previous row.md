---
title : BigQuery - Get the value from the previous row
notetype : feed
date : 22-11-2022
---


Recently I came across the use-case that, we would like to see the page "BEFORE" the users made the purchase event from the interactions data.

To do this, one of the option is "Window function".

### Window Function

There are really useful examples on [Google website](https://cloud.google.com/bigquery/docs/reference/standard-sql/window-function-calls#window_function_examples). You can check out, it may already have the use-case you are looking for.


### Use-case: Page before Purchase event

Starting with the events data

| event_timestamp | event_name | user_id | page |
|-------------------|-------------|---------|-----|
| 2022-11-22 10:00 | screen_view | 5 | home |
| 2022-11-22 10:05 | click | 5 | home |
| 2022-11-22 10:06 | screen_view | 5 | item_detail |
| 2022-11-22 10:06 | purchase | 5 | checkout |
| 2022-11-22 10:03 | screen_view | 7 | home |
| 2022-11-22 10:06 | click | 7 | home |
| 2022-11-22 10:08 | screen_view | 7 | category_page |
| 2022-11-22 10:10 | click | 7 | category_page |
| 2022-11-22 10:15 | screen_view | 7 | item_detail |
| 2022-11-22 10:18 | purchase | 7 | checkout |

To see the previous page we can just simply use the "window" function

```sql
SELECT
    event_timestamp
    ,event_name
    ,user_id
    ,page
    ,FIRST_VALUE(page) OVER(partition by user_id ORDER BY event_timestamp_ict asc ROWS 1 PRECEDING) as previous_1_page
    ,FIRST_VALUE(page) OVER(partition by user_id ORDER BY event_timestamp_ict asc ROWS 2 PRECEDING) as previous_2_page
FROM INTERACTION_TABLE
```

The result should be

| event_timestamp   | event_name  | user_id | page | previous_1_page | previous_2_page |
|-------------------|-------------|---------|------|-------------------|------------------|
| 2022-11-22 10:00  | screen_view | 5       | home | null | null |
| 2022-11-22 10:05  | click       | 5       | home | home | null |
| 2022-11-22 10:06  | screen_view | 5       | item_detail | home | home |
| 2022-11-22 10:06  | purchase    | 5       | checkout | item_detail | home |
| 2022-11-22 10:03  | screen_view | 7       | home | null | null |
| 2022-11-22 10:06  | click       | 7       | home | home | null |
| 2022-11-22 10:08  | screen_view | 7       | category_page | home | home |
| 2022-11-22 10:10  | click       | 7       | category_page | category_page | home |
| 2022-11-22 10:15  | screen_view | 7       | item_detail | category_page | category_page |
| 2022-11-22 10:18  | purchase    | 7       | checkout | item_detail | category_page |


Then, we can select only the `purchase` event and observe the page users have pass through.

| event_timestamp | event_name | user_id | page | previous_1_page | previous_2_page |
|-------------------|-------------|---------|-----|-------------------|------------------|
| 2022-11-22 10:06 | purchase | 5 | checkout | item_detail | home |
| 2022-11-22 10:18 | purchase | 7 | checkout | item_detail | category_page |

Finally, we can see where the users come from before they made the purchase!.