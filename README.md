# How Much Does the Furnace Impact the Gas Bill
test test etst



## 1. Visualizing the Data:

- We will visulize the data we have currently.
- This is from the Ecobee Thermostat from January 1st to December 30th
- Here is the first 5 rows of the data

Date |	Time |	System Setting |    System Mode 	| Calendar Event |	Program Mode | Cool Set Temp (C) |	Heat Set Temp (C) |Current Temp (C) |Current Humidity (%RH)
|--- | --- | --- | --- |--- |--- |--- |--- |--- |--- |
|	2022-01-01 |	00:00:00 |	heat |	heatOff |	NaN |	Sleep| 26.5 |	19.5 |	24.8 |	39.0 
|	2022-01-01 |	00:05:00 |	heat |	heatOff |	NaN |	Sleep| 26.5 |	19.5 |	24.7 |	39.0
|	2022-01-01 |	00:10:00 |	heat |	heatOff |	NaN |	Sleep| 26.5 |	19.5 |	24.6 |	39.0 
|	2022-01-01 |	00:15:00 |	heat |	heatOff |	NaN |	Sleep| 26.5 |	19.5 |	24.5 |	39.0 
|	2022-01-01 |	00:20:00 |	heat |	heatOff |	NaN |	Sleep| 26.5 |	19.5 |	24.5 |	39.0 

5 rows × 10 columns



- This is a graph of the average temperature per day for the whole year:

![image](https://user-images.githubusercontent.com/47339289/217299234-aab32539-dff5-4117-9d65-31449ff77081.png)

- There are no breaks in the data from June 29th 2022 to December 18 2022 therefore we will only be focusing on this range of data


## 2. How much does the furnace cost per day

- In the days the furnace runs how much does it cost?


|Start_Range| End_Range| Amount| Natural_Gas_Supply_Rate (cents/m^3)| M^3 of Gas used|
|--- |--- |--- |--- |--- |
|2022-06-23	|2022-09-01	|109.33	|26.868	  |81|
|2022-09-02	|2022-10-05	|59.51	|27.9027	|57|
|2022-10-06	|2022-11-01	|105.43	|27.9027	|128|
|2022-11-02	|2022-12-02	|164.99	|27.9027	|224|



