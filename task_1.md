# VISUALIZATION LIBRARIES DOCUMENTATION

**Subject:** Python Programming Lab
**Topic:** Python Visualization Libraries - Matplotlib and Seaborn

---

## Introduction

Visualization is a way of representing data in a graphical or pictorial format. It helps in understanding the data better and finding patterns or trends in it. Instead of looking at rows of numbers, a graph makes it much easier to understand what the data is saying.

Visualization is important because:

- It helps in understanding large amounts of data quickly.
- Patterns and trends are easy to spot in a graph compared to a table.
- It makes presenting results to others much simpler.

Python has several libraries for data visualization. Some common ones are:

- **Matplotlib** - one of the oldest and most widely used plotting libraries.
- **Seaborn** - built on top of Matplotlib, used mainly for statistical plots.
- **Plotly** - used for interactive charts.
- **Bokeh** - also used for interactive visualizations.

This document focuses on **Matplotlib** and **Seaborn** only.

---

## 1. Matplotlib

### Overview

Matplotlib is a Python library used for creating 2D plots and graphs. It was introduced in 2002 by John Hunter. It is one of the most popular visualization libraries in Python.

**Main Features:**

- Can create a wide variety of plots like line, bar, scatter, pie, histogram, etc.
- Works well with NumPy arrays directly.
- Gives full control over every part of a figure - colors, labels, axes, titles, etc.
- Can save plots as image files (PNG, PDF, SVG, etc.).

**Common Use Cases:**

- Plotting mathematical functions.
- Visualizing data from NumPy arrays or Pandas DataFrames.
- Creating publication-ready figures.

**Relationship with NumPy:**

Matplotlib works very closely with NumPy. Most of the time, the data passed into Matplotlib functions is in the form of NumPy arrays. Functions like `np.array()`, `np.arange()`, and `np.random` are commonly used to generate data for plotting.

We import Matplotlib's pyplot module like this:

```python
import matplotlib.pyplot as plt
import numpy as np
```

A Matplotlib figure contains:

1. **Figure** - the overall container that holds everything.
2. **Axes** - the actual plot area where data is drawn.
3. **Axis** - the x and y axis lines with ticks and limits.
4. **Artists** - everything visible in the figure (lines, text, labels, etc.).

---

### Graph Types in Matplotlib

---

#### 1.1 Line Plot

**Description:** A line plot connects data points with a continuous line. It is used to show how values change over a sequence or time. It is one of the simplest and most commonly used plots.

**Use Case:** Useful for tracking temperature changes over months, or showing how student marks change over semesters.

**Code Snippet:**

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.arange(1, 7)
y = np.array([55, 62, 70, 65, 80, 75])

plt.plot(x, y, color="blue", marker="o")
plt.title("Monthly Test Scores")
plt.xlabel("Month")
plt.ylabel("Score")
plt.show()
```

**Explanation:**

`np.arange(1, 7)` creates an array from 1 to 6 representing months. `plt.plot()` draws the line chart. The `marker="o"` parameter adds a dot at each data point. `plt.title()`, `plt.xlabel()`, and `plt.ylabel()` are used to label the chart.

---

#### 1.2 Scatter Plot

**Description:** A scatter plot shows individual data points as dots on a graph. It does not connect the dots. It is used to see if there is any relationship between two variables.

**Use Case:** Useful for checking if there is a relationship between study hours and exam scores.

**Code Snippet:**

```python
import numpy as np
import matplotlib.pyplot as plt

np.random.seed(42)
study_hours = np.random.randint(1, 10, 30)
exam_scores = study_hours * 8 + np.random.randint(-5, 5, 30)

plt.scatter(study_hours, exam_scores, color="green")
plt.title("Study Hours vs Exam Scores")
plt.xlabel("Study Hours")
plt.ylabel("Exam Score")
plt.show()
```

**Explanation:**

`np.random.randint()` generates random integer values. `plt.scatter()` draws the scatter plot with `x` and `y` as the two variables. Each dot represents one student's data. Setting `np.random.seed(42)` makes sure the random values are the same every time the code runs.

---

#### 1.3 Bar Chart

**Description:** A bar chart uses rectangular bars to represent data. The height of each bar shows the value of that category. Bars can be vertical or horizontal.

**Use Case:** Useful for comparing the sales of different products or the marks of different students.

**Code Snippet:**

```python
import numpy as np
import matplotlib.pyplot as plt

