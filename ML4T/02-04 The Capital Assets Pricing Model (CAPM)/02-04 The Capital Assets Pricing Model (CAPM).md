# 02-04 The Capital Assets Pricing Model (CAPM)

## The Capital Asset Pricing Model
#### Lesson Overview

In this lesson, we're going to cover one of the most significant ideas affecting finance in the last century. It explains how the market impacts individual stock prices and it also provides a mathematical framework for hedge fund investing.

#### The Capital Asset Pricing Model (CAPM)

It's called the capital asset pricing model or CAPM for short. It was developed by a number of researchers independently in the 1960s.

#### Nobel Prize Winners

William Sharpe, Harry Markowitz, and Merton Miller jointly received the Nobel Prize for this contribution in 1990.

#### Impact of CAPM

The CAPM led to the development of index funds and the belief that you can't beat the market.

## Definition of a portfolio

#### Introduction to Capital Assets Pricing Model

Before we launch into details of the capital assets pricing model, we have to lay down a little bit of groundwork.

#### Definition of a Portfolio

Let's start with the definition of a portfolio. A portfolio is a weighted set of assets. So as an example, let's suppose you've got a portfolio that's got three different assets in it, Apple, Google, and Oracle. And if you look at the entire value of your portfolio, let's suppose that 60% of it is in Apple, 20% is in Google, and 20% is in Oracle. If we consider this as a set of weights, that means we've got 0.6 in Apple, 0.2 in Google and 0.3 in oracle.

#### Portfolio Weights

So, the first part of our definition of a portfolio is that $$w_i$$ is the proportion of funds that are in asset $$i$$. We require that the sum of all these $$w_i$$ is equal to 1, in other words they add up to 100%. Now sometimes, for leveraged portfolios that we're not going to cover in this class, this number might be greater than one. But skip that for now.

#### Shorting Stocks

We do allow that you might short some stocks. So for instance, let's suppose you shorted Google. Your allocation there would be, minus point two. So, let's refine this equation a little bit and require that the sum of the absolute value of the weights is equal to one. So, some of them might be short, some of them might be long. But, if you add up the absolute value their weights will require that to be 1.0.

#### Portfolio Returns

So now that we've defined what a portfolio is, let's think for a moment about what will the returns on a portfolio look like. So, it's a simple equation, really. It's the sum for each asset of the weight of that asset in the portfolio, times the return for that day, of the asset. We just add all those up, one by one, and boom, that's the return on the portfolio for that day.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/02-04%20The%20Capital%20Assets%20Pricing%20Model%20(CAPM)/images/2.png)

## Portfolio return

#### Question:
Okay, let's suppose you've got two stocks in your portfolio. Stock A and Stock B and 75% of your portfolio is in Stock A and -25% is in Stock B. In other words, you've taken a short position in Stock B. Now let's suppose on a particular day Stock A goes up 1%, and stock B goes down 2%. What's the return on your portfolio if this occurs

#### Answer
So remember from our equation on the previous page that the return on the portfolio is the sum of each return times the respective weight added together. So the weight for Stock A is 0.75 times 1%, and the weight for Stock B is negative 25%. The return was negative 2% for that stock also. So because we shorted B and it went down, we got a positive component there, or 0.5. And our long on A adds up to 0.75 so our total is 1.25.


![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/02-04%20The%20Capital%20Assets%20Pricing%20Model%20(CAPM)/images/3.png)


## The market portfolio

A concept that's important to the capital assets pricing model is this thing called The Market Portfolio. When someone refers to the Market, they're usually referring to an index that broadly covers a large set of stocks. In the US, the best example of that is the S&P500. The S&P 500 represents the 500 largest companies that are traded on exchanges, and that index changes each day according to the prices of all of its components. There are similar indexes in the United Kingdom, Japan, and any country or large market has indexes that represent this.

#### Composition of the Market Portfolio

These indexes are composed of many, many individual stocks, and the market portfolio is a combination of those stocks in a certain weighting. Most of the important indexes are what we call Cap Weighted. And what that means is the individual weight of each stock in the portfolio is set according to that stock's market cap. So, market cap, if you recall, stands for Market Capitalization, and it's simply the number of shares available for the stock times its price. So to calculate the weight for any particular stock, you take its market cap and divide it by the sum of the market caps of all the stocks.

