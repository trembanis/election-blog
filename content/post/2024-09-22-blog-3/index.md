---
title: 'Blog Post #3'
author: "By Ella Trembanis"
date: '2024-09-22'
output:
  html_document:
    df_print: paged
categories: []
tags: []
slug: "blog-post-3"
---

# Polls and Campaign Narratives

Felonies! Assassination attempts! Debate match-ups! With less than two months to go, the 2024 presidential race has already had its fair share of front-page moments -- but which will truly stick with voters?

Figure I (below) plots some newsworthy events from the past several months against the candidates' performance in national polls.









<img src="{{< blogdown/postref >}}index_files/figure-html/fig 1 print-1.png" width="672" />

In some cases, the graph lends itself to story-driven interpretations: there is, for instance, President Trump's short-lived bump in approval around the time of his conviction and the dramatic blue spike where Vice President Harris first assumed the role of presumptive candidate in lieu of Biden. 

At other times, however, the polls defy the headlines. The first assassination attempt against President Trump is virtually indistinguishable in this aggregation. While Biden's numbers were already low in early July, confusing Putin and Zelenskyy -- not to mention his opponent and his own vice president -- did not perceivably worsen his standing in the polls. Even the DNC, with its splashy line-up of Democratic stalwarts and Republicans for Harris, fades into the background.

Notice, too, how close the polls remain across these data. Even when one candidate has a particularly good week or month, they tend to remain within a scant few points of their opponent.

Polls can sometimes seem like a cheat code; a no-nonsense way to get into the minds of the electorate and satisfy our curiosity long before Election Day hands down its verdict. But as these inconsistent trends suggest, polls are deeply imperfect. They are swayed not just by what "should" matter -- policy proposals, scandals, good or bad speeches -- but also by the framing of the poll itself.

Do the pollsters have a partisan bias? How do they adjust their raw data, if it is lopsided demographically or politically? Will their respondents actually turnout in November? If they do, will they change their minds? All of these answers have powerful implications for poll-dependent forecasts.

The dull truth is that polls lie somewhere between magic bullet and useless drivel. My prediction for this week, like the graph above, uses simple aggregation to curb the effects of potential outliers among the major pollsters, and incorporates a measure of fundamental economic conditions to account for the influence of broad, retrospective evaluation on voter behavior.

# Predictions and Methodology



<img src="{{< blogdown/postref >}}index_files/figure-html/fig 2 print-1.png" width="672" />




|Model                  | Harris| Trump|
|:----------------------|------:|-----:|
|Polls by Week (A)      |  51.81| 50.58|
|Polls by Proximity (B) |  44.00| 42.95|
|GDP Growth (C)         |  51.93| 47.42|
|Combined (AC)          |  51.98| 47.94|
|Combined (BC)          |  47.96| 45.19|

# Assessing the Experts