subjects = ["Maths", "Science", "English", "History", "CS"]
marks = np.array([88, 92, 75, 65, 95])

plt.bar(subjects, marks, color="orange", width=0.5)
plt.title("Marks by Subject")
plt.xlabel("Subject")
plt.ylabel("Marks")
plt.show()
```

**Explanation:**

`np.array()` stores the marks for each subject. `plt.bar()` creates the bar chart where the first argument is the category labels and the second is the values. The `width` parameter controls how wide each bar is. The `color` parameter sets the bar color.

---

#### 1.4 Histogram

**Description:** A histogram looks similar to a bar chart, but it is used for continuous data. It groups data into ranges called bins and shows how many values fall in each bin.

**Use Case:** Useful for checking the distribution of exam scores or ages in a dataset.

**Code Snippet:**

```python
import numpy as np
import matplotlib.pyplot as plt

np.random.seed(10)
scores = np.random.normal(70, 10, 200)

plt.hist(scores, bins=15, color="steelblue", edgecolor="black")
plt.title("Distribution of Exam Scores")
plt.xlabel("Score")
plt.ylabel("Number of Students")
plt.show()
```

**Explanation:**

`np.random.normal(70, 10, 200)` generates 200 values with a mean of 70 and standard deviation of 10. `plt.hist()` draws the histogram. The `bins` parameter sets how many groups the data is divided into. `edgecolor="black"` adds a black border around each bar so they are easy to separate visually.

---

#### 1.5 Pie Chart

**Description:** A pie chart represents data as slices of a circle. Each slice shows what percentage of the total a category takes up. All slices together make 100%.

**Use Case:** Useful for showing how a student spends their day or what percentage each department contributes to total sales.

**Code Snippet:**

```python
import numpy as np
import matplotlib.pyplot as plt

activities = ["Sleeping", "Studying", "Sports", "Leisure"]
hours = np.array([8, 6, 2, 8])
colors = ["skyblue", "orange", "green", "tomato"]

plt.pie(hours, labels=activities, colors=colors,
        autopct="%1.1f%%", wedgeprops={"edgecolor": "black", "linewidth": 1})
plt.title("How a Student Spends Their Day")
plt.show()
```

**Explanation:**

`np.array()` holds the hours spent on each activity. `plt.pie()` draws the pie chart. The `labels` parameter adds category names. `autopct="%1.1f%%"` displays the percentage on each slice. `wedgeprops` is used to add a black border around each slice.

---

#### 1.6 Area Chart

**Description:** An area chart is similar to a line chart, but the area between the line and the x-axis is filled with color. It is good for showing cumulative values or comparing multiple groups.

**Use Case:** Useful for showing how website traffic grows over a period, or comparing sales of multiple products.

**Code Snippet:**

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.arange(1, 7)
y = np.array([10, 25, 20, 35, 30, 45])

plt.fill_between(x, y, alpha=0.5, color="purple")
plt.plot(x, y, color="purple")
plt.title("Monthly Website Traffic")
plt.xlabel("Month")
plt.ylabel("Visitors (thousands)")
plt.show()
```

**Explanation:**

`plt.fill_between()` fills the area under the line with color. The `alpha` parameter controls how transparent the fill is (0 is fully transparent, 1 is fully solid). `plt.plot()` draws the line on top of the filled area. Both are used together to get the area chart look.

---

## 2. Seaborn

### Overview

Seaborn is a Python visualization library that is built on top of Matplotlib. It makes it easier to create good-looking statistical plots with less code. Seaborn comes with default themes and color palettes that make plots look nicer without needing to set them manually.

**How it is built on Matplotlib:** Seaborn uses Matplotlib internally to render plots. This means that Matplotlib functions like `plt.title()`, `plt.xlabel()`, and `plt.show()` still work even when using Seaborn.