#### Market Sectors

Now within each of these oceans if you like, there are a number of sectors. For instance, in the US we typically break the market into ten different sectors, I list four of them here: Energy, technology, manufacturing, finance and so on. And these are essentially the islands. So, if some malaise occurs to, say, energy stocks, you can think of that as something bad happening to the energy island. These things might be Saudi Arabia is pumping more oil, so the cost of oil is going to go down. That usually would have a negative impact on energy, so the energy island would be negatively impacted. Same thing with these other sectors. The main point here being that positive and negative news can affect each of these sectors individually without necessarily affecting the others.

#### Recap

Now just recapping before we depart, when we talk about the market portfolio in this class, we are almost always talking about the S&P 500. And that market portfolio consists of 500 stocks, the largest stocks in the U.S. that are traded publicly, with a weighting set like this. One thing to keep in mind is some stocks have surprisingly large weightings. For instance, Apple and Exxon each are about 5% of the S&P 500. So those two stocks have a strong effect on what happens to this index. There are smaller stocks that comprise say only a tenth of a percent of the overall effect on this market.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/02-04%20The%20Capital%20Assets%20Pricing%20Model%20(CAPM)/images/4.png)

## The CAPM equation

#### The Core of the Capital Assets Pricing Model

We're finally able now to get to the core of the capital assets pricing model, and that's expressed in this single equation that's really important. You need to memorize it and understand it. And here's what that equation is:

The capital assets pricing model says that the return for an individual stock on a particular day $$t$$ equals $$\beta$$ times the return on the market. So, when we say the market in the United States, we're usually referring to the S&P 500. And this particular stock, $$i$$, is one of the stocks in the S&P 500. So its return on a particular day, again, is $$\beta$$ times the return on the market of that day plus $$\alpha$$ of that particular stock on that day.

#### The Significance of the Market

What the capital assets pricing model is asserting, and this is important, is that a significant portion of the return for a particular stock is due to the market. In other words, the market moving up or down strongly affects the change in price on every individual stock. And the extent to which the market affects a particular stock is encapsulated in this $$\beta$$ which we'll talk about in just a second.

#### Beta and Alpha

Every stock has its individual $$\beta$$ that specifies how much it's affected. Many stocks have a $$\beta$$ near one which means when the market goes up or down 1%, that stock goes up or down 1%. But if you had say a larger $$\beta$$, say two, that means if the market goes up 1% we would expect, all else being equal, that the stock goes up 2%.

This other component, $$\alpha$$, is called the residual. So of course, if you look at all the stocks over one day and look at how much the market goes up or down, and you calculate how much the stock should have gone up or down according to $$\beta$$. Well there'll be something left over. It won't exactly match what $$\beta$$ predicted. And that's what this $$\alpha$$ or residual component is. An important part of the capital assets pricing model is that the expectation for $$\alpha$$ is 0. Essentially this is a random variable with an expected value of 0. It's important to remember that.

#### Beta and Alpha in the Capital Assets Pricing Model

Beta ($$\beta$$) and Alpha ($$\alpha$$) are derived from daily returns and essentially how the daily returns for a particular stock relate to the daily returns of the market. 

Consider the S&P 500 in comparison to another stock, say XYZ. If the S&P 500 goes up a little, XYZ stock goes up more. We can look at what happens with the returns on each day and plot them in a scatter plot. Each point in the scatter plot represents one day. If we fit a line to it, beta is simply the slope of this line, and alpha is simply the y-intercept of that line.

Now, this is an after-the-fact calculation. In other words, just because historically a particular stock, looking back at time, gave you a particular alpha, you shouldn't necessarily expect that in the future. The Capital Assets Pricing Model (CAPM) asserts that you should expect alpha to be 0. In reality, though, it's not always 0.

So, that's the key to the capital assets pricing model and where beta and alpha come from.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/02-04%20The%20Capital%20Assets%20Pricing%20Model%20(CAPM)/images/5.png)


## Compare alpha and beta 
#### Question
Consider these two scatter plots. This one is for stock XYZ versus S&P 500. This one is for stock ABC versus S&P 500. And each one of these dots represents the return for S&P 500 versus ABC or XYZ for that particular day. Okay. So look at these two plots and tell me, which one has higher alpha and which one has higher beta?

