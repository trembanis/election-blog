---
title: "Post-Election Reflection"
author: Ella Trembanis
date: '2024-11-18'
output:
  html_document:
    df_print: paged
categories: []
tags: []
slug: "post-election-reflection"
---










































Welcome back! Now that the dust has (more or less) settled, I am back on the blog to reflect on my model’s performance on Election Day.

# A Tale of Two Models

As a reminder, the following table summarizes the basic characteristics of my two models. Note that the R-squared and adjusted R-squared statistics are taken from the pre-election data pool – these will be updated later on in this post.


|                                                    |Popular Vote Model |Electoral College Model |
|:---------------------------------------------------|:------------------|:-----------------------|
|Intercept                                           |15.806             |8.105                   |
|Index of Consumer Sentiment (C)                     |0.008              |-0.035                  |
|National Poll Average, 1 Week Left (P)              |0.674              |-0.033                  |
|Candidate Was In Previous Administration (A)        |-1.358             |-4.307                  |
|Previous Year National Two-Party Vote Share (L)     |0.074              |not included            |
|Previous Year State Two-Party Vote Share (V)        |not included       |0.6                     |
|State Poll Average or Imputed Support, All-Time (S) |not included       |0.425                   |
|Number of Observations                              |13                 |559                     |
|R-squared                                           |0.806              |0.779                   |
|Adjusted R-squared                                  |0.709              |0.777                   |

<img src="{{< blogdown/postref >}}index_files/figure-html/print fig1-1.png" width="672" />

# Assessing My Popular Vote Model

<img src="{{< blogdown/postref >}}index_files/figure-html/print pop_acc_plot-1.png" width="672" />


|Regression                                       | Adjusted R-squared| 2024 Bias (Actual - Predicted)| Mean Squared Error| Root Mean Squared Error|
|:------------------------------------------------|------------------:|------------------------------:|------------------:|-----------------------:|
|All Variables                                    |               0.69|                          -1.96|               4.78|                    2.19|
|No Polling Average                               |               0.60|                          -0.04|               7.03|                    2.65|
|No Index of Consumer Sentiment                   |               0.72|                          -2.05|               4.83|                    2.20|
|No Previous Administration Dummy                 |               0.69|                          -3.34|               5.47|                    2.34|
|No Lagged Vote Share                             |               0.69|                          -2.76|               5.30|                    2.30|
|Swap GDP Growth for ICS                          |               0.73|                          -2.51|               4.25|                    2.06|
|Swap Incumbent Party for Previous Administration |               0.65|                          -3.40|               5.47|                    2.34|

# Assessing My Electoral College Model

<img src="{{< blogdown/postref >}}index_files/figure-html/print fig_er-1.png" width="672" />


|Metric                  | All States| Battlegrounds|
|:-----------------------|----------:|-------------:|
|Bias                    |      -1.06|          0.65|
|Mean Squared Error      |       2.94|          0.75|
|Root Mean Squared Error |       1.71|          0.86|
|Mean Absolute Error     |       1.39|          0.77|

# Failures, Successes, & Hypotheses

In the following several sections, I will discuss some possible blindspots in my models. Though I will not resolve these issues in full today, I will outline a few strategies for improving the models that could be implemented given enough time and high quality data.

## Global Context

## Inclusivity of “Previous Administration”

## Name Recognition

## Ambiguity of ICS

## Sample Size

## A Polling Paradox

# That’s All, Folks!

Thank you for joining me this week! This is, unfortunately, the end of the road for these particular predictive models, but I look forward to returning in a few weeks’ time with my final post, which will discuss the election through the lens of Nebraska politics. See you then!
