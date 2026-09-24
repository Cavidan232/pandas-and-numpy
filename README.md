# pandas-and-numpy


---

# 🚀 Complete NumPy & Pandas Cheatsheet

A comprehensive, all-in-one guide and reference sheet for **NumPy** and **Pandas** in Python.

---

## 📌 Table of Contents

1. [NumPy Basics](https://www.google.com/search?q=%25231-numpy-basics&utm_source=gemini)
2. [Array Operations & Math](https://www.google.com/search?q=%25232-array-operations--math&utm_source=gemini)
3. [Indexing, Slicing & Reshaping](https://www.google.com/search?q=%25233-indexing-slicing--reshaping&utm_source=gemini)
4. [Advanced NumPy (Broadcasting, Random, Stacking)](https://www.google.com/search?q=%25234-advanced-numpy&utm_source=gemini)
5. [Pandas Data Structures (Series & DataFrame)](https://www.google.com/search?q=%25235-pandas-data-structures&utm_source=gemini)
6. [Data Loading & Exporting](https://www.google.com/search?q=%25236-data-loading--exporting&utm_source=gemini)
7. [Data Inspection & Selection](https://www.google.com/search?q=%25237-data-inspection--selection&utm_source=gemini)
8. [Data Cleaning & Transformation](https://www.google.com/search?q=%25238-data-cleaning--transformation&utm_source=gemini)
9. [Aggregation, GroupBy & Pivot Tables](https://www.google.com/search?q=%25239-aggregation-groupby--pivot-tables&utm_source=gemini)
10. [Merging, Joining & Concatenating](https://www.google.com/search?q=%252310-merging-joining--concatenating&utm_source=gemini)
11. [Time Series Handling](https://www.google.com/search?q=%252311-time-series-handling&utm_source=gemini)

---

## 1. NumPy Basics

```python
import numpy as np

# -----------------------------------------------------------------------------
# 1.1 Creating Arrays
# -----------------------------------------------------------------------------
arr_1d = np.array([1, 2, 3, 4, 5])                  # 1D array
arr_2d = np.array([[1, 2, 3], [4, 5, 6]])           # 2D array
arr_3d = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]]) # 3D array

zeros = np.zeros((3, 3))                            # 3x3 array of zeros
ones = np.ones((2, 4))                              # 2x4 array of ones
full = np.full((2, 2), 7)                           # 2x2 array with value 7
eye = np.eye(4)                                     # 4x4 Identity matrix
empty = np.empty((2, 3))                            # Uninitialized array

arange_arr = np.arange(0, 10, 2)                    # [0, 2, 4, 6, 8]
linspace_arr = np.linspace(0, 1, 5)                 # 5 linearly spaced points from 0 to 1

# -----------------------------------------------------------------------------
# 1.2 Array Attributes
# -----------------------------------------------------------------------------
arr = np.array([[1, 2, 3], [4, 5, 6]])

print(arr.ndim)     # Number of dimensions (2)
print(arr.shape)    # Shape tuple (2, 3)
print(arr.size)     # Total number of elements (6)
print(arr.dtype)    # Data type of elements (e.g., int64)
print(arr.itemsize) # Size of each element in bytes
print(arr.nbytes)   # Total bytes consumed by array

```

---

## 2. Array Operations & Math

```python
a = np.array([10, 20, 30, 40])
b = np.array([1, 2, 3, 4])

# Element-wise Arithmetic
add = a + b         # np.add(a, b) -> [11, 22, 33, 44]
sub = a - b         # np.subtract(a, b)
mul = a * b         # np.multiply(a, b)
div = a / b         # np.divide(a, b)
pow_arr = a ** 2    # np.power(a, 2)
mod = a % 3         # np.mod(a, 3)

# Universal Functions (ufuncs)
np.sqrt(a)          # Square root
np.exp(a)           # Exponential (e^x)
np.log(a)           # Natural logarithm
np.log10(a)         # Log base 10
np.sin(a)           # Trigonometric Sine
np.abs([-1, -2])    # Absolute values

# Summary Statistics
arr = np.array([[1, 2, 3], [4, 5, 6]])

np.sum(arr)         # Sum of all elements (21)
np.sum(arr, axis=0) # Sum along columns ([5, 7, 9])
np.sum(arr, axis=1) # Sum along rows ([6, 15])
np.mean(arr)        # Mean
np.std(arr)         # Standard deviation
np.var(arr)         # Variance
np.min(arr)         # Minimum value
np.max(arr)         # Maximum value
np.argmin(arr)      # Index of minimum element
np.argmax(arr)      # Index of maximum element
np.cumsum(arr)      # Cumulative sum
np.percentile(arr, 50) # 50th percentile (median)

```

---

## 3. Indexing, Slicing & Reshaping

```python
# -----------------------------------------------------------------------------
# 3.1 Indexing & Slicing
# -----------------------------------------------------------------------------
arr = np.array([10, 20, 30, 40, 50])
print(arr[0])       # First element (10)
print(arr[1:4])     # Slicing [20, 30, 40]
print(arr[::-1])    # Reverse array

matrix = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(matrix[0, 1])     # Element at row 0, column 1 (2)
print(matrix[:2, 1:])   # First 2 rows, columns from index 1 onwards

# Boolean Masking
mask = arr > 25
print(arr[mask])        # Elements > 25 -> [30, 40, 50]

# Fancy Indexing
indices = [0, 2, 4]
print(arr[indices])     # [10, 30, 50]

# -----------------------------------------------------------------------------
# 3.2 Reshaping & Manipulations
# -----------------------------------------------------------------------------
arr = np.arange(12)               # [0, 1, 2, ..., 11]
reshaped = arr.reshape(3, 4)      # Convert to 3x4 matrix
flattened = reshaped.flatten()    # Convert back to 1D (copy)
ravelled = reshaped.ravel()       # Convert back to 1D (view)

transposed = reshaped.T           # Transpose matrix (4x3)
np.swapaxes(reshaped, 0, 1)      # Swap axes

```

---

## 4. Advanced NumPy

```python
# -----------------------------------------------------------------------------
# 4.1 Stacking and Splitting
# -----------------------------------------------------------------------------
a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6], [7, 8]])

v_stacked = np.vstack((a, b))    # Vertical stack
h_stacked = np.hstack((a, b))    # Horizontal stack
c_stacked = np.concatenate((a, b), axis=0)

split_arr = np.array([1, 2, 3, 4, 5, 6])
np.split(split_arr, 3)           # Split into 3 equal arrays

# -----------------------------------------------------------------------------
# 4.2 Random Module
# -----------------------------------------------------------------------------
np.random.seed(42)               # Set seed for reproducibility

rand_uniform = np.random.rand(3, 3)     # Uniform distribution [0, 1)
rand_normal = np.random.randn(3, 3)     # Standard normal distribution
rand_ints = np.random.randint(1, 10, (2, 2)) # Integers between 1 and 10
choice = np.random.choice([10, 20, 30], size=5) # Random samples from list
np.random.shuffle(arr)                  # Shuffle array in-place

# -----------------------------------------------------------------------------
# 4.3 Linear Algebra & Useful Functions
# -----------------------------------------------------------------------------
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

dot_prod = np.dot(A, B)          # Dot product
matmul = A @ B                   # Matrix multiplication
inv_A = np.linalg.inv(A)         # Inverse of matrix
det_A = np.linalg.det(A)         # Determinant
eigvals, eigvecs = np.linalg.eig(A) # Eigenvalues & Eigenvectors

# Conditional Replacement
arr = np.array([1, 2, 3, 4, 5])
result = np.where(arr > 3, 99, arr)  # Replace values > 3 with 99

```

---

## 5. Pandas Data Structures

```python
import pandas as pd
import numpy as np

# -----------------------------------------------------------------------------
# 5.1 Series (1D)
# -----------------------------------------------------------------------------
s = pd.Series([10, 20, 30, 40], index=['a', 'b', 'c', 'd'], name='Numbers')
print(s['a'])                    # Access by label (10)
print(s.values)                  # NumPy array underlying
print(s.index)                   # Index range/labels

# -----------------------------------------------------------------------------
# 5.2 DataFrame (2D)
# -----------------------------------------------------------------------------
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David'],
    'Age': [25, 30, 35, 40],
    'City': ['New York', 'London', 'Paris', 'Tokyo'],
    'Salary': [70000, 80000, 120000, 110000]
}

df = pd.DataFrame(data)

```

---

## 6. Data Loading & Exporting

```python
# Reading Files
df_csv = pd.read_csv('data.csv', encoding='utf-8', sep=',')
df_excel = pd.read_excel('data.xlsx', sheet_name='Sheet1')
df_json = pd.read_json('data.json')
df_sql = pd.read_sql('SELECT * FROM my_table', con=db_connection)

# Exporting Files
df.to_csv('output.csv', index=False)
df.to_excel('output.xlsx', index=False)
df.to_json('output.json')

```

---

## 7. Data Inspection & Selection

```python
# -----------------------------------------------------------------------------
# 7.1 Inspection
# -----------------------------------------------------------------------------
df.head(3)              # First 3 rows
df.tail(2)              # Last 2 rows
df.info()               # Structure, column data types, non-null counts
df.describe()           # Summary statistics for numeric columns
df.shape                # (rows, columns)
df.columns              # Column names
df.dtypes               # Data types of each column
df.nunique()            # Number of unique values per column
df['City'].value_counts() # Count of unique values in a Series

# -----------------------------------------------------------------------------
# 7.2 Selection & Slicing
# -----------------------------------------------------------------------------
# Columns
df['Age']               # Select single column (Series)
df[['Name', 'Salary']]  # Select multiple columns (DataFrame)

# loc (Label-based)
df.loc[0, 'Name']                       # Value at row 0, column 'Name'
df.loc[0:2, ['Name', 'Age']]            # Rows 0-2 (inclusive), specific columns

# iloc (Position-based)
df.iloc[0, 0]                           # Value at row 0, col 0
df.iloc[0:2, 0:3]                       # Rows 0-1, cols 0-2

# Filtering / Querying
df[df['Age'] > 30]                      # Filter rows where Age > 30
df[(df['Age'] > 25) & (df['Salary'] > 75000)] # Multiple conditions AND
df[(df['City'] == 'London') | (df['City'] == 'Paris')] # Multiple conditions OR
df[df['City'].isin(['London', 'Tokyo'])] # Matching list of values
df.query('Age > 25 and Salary < 100000') # Query string syntax

```

---

## 8. Data Cleaning & Transformation

```python
# -----------------------------------------------------------------------------
# 8.1 Missing Data Handling
# -----------------------------------------------------------------------------
df.isna() / df.isnull()         # Boolean mask for missing values
df.isnull().sum()               # Count missing values per column
df_cleaned = df.dropna()        # Drop rows with any NaN
df_cleaned_col = df.dropna(axis=1) # Drop columns with any NaN

df['Salary'].fillna(df['Salary'].mean(), inplace=True) # Fill NaNs with mean
df.fillna({'Age': 0, 'City': 'Unknown'}) # Fill NaNs per column

# -----------------------------------------------------------------------------
# 8.2 Column & Row Operations
# -----------------------------------------------------------------------------
# Renaming
df.rename(columns={'Name': 'Full_Name', 'Salary': 'Pay'}, inplace=True)

# Adding/Modifying Columns
df['Bonus'] = df['Pay'] * 0.1
df['Is_Senior'] = df['Age'] > 30

# Applying Functions
df['Name_Upper'] = df['Full_Name'].apply(lambda x: x.upper())
df.map({'New York': 'NY', 'London': 'LDN'}) # Map values in Series

# Type Conversion
df['Age'] = df['Age'].astype(float)

# Dropping
df.drop(columns=['Bonus', 'Is_Senior'], inplace=True) # Drop columns
df.drop(index=[0, 1], inplace=True)                    # Drop rows by index

# Duplicate Management
df.duplicated()                 # Check for duplicate rows
df.drop_duplicates(inplace=True) # Remove duplicates

```

---

## 9. Aggregation, GroupBy & Pivot Tables

```python
# -----------------------------------------------------------------------------
# 9.1 GroupBy
# -----------------------------------------------------------------------------
# Single Column Grouping
df.groupby('City')['Pay'].mean()

# Multiple Aggregations
df.groupby('City').agg({
    'Pay': ['mean', 'min', 'max'],
    'Age': 'median'
})

# -----------------------------------------------------------------------------
# 9.2 Pivot Tables & Crosstab
# -----------------------------------------------------------------------------
pivot = df.pivot_table(
    values='Pay', 
    index='City', 
    columns='Age', 
    aggfunc='mean', 
    fill_value=0
)

cross = pd.crosstab(df['City'], df['Age'])

```

---

## 10. Merging, Joining & Concatenating

```python
df1 = pd.DataFrame({'ID': [1, 2, 3], 'Name': ['Alice', 'Bob', 'Charlie']})
df2 = pd.DataFrame({'ID': [1, 2, 4], 'Score': [85, 90, 95]})

# -----------------------------------------------------------------------------
# 10.1 Merge (SQL-like Join)
# -----------------------------------------------------------------------------
inner = pd.merge(df1, df2, on='ID', how='inner')  # Matching IDs only
left = pd.merge(df1, df2, on='ID', how='left')    # All from df1
right = pd.merge(df1, df2, on='ID', how='right')  # All from df2
outer = pd.merge(df1, df2, on='ID', how='outer')  # All unique IDs

# -----------------------------------------------------------------------------
# 10.2 Concatenation (Stacking)
# -----------------------------------------------------------------------------
row_concat = pd.concat([df1, df2], axis=0, ignore_index=True) # Vertically
col_concat = pd.concat([df1, df2], axis=1)                    # Horizontally

```

---

## 11. Time Series Handling

```python
# Create Date Range
dates = pd.date_range(start='2026-01-01', periods=6, freq='D')
ts_df = pd.DataFrame({'Date': dates, 'Value': [10, 20, 15, 30, 25, 40]})

# Convert to Datetime object
ts_df['Date'] = pd.to_datetime(ts_df['Date'])

# Set Datetime Index
ts_df.set_index('Date', inplace=True)

# Date Features
print(ts_df.index.year)
print(ts_df.index.month)
print(ts_df.index.day_name())

# Resampling & Shifting
monthly_mean = ts_df.resample('M').mean() # Resample to monthly frequency
ts_df['Lagged_Value'] = ts_df['Value'].shift(1) # Shift rows by 1
ts_df['Rolling_Mean'] = ts_df['Value'].rolling(window=2).mean() # Moving average

```