#### Answer
So recall that beta is the slope of the line and alpha is where it hits the y-intercept there. So, higher alpha. Well ABC is intersecting the y-axis there much further up than XYZ so ABC's got higher alpha. In terms of beta, look, the slope of ABC is much higher than XYZ so ABC also wins on the higher beta question.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/02-04%20The%20Capital%20Assets%20Pricing%20Model%20(CAPM)/images/6.png)

## CAPM vs active management


### Passive vs Active Investing

Now you may have heard about the debate of passive investing versus active investing. This question about passive versus active didn't really exist before the capital assets pricing model came out. And I'll explain why in just a moment.

#### Explanation of Passive and Active Investing

But let me just briefly tell you about passive versus active. So passive essentially says that you should just buy an index portfolio. Like buy something that represents the S&P 500, and hold. Just sit on it and let it grow.

Active portfolio managers don't just buy the index portfolio, they pick individual stocks. Another way you can think of this is if you compare the active managers portfolio to the index. You'll find that he or she has higher weights for some stocks and lowers weights for other stocks. Of course those weights could be zero, or even negative.

But the general idea here is that the active portfolio manager's portfolio differs from the market portfolio by selecting different weights on different stocks.

#### Capital Asset Pricing Model

Let's return now to the capital asset pricing model here, and consider passive versus active in that context.

#### Agreement Between Active and Passive Managers

Both active managers and passive managers agree with this part of the equation. In other words, however the stock moves each day is most significantly influenced by the market, and that the amount that it moves is strongly related to beta.

#### Differing Views on Alpha

Where they differ is with regard to their treatment of alpha. The CAPM says two important things about alpha. First, it's random. You can't predict it, and the expected value is zero. Some days it'll be positive, some days it'll be negative. It may be large, it may be small, but it's random. And on average, its value is going to be zero.

#### Active Managers and Alpha

Active managers, on the other hand, believe they can predict alpha. In other words, they can compare two stocks and they say I think this one is going to go up relative to the market. Remember, this alpha is market-relative. Or, I think this other stock is going to go down relative to the market. Now, they might not be exactly right on every single pick. But they believe on average they're better than just flipping a coin.

#### Using Information and Machine Learning

So if you believe what active managers say, you can use information and perhaps machine learning to find stocks that have either positive or negative alpha. And you can use that information to select your stock picks. And we'll show some examples of that later on.

#### Belief in the Capital Assets Pricing Model

Anyways, if you believe the capital assets pricing model, in other words, this alpha is fully random, then you should be a passive investor. Just buy an index and hold it.

#### Belief in Active Managers

If you believe active managers, that they can find alpha, then you should consider being an active investor.


![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/02-04%20The%20Capital%20Assets%20Pricing%20Model%20(CAPM)/images/7.png)

## CAPM for portfolios

#### Considering a Portfolio

Suppose now that instead of just looking at one stock, you want to think about a portfolio. And remember that a portfolio is defined by the various weights that indicate how much of your funds you've allocated to each stock.

#### Return for an Individual Stock

So recall that for an individual stock, i, its return on any particular day is Bi times return on the market for that day plus alpha for that particular day.

#### Computing the Return for the Entire Portfolio

So, to compute the return for the entire portfolio, we compute this return for each individual stock, multiply it by the weight for that stock and then we take the sum across all the stocks. And that's what we get for the entire portfolio.

#### Calculating Beta for the Entire Portfolio

Now if you note we can calculate beta for the entire portfolio simply by doing this. Beta for the overall portfolio is simply a weighted sum of the individual betas for each of the stocks.

#### Simplifying the Expected Overall Return for a Portfolio

So the capital assets pricing model tells us that we can simplify the expected overall return for a portfolio by computing a beta for that portfolio, multiplying it by the return on the market and then there's some alpha.

#### Alpha Composed of Multiple Examples

So that alpha is composed of multiple examples. So this alpha, remember capital assets pricing models says that all of these are on average going to be zero, so we don't need to bother necessarily adding them up, we can just approximate it by an overall portfolio alpha.

#### What the CAPM Tells Us

