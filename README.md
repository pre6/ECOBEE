# ECOBEE

This is my code:

``` SQL

//SELECT 'SUM' Date, COUNT(Date)
FROM Thermostat
WHERE [System Mode] = 'heatStage1On'
AND Date BETWEEN '2022-06-23' AND '2022-09-01'

UNION ALL


SELECT 'SUM' Date, COUNT(Date)
FROM Thermostat
WHERE [System Mode] = 'heatStage1On'
AND Date BETWEEN '2022-09-02' AND '2022-10-05'

UNION ALL


SELECT 'SUM' Date, COUNT(Date)
FROM Thermostat
WHERE [System Mode] = 'heatStage1On'
AND Date BETWEEN '2022-10-06' AND '2022-11-01'

UNION ALL

SELECT 'SUM' Date, COUNT(Date)
FROM Thermostat
WHERE [System Mode] = 'heatStage1On'
AND Date BETWEEN '2022-11-02' AND '2022-12-02' 
```


Attempt | #1 | #2 | #3 | #4 | #5 | #6 | #7 | #8 | #9 | #10 | #11
--- | --- | --- | --- |--- |--- |--- |--- |--- |--- |--- |---
Seconds | 301 | 283 | 290 | 286 | 289 | 285 | 287 | 287 | 272 | 276 | 269
