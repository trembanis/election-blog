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

As a reminder, the following table summarizes the basic characteristics of my two models.


|                                                    |Popular Vote Model          |Electoral College Model |
|:---------------------------------------------------|:---------------------------|:-----------------------|
|Intercept                                           |15.806                      |8.105                   |
|Index of Consumer Sentiment (C)                     |0.008                       |-0.035                  |
|National Poll Average, 1 Week Left (P)              |0.674                       |-0.033                  |
|Candidate Was In Previous Administration (A)        |-1.358                      |-4.307                  |
|Previous Year National Two-Party Vote Share (L)     |0.074                       |not included            |
|Previous Year State Two-Party Vote Share (V)        |not included                |0.6                     |
|State Poll Average or Imputed Support, All-Time (S) |not included                |0.425                   |
|Prediction for Harris 2024                          |51.26% Two-Party Vote Share |226 Votes               |

The first three explanatory variables – C, P, and A, in the table above – are exactly the same across both models. Together, they roughly mirror the three facets of Abramowitz’s Time for Change model: a measure of economic performance, a survey of public opinion, and an indicator of incumbency status.

The models are differentiated by the final two components: lagged vote share and state-level polling. My goal was to make the models as similar as possible, so both incorporate a measure of previous year Democratic two-party vote share, but the popular vote model only uses the national result (L), while the electoral college model uses state results (V). S, an all-time state-level polling average, is the only variable with no equivalent in the popular vote regression. Since polls are not – or were not, at the time that I finalized the prediction – available in all states, S also has some internal inconsistencies, as “missing” states were populated by applying their deviation from the national popular vote in 2020 to P, the most recent national polling average from 538.

Intriguingly, my electoral college model hit the mark (see Figure I below, which correctly predicts Trump’s sweep of the battleground states) while my nearly identical popular vote model floundered, predicting a Harris victory that clearly has not come to pass.

<img src="{{< blogdown/postref >}}index_files/figure-html/print fig1-1.png" width="672" />

# Assessing My Popular Vote Model

Let’s start with what went wrong: the popular vote model.

When we zoom out to look at the model’s predictions over multiple election years, the model’s accuracy begins to look more respectable. Figure II shows that the historical elections are well distributed along the fitted line, with 2024 falling roughly in the middle of the pack in terms of accuracy.

<img src="{{< blogdown/postref >}}index_files/figure-html/print pop_acc_plot-1.png" width="672" />

Admittedly, the data points are few and far between, but based on this visualization, the model does not seem to be getting substantially better – or worse – over time. The model does slightly overestimate Democratic vote share in 2020 and 2024, but I am hesitant to take those two observations as proof of a systematic tendency to underestimate Trump, especially since the model is inclined to overestimate Clinton’s vote share in 2016.

Next, I tweaked the regression formula, one element at a time, with the hope of weeding out any problematic variables. The results of this investigation can be found in the table below.


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

In the following several sections, I will discuss some possible blindspots in my models. Though I will not resolve these issues in full today, I will outline a few strategies that could be implemented given enough time and sufficiently robust data.

## Global Context

## Inclusivity of “Previous Administration”

## Name Recognition

## Ambiguity of Consumer Sentiment

## Sample Size

## A Polling Paradox

# That’s All, Folks!

Thank you for joining me this week! This is, unfortunately, the end of the road for these particular predictive models, but I look forward to returning in a few weeks’ time with my final post, which will discuss the election through the lens of Nebraska politics. See you then!
