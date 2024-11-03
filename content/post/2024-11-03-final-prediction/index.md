---
title: "Final Prediction"
author: Ella Trembanis
date: '2024-11-03'
output:
  html_document:
    df_print: paged
categories: []
tags: []
slug: "final-prediction"
---



























# Introduction

Welcome to my final prediction for the 2024 presidential election!

With early voting well underway and only a few days left until Election Day, the race remains stubbornly in the toss-up category, according to expert forecasters such as the Cook Political Report and Sabato’s Crystal Ball. My prediction, unfortunately, is no exception to this trend. While I will predict a winner in today’s post, the predictive intervals produced by both my popular vote and electoral college models encompass scenarios in which either candidate could win.

# My 2024 Model

My model uses a simple OLS regression, with the following explanatory variables: a dummy indicator of whether the candidate served in a previous presidential administration, Q2 consumer sentiment, lagged vote share, and a recent polling average. The outcome variable is the two-party vote share for the Democratic candidate.

## Previous Administration



## Index of Consumer Sentiment

<img src="{{< blogdown/postref >}}index_files/figure-html/print ics_outliers-1.png" width="672" />


## Lagged Vote Share



## Poll Average


|State         |Dem Two-Party Vote Share (Polls Available) |Dem Two-Party Vote Share (Polls Imputed) |
|:-------------|:------------------------------------------|:----------------------------------------|
|Indiana       |41.47                                      |41.76                                    |
|Massachusetts |65.48                                      |66.95                                    |
|Nebraska      |40.19                                      |40.18                                    |
|Washington    |59.28                                      |59.79                                    |


# Out-of-Sample Tests

<img src="{{< blogdown/postref >}}index_files/figure-html/print figa-1.png" width="672" />

<img src="{{< blogdown/postref >}}index_files/figure-html/print figx-1.png" width="672" />

<img src="{{< blogdown/postref >}}index_files/figure-html/print figy-1.png" width="672" />

<img src="{{< blogdown/postref >}}index_files/figure-html/print figza-1.png" width="672" />

<img src="{{< blogdown/postref >}}index_files/figure-html/print figzb-1.png" width="672" />


# Popular Vote Results


| Dem Two-Party Vote Share| Lower Bound| Upper Bound|
|------------------------:|-----------:|-----------:|
|                    51.26|       46.52|       55.99|

# Electoral College Results

<img src="{{< blogdown/postref >}}index_files/figure-html/print fig1-1.png" width="672" />


|Region               | Dem Two-Party Vote Share|Winner     |
|:--------------------|------------------------:|:----------|
|Alaska               |                    42.53|Republican |
|District Of Columbia |                    94.12|Democrat   |
|Hawaii               |                    71.77|Democrat   |


|State          | Dem Two-Party Vote Share| Lower| Upper|Winner     |
|:--------------|------------------------:|-----:|-----:|:----------|
|Arizona        |                    47.58| 41.98| 53.18|Republican |
|Georgia        |                    47.64| 42.04| 53.23|Republican |
|Michigan       |                    48.92| 43.33| 54.52|Republican |
|Nevada         |                    47.88| 42.28| 53.48|Republican |
|North Carolina |                    46.99| 41.39| 52.58|Republican |
|Pennsylvania   |                    48.58| 42.98| 54.18|Republican |
|Wisconsin      |                    48.40| 42.80| 54.00|Republican |

<img src="{{< blogdown/postref >}}index_files/figure-html/print fig2-1.png" width="672" />

