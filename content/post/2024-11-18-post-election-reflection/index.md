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


|                                                 | Adjusted R-squared| 2024 Bias (Actual - Predicted)| Mean Squared Error| Root Mean Squared Error|
|:------------------------------------------------|------------------:|------------------------------:|------------------:|-----------------------:|
|All Variables                                    |               0.69|                          -1.96|               4.78|                    2.19|
|No Polling Average                               |               0.60|                          -0.04|               7.03|                    2.65|
|No Index of Consumer Sentiment                   |               0.72|                          -2.05|               4.83|                    2.20|
|No Previous Administration Dummy                 |               0.69|                          -3.34|               5.47|                    2.34|
|No Lagged Vote Share                             |               0.69|                          -2.76|               5.30|                    2.30|
|Swap GDP Growth for ICS                          |               0.73|                          -2.51|               4.25|                    2.06|
|Swap Incumbent Party for Previous Administration |               0.65|                          -3.40|               5.47|                    2.34|

Generally speaking, the adjusted r-squared improvements were minimal. In most cases, dropping or swapping a variable produced a model that explained only about as much, if not less, of the variation in Democratic two-party vote share. 

The exceptions to this are the model that dropped ICS and the model that substituted GDP growth in its place. In both cases, I should note, the percentage of variation explained increased by a modest 3 to 4 points, the MSE (mean squared error) and RMSE (root mean squared error) barely moved, and the resulting prediction overestimated Harris more severely than the original model. While I am not convinced that consumer sentiment is the driving factor behind my model’s failure in 2024 specifically, there seems to be reason to be cautious of consumer sentiment’s long-term predictive power, at least when it is serving as the sole economic indicator.

The other standout from this table is the “no polling average” model, which yielded a 2024 national popular vote prediction that was just 0.04 points over Harris’s two-party vote share (though the actual number may shift slightly in the coming days and weeks as the last votes are tallied). This improvement, however, comes at the cost of a lower adjusted r-squared and the highest MSE and RMSE of all seven models – this is perfectly fine if the model’s only purpose is to predict the 2024 results, but it could compromise its ability to generate plausible predictions for future elections.

So far, we have identified two possible weakness areas: polls and consumer sentiment. I will revisit both and offer substantive hypotheses in the final section of this post. For now, we should check in on the electoral college model.

# Assessing My Electoral College Model

Predicting a winner in each state is one thing – the real challenge is predicting state-level vote share, and my model had its fair share of mistakes in that respect.

Figure III, below, displays each state’s prediction error. Blue states had predictions that overestimated Harris’s eventual vote share, while red states underestimated her.

The most biased states were New Jersey (-4.7 points) and Illinois (-3.5 points). By contrast, the state most biased in favor of Trump, North Carolina, was much closer to that state’s observed vote share (+1.3 points).

<img src="{{< blogdown/postref >}}index_files/figure-html/print fig_er-1.png" width="672" />

The following table breaks these results down by two salient characteristics: poll availability and battleground status.


|                        | All States| Polls Imputed| Polls Available| Battlegrounds|
|:-----------------------|----------:|-------------:|---------------:|-------------:|
|Bias                    |      -1.06|         -1.33|           -0.73|          0.65|
|Mean Squared Error      |       2.94|          3.30|            2.24|          0.75|
|Root Mean Squared Error |       1.71|          1.82|            1.50|          0.86|
|Mean Absolute Error     |       1.39|          1.49|            1.26|          0.77|

The first takeaway from this table is that, on average, my model overestimated Harris’s performance. This in itself is interesting, since I ultimately predicted a comfortable Trump win in the electoral college, and the second and third columns help shed some light on this discrepancy.

As I mentioned earlier, I had to rely on an imputation procedure for the 27 states (and one district) that did not have accessible polling data for 2024. These states (New Jersey and Illinois included) seemed to have received predictions that were more biased in favor of Harris than the nation as a whole.

Where polls were available, they seem to have yielded better, though still slightly left-skewing, predictions. This is yet another mystery to tuck in your back pocket for later: national polls seem to have, if anything, overinflated Harris’s vote share in my popular model, but state-level polls nudged my electoral college predictions to the right.

Still, the table has one more surprise in store: the battleground states. All seven swing states had polling data available, but their predictions were even less favorable to Harris than in non-competitive polled states. In fact, my battleground predictions slightly underestimated Harris’s actual performance. Here, perhaps, is evidence of the Harris campaign apparatus at work.

# Failures, Successes, & Hypotheses

In the following several sections, I will discuss some possible blindspots in my models. Though I will not resolve these issues in full today, I will outline a few strategies that could be implemented given enough time and sufficiently robust data.

## Global Context

## Inclusivity of “Previous Administration”

## Name Recognition

## Ambiguity of Consumer Sentiment

## Sample Size

## A Polling Paradox

I have left the most pressing question for last: why did polls improve my electoral college predictions and mislead my popular vote model in the very same election cycle?

The answer, I think, lies in the type of polls involved.

My popular vote model exclusively uses 538's national polling average from the week before Election Day, under the assumption, borrowed from Gelman and King, that voters will converge on their intended candidate in the final stretch of the campaign. However, it could also be the case that, in the run-up to Election Day, pollsters under pressure to land on the "correct" estimate exhibit more herding behavior, and that post-hoc re-weighting and/or reluctance to release outlier results creates a systematic bias in the last-minute average. If that was the case this year, a slight initial skew in favor of Harris -- whether it resulted from pure chance or left-leaning pollsters putting their thumbs on the scale -- could have played a role in the failure of my model.

To test this, I would first compare the prediction generated with 538's weighted average to RealClearPolitics' simple average, to see if 538's pollster ratings exacerbated the potential herding problem, and I would also examine historical data, broken down by pollster, to see how variance between pollsters develops immediately before Election Day. I might also want to look at trends in pollsters' output over time -- it seems unlikely that pollsters would disclose that they decided not to publish a faulty poll, but a drop in publicized data before Election Day could perhaps provide a hint at these behind-the-scenes practices.

Despite these reservations, the decent performance of both of my models leads me to think that the last-minute national polling average is not without its benefits. In the case of the electoral college model, combining the weekly national average with an all-time state-level polling average, which should in theory be more resistant to short-term shocks, seems to have done a better job of predicting voter behavior. This, too, makes a certain amount of sense. It can be convenient to describe voters in unambiguous terms -- myopic, retrospective, disengaged, etc. -- but in practice, there is no way of neatly separating long-term preferences from last-minute jolts. Many voters will wrestle with both at the ballot box, and both have their role to play in the models.

# That’s All, Folks!

Thank you for joining me this week! This is, unfortunately, the end of the road for these particular predictive models, but I look forward to returning in a few weeks’ time with my final post, which will discuss the election through the lens of Nebraska politics. See you then!