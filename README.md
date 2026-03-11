# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 24-02-2026

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:

#### Name : Sasinthar P
#### Reg.No : 212223230199
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load the dataset
data = pd.read_csv("/content/bike_sales_india.csv")   # change to your file name

# Select the column you want to analyze
series = data["Avg Daily Distance"].dropna()

# Convert to numpy array
data_values = series.values

# Length of data
N = len(data_values)

# Define lags
lags = range(35)

# Pre-allocate autocorrelation list
autocorr_values = []

# Mean and variance
mean_data = np.mean(data_values)
variance_data = np.var(data_values)

# Normalize data
normalized_data = (data_values - mean_data) / np.sqrt(variance_data)

# Compute ACF
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data_values[:-lag] - mean_data) * (data_values[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)

# Plot the ACF graph
plt.figure(figsize=(10,6))
plt.stem(lags, autocorr_values)
plt.title("Autocorrelation of Avg Daily Distance")
plt.xlabel("Lag")
plt.ylabel("Autocorrelation")
plt.grid(True)
plt.show()
```

### OUTPUT:

<img width="1082" height="663" alt="Screenshot 2026-03-11 195226" src="https://github.com/user-attachments/assets/d6708d84-b8e7-4906-9a62-26af2edfb7de" />


### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
