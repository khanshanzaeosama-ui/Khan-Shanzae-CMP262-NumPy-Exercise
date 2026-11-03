# NumPy Student Handout

CMP 262 Data Science Programming
Prof Amjed Hedhli

Use this guide while completing NumPyAssignment.ipynb. NumPy helps Python work with groups of numbers. The examples teach the tools using different data; you will apply them to the visitor and sales exercises.

## Start with an array

Import the library once. The name np is a common abbreviation. An array stores values with one shared data type. A one dimensional array is a sequence; a two dimensional array is a grid.

```python
import numpy as np

# Three book prices in dollars.
prices = np.array([6, 9, 12])
print(prices)  # [ 6  9 12]
```

## An array and a list behave differently

```python
# A list repeats when multiplied by 2.
print([6, 9, 12] * 2)
# [6, 9, 12, 6, 9, 12]

# An array multiplies each number by 2.
print(prices * 2)  # [12 18 24]
```

This element by element behavior makes arrays useful for numeric analysis. You can transform many measurements with one expression instead of writing a loop.

## Before you begin

Open your own repository in VS Code, select a Python notebook kernel, and run the import cell. If NumPy is missing, run %pip install numpy in a notebook cell and restart the kernel. Code cells run Python; Markdown cells hold your explanations.

Assignment connection  Parts 1 and 3 use array creation and elementwise calculations.

# What NumPy is used for

NumPy stands for Numerical Python. It is a Python library for storing and calculating with numeric data. In data science, you often need to apply the same calculation to many values. NumPy arrays make that work convenient and efficient, especially for larger numeric datasets.

## Common uses

Summarize data  Find totals, averages, minimums, and maximums in measurements, sales records, or experiment results.

Transform measurements  Convert temperatures or distances, calculate percentage changes, or adjust many prices at once.

Find values that meet a condition  Select unusually high readings, values within a range, or records that need closer inspection.

Prepare numeric data for analysis  Arrange numbers into rows and columns and perform calculations before creating charts or building models.

## A practical example

Imagine a store with thousands of product prices. To estimate a five percent increase, you can multiply the entire price array by 1.05. Each product receives the same calculation, and the result can be stored separately for comparison.

```python
# Example prices for a different store.
old_prices = np.array([10.0, 20.0, 30.0])
new_prices = old_prices * 1.05
print(new_prices)  # [10.5 21.  31.5]
```

## How it connects to other tools

NumPy focuses on numeric arrays. pandas adds labeled tables for exploring and cleaning datasets. Matplotlib creates charts. These tools often work together: calculate with arrays, organize results in tables, and visualize the findings.

## Why you are learning it

This assignment builds the foundation for working with numerical data. Your visitor calculations practice summarizing and filtering, while the sales table shows how one array can organize several weeks and products.

# Create and inspect arrays

The properties below describe the structure of an array. They do not change its values.

```python
readings = np.array([[10, 14, 18],
                     [12, 16, 20]])
print(readings.ndim)   # 2 dimensions
print(readings.shape)  # (2, 3): 2 rows, 3 columns
print(readings.size)   # 6 values in total
print(readings.dtype)  # Integer type; width may vary
```

shape tells you the length of each axis. size counts all values. For a 2D array, multiply rows by columns to check size. A 1D array of three values has shape (3,), not (1, 3).

## Useful creation functions

```python
# Start with known placeholder values.
print(np.zeros(3))  # [0. 0. 0.]
print(np.ones(2))   # [1. 1.]

# arange uses a step and excludes the stop.
print(np.arange(3, 12, 3))  # [3 6 9]

# linspace uses a count and includes both endpoints.
print(np.linspace(2, 8, 4))  # [2. 4. 6. 8.]
```

The dots in 0. and 1. indicate floating point values. To request integer zeros, use np.zeros(3, dtype=int). Use arange for an integer step and linspace when you know how many evenly spaced values you need.

## Check your understanding

How many values are in an array with shape (2, 4)? Which function would you choose for exactly six evenly spaced values? Explain before running code.

Assignment connection  Part 1 asks you to create arrays and report their properties.

# Select values with indexing and slicing

Indices start at zero. For a 2D array, put the row first and the column second. A colon selects a range or an entire axis.

```python
weights = np.array([11, 15, 19, 23, 27])
print(weights[0])    # 11: first value
print(weights[-1])   # 27: last value
print(weights[1:4])  # [15 19 23]: stop 4 excluded
```

## Read a two dimensional selection

```python
readings = np.array([[10, 14, 18],
                     [12, 16, 20]])
print(readings[1, 2])   # 20: second row, third column
print(readings[0, :])   # [10 14 18]: first row
print(readings[:, 1])   # [14 16]: second column
print(readings[:, :2])  # First two columns of every row
# [[10 14]
#  [12 16]]
```

