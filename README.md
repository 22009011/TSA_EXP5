### Developed by: Thanjiyappan k
### Register Number:212222240108
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on Ev sales dataset.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load your dataset (replace with your file path if needed)
data = pd.read_csv('ev.csv')

# Extract the relevant columns: 'year' and 'value'
data_filtered = data[['year', 'value']].dropna()

# Convert 'year' to datetime to handle it as a time series
data_filtered['year'] = pd.to_datetime(data_filtered['year'], format='%Y')
data_filtered.set_index('year', inplace=True)

# Plot the data
plt.figure(figsize=(10, 6))
plt.plot(data_filtered['value'], label='Data')
plt.title('EV Data Over Time (Year vs. Value)')
plt.xlabel('Year')
plt.ylabel('Value')
plt.legend()
plt.show()

# Performing seasonal decomposition
period = 12  # Assuming yearly seasonality for now
result = seasonal_decompose(data_filtered['value'], model='multiplicative', period=period)

# Plotting the decomposed components
plt.figure(figsize=(12, 8))

# Original data
plt.subplot(4, 1, 1)
plt.plot(data_filtered['value'], label='Original')
plt.title('Original Time Series')
plt.legend()

# Trend component
plt.subplot(4, 1, 2)
plt.plot(result.trend, label='Trend', color='orange')
plt.title('Trend Component')
plt.legend()

# Seasonal component
plt.subplot(4, 1, 3)
plt.plot(result.seasonal, label='Seasonal', color='green')
plt.title('Seasonal Component')
plt.legend()

# Residual component
plt.subplot(4, 1, 4)
plt.plot(result.resid, label='Residual', color='red')
plt.title('Residual Component')
plt.legend()

plt.tight_layout()
plt.show()
```
### OUTPUT:
#### FIRST FIVE ROWS:
![image](https://github.com/user-attachments/assets/a4285aa6-378a-4b26-852b-f01cd562bea0)


#### PLOTTING THE DATA:
![plot](https://github.com/user-attachments/assets/8aa8b7a4-5c09-4bdc-be19-3df957ac81cb)


#### SEASONAL PLOT REPRESENTATION :
![seasonal](https://github.com/user-attachments/assets/3004a1be-87f2-4ccc-968e-9e473705372b)


#### TREND PLOT REPRESENTATION :
![trend](https://github.com/user-attachments/assets/a0c5234e-beff-467b-a142-212ee52ebd75)



#### OVERAL REPRESENTATION:
![original](https://github.com/user-attachments/assets/4e9ef79b-96c3-403a-b74e-ca2cd0b50d5f)


### RESULT:
Thus, The python code for the time series analysis and decomposition is executed successfully.