So again, this is what the CAPM tells us we can expect on any particular day, and again, CAPM asserts that this alpha is random with mean 0.

#### Active Portfolio Manager's View

The active portfolio manager will say, okay, yes, I agree that the beta component is the same as CAPM at pricing model says. But I think I can find value in this alpha and it needs to be broken out individually.

#### Active Portfolio Manager's Formulation

So the active portfolio manager is going to have this formulation of what they could expect in return each day compared to the CAPM, which is a little bit simpler.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/02-04%20The%20Capital%20Assets%20Pricing%20Model%20(CAPM)/images/8.png)

## Implications of CAPM quiz
#### Question
So for upward markets, we want larger beta because that means we'll go up even more than the market if beta is greater than 1. If we have a smaller beta, that means we're not getting the full advantage of the market going up. In downward markets, we want smaller beta. So for instance, if the market goes down 1% and our beta is much less than one, that means our portfolio will go down less than 1%. So on a downward market, the smaller the beta the better.

#### Answer
So for upward markets, we want larger beta because that means we'll go up even more than the market if beta is greater than 1. If we have a smaller beta, that means we're not getting the full advantage of the market going up. In downward markets, we want smaller beta. So for instance, if the market goes down 1% and our beta is much less than one, that means our portfolio will go down less than 1%. So on a downward market, the smaller the beta the better.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/02-04%20The%20Capital%20Assets%20Pricing%20Model%20(CAPM)/images/9.png)

## Implications of CAPM

#### Implications of CAPM

Let's summarize now the implications of CAPM. Let's start first with the equation. So the CAPM tells us that the expected return on our portfolio is the beta of the portfolio times the return on the market plus alpha of the portfolio.

#### Alpha and Its Implications

The first point, an important point, is that alpha is random, and the expected value of alpha is zero. So that excludes alpha from our toolbox of ways to make money.

#### Beta and Its Role

What's left? So the only way we can beat the market now is by cleverly choosing beta, so that when the market is going up, we choose a positive beta, and when a markets going down we choose a lower or even negative beta. So CAPM says the only way we can beat the market is with high beta in up markets and low beta in down markets.

#### Efficient Markets Hypothesis

The only problem with that is the efficient markets hypothesis. We haven't covered that yet, but it's coming soon. But anyways, the efficient markets hypothesis says you can't predict the market. So, these avenues are not available to you, either.

#### Can We Beat the Market?

So, all these things taken together say that you can't beat the market. If the capital assets pricing model is true, we can't beat the market. Now, I don't believe that, and this whole course is about ways that you can potentially beat the market. So, we're going to get to those eventually, but we had to present the capital assets pricing model as a framework in which to consider all these other things.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/02-04%20The%20Capital%20Assets%20Pricing%20Model%20(CAPM)/images/10.png)

## Arbitrage Pricing Theory

#### Arbitrage Pricing Theory

Now before we close, there's one other thing I want to touch on. It's called Arbitrage Pricing Theory. Arbitrage Pricing Theory was developed by Stephen Ross and first published in 1976.

#### Observations on CAPM

So Dr. Ross observed the CAPM as it was. But he said look, we have this single beta that represents a particular stock's relationship to the market. Maybe really we ought to have multiple betas. The CAPM is really only allowing us to consider a stock in the entire ocean.

#### Analogy of Islands

And his idea, if you continue the sort of analogy we've been doing in this class, is that we ought to consider the different islands. In other words, a particular stock might have exposure to different aspects of the market.

#### Exposure to Different Aspects of the Market

So, the stock might have some exposure to finance, so we could compute the component of return due to finance via the beta with regard to finance and the return for finance of that day. So we could compute for each stock, for each sector, an individual beta.

#### Breaking Out the Betas

And so his assertion was that by breaking out the betas into these different factors, we could get a more accurate forecast of what the return's going to look like. And of course we still have our alpha over here.

#### Not Using APT in This Class

We're not going to use APT in this class, but since we've been going forward with this analogy of oceans and islands and so on, I wanted to bring it to your attention because I thought you might find it interesting.

Okay, that's it for the capital assets pricing model. I'll see you again soon.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/02-04%20The%20Capital%20Assets%20Pricing%20Model%20(CAPM)/images/11.png)