# How Much Does the Furnace Impact the Gas Bill?


## 1. Visualizing the Data:

The dataset used is from the house thermostat we got in June 29 2022. The data recorded various parameters every 5 minutes till Dec 18th. These are the first 5 row and 10 columns of the data.						


Date |	Time |	System Setting |    System Mode 	| Calendar Event |	Program Mode | Cool Set Temp (C) |	Heat Set Temp (C) |Current Temp (C) |Current Humidity (%RH)
|--- | --- | --- | --- |--- |--- |--- |--- |--- |--- |
|	2022-06-29 |	18:05:00 |	off |	heatOff |	NaN |	Home| 25.5 |	20.5 |	25 |	59
|	2022-06-29 |	18:10:00 |	off |	heatOff |	NaN |	Home| 25.5 |	20.5 |	25 |	60
|	2022-06-29 |	18:15:00 |	off |	heatOff |	NaN |	Home| 25.5 |	20.5 |	25.1 |	59
|	2022-06-29 |	18:20:00 |	off |	heatOff |	NaN |	Home| 25.5 |	20.5 |	25.1 |	60
|	2022-06-29 |	18:25:00 |	off |	heatOff |	NaN |	Home| 25.5 |	20.5 |	25.1 |	60

49574 rows × 39 columns



- This is a graph of the average temperature per day in the range (python code at the bottom):

![image](https://user-images.githubusercontent.com/47339289/218004722-7e02fd14-52b3-4e14-9a14-e078b390c45c.png)


## 2. How much does the furnace cost per day?

In the days the furnace runs how much does it cost? Roughly how much does the furnace cost when it turns one once?

This table represents the information in the gas bill.

|Start_Range| End_Range| Amount| Natural_Gas_Supply_Rate (cents/m^3)| M^3 of Gas used|
|--- |--- |--- |--- |--- |
|2022-06-23	|2022-09-01	|109.33	|26.868	  |81|
|2022-09-02	|2022-10-05	|59.51	|27.9027	|57|
|2022-10-06	|2022-11-01	|105.43	|27.9027	|128|
|2022-11-02	|2022-12-02	|164.99	|27.9027	|224|


- The average spent on gas between these 4 ranges is $3.45/day. This was done by taking the total amount in a range and dividing by the number of days in range. Then we averaged the three value for the three ranges

$$ \frac{Total}{days}  $$

- To roughly find the amount the furnace cost per day, a baseline amount was estimated. The baseline is taken from the first range in which the furnace was not used once. This was on average $1.54 / day.
- Next we subract this baseline from the average cost per day for all the other ranges

Example: With the range from Oct 06 to Nov 11

$$ 3.90 - 1.54 \\approx 2.36 $$

- Then we multiply the value by the number of days the furance was on. This is the average amount per day the furnace costs!

$$ 2.36* 23 \\approx 128.56 $$

- We can furthur divide by the number of time the furnace was on in the corresponding range to get a rough idea bout how much the furnace cost each time it turns on.

$$128.56/546 \\approx 0.099413$$


|Start_Range| End_Range| Amount|Times furnace On| Days furnace was on| Total days|amount per day|amount without the baseline|Amount Furnace costs every 5 mins|
|--- |--- |--- |--- |--- |--- |--- |--- |--- |
|2022-06-23|	2022-09-01|	109.33|	   0|	 0|	71|	1.53985915492958|	-0.0|          NULL|
|2022-09-02|	2022-10-05|	59.51	|   57|	 7|	34|	1.75029411764706|	0.21043496271748|	0.04332484526536|
|2022-10-06|	2022-11-01|	105.43|	 546|	23|	27|	3.90481481481482|	2.36495565988524|	0.09962267431751|
|2022-11-02|	2022-12-02|	164.99|	1355|	30|	31|	5.32225806451613|	3.78239890958655|	0.08374314928974|


### Assumptions:
- The other appliance and things that use gas are not accounted for. 
- The number of degrees outside affects the amount of times the furnace turns on.

## 3. When will I break even with my thermostat?

My thermostat cost $330. This will be compared to a standard government issued thermostat which holds 22 degrees celcius. The cycle the thermostat was on is:

|Start Time|End Time| Mode| Temperature|
|--- |--- |--- |--- |
|00:00:00|05:30:00|Sleep|19.5|
|05:30:00|22:30:00|Home|22|
|22:30:00|23:59:59|Home|22|

There is 17 hours in which the furance is turned on. Therefore the amount per day for gas actually pertains to 17 hours in which the furnace is on. Now we need to find out how much it would cost for the whole day:

$$ \frac{$3.54}{17hrs} = \frac{x}{24hrs} $$

$$ x \\approx 5.00$$

It is around $5.00 per day if the temperature was kept at 22 degrees celcius each day. The furance (from the ranges before) turns on at September 29th to Dec 18th. This is 81 days. If the furnace was set at 22 degrees the whole time, the amount would be:

$$ 5.00 * 81 = 405 $$
$$ 3.45 * 81 = 286.47 $$

$$405-286.47 = 118.26$$

We saved about 118.26

I esitmate in Canada we will have the furnace on for 8 months, which is 241 days

$$ 5.00 * 241 = 1205 $$
$$ 3.45 * 241 = 853.14 $$
$$ 1205 - 853.14 = 351.86$$

In 8 months you can break even with the thermostat.

### Assumptions:

We assume the the furnace would be running everyday.
Some days the furnace will run loger because it is colder
The cycle we set wasnt perfect. These were the average values


## 4. When will I have to adjust the temperature to save 10%?

Per day it is $3.54. If we saved 10% of that it would be:

$$ 3.54 * 0.1 = 0.354 $$

$$ 3.54 - 0.354 \\approx 3.19 $$

$$ \frac{3.54}{17} = \frac{3.19}{x} $$

$$ x \\approx 15 $$

If we have a 15 hr period where the furnace is on and the other 9 hours the furnace is not on we should save 10%

### Assumptions:

These assumptions will be simillar to the other assumptions. We are assuming the gas bill is just from the furnace. Also we assume that the furnace will turn on the same amount per day despite the temperature outside


## Queries:
1. Visualization code
- Look in Jupyter notebook
```python
Average_temp = df.groupby('Date', as_index=False, sort=False)['Current Temp (C)'].mean()
Average_humidity = df.groupby('Date', as_index=False, sort=False)['Current Humidity (%RH)'].mean()

# Combine both tables:

result = pd.concat([Average_temp, Average_humidity["Current Humidity (%RH)"]], axis=1, join="inner")
```


2. How much does the furnace cost per day:
```sql

SELECT 

Enridge_Bill.Start_Range, 

Enridge_Bill.End_Range,

Enridge_Bill.Gas_Supply_Charge, 

Enridge_Bill.[Meters Cubed Used], 

subq.count_furnace, 

subq.count_days_with_furnace, 

subq1.days_in_range, 

ROUND(CAST(Enridge_Bill.[Meters Cubed Used] AS FLOAT)/subq1.days_in_range , 3) m3_per_day,

Enridge_Bill.Gas_Supply_Charge/subq1.days_in_range amount_per_day,

Enridge_Bill.Gas_Supply_Charge/subq1.days_in_range - 1.53985915492958 Amount_per_day_without_baseline,

(((Enridge_Bill.Gas_Supply_Charge/subq1.days_in_range) - 1.53985915492958) * subq.count_days_with_furnace) / subq.count_furnace Amount_furnace_ever_5_mins

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