Read [:, 1] as all rows, column at index 1. Read [0, :] as row at index 0, all columns. Selecting one row this way returns a 1D array.

## Avoid off by one errors

To include an index in a slice, put the stop one position after it. A length five array has indices 0 through 4; index 5 is outside the array.

Basic slices share the original array's data. Reading a slice is safe, but changing values through that slice can change the original. Make an explicit copy when you want independent values.

## Try first then check

Predict readings[0, 1] and weights[2:4]. Run the expressions and explain any difference from your prediction.

Assignment connection  Parts 2 and 4 ask for individual values, rows, columns, and slices.

# Calculate and summarize

Scalar arithmetic applies to each array value. Assign the result to a new name if you need to keep the original. For same-shaped arrays, +, -, *, and / pair corresponding positions. The * operator is not matrix multiplication.

```python
prices = np.array([6, 9, 12])
print(prices + 1)  # [ 7 10 13]
print(prices / 3)  # [2. 3. 4.]
print(prices)      # [ 6  9 12]: unchanged
print(prices.sum())   # 27
print(prices.mean())  # 9.0
print(prices.min())   # 6
print(prices.max())   # 12
```

## Understand the axis

For the readings grid, each row represents a sensor and each column represents a time. A summary without axis uses every value. axis=0 combines rows and leaves one result per column. axis=1 combines columns and leaves one result per row.

```python
readings = np.array([[10, 14, 18],
                     [12, 16, 20]])
print(readings.sum())        # 90: all six values
print(readings.sum(axis=0))  # [22 30 38]: by time
print(readings.sum(axis=1))  # [42 48]: by sensor
print(readings.mean(axis=0)) # [11. 15. 19.]
```

Check the first column: 10 + 12 gives 22. Check the first row: 10 + 14 + 18 gives 42. Always connect your axis choice to what the rows and columns mean in the scenario.

## Explain a result

A useful explanation names the unit and the group. For example, the first sensor has a total reading of 42 across the three times. A printed number alone does not explain what you measured.

Assignment connection  Parts 3 and 4 require summary statistics and explicit axis choices.

# Filter values using conditions

A comparison creates a Boolean array containing True or False at each position. This is a mask. Place the mask inside square brackets to keep only matching values.

```python
weights = np.array([11, 15, 19, 23, 27])
mask = weights > 20
print(mask)  # [False False False True True]
print(weights[mask])  # [23 27]
print(np.count_nonzero(mask))  # 2 matching values
```

## Combine conditions

```python
# Keep values greater than 12 and no more than 23.
selected = weights[(weights > 12) & (weights <= 23)]
print(selected)  # [15 19 23]
```

Use & for elementwise AND and put each comparison in parentheses. Python's and tries to treat the whole array as one truth value and does not perform this array filtering operation. Use | for elementwise OR.

## Separate the question from the code

First describe which values you want in everyday language. Then choose the comparison signs. At least includes the boundary, so it uses >=. Fewer than excludes the boundary, so it uses <.

Inspect the mask as well as the selected values. The number of True positions should equal the number of selected values. This gives you a simple way to verify your result.

## Check your understanding

Predict how many values would remain if the condition were weights >= 19. Explain whether 19 is included before running the comparison.

Assignment connection  Part 5 asks you to create a mask, filter, count, and combine two conditions.

# Reshape copy and check your work

## Reshape keeps the same number of values

```python
sequence = np.arange(20, 26)  # Six integers
grid = sequence.reshape(2, 3)
print(grid)
# [[20 21 22]
#  [23 24 25]]
```

Two rows times three columns equals six values. A (4, 2) shape would need eight values and would raise an error. Reshape changes arrangement, not the number of elements. It can share data with the original, so do not assume it makes an independent copy.

## Use copy for independent data

```python
original = np.array([3, 7, 11])
trial = original.copy()
trial[0] = 99
print(original)  # [ 3  7 11]
print(trial)     # [99  7 11]
```

trial = original gives another name to the same array. A copy gives you independent data. Compare both arrays after your change to verify this distinction.

## Submission check

Complete every TODO and explain your results in Markdown. Restart the kernel, Run All, and inspect every output. Save the notebook with its output. Complete AI-Use-Report.md even if no AI was used. Commit and push, then submit the repository link and notebook through Blackboard Ultra.

## Official references

NumPy quickstart
https://numpy.org/doc/stable/user/quickstart.html
NumPy beginner guide
https://numpy.org/doc/stable/user/absolute_beginners.html
Indexing
https://numpy.org/doc/stable/user/basics.indexing.html
Copies and views
https://numpy.org/doc/stable/user/basics.copies.html

Assignment connection  Part 6 covers reshape and copy. Part 7 asks you to reflect and verify.
