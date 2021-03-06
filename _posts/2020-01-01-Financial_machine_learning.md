---  
toc: false  
layout: post  
description: Outlining challenges and their solution of machine learning applied to financial data.  
categories: [efficiency, deep learning, time series, panel, nonstationarity, heteroskedastisity, hierarchical, bayesian,]  
title: Challenges in Financial Machine Learning
---  
  
Why is machine learning applied to financial data hard? What are the main differences of financial data compared to datasets where machine learning techniques work well.
  
  
  
## Panel model  
- $p$ assets.  
- $n$ time steps.  
  
1. Nonlinearity of conditional expectation  
   - Deep neural network  
  
2. Nonstationarity of conditional expectation  
   - Financial markets are dynamic; old patterns are arbitraged away and new patterns emerge.  
   - The optimal weights of neural networks change smoothly over time  (there might also be sudden shocks).  
   - Layers close to the input are more stable while layers closer to the output must adapt quickly to new market dynamics.
   - <https://jpwoeltjen.github.io/researchBlog/efficiency/time%20series/deep%20learning/2020/08/28/random_walk_deep_net_reg.html>
  
3. Hierarchical structure  
   - Each asset/sector can have different weights (esp. in the last layer).
   - But there is dependence.
   - Even though the absolute amount of data is big when pooled. Data is limited relative to model complexity.  
   - Use covariance matrix as measure of similarity.  
   - Dirichlet process  
		- Allows for infinite clusters but promotes sparsity.  
   - Alternatively, use asset type encoding (loadings on sector, industry, risk factors) as feature in a standard net.
  
4. High noise component with cross-sectional correlation and longitudinal volatility clusters.
   - Assets are correlated.  
   - Volatility is stochastic and autoregressive. 
   - Improve data efficiency of conditional expectation models by accounting for it.
	    - <https://jpwoeltjen.github.io/researchBlog/efficiency/deep%20learning/time%20series/panel/2020/08/10/Efficient_estimation_of_predictive_models-using_high-frequency_high-dimensional_data.html>
   - In a Bayesian setting, compute the daily integrated covariance matrix with high-frequency data and use the Kalman smoother to get a better estimate (this is more principled and Bayesian than the adhoc moving average I used in the thesis). Then use this estimator as the covariance matrix model of the multivariate (Gaussian) likelihood function of the p dimensional asset returns. (Remember: The covariance matrix estimate may use future data in the training phase.)
   - For forecasting: Use stochastic volatility models or multivariate GARCH models.
       - Condition on events (earnings announcements, news, etc.)
  
5. The dimensionality of the covariance matrix is high.  
   - The number of assets is large relative to the sample size.  
   - Hence sample eigenvalues are over-dispersed and the sample covariance matrix is ill-conditioned.  
  
6. Prices are observed irregularly and with noise at high frequency.  
   - Intraday prices contain microstructure noise and are observed non-synchronously across assets.
   - <https://hfhd.readthedocs.io/>
  
7. Estimates of uncertainty is important.
   - Bayesian framework allows for uncertainty estimates. 
   - A decision is always better if one accounts for uncertainty.  
   - Main portfolio optimization result is Markowitz:  
        - optimal weights depend on mean and variance of returns.  
        - assumes first two moments are known.  
        - when estimates are used instead, need to account for epistemic uncertainty of estimates as well  
          - Aleatoric uncertainty: noise inherent in the observations. (i.e. variance of returns)  
          - Epistemic uncertainty accounts for uncertainty in the model -- uncertainty which can be explained away given enough data. (i.e. variance of mean and variance estimates)
          - <https://jpwoeltjen.github.io/researchBlog/probabilistic%20programming/bayesian/portfolio%20optimization/2020/10/01/bayesian_porfolio_optimization.html>

8. Time series features.
	- Recurrent neural networks (LSTM, GRU)
	- Transformers adapted to time series.
	
   
2 and 3: Each point in asset-time has different weights, but there is dependence between them. Weights change smoothly over time and weights of similar stocks are themself similar. A stock is similar to another, e.g., if it operates in the same industry. A company can have several arms, though. A stock can be correlated to many other stocks, the covariance matrix is the right object to encode this similarity.    

  


  

  

