---
toc: false
layout: post
description: Data efficiency of linear and nonlinear regression models of asset return panel data is enhanced by accounting for cross-sectional correlations and longitudinal volatility clusters of residuals.
categories: [efficiency, deep-learning, time series, panel]
title: Efficient estimation of predictive models using high-frequency high-dimensional data

---

My Master's thesis, submitted to the Institute for Statistics and Econometrics of the Christian-Albrechts-Universität zu Kiel, Germany, proposes a method to increase the data efficiency of neural networks for asset return prediction.


## Abstract

In this thesis, the data efficiency of linear and nonlinear regression models of asset return panel data is enhanced by accounting for cross-sectional correlations and longitudinal volatility clusters of residuals. The procedure is motivated by the infeasible generalized least squares estimator. In an extension, a generalized least squares loss function is proposed to efficiently fit nonlinear relationships via deep neural networks. Feasibility is achieved by estimating the unobserved covariance matrix of residuals with a nonparametrically eigenvalue-regularized ensembled pairwise integrated covariance (NER EPIC) matrix estimator applied to high-frequency returns in high dimensions. Monte Carlo evidence confirms efficiency gains for linear and nonlinear conditional expectation models in finite- samples. A study of historical stock market data for the 100 largest US-based stocks shows substantially improved portfolio return characteristics of general- ized models compared to their standard counterparts. A trading strategy based on the predictions of a neural network, minimizing the proposed generalized ob- jective function, generates an out-of-sample information ratio of 2.59. Compared to a model with the same hyperparameters but minimizing the conventional MSE loss function, this represents an improvement of close to 150%.

Get the thesis [here](https://github.com/jpwoeltjen/researchBlog/blob/master/_posts/Thesis.pdf). 

