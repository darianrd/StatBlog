---
layout: post
title: "Tutorial: Create and Customize EDA Plots in R and Python"
description: A tutorial for creating plots for exploratory data analysis using R and Python.
---

# Introduction

In this blog post, I will be explaining how to create EDA plots and add customizations to them in R and Python. First, let's talk about some basics of data analysis.

### What is EDA?

In statistics, exploratory data analysis (or EDA) is a method of gaining information about the data we are working with before using it to create models and made predictions. EDA is typically used to summarize data through exploring patterns and relationships between the variables of interest and usually includes visual representations of the data, such as scatterplots and histograms.

### Why learn how to analyze data in more than one language?

Many of you may be familiar with creating EDA plots in at least one programming language and may be wondering why you would create plots in any other language. However, there are several reasons why it could be useful to be familiar with more than one language for analyzing data, including:
- Some languages may be easier to navigate but have less customizability, while other languages are more complex to learn but may be more flexible with customizability.
- Different languages have different tools, so you can choose a language with tools that may be better suited for your specific project.
- It can help you learn how to approach data-related problems from different perspectives.
- It makes you more marketable to potential employers.

# Creating Plots

Now, let's get into creating some EDA plots. For this tutorial, I will be using Titanic passenger data from the [Titanic Disaster Dataset](https://data.world/nrippner/titanic-disaster-dataset). We'll start by learning how to create a histogram and boxplot in R using the ggplot2 package.

### Plotting in R

First, we will load the *tidyverse* package (which contains ggplot2) and read in our dataset.

```
library(tidyverse)

data <- read.csv("~/Desktop/titanic.csv")
```


