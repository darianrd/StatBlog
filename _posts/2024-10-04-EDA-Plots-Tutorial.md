---
layout: post
title: "Tutorial: Create and Customize EDA Plots in R and Python"
description: A tutorial on creating plots for exploratory data analysis using R and Python.
---

# Introduction

In this blog post, I will be explaining how to create EDA plots and add customizations to them in R and Python. First, let's talk about some basics of data analysis.

### What is EDA?

In statistics, exploratory data analysis (or EDA) is a method of gaining information about the data we are working with before using it to create models and make predictions. EDA is typically used to summarize data through exploring patterns and relationships between the variables of interest and usually includes visual representations of the data, such as scatterplots and histograms.

### Why learn how to analyze data in more than one language?

Many of you may be familiar with creating EDA plots in at least one programming language and may be wondering why you would create plots in any other language. However, there are several reasons why it could be useful to be familiar with more than one language for analyzing data, including:
- Some languages may be easier to navigate but have less customizability, while other languages are more complex to learn but may be more flexible with customizability.
- Different languages have different tools, so you can choose a language with tools that may be better suited for your specific project.
- It can help you learn how to approach data-related problems from different perspectives.
- It makes you more marketable to potential employers.

# Creating Plots

Now, let's get into creating some EDA plots. For this tutorial, I will be using Titanic passenger data from the [Titanic Disaster Dataset](https://data.world/nrippner/titanic-disaster-dataset). We'll start by learning how to create a histogram and boxplot in R using the *ggplot2* package.

### Plotting in R

First, we will load the *tidyverse* package (which contains *ggplot2*) and read in our dataset.

```r
library(tidyverse)

data <- read.csv("~/Desktop/titanic.csv")
```

Our first plot will be a histogram of the age distribution of Titanic passengers. For this, we will pipe our data into the *ggplot* function and customize from there. Our first customization is to set the x-axis as the *age* variable, which is done by using the *aes* function within the *ggplot* function. *aes* stands for aesthetics and is used to specify how variables will be mapped in the visual representation.

```r
data |> ggplot(aes(x = age))
```

