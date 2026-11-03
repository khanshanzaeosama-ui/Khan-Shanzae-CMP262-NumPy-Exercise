# CMP 262 NumPy Fundamentals

Practice basic NumPy skills in a guided notebook. You will create, select, calculate, and summarize numeric data, then explain what your output means.

## GitHub Starter Repository

[Open the NumPy starter repository](https://github.com/ahedhli12/CMP262-NumPy-Exercise-)

## Getting Started

1. Create your own copy. If **Use this template** is available, select it and create a new repository. Otherwise, select **Fork** to create your own copy.
2. Choose your personal GitHub account as owner and name the repository **LastName-FirstName-CMP262-NumPy**.
3. Set your repository to **Public**, following the format of our previous assignment.
4. Clone your own copy and open its folder in Visual Studio Code.
5. Open **NumPyAssignment.ipynb** and select your Python notebook kernel.
6. Run the import cell. If NumPy is missing, use the setup instructions below.
7. Complete every code and Markdown **TODO**. Use the handout for explanations.
8. Restart the kernel and select **Run All**. Check the results, then save.
9. Complete **AI-Use-Report.md**, commit, and push your work.
10. Submit your repository link and completed notebook through **Blackboard Ultra**.

Do not edit the instructor's repository. Do not include private information in a public repository.

## Setup

Use the course Python environment with the VS Code Python and Jupyter extensions. If the import fails, run the following in a notebook cell, then restart the kernel:

```python
%pip install numpy
```

This installs NumPy into the selected notebook environment. No CSV files, pandas, charts, or additional datasets are required.

## Objective

By the end, you should be able to create 1D and 2D arrays, inspect their properties, select values, perform elementwise calculations, summarize rows and columns, filter values, reshape data, and make an independent copy.

## Assignment

Use the supplied values exactly. Write your own code and display clearly labeled output. Answer each written question in your own words in two or three sentences.

### Part 1 Create and inspect arrays

Create a one-dimensional array named daily_visitors using [45, 52, 38, 61, 49, 70, 55]. Display the array, ndim, shape, size, and dtype with clear labels. Create and display an array of five zeros and an array of four ones. Use arange to create the even numbers from 2 through 12 inclusive. Use linspace to create five equally spaced values from 0 to 1 inclusive.

**Explain:** Explain shape versus size. Explain why the stop value you used in arange produces the requested sequence.

### Part 2 Select values

Using daily_visitors, display the first value, the last value, the first three values, and values at indices 2 through 5 inclusive. Use indexing and slicing rather than retyping values. Do not change the original array.

**Explain:** Explain the difference between selecting one value and selecting a slice.

### Part 3 Calculate with arrays

Create projected_visitors by adding 8 to every value in daily_visitors. Create double_visitors by multiplying the original daily_visitors by 2. Display both arrays and the original array to show it is unchanged. Calculate the total, mean, minimum, and maximum of the original values using NumPy. Use array operations rather than a Python loop.

**Explain:** Explain what adding one number to an array does. Interpret the mean in this seven-day scenario.

### Part 4 Work with a two dimensional array

Run the supplied sales cell. Rows represent weeks 1 through 4. Columns represent notebooks, pens, and folders in that order; values are units sold. Display shape, ndim, and size. Select the entire second week, all pen sales, and the folder sales value in week 4. Calculate total units for each week, total units for each product, and mean weekly units for each product. Label the outputs and use axis explicitly.

**Explain:** Explain which axis gives one total per week and why. Identify the product with the greatest four-week total using your results.

### Part 5 Filter and count

Using the original daily_visitors, create and display a Boolean mask for days with at least 55 visitors. Use that mask to select the matching values. Count the matching days using np.count_nonzero. Then select days with at least 45 but fewer than 60 visitors using one combined Boolean condition. Display the results. Do not use a loop.

**Explain:** Explain what True means in your mask and why filtering returns fewer values than the original array.

### Part 6 Reshape and make a copy

Create an array containing the integers 1 through 12 and reshape it into 3 rows and 4 columns. Display the original one-dimensional array and the reshaped array. Make an independent copy of sales named trial_sales. Change only the first value of trial_sales to 999. Display both sales and trial_sales to demonstrate that sales is unchanged.

**Explain:** Explain why 12 values fit a (3, 4) shape but not a (5, 3) shape. Explain why trial_sales = sales would not make an independent copy.

### Part 7 Reflect and submit

In a final Markdown cell, explain one situation where a NumPy array is useful in data science, identify one error you corrected or one result you checked, and describe how you verified it. Complete the AI report even if you did not use AI.

## Rubric 100 Points

| Area | Points |
|---|---:|
| Create arrays and inspect properties | 15 |
| Indexing and slicing | 15 |
| Elementwise calculations and summary statistics | 15 |
| Two dimensional selections and axis summaries | 20 |
| Boolean filtering and counting | 15 |
| Reshaping and independent copying | 10 |
| Written explanations and final reflection | 5 |
| Complete AI report and organized submission | 5 |

The first six categories assess code correctness and visible output. The written-explanation category assesses the explanations throughout the notebook and final reflection.

## Required Files

- NumPyAssignment.ipynb with completed code, saved output, and written answers
- AI-Use-Report.md completed by the student

Keep the starter README, requirements file, handout, and tutoring instructions in your copy.

## Save and Submit

Ctrl+S saves locally. Commit and push to update GitHub:

```bash
git status
git add .
git commit -m "Complete NumPy fundamentals assignment"
git push
```

Open your repository on GitHub and check that the latest notebook and AI report are visible. Submit the public repository link and the completed notebook through Blackboard Ultra. GitHub alone is not the official submission.

## Learning Resources

- [Student handout](NumPy_Student_Handout.md)
- [Official NumPy quickstart](https://numpy.org/doc/stable/user/quickstart.html) — focus on basics, array creation, basic operations, indexing and slicing, and shape manipulation.
- [NumPy beginner guide](https://numpy.org/doc/stable/user/absolute_beginners.html)

Advanced linear algebra, advanced broadcasting, stacking, and random-number generation are outside this assignment.
