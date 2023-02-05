# How Much Does the Furnace Impact the Gas Bill

I am recent graduate and am currently living at my parents house. In an attempt to understand how much my actions (ie. increasing the temperature) will contribute to the gas bill, I have analysed data available to me through my ECOBEE thermostat. 








This is my code:

``` SQL

SELECT 'SUM' Date, COUNT(Date)
FROM Thermostat
WHERE [System Mode] = 'heatStage1On'
AND Date BETWEEN '2022-11-02' AND '2022-12-02' 
```


Attempt | #1 | #2 | #3 | #4 | #5 | #6 | #7 | #8 | #9 | #10 | #11
--- | --- | --- | --- |--- |--- |--- |--- |--- |--- |--- |---
Seconds | 301 | 283 | 290 | 286 | 289 | 285 | 287 | 287 | 272 | 276 | 269
