### **Interactive Project Page**: 
[>>>Click Here<<<
](https://jb0hn.github.io/ApplicationLog/applications_log.html)
### **Objective**: 
To analyze and visualize the frequency and distribution of applications over time.

### **Data Source**: 
Excel file named `applications_analytics_randomized.xlsx`.

**IMPORTANT: Data was generated randomly.**

```python
# Randomize Date
random_shift = pd.Timedelta(np.random.randint(-365, 365), 'D')
df['Date'] = df['Date'] + random_shift

# Randomize Number of Applications using a normal distribution
mean_applications = df['Number of Applications'].mean()
std_dev_applications = df['Number of Applications'].std()

randomized_applications = np.random.normal(mean_applications, std_dev_applications, len(df))
randomized_applications = np.round(randomized_applications)  # Rounding to get whole numbers
randomized_applications = np.clip(randomized_applications, 0, None)  # Ensuring no negative values

df['Number of Applications'] = randomized_applications

# Overwrite the original Excel file with the randomized data
df.to_excel('./applications_analytics_randomized.xlsx', engine='openpyxl', index=False)
```

### **Key Data Points**:

1. **Date**: The date when the applications were received.
2. **Number of Applications**: The count of applications received on that specific date.

### **Processing Steps**:

1. **Data Import**:
    - Loaded the data from the Excel file using the `pandas` library.
    - Converted the 'Date' column from a string to a datetime format.

2. **Weekly Analysis**:
    - Extracted the week number of the year for each date and stored it in a new column 'Week_Number'.
    - Aggregated the number of applications per week by summing them up.

3. **Monthly Analysis**:
    - Extracted the month for each date and stored it in a new column 'Month'.
    - Aggregated the number of applications per month by summing them up, and ensured all months were present.

4. **Descriptive Statistics**:
    - Calculated various statistics such as mean, standard deviation, min, max, and rolling averages for both the weekly and monthly datasets.

### **Visualizations**:

1. **Seaborn & Matplotlib**: 
    - Created line plots of the number of applications over time.
    - Added a trend line to show the overall trend.
    - Used a custom color palette for a pleasing aesthetic.

2. **Plotly**:
    - Introduced interactive visualizations that let users hover over data points to view details and zoom in/out for better granularity.

### **Additional Notes**:

- You wanted to anonymize your dataset for portfolio purposes, and in the process, you accidentally lost the original data.
- We recreated the daily dataset from your weekly and monthly data using randomization based on the general patterns and statistics you provided.
- The dataset is stored in a Jupyter Notebook, and it's important to take care with version control to avoid future data losses or overwrites.

### **Recommendations for Future Development**:

1. **Enhanced Visualizations**: Introduce more interactive plots, perhaps comparing year-on-year or quarter-on-quarter application numbers.
2. **Data Enrichment**: If you have other related datasets or additional features, they can be added to provide more depth to the analysis, such as the source of the applications, the demographic details of the applicants, etc.

