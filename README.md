Download Link: https://assignmentchef.com/product/solved-ie567-homework2-delta-normal-and-historical-simulation-var
<br>



<ol>

 <li><strong> Delta-Normal VaR.</strong> (total 2 points) The current value of the S&amp;P 500 index is 3,295.47, and you have written 60 calls with a strike price of 3,300 and written 60 puts with a strike price of 3,300. The calls and puts each have a multiplier of 100, that is the payoff of one call is 100 × max(<em>S<sub>T</sub></em> – 3,300), where <em>S<sub>T</sub></em> is the index number on the option expiration date <em>T</em>, and the payoff of one put is 100 × max(3,300  <em>S<sub>T</sub></em>).  Thus, the portfolio payoff will be payoff60 × 100 × max(<em>S<sub>T</sub></em> – 3,300) – 60 × 100 × max(3,300  <em>S<sub>T</sub></em>).  The options expire in one month (0.08333 year), the continuously compounded interest rate is 0.01 or 1% per year, the (continuous) dividend yield on the portfolio that underlies that S&amp;P 500 index is 0.02 or 2% per year, and the implied volatility of the options is 0.22 or 22%.  Please answer the following questions.</li>

</ol>




<ul>

 <li>(1/2 point) Please use the Black-Scholes-Merton formula to compute the current market value of the portfolio and also the portfolio delta, gamma, vega, and theta. What are the portfolio value, delta, gamma, vega, and theta?</li>

</ul>




<ul>

 <li>(1/2 point) Your estimate of the standard deviation of the simple return on the S&amp;P 500 index is 0.013 or 1.3% per day. Consider a simple VaR model in which the only market factor is the S&amp;P 500 index, and use the delta-Normal method with a probability of 5% to compute the VaR of the portfolio.  What is your estimate of the 5% VaR?</li>

</ul>




<ul>

 <li>(1/2 point) Next consider a more sophisticated VaR model with two market factors, the S&amp;P 500 index and the implied volatility.  Assume that the standard deviation of percentage changes in the implied volatility is 0.04 or 4% per day and the correlation between S&amp;P 500 returns and percentage changes in the implied volatility is 8.  What is your estimate of the 5% VaR? (The standard deviation of 4% per day means 4% of the previous value, not 4 percentage points.)</li>

</ul>




<ul>

 <li>(1/2 point) Why are your answers to parts (c) and (d) so different?</li>

</ul>




<em>Remark.</em>You might find the R package fOptions useful. It includes functions GBSOptions() and GBSGreeks() that will allow you to compute the values and Greeks of the options.

To use it, execute the command install.packages(“fOptions”) from the R Studio console. You should also include the line library(“fOptions”) in your R script before you call the functions.

<strong> </strong>

<ol start="2">

 <li><strong> Gather the data for questions 3-7.</strong> (0 points) Go to WRDS, and find the CRSP daily stock returns data. Download the returns of the SPDR S&amp;P 500 (ticker = SPY), SPDR Financial Select Sector Fund (ticker = XLF), Microsoft (ticker = MSFT), and Apple (ticker = AAPL) for the period running from January 2004 through December 2018. Create an R dataframe that contains the returns data. Your data frame should contain 3,775 observations of five variables, these being the date and the returns of the four securities.</li>

</ol>




<em>Remark.</em>  WRDS is at https://wrds-www.wharton.upenn.edu/.  We will talk about how you can access the WRDS data during class.




<h1>3.  A few preliminary calculations.</h1>




<ul>

 <li> Using the full data sample, what are the means of the daily returns of the four securities? What are the standard deviations?  What are the 5% quantiles?</li>

</ul>




<ul>

 <li> Using the returns from 2008, what are the means of the daily returns of the four securities? What are the standard deviations?  What are the 5% quantiles? (There were 253 trading days during 2008.)</li>

</ul>




<ol start="4">

 <li><strong>Historical simulation method.</strong>  (2 points)  Assume that you held a position of $5 million invested in the SPY, $3 million in the XLF, $1 million in MSFT, and $1 million in AAPL during each trading day in 2008 and 2009.  Specifically, you held this position from the close of trading on December 31, 2007 until the end of January 2, 2008 (the first day of 2008), then adjusted the position so that you had $5 million invested in the SPY, $3 million in the XLF, $1 million in MSFT, and $1 million in AAPL and held this position to the next day, and then adjusted the position again and held it to the next day, etc. Thus, each day you have had $5 million invested in the SPY, $3 million in the XLF, $1 million in MSFT, and $1 million in AAPL. The last day you should consider is December 31, 2009; this is the gain or loss on the position that you established at the close of trading on December 30, 2009 and held until the close of trading on December 31, 2009.</li>

</ol>




Use the historical simulation method with a one-day horizon and a confidence level of 99% (equivalently, a probability of 1%) to compute the value-at-risk of your portfolio during each trading day of 2008 and 2009.  In doing this, for each day use the returns on the market factors during the previous 1,000 days.




Create a graph to show how your estimates of value-at-risk vary throughout 2008 and 2009.  The horizontal axis should show the date, and the graph should show the estimates of the value-atrisk for each date.  (Your graph should show all four time series of VaR’s for Questions 47 on the same graph.)  Include the graph in the .docx or .pdf file that you submit via the Compass site.




<h1>5. Delta-Normal method with the equally-weighted covariance matrix estimator.</h1>

Use the delta-Normal method with a one-day horizon and a confidence level of 99% (equivalently, a probability of 1%) to compute the value-at-risk of your portfolio during each trading day of 2008 and 2009.  For each day estimate the covariance matrix using the equallyweighted estimator on p. 68 of Christoffersen (2012) and the simple returns on the market factors during the most recent 1,000 days, and assume that the expected returns are zero.




<h1>6.  Delta-Normal method using the exponentially-weighted covariance estimator.</h1>

Read about the RiskMetrics exponentially-weighted variance estimator on pp. 6970 of Christoffersen (2012).  Although Christoffersen does not discuss it, the generalization to the exponentially-weighted covariance estimator should be obvious.  Compute the delta-Normal value-at-risk for each trading day in 2008 and 2009, where for each day the covariance matrix is estimated using the exponentially-weighted estimator using  = 0.94.




<em>Remark</em>. Compute the covariance matrix using the simple returns, not the continuously compounded returns.  In thinking about how many past days should you use to compute the exponentially-weighted covariance matrix you should think about how large is <sup></sup> for various values of .




<ol start="7">

 <li><strong> Weighted historical simulation</strong>. (2 points) Use the weighted historical simulation method with a one-day horizon and a confidence level of 99% (equivalently, a probability of 1%) to compute the value-at-risk of your portfolio during each trading day of 2008 and 2009. In doing this, for each day use the returns on the market factors during the previous 1,000 days and set  = 0.995.</li>

</ol>