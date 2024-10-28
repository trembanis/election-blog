---
title: "Blog Post #8"
author: Ella Trembanis
date: '2024-10-28'
output:
  html_document:
    df_print: paged
categories: []
tags: []
slug: "blog-post-8"
---

Welcome to my final regular blog post before Election Day! At T-minus 8 days until November 5th, we are firmly in the eleventh hour of the 2024 race – perfect timing for my predictive model to shake up the electoral map.

# Popular Vote

In – hopefully – a promising sign, my popular vote model has begun to stabilize. Since there is a slight lag in 538’s poll aggregation reporting, the regression still uses the national poll average from three weeks before Election Day. I have substituted the incumbent variable, which seems ill-equipped to handle Harris’ and Trump’s competing claims to incumbency advantages, with a dummy variable that is coded 1 if the candidate is a member of a previous presidential administration, and 0 otherwise. Note that the model only predicts Democratic vote share, so it does not address how Trump’s status should be classified. The Q2 Index of Consumer Sentiment and lagged vote share variables have been retained from previous iterations of my model.

I am currently predicting a 52.78% Harris two-party popular vote share, down just 0.76% from last week. The table below shows the point estimate along with upper and lower bounds at the 80% confidence level. The interval straddles the 50% mark, so the model cannot predict a clear winner without incorporating much more uncertainty.
















| Dem Two-Party Vote Share| Lower Bound| Upper Bound|
|------------------------:|-----------:|-----------:|
|                    52.78|       48.24|       57.32|

The adjusted R-squared, which measures the amount of variation in Democratic vote share that can be explained by the four included variables, is approximately the same, at 0.76. The mean of the absolute value of out-of-sample residuals, based on the results of a cross-validation procedure, is very slightly smaller: 2.35, compared to 2.65. Overall, the in- and out-of-sample accuracy seems to be roughly equivalent between the models.

# Electoral College

In lieu of dedicating a separate section to shocks, this week’s thematic focus, I am featuring one in my new electoral college prediction!

Intriguingly, while swapping in the previous administration variable had little impact on my popular vote prediction, it drastically changed the electoral map. Last week, my model predicted that Harris would secure the Blue Wall and narrowly clinch a victory in the electoral college with exactly 270 votes. As the table below indicates, the new model has all seven swing states breaking for Trump. Once again, wide confidence intervals at the 80% confidence level blur the point estimates.







|State          | Dem Two-Party Vote Share| Lower| Upper|Winner     |
|:--------------|------------------------:|-----:|-----:|:----------|
|Arizona        |                    48.13| 42.57| 53.70|Republican |
|Georgia        |                    48.18| 42.62| 53.74|Republican |
|Michigan       |                    49.45| 43.89| 55.01|Republican |
|Nevada         |                    48.42| 42.86| 53.99|Republican |
|North Carolina |                    47.51| 41.94| 53.07|Republican |
|Pennsylvania   |                    49.09| 43.52| 54.65|Republican |
|Wisconsin      |                    48.90| 43.33| 54.46|Republican |

The map below visualizes the same results. Under this model, Harris would receive 223 electoral votes (not counting D.C.) and Trump would comfortably win the presidency.

<img src="{{< blogdown/postref >}}index_files/figure-html/fig 1 print-1.png" width="672" />

Given this big swing, it is worth performing a quick sanity check on the rest of the map. From the simple map above, it does seem like the predictions for the noncompetitive states are plausible. Another map, below, goes somewhat further by sketching the predicted two-party popular vote margin for each state. I should caution against directly interpreting these results, since I am approximating Trump’s two-party vote share (100 - Harris’ vote share), but it is not being directly predicted by the model. As a quick visual test of the model’s coherence, however, it does pretty well (Pennsylvania is very light-colored, California is dark blue, etc.).



<img src="{{< blogdown/postref >}}index_files/figure-html/fig 2 print-1.png" width="672" />

So, what is the substantive meaning of this red wave? In lecture, we discussed the possibility that polls across the nation could be systematically biased in one direction or the other. If Trump voters are even shier than pollsters expect this year, for instance, we might expect a map like this one to result. However, the difference between this model and its previous iteration has nothing to do with polls: due to the 538 lag, only the previous administration variable changed. Perhaps the real story is that members of previous administrations enjoy more of the downsides of “incumbency” – association with economic downturns and unpopular policies – and fewer of the advantages. In other words, I may have been treating Harris too much like Biden and too little like herself.

That’s it for today – thank you for joining me for these weekly blog posts! I will be back next Monday with my final predictions.