**Main Advantages:**

- Cleaner and more attractive default styles compared to Matplotlib.
- Has built-in support for statistical visualizations like box plots, KDE plots, and regression plots.
- Works directly with Pandas DataFrames.
- Less code is needed to produce complex plots.

**Typical Use Cases:**

- Exploratory Data Analysis (EDA).
- Visualizing distributions and relationships in data.
- Statistical comparisons between categories.

We import Seaborn like this:

```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
```

---

### Graph Types in Seaborn

---

#### 2.1 Scatter Plot

**Description:** Seaborn's scatter plot shows the relationship between two numeric variables. It supports a `hue` parameter which can color the dots based on a third categorical variable.

**Use Case:** Checking if height and weight are related in a group of people.

**Code Snippet:**

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(5)
height = np.random.randint(150, 190, 80)
weight = height * 0.45 + np.random.randint(-5, 5, 80)
gender = np.where(np.arange(80) % 2 == 0, "Male", "Female")

df = pd.DataFrame({"Height": height, "Weight": weight, "Gender": gender})

sns.scatterplot(x="Height", y="Weight", hue="Gender", data=df)
plt.title("Height vs Weight")
plt.show()
```

**Explanation:**

The data is created using NumPy and stored in a Pandas DataFrame. `sns.scatterplot()` plots the points. The `hue="Gender"` parameter colors the points differently based on the gender column. This makes it easy to compare two groups in the same plot.

---

#### 2.2 Line Plot

**Description:** Seaborn's line plot draws a line through data points. It also shows a shaded confidence interval around the line by default, which shows the range of uncertainty.

**Use Case:** Showing the average temperature recorded each month across a year.

**Code Snippet:**

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(1)
months = np.arange(1, 13)
temperature = np.array([22, 24, 28, 32, 36, 38, 37, 35, 31, 27, 24, 21])

df = pd.DataFrame({"Month": months, "Temperature": temperature})

sns.lineplot(x="Month", y="Temperature", data=df, color="red", marker="o")
plt.title("Average Monthly Temperature")
plt.xlabel("Month")
plt.ylabel("Temperature (C)")
plt.show()
```

**Explanation:**

The `months` and `temperature` arrays are created using NumPy and placed in a DataFrame. `sns.lineplot()` draws the line. The `marker="o"` adds dots at each month. Seaborn automatically handles axis labels from the DataFrame column names.

---

#### 2.3 Bar Plot

**Description:** Seaborn's bar plot shows the average (mean) value of a numeric variable for each category. It also adds error bars by default to show the confidence interval.

**Use Case:** Comparing average scores of students from different sections.

**Code Snippet:**

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(7)
sections = np.repeat(["A", "B", "C"], 30)
scores = np.concatenate([
    np.random.normal(75, 8, 30),
    np.random.normal(82, 6, 30),
    np.random.normal(70, 10, 30)
])

df = pd.DataFrame({"Section": sections, "Score": scores})

sns.barplot(x="Section", y="Score", data=df, palette="Set2")
plt.title("Average Score by Section")
plt.xlabel("Section")
plt.ylabel("Average Score")
plt.show()
```

**Explanation:**

`np.repeat()` creates the section labels for 90 students (30 per section). `np.concatenate()` merges three arrays of scores. `sns.barplot()` calculates and plots the mean score for each section. The `palette` parameter sets the color scheme.

---

#### 2.4 Count Plot

**Description:** A count plot is like a bar chart that automatically counts how many times each category appears in a column. There is no need to calculate counts manually.

**Use Case:** Counting how many students belong to each year of study.

**Code Snippet:**

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(3)
years = np.random.choice(["First Year", "Second Year", "Third Year", "Fourth Year"], 120)

df = pd.DataFrame({"Year": years})

sns.countplot(x="Year", data=df, palette="Set1")
plt.title("Number of Students per Year")
plt.xlabel("Year")
plt.ylabel("Count")
plt.show()
```

**Explanation:**

`np.random.choice()` randomly picks year labels for 120 students. `sns.countplot()` counts the occurrences of each category automatically and draws a bar for each one. No need to use `value_counts()` or any manual counting.