Our next customization is to create a histogram and set colors for the graph. We do this by using the *geom_histogram* function with the arguments *fill* and *color*. *fill* is used to fill the whole shape of the graph with a specified color, while *color* is used to outline the shape of the graph with a specified color. Color options can be specified either by hexadecimal codes or from R's built-in color library. [Here is a list of colors in R's library](http://www.stat.columbia.edu/~tzheng/files/Rcolor.pdf). We will also adjust the width of the histogram bars using the *bins* argument.

```r
data |> ggplot(aes(x = age)) +
  geom_histogram(fill = "pink2",
                 color = "pink4",
                 bins = 20)
```

Our next customization is to add labels to our graphs. This is done using the *labs* function (which stands for labels), and we will be adding labels to the x and y axes, as well as adding a title and caption to the graph.

```r
data |> ggplot(aes(x = age)) +
  geom_histogram(fill = "pink2",
                 color = "pink4",
                 bins = 20) +
  labs(x = "Age in Years",
       y = "Frequency",
       title = "Age of Titanic Passengers",
       caption = "Source: https://data.world/nrippner/titanic-disaster-dataset")
```

Our final customization is to change the background of the plot to make it white and remove grid lines. We do this using the *theme_classic* function with no arguments passed in.

```r
data |> ggplot(aes(x = age)) +
  geom_histogram(fill = "pink2",
                 color = "pink4",
                 bins = 20) +
  labs(x = "Age in Years",
       y = "Frequency",
       title = "Age of Titanic Passengers",
       caption = "Source: https://data.world/nrippner/titanic-disaster-dataset") +
  theme_classic()
```

Here is the completed output.

![R Histogram](https://raw.githubusercontent.com/darianrd/StatBlog/refs/heads/main/assets/img/RHist.png)

We can create a boxplot using a similar structure, except we will be adding a y-axis variable and a grouping variable within the aesthetic mapping (in the *aes* function). *group* is used to indicate which variable to split the boxplots on so that instead of one large boxplot, there are separate boxplots for each value of the grouping variable. Additionally, we will be using the *geom_boxplot* function in place of the *geom_histogram* function from the last example.

```r
data |> ggplot(aes(x = survived, y = fare, group = survived)) +
  geom_boxplot(fill = "pink2",
               color = "pink4")
```

Our next customization is to add error bars to the whiskers of the boxplots using the *stat_boxplot* function with the *geom* and *width* arguments. *geom* is used to specify an element of a graph, while *width* specifies the width of that element.

```r
data |> ggplot(aes(x = survived, y = fare, group = survived)) +
  geom_boxplot(fill = "pink2",
               color = "pink4") +
  stat_boxplot(geom = "errorbar",
               width = 0.5)
```

Our last customization is to add labels and change the background, which works exactly the same as before.

```r
data |> ggplot(aes(x = survived, y = fare, group = survived)) +
  geom_boxplot(fill = "pink2",
               color = "pink4") +
  stat_boxplot(geom = "errorbar",
               width = 0.5) +
  labs(x = "Passenger Survived",
       y = "Passenger Fare in Dollars",
       title = "Comparison of Titanic Passenger Fare to Survival Rate",
       caption = "Source: https://data.world/nrippner/titanic-disaster-dataset") +
  theme_classic()
```

Here is the completed output.

![R Boxplot](https://raw.githubusercontent.com/darianrd/StatBlog/refs/heads/main/assets/img/RBox.png)

Now, let's create these same plots with Python.

### Plotting in Python

First, we will import the *matplotlib* library, the *pandas* library, and the *seaborn* library, then read in our dataset.

```python
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
data = pd.read_csv("titanic.csv")
```

To create our histogram, we will use the *sns.histplot* function and call the *age* variable from our dataset. Our first customization will be the same as before—changing the colors and bin width. In this case, the *color* argument is used for the fill color and the *edgecolor* argument is used for the outline color. [Here are the color options in *matplotlib* which can be used with *seaborn*](https://matplotlib.org/stable/gallery/color/named_colors.html).

```python
sns.histplot(data["age"], color = "pink", edgecolor = "maroon", bins = 20)
```

Our next customization is, once again, adding labels to our graph. In Python, we will use four different functions to accomplish this—*plt.xlabel*, *plt.ylabel*, *plt.title*, and *plt.figtext*. These functions will respectively create labels for the x and y axes, a title, and a caption. There are two additional arguments required in the *plt.figtext* function which are the x and y coordinates for positioning the caption in relation to the graph.

```python
sns.histplot(data["age"], color = "pink", edgecolor = "maroon", bins = 20)
plt.xlabel("Age in Years")
plt.ylabel("Frequency")
plt.title("Age of Titanic Passengers")
plt.figtext(0.3, -0.01, "Source: https://data.world/nrippner/titanic-disaster-dataset")
```

Here is the completed output.

![Python Histogram](https://raw.githubusercontent.com/darianrd/StatBlog/refs/heads/main/assets/img/PyHist.png)

Again, when creating our boxplot, the format will be very similar to the histogram. In this case, we will call the *survived* and *fare* variables from our dataset. Customizing the colors is essentially the same as before, except that we will use the argument *linecolor* instead of *edgecolor* to specify the outline color for the graph. We will also be changing the outlier markers using the *flierprops* argument and changing the shape and fill color. Adding labels to the graph works exactly the same as with the histogram.

```python
sns.boxplot(x = data["survived"], y = data["fare"], color = "pink", linecolor = "maroon", flierprops = {"marker":".", "markerfacecolor":"maroon")
plt.xlabel("Passenger Survived")
plt.ylabel("Passenger Fare in Dollars")
plt.title("Comparison of Titanic Passenger Fare to Survival Rate")
plt.figtext(0.3, -0.01, "Source: https://data.world/nrippner/titanic-disaster-dataset")
```

Here is the completed output.

![Python Boxplot](https://raw.githubusercontent.com/darianrd/StatBlog/refs/heads/main/assets/img/PyBox.png)

# Conclusion

I hope that this tutorial has been helpful and informative. Try creating and customizing these plots for yourself, and send me an email with any questions or additional insights you have!
