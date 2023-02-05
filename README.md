# ECOBEE

This is my code:

```SELECT 'SUM' Date, COUNT(Date)
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
AND Date BETWEEN '2022-11-02' AND '2022-12-02' ```