---

#### 2.5 Box Plot

**Description:** A box plot shows the distribution of a numeric variable using five summary values: minimum, Q1 (25th percentile), median, Q3 (75th percentile), and maximum. Points that fall outside the whiskers are outliers.

**Use Case:** Comparing the spread of marks across different sections or subjects.

**Code Snippet:**

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(9)
subjects = np.repeat(["Maths", "Science", "English"], 40)
marks = np.concatenate([
    np.random.normal(70, 12, 40),
    np.random.normal(80, 8, 40),
    np.random.normal(65, 15, 40)
])

df = pd.DataFrame({"Subject": subjects, "Marks": marks})

sns.boxplot(x="Subject", y="Marks", data=df, palette="Pastel1")
plt.title("Marks Distribution by Subject")
plt.xlabel("Subject")
plt.ylabel("Marks")
plt.show()
```

**Explanation:**

Each subject has 40 randomly generated marks using `np.random.normal()`. `sns.boxplot()` draws the box for each subject. The box shows the interquartile range (IQR). The line inside the box is the median. Points outside the whiskers are shown as dots and are considered outliers.

---

#### 2.6 Histogram (histplot)

**Description:** Seaborn's `histplot()` function works like Matplotlib's histogram but with better default styling. It can also overlay a KDE curve on top of the histogram.

**Use Case:** Seeing how exam scores are distributed across a class.

**Code Snippet:**

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(11)
scores = np.random.normal(68, 12, 150)

df = pd.DataFrame({"Score": scores})

sns.histplot(x="Score", data=df, bins=15, kde=True, color="teal")
plt.title("Score Distribution")
plt.xlabel("Score")
plt.ylabel("Count")
plt.show()
```

**Explanation:**

`np.random.normal(68, 12, 150)` generates 150 scores with mean 68 and standard deviation 12. `sns.histplot()` draws the histogram. Setting `kde=True` adds a smooth density curve on top of the bars. This helps in understanding the shape of the distribution better.

---

#### 2.7 KDE Plot

**Description:** KDE stands for Kernel Density Estimate. It draws a smooth curve that shows the probability distribution of the data. It is a smoothed version of a histogram.

**Use Case:** Comparing the distribution of heights between male and female students.

**Code Snippet:**

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(4)
male_height = np.random.normal(172, 6, 100)
female_height = np.random.normal(161, 5, 100)
gender = np.concatenate([np.repeat("Male", 100), np.repeat("Female", 100)])
height = np.concatenate([male_height, female_height])

df = pd.DataFrame({"Height": height, "Gender": gender})

sns.kdeplot(x="Height", hue="Gender", data=df, fill=True)
plt.title("Height Distribution by Gender")
plt.xlabel("Height (cm)")
plt.show()
```

**Explanation:**

Two separate arrays are created for male and female heights and then merged. `sns.kdeplot()` draws the density curves. `hue="Gender"` draws a separate curve for each group. `fill=True` fills the area under each curve with a light color.

---

#### 2.8 Heatmap

**Description:** A heatmap displays a matrix of values using colors. Higher values usually get brighter or warmer colors and lower values get darker or cooler colors. It is commonly used to visualize correlation matrices.

**Use Case:** Checking how different variables in a dataset are related to each other.

**Code Snippet:**

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(6)
data = np.random.rand(5, 5)
columns = ["Maths", "Science", "English", "History", "CS"]

df = pd.DataFrame(data, columns=columns, index=columns)
corr = df.corr()

sns.heatmap(corr, annot=True, cmap="coolwarm", linewidths=0.5)
plt.title("Correlation Heatmap")
plt.show()
```

**Explanation:**

A 5x5 matrix is created using `np.random.rand()` and stored in a DataFrame. `.corr()` computes the correlation between columns. `sns.heatmap()` plots the correlation matrix. `annot=True` shows the actual values inside each cell. `cmap="coolwarm"` sets the color scale from blue (low) to red (high).

---

#### 2.9 Regression Plot

