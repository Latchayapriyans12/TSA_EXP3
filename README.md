# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 

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
```

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Read the Nile dataset
df = pd.read_csv('Nile.csv')

# Extract the data column (excluding Year)
data = df.select_dtypes(include=np.number).iloc[:, -1].values

# Find the length of data
N = len(data)

# Define lags
lags = range(50)

# Pre-allocate autocorrelation table
autocorr_values = np.zeros(50)

# Calculate mean and variance
mean_data = np.mean(data)
variance_data = np.var(data)

print("Mean of the data:", mean_data)
print("Variance of the data:", variance_data)

# Normalize the data
normalized_data = (data - mean_data) / np.sqrt(variance_data)

print("Normalized data:")
print(normalized_data)

# Calculate autocorrelation
for lag in lags:
    if lag == 0:
        autocorr_values[lag] = 1
    else:
        autocorr_values[lag] = np.sum(
            normalized_data[:-lag] * normalized_data[lag:]
        ) / N

# Display autocorrelation values
print("\nAutocorrelation values:")
print(autocorr_values)

# Plot the ACF graph
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)

plt.title('Autocorrelation Function (ACF) - Nile Dataset')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)

plt.show()

```

### OUTPUT:

<img width="557" height="562" alt="image" src="https://github.com/user-attachments/assets/6ef60483-f40c-4fd0-9cf2-7b1b97c45959" />
<img width="771" height="452" alt="image" src="https://github.com/user-attachments/assets/2881ca58-e0f3-4c00-a691-73275baed4ee" />


### RESULT:

Thus we have successfully implemented the auto correlation function in python.
