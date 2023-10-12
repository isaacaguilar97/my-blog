---
layout: post
cover: 'assets/images/digitization.jpg'
navegation: True
title:  Exploratory Data Analysis Basics in R
date: 2023-10-11 15:18:00
tags: Data Science
subclass: 'post tag-test tag-content'
logo: 'assets/images/ghost.png'
author: Isaac
categories: Isaac
--- 

<p></p>

<p>As a data scientist, I understand the critical role that Exploratory Data Analysis (EDA) plays in the process of turning raw data into actionable insights. EDA serves as the foundation upon which data-driven decisions are built, making it a fundamental step in any data analysis project. In this blog post, we'll explore the why, what, and how of EDA, using the versatile R programming language to uncover the hidden gems within our dataset. Let's dive in!</p>

<h2 id="EDA_matters">Why EDA Matters</h2>

<p><b>A solid EDA is the compass that guides the data scientist through the tumultuous sea of raw data.</b> It allows us to grasp the essence of our dataset, understand its nuances, and identify potential pitfalls early in the analysis. A well-executed EDA not only saves time but also mitigates the risks of making erroneous conclusions based on flawed data. Conversely, neglecting EDA can lead to costly errors, missed opportunities, and flawed models.
Now, you might wonder, "Why R for EDA?" R is the perfect tool for the job because of its extensive libraries, packages, and its deep integration with data visualization tools. Plus, it's free and open-source. Now, let's get into the nitty-gritty of EDA.
</p>

<h2 id="TheWhat">What is Exploratory Data Analysis?</h2>

<p>Exploratory Data Analysis is the process of examining a dataset to summarize its main characteristics, often employing graphical representations and statistical techniques. The main objectives are to understand the data's structure, detect anomalies, uncover patterns, and form hypotheses for further analysis.</p>

<h2 id="EDAProcess">The EDA Process: A Quick Overview</h2>

<h3 id="Step1">Step 1 – Observe your Dataset (High level overview)</h3>

<p>Begin by loading your dataset into R and taking a preliminary look at its structure, dimensions, and the first few rows. This step gives you a bird's eye view of your data.</p>

<pre>
    {% raw %}
    {% highlight r %}
    # Lodad libraries
    library(tidyverse)
    library(DataExplorer)
    
    # Load the dataset
    data <- read.csv("bike share.csv")

    # Display the first few rows
    head(data)
    {% endhighlight %}
    {% endraw %}
</pre>

<p><img src="https://isaacaguilar97.github.io/my-blog/assets/images/head2.png" alt="Displaying Head Function" /></p>

<pre>
    {% raw %}
    {% highlight r %}
    # Other ways to overview you data:
    glimpse(data) # Lists the variable type of each column
    skim(bike) # Another view of summary
    summary(bike) # Produces result summaries of the results of various model fitting functions.
    {% endhighlight %}
    {% endraw %}
</pre>

<h3 id="Step2">Step 2 - Find missing values</h3>

<p>Identify and handle missing data to prevent inaccuracies and biases in your analysis. Visualizations like bar plots or heatmaps can be quite handy in spotting gaps in your data.</p>

<pre>
    {% raw %}
    {% highlight r %}
    # Show the percent missing in each column
    plot_missing(data)
    {% endhighlight %}
    {% endraw %}
</pre>

<p><img src="https://isaacaguilar97.github.io/my-blog/assets/images/missing.png" alt="Displaying missing value percentages"/></p>

<pre>
    {% raw %}
    {% highlight r %}
    # Other ways to check for missing data

    # Check for missing values 
    missing_values <- sum(is.na(data)) 

    # Create a bar plot barplot(missing_values, names.arg = names(data), col = "skyblue", xlab = "Variables", ylab = "Missing Values") 
    {% endhighlight %}
    {% endraw %}
</pre>

<h3 id="Step3">Categorize Values</h3>

<p>Distinguish between different types of variables - categorical (qualitative), continuous (quantitative), and discrete. This classification will inform if there is a need to change a variable type depending on your intent to use it, like changing a double to a factor or character to a double.</p>

<pre>
    {% raw %}
    {% highlight r %}
    # Lists the variable type of each column
    glimpse(data)
    {% endhighlight %}
    {% endraw %}
</pre>

<p><img src="https://isaacaguilar97.github.io/my-blog/assets/images/glimpse.png" alt="See variables' categories"/></p>

<pre>
    {% raw %}
    {% highlight r %}
    # Another way to check your data category 
    sapply(data, class) 
    {% endhighlight %}
    {% endraw %}
</pre>

<h3 id="Step4">Step 4 – Find Shape of Dataset</h3>

<p>Understanding the shape of your dataset is essential to help you choose the appropriate machine learning or statistical methods to use. The approach varies depending on the type of variable: categorical, continuous, or discrete. Let's explore how to visualize the distribution of these variable types using R.</p>

<p><b>For Continuous Variables:</b></br>
For continuous variables like temperature (temp), it's common to use histograms to visualize the distribution. Histograms divide the range of values into bins and display the frequency of data points within each bin. This helps you identify patterns and central tendencies.
</p>

<pre>
    {% raw %}
    {% highlight r %}
    # Plot a histogram for a continuous variable (e.g., 'temp') 
    hist(data$temp, col = "lightblue", main = "Temperature Distribution", xlab = "Temperature") 
    {% endhighlight %}
    {% endraw %}
</pre>

<p><img src="https://isaacaguilar97.github.io/my-blog/assets/images/temp.png" alt="Continuous category"/></p>

<p><b>For Categorical Variables:</b></br>
Categorical variables, like 'season,' can be explored using bar plots. Bar plots display the frequency of each category, making it easier to understand the distribution of these variables.
</p>

<pre>
    {% raw %}
    {% highlight r %}
    # Create a bar plot for a categorical variable (e.g., 'season') 
    barplot(table(data$season), col = "lightgreen", main = "Season Distribution", xlab = "Season", ylab = "Frequency")  
    {% endhighlight %}
    {% endraw %}
</pre>

<p><img src="https://isaacaguilar97.github.io/my-blog/assets/images/temp.png" alt="Continuous category"/></p>

<h3 id="Step5">Categorize Values</h3>

<h3 id="Step6">Categorize Values</h3>