**Description:** A regression plot shows a scatter plot along with a fitted regression line. The shaded area around the line is the confidence interval. It helps in understanding the linear relationship between two variables.

**Use Case:** Checking if there is a linear relationship between the number of hours studied and marks obtained.

**Code Snippet:**

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(8)
hours = np.random.uniform(1, 10, 60)
marks = hours * 7 + np.random.normal(0, 5, 60)

df = pd.DataFrame({"Hours Studied": hours, "Marks": marks})

sns.regplot(x="Hours Studied", y="Marks", data=df, color="darkblue",
            scatter_kws={"alpha": 0.6})
plt.title("Hours Studied vs Marks")
plt.xlabel("Hours Studied")
plt.ylabel("Marks")
plt.show()
```

**Explanation:**

`np.random.uniform()` generates random hours between 1 and 10. Marks are calculated based on hours with some added noise using `np.random.normal()`. `sns.regplot()` draws both the scatter points and the regression line. `scatter_kws={"alpha": 0.6}` makes the dots slightly transparent.

---

## 3. Comparison of Matplotlib and Seaborn

| Feature | Matplotlib | Seaborn |
|---|---|---|
| Ease of Use | Requires more code for basic plots | Less code needed, simpler syntax |
| Learning Curve | Steeper, more functions to learn | Easier for beginners |
| Customization | Very high, full control over every element | Moderate, some things need Matplotlib |
| Built-in Themes | No default themes, plain style | Yes, comes with attractive themes |
| Statistical Visualizations | Not built-in, needs manual setup | Yes, built-in support |
| Flexibility | Very flexible, any type of plot possible | Less flexible, limited to common plots |
| Integration with NumPy | Direct and seamless | Works via Pandas DataFrames |
| Integration with Pandas | Possible but needs extra steps | Very seamless and straightforward |
| Performance | Fast for simple plots | Slightly slower due to additional processing |
| Best Use Cases | Custom figures, mathematical plots, full control | EDA, statistical plots, quick visualizations |

---

## 4. Strengths and Weaknesses

### Matplotlib

**Strengths:**

- Gives complete control over every part of the figure.
- Can create almost any type of chart or plot.
- Works directly and smoothly with NumPy arrays.
- Well-documented and has a large user community.
- Plots can be saved in many formats like PNG, PDF, SVG, etc.

**Weaknesses:**

- Requires more lines of code even for basic plots.
- Default plots look plain and need extra styling to look good.
- Can be confusing for beginners due to the many options available.
- Statistical plots are not built-in and need to be built manually.

---

### Seaborn

**Strengths:**

- Much less code is needed to create attractive plots.
- Comes with built-in statistical plot types (box plot, KDE, regression, etc.).
- Default colors and themes look clean without any extra setup.
- Works very naturally with Pandas DataFrames.
- The `hue` parameter makes it easy to add a third variable to any plot.

**Weaknesses:**

- Less control over fine details compared to Matplotlib.
- Not as flexible for creating unusual or highly customized plots.
- Slower compared to Matplotlib for large datasets.
- Still needs Matplotlib for things like saving files, adding titles, and adjusting figure size.

---

## 5. Conclusion

Both Matplotlib and Seaborn are useful, and the choice between them depends on what kind of task is being done.

**Matplotlib** should be used when full control is needed over a plot, when creating custom figures, or when working directly with NumPy arrays without Pandas.

**Seaborn** should be used when the goal is quick and clean statistical visualizations, especially during data exploration. It is also the better choice when the data is already in a Pandas DataFrame.

Most people use both libraries together. For example, Seaborn is used to draw the plot, and Matplotlib functions like `plt.title()`, `plt.savefig()`, or `plt.figure(figsize=...)` are used to adjust and save it. This combination gives the best of both libraries.

---

## References

1. Matplotlib Official Documentation - Quick Start Guide
   [https://matplotlib.org/stable/users/explain/quick_start.html](https://matplotlib.org/stable/users/explain/quick_start.html)

2. Seaborn Official Documentation - Introduction Tutorial
   [https://seaborn.pydata.org/tutorial/introduction.html](https://seaborn.pydata.org/tutorial/introduction.html)

---
