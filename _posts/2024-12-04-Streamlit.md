---
layout: post
title: The Only App You’ll Ever Need (For Analyzing Car Crash Data in Utah in 2022)
description: Introducting a Streamlit app for analyzing the FARS data from my last blog post.
---

# Introduction
In my last blog post, I discussed a dataset that I compiled from the Fatality Analysis Reporting System (FARS) API, and in this post we will be further exploring the data through a Streamlit app that I created to display the data I collected. My app focuses on answering the same questions as my last post:

1. Which day of the week had the highest number of crashes?

2. What type of weather resulted in the highest average number of fatalities?

3. How are lighting condition, population type, and number of car crashes related?

However, I chose to display the data a little differently than in my exploratory data analysis from my last post to hopefully gain some additional insights about these questions.

# Streamlit App
For those who aren’t familiar with Streamlit, it is a service which allows you to create dynamic, interactive web applications for various purposes. The code is written in Python, ran on a local server, and then pushed to and deployed through GitHub. For simple data exploration, the creation of a Streamlit app is fairly straightforward. If you want to view my code to see how I created my app, you can access [my GitHub repository here](https://github.com/darianrd/Accident-Data). 

For now, I want to walk you through my app and how it can be used to derive answers and insights to the questions I’ve posed. To follow along, you can view [my Streamlit app here](https://accident-data.streamlit.app).

The first thing to notice are the tabs at the top of the page, which can be clicked to access different aspects of my data.

![Tabs](https://raw.githubusercontent.com/darianrd/StatBlog/refs/heads/main/assets/img/Tabs.png)

The first tab is simply a description of the variables in my dataset so that the user knows how to interpret each of the visuals included in the subsequent tabs.

The second thing to notice are the filtering options on the left side of the screen.

![Filters](https://raw.githubusercontent.com/darianrd/StatBlog/refs/heads/main/assets/img/Filters.png)

The first filter for city is associated with the second tab, “Raw Data Table”. This filter enables the user to select one or more Utah cities to display in the data table for more selective viewing of the data.

The third tab, “Day of Week Graph”, does not have any filtering options and simply displays a line chart of the frequency of accidents for each day of the week. However, the data points can be hovered over to view the exact number of fatalities for each day of the week.

The second filter for weather category is associated with the fourth tab, “Weather Graph”. I have grouped each weather category into groups labeled “Mild”, “Moderate”, and “Severe”, and this filter allows the user to view the average number of fatalities for each weather type with separate graphs for each of the three new groups.

The third and final filter for population type is associated with the fifth and final tab, “Lighting and Population Graph”. Similar to the weather graph, this allows the user to view separate graphs for the two different population types, with each graph displaying the average number of fatalities for each lighting type.

# Insights
To answer my first question, the Day of Week Graph once again makes it clear that Saturday had the highest number of fatalities, with 102 fatalities. The second highest number of fatalities occurred on Friday, accounting for 80 fatalities.

![Day of Week Graph](https://raw.githubusercontent.com/darianrd/StatBlog/refs/heads/main/assets/img/Day%20of%20Week%20Graph.png)

In answering my second question, We can use the new weather groups I’ve created. The moderate weather category (fog, smog, smoke, rain, and snow) have the lowest average fatalities, with all of them being 1 (the lowest possible number of fatalities in this dataset). The weather types in the mild category (clear and cloudy) each only have slightly above an average of 1 fatality. In the severe category, two of the weather categories (blowing snow, and sleet or hail) only have an average of 1 fatality each, but as I mentioned in my last post, the severe crosswinds category has an average of 1.33 fatalities, which is the highest of all the averages. The moderate weather category seems to be least likely to lead to a higher number fatalities, while the mild and severe weather categories both seem to have about the same likelihood of causing more fatalities.

![Mild Weather](https://raw.githubusercontent.com/darianrd/StatBlog/refs/heads/main/assets/img/Mild%20Weather.png)
![Moderate Weather](https://raw.githubusercontent.com/darianrd/StatBlog/refs/heads/main/assets/img/Moderate%20Weather.png)
![Severe Weather](https://raw.githubusercontent.com/darianrd/StatBlog/refs/heads/main/assets/img/Severe%20Weather.png)

For my last question, the graphs clearly show two things: That there were less fatal car crashes in rural areas overall, possibly due to the lower volume of traffic, and that for both rural and urban areas, fatal crashes were more likely to occur in daylight conditions, which I don’t have an explanation for. I would be interested to do further exploration and understand why there would be more crashes in good lighting conditions than in poor ones.

![Rural Lighting](https://raw.githubusercontent.com/darianrd/StatBlog/refs/heads/main/assets/img/Rural%20Lighting.png)
![Urban Lighting](https://raw.githubusercontent.com/darianrd/StatBlog/refs/heads/main/assets/img/Urban%20Lighting.png)

# Conclusion
In closing, there is a lot that could be explored with this dataset, especially with the powerful functionality of tools like Streamlit. I appreciate you taking the time to check out my blog posts and my app, and hope that they have both shown you the possibilities available to you for data exploration. If you would like to learn more about Streamlit and possibly create your own app, I would encourage you to check out the [documentation provided on their website](https://docs.streamlit.io). I found the [widget documentation](https://docs.streamlit.io/develop/api-reference/widgets) especially helpful in creating my app. [Here is a more comprehensive guide](https://www.datacamp.com/tutorial/streamlit) for creating a Streamlit app.

