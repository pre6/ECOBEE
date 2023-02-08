# How Much Does the Furnace Impact the Gas Bill
test test etst



## 1. Visualizing the Data:

- We will visulize the data we have currently.
- This is from the Ecobee Thermostat from January 1st to December 30th
- Here is the first 5 rows of the data

Date |	Time |	System Setting |    System Mode 	| Calendar Event |	Program Mode | Cool Set Temp (C) |	Heat Set Temp (C) |Current Temp (C) |Current Humidity
|--- | --- | --- | --- |--- |--- |--- |--- |--- |--- |
|	2022-01-01 |	00:00:00 |	heat |	heatOff |	NaN |	Sleep| 26.5 |	19.5 |	24.8 |	39.0 
|	2022-01-01 |	00:05:00 |	heat |	heatOff |	NaN |	Sleep| 26.5 |	19.5 |	24.7 |	39.0
|	2022-01-01 |	00:10:00 |	heat |	heatOff |	NaN |	Sleep| 26.5 |	19.5 |	24.6 |	39.0 
|	2022-01-01 |	00:15:00 |	heat |	heatOff |	NaN |	Sleep| 26.5 |	19.5 |	24.5 |	39.0 
|	2022-01-01 |	00:20:00 |	heat |	heatOff |	NaN |	Sleep| 26.5 |	19.5 |	24.5 |	39.0 

5 rows × 39 columns




Attempt | #1 | #2 | #3 | #4 | #5 | #6 | #7 | #8 | #9 | #10 | #11
--- | --- | --- | --- |--- |--- |--- |--- |--- |--- |--- |---
Seconds | 301 | 283 | 290 | 286 | 289 | 285 | 287 | 287 | 272 | 276 | 269



- This is a graph of the average temperature per day for the whole year:

![image](https://user-images.githubusercontent.com/47339289/217299234-aab32539-dff5-4117-9d65-31449ff77081.png)


## This is what  I found:











This is my code:

``` SQL

SELECT 

Enridge_Bill.Start_Range, 

Enridge_Bill.End_Range,

Enridge_Bill.Amount, 

subq.count_furnace, 

subq.count_days_with_furnace, 

subq1.days_in_range, 

subq1.Minimum minimum_temp_for_range,

Enridge_Bill.Amount/subq1.days_in_range amount_per_day,

Enridge_Bill.Amount/subq1.days_in_range - 1.53985915492958 Amount_per_day_without_baseline,

(((Enridge_Bill.Amount/subq1.days_in_range) - 1.53985915492958) * subq.count_days_with_furnace) / subq.count_furnace Amount_furnace_ever_5_mins

FROM Enridge_Bill

JOIN (
  SELECT COUNT(Date) count_furnace, '2022-06-23' Start_range,COUNT(Distinct Date) count_days_with_furnace
  FROM Thermostat
  WHERE [System Mode] = 'heatStage1On'
  AND Date BETWEEN '2022-06-23' AND '2022-09-01'

  UNION ALL

  SELECT COUNT(Date) count_furnace,'2022-09-02' Start_Range,COUNT(Distinct Date) count_days_with_furnace
  FROM Thermostat
  WHERE [System Mode] = 'heatStage1On'
  AND Date BETWEEN '2022-09-02' AND '2022-10-05'

  UNION ALL

  SELECT COUNT(Date) count_furnace, '2022-10-06' Start_Range,COUNT(Distinct Date) count_days_with_furnace
  FROM Thermostat
  WHERE [System Mode] = 'heatStage1On'
  AND Date BETWEEN '2022-10-06' AND '2022-11-01'

  UNION ALL

  SELECT COUNT(Date) count_furnace, '2022-11-02' Start_Range,COUNT(Distinct Date) count_days_with_furnace
  FROM Thermostat
  WHERE [System Mode] = 'heatStage1On'
  AND Date BETWEEN '2022-11-02' AND '2022-12-02'
) AS subq

ON Enridge_Bill.Start_Range = subq.Start_Range


JOIN(

SELECT COUNT(Distinct Date) days_in_range, '2022-06-23' Start_range, '2022-09-01' End_Range, min([Outdoor Temp (C)]) Minimum
FROM Thermostat
WHERE Date BETWEEN '2022-06-23' AND '2022-09-01'
  
UNION ALL
  
SELECT COUNT(Distinct Date) days_in_range,'2022-09-02' Start_Range, '2022-10-05' End_Range, min([Outdoor Temp (C)]) Minimum
FROM Thermostat
WHERE Date BETWEEN '2022-09-02' AND '2022-10-05'
  
UNION ALL

SELECT COUNT(Distinct Date) days_in_range,'2022-10-06' Start_Range,'2022-11-01' End_Range, min([Outdoor Temp (C)]) Minimum
FROM Thermostat
WHERE Date BETWEEN '2022-10-06' AND '2022-11-01'
  
UNION ALL

SELECT COUNT(Distinct Date) days_in_range,'2022-11-02' Start_Range,'2022-12-02' End_Range, min([Outdoor Temp (C)]) Minimum
FROM Thermostat
WHERE Date BETWEEN '2022-11-02' AND '2022-12-02'

) AS subq1

ON Enridge_Bill.Start_Range = subq1.Start_Range










```

