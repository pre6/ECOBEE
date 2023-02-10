# How Much Does the Furnace Impact the Gas Bill?


## 1. Visualizing the Data:

The dataset used is from the house thermostat we got in June 29 2022. The data recorded various parameters ever 5 minutes till Dec 18th. These are the first 5 row of the data. 									


Date |	Time |	System Setting |    System Mode 	| Calendar Event |	Program Mode | Cool Set Temp (C) |	Heat Set Temp (C) |Current Temp (C) |Current Humidity (%RH)
|--- | --- | --- | --- |--- |--- |--- |--- |--- |--- |
|	2022-06-29 |	18:05:00 |	off |	heatOff |	NaN |	Home| 25.5 |	20.5 |	25 |	59
|	2022-06-29 |	18:10:00 |	off |	heatOff |	NaN |	Home| 25.5 |	20.5 |	25 |	60
|	2022-06-29 |	18:15:00 |	off |	heatOff |	NaN |	Home| 25.5 |	20.5 |	25.1 |	59
|	2022-06-29 |	18:20:00 |	off |	heatOff |	NaN |	Home| 25.5 |	20.5 |	25.1 |	60
|	2022-06-29 |	18:25:00 |	off |	heatOff |	NaN |	Home| 25.5 |	20.5 |	25.1 |	60

49574 rows × 39 columns



- This is a graph of the average temperature per day in the range:

![image](https://user-images.githubusercontent.com/47339289/218004722-7e02fd14-52b3-4e14-9a14-e078b390c45c.png)


## 2. How much does the furnace cost per day

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
- Then we multiply the value by the number of days the furance was on. This is the average amount per day the furnace costs!
- We can furthur divide by the number of time the furnace was on in the corresponding range to get a rough idea bout how much the furnace cost each time it turns on.


|Start_Range| End_Range| Amount|Times furnace On| Days furnace was on| Total days|amount per day|amount without the baseline|Amount Furnace costs every 5 mins|
|--- |--- |--- |--- |--- |--- |--- |--- |--- |
|2022-06-23|	2022-09-01|	109.33|	   0|	 0|	71|	1.53985915492958|	-0.0|          NULL|
|2022-09-02|	2022-10-05|	59.51	|   57|	 7|	34|	1.75029411764706|	0.21043496271748|	0.04332484526536|
|2022-10-06|	2022-11-01|	105.43|	 546|	23|	27|	3.90481481481482|	2.36495565988524|	0.09962267431751|
|2022-11-02|	2022-12-02|	164.99|	1355|	30|	31|	5.32225806451613|	3.78239890958655|	0.08374314928974|


## 3. When will I break even with my thermostat?

My thermostat cost $330. This will be compared to a standard government issued thermostat which holds 22 degrees celcius. The cycle the thermostat was on is:

|Start Time|End Time| Mode| Temperature|
|--- |--- |--- |--- |
|00:00:00|05:30:00|Sleep|19.5|
|05:30:00|22:30:00|Home|22|
|22:30:00|23:59:59|Home|22|

$$ \frac{$3.54}{17hrs} = \frac{x}{24hrs} $$

math math
table 
table
## 4. When will I have to adjust the temperature to save 10%???


math math 
table 
table
