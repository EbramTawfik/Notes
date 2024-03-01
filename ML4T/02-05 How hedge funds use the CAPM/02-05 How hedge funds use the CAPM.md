# 02-05 How hedge funds use the CAPM

## Risks for hedge funds
#### Hedge Fund Strategies

The typical hedge fund develops methods to find stocks they think will perform well. 

#### Informational Edge

The informational edge that they're seeking is usually market relative, meaning they're looking for stocks that will go up more than the market. If the market goes up, your stocks will go down less than the market if the market goes down. 

#### Reliable Information and Positive Returns

If this information they have is reliable, they can take advantage of the cap m to virtually guarantee positive return. 

#### Conclusion

In this lesson, I'll show you how all of that works.

## Two stock scenario

#### Hedge Funds and CAPM

As an illustration of how hedge funds use CAPM, let's consider a two stock scenario. So our hedge fund has done some research maybe they've used machine learning, maybe they've used some other method or maybe they've just thought very hard and for whatever reason they predict that stock A is going to go up 1% over the market in the next ten days. And they've looked backwards in history and observed that the beta for stock A, with regard to the market, is 1.0. So plus 1% beta of 1.0.

They've looked at another stock, B, which they predict to go down 1% whichever way the market goes, it'll go 1% below it. And the beta for stock B is 2.0. So this introduces for the first time this idea of a long short portfolio. In other words, we think that stock A's going to go up, so we should long it. And we think stock B's going to go down, so we should short it. And there's some strong advantages to this long short approach that'll begin to emerge as we go through this lesson.

#### Scenarios and Predictions

So we're going to talk a look at a couple scenarios with these two stocks to see how we should best allocate between the two. So looking back, this is what the S&P 500 has been doing. Remember stock A has a beta of one, so it follows what the S&P 500 does pretty closely. Stock B, on the other hand, has this beta of greater than one, or two. And so it's reacting much more wildly than stock A. Here's our first scenario.

Let's assume the market stays flat, in other words it returns 0% over these following ten days, and that we enter our positions as of this day and our positions are going to be a $50 long position in stock A and a $50 short position in stock B. Now assume going forward also that our predictions are perfect. That A goes up 1% over the market and B goes down 1% below the market. What will happen?

Well, if our predictions were perfect, stock B should go down 1% below the market, and stock A should go up 1% above the market. What does that mean in terms of how much money we would see returned?

#### Returns and Investments

So if we look at stock A, and remember we're using the CAPM, we should expect to see the return for A as beta of A times return on the market plus alpha. So, the market didn't move at all so this gets nullified so alpha for A is one percent and we invested $50 in that so our return is $0.50.

Similarly for B, this element is removed because our return was zero and all we're left with is alpha. Now essentially our alpha here was negative and we made a negative bet, so our return is 0.5 or altogether $1.0 or 1% for our total investment.

## Two stock scenario quiz 
#### Question
I'd like you to consider another scenario now. Instead of the market staying flat, what if the market goes up 10%? I want you, for stock A and stock B, to compute the expected return percentage-wise and then also in terms of dollars. And then compute the total for both down here at the bottom or, in other words, what's the return on your portfolio.

#### Answer

Let's start by taking a look at stock A. So, market one up 10%, we predicted that A would go up one percent over the market and its beta is one. So, we should see a return of about 11%. So, we get 11% here and $5.50 here. B is a little bit more tricky. Remember, B has a beta of two. The market went up 10%, so B's going to go up 20% minus the one percent we thought it would do relative to the market. So for B, the stock price went up 19% but we had a negative bet there, so we get negative 19% here. So, we're going to lose $9.50 on that bet. Now, to compute the totals here, let's do the dollars first. So, we made $5.50 on stock A, but we lost $9.50 on stock B, so altogether, we lost $4. Now, when you calculate the total return here, you can't just add these two up and get negative eight, because remember, we only had .5 over allocation in each one of these. So, to get the total, you multiply this return by .5, that return by .5, and you get negative four. Yes, it's a little bit tricky. Let's run through one more example here just so we get it straight. Let's assume now that the market goes down 10%. How does this all work out? Stock A should only go down nine percent because we think it's going to perform one percent over the market and its beta is one. Stock B is going to go down 20% and minus that one percent that we think is going to go below the market. So let's talk B is going to go down 21%. So we're going to lose nine percent or $4.50 on stock A, but we're going to really kick butt on stock B. Stock B went down 21%, but remember we shorted it, so we're going to get all together $10.50. So all together we're going to win six dollars or six percent. What's the takeaway here? The takeaway is even if we have perfect alpha and perfect beta, if we're not careful about how we allocate our money, we can still lose. How can we fix this? The CAPM can help.

## Two stock CAPM math

#### CAPM and Portfolio Analysis

Let's pull out the CAPM and take a look at this portfolio. Remember for each individual stock, the expected return is beta times return on the market plus alpha times the weight for that particular stock and when we're short, the weight is negative. And we do this across the stocks in our portfolio. And then, that's our expected return for the portfolio.

#### Beta Component

So, I'm going to expand this sum. First, I'm going to start with the beta component. So we get, weight a times beta b, plus weight b times beta b, times return on the market. So recall the numbers from earlier. Our weights for A and B were each .5 and -.5. We got a beta of 1.0 for A and a beta of 2.0 for B. For our alphas we had plus 1% for stock A and -1% for stock B. We can plug all these into our equation and work it out.

#### Expected Return

For our beta component, we end up with a beta for the portfolio of -.5. Our alpha component for stock A ends up just being .5 and for stock B, -.5 times -1 or .5. Bringing it all together under these assumptions, using the CAPM, our expected return for this allocation is -.5 times a market return + 1%.

#### Market Scenarios

Let's double-check this by plugging in one of our earlier examples. Consider that example where the market went up 10%. So we've got -.5 times 10% + 1%. So in the case where the market goes up 10%, we expect a -4% return for our portfolio.

#### Information and Market Risk

So if you step back a little bit, remember that we arrived at this 1% using information. So we have some information about these stocks that lead us to believe one would go up 1% over the market, another would go down 1% over the market. On the other hand, we don't really have any knowledge about what's going to happen for the market over all. So we have no control over this component.

#### Removing Market Risk

Is there some way that we can remove this? Can we make this part equal to 0? If we can do that, then we essentially remove market risk from our portfolio. And we preserve this 1% over here. Well, the way to do that is to focus on this part. Remember, this is beta for the portfolio. Can we make beta for the portfolio = 0? Or in other words, can we find weights for A and B, such that their sum turns out to be 0? What are these two weights so that the overall portfolio beta is 0?


## Allocations remove market risk 

#### Question
Suppose we have two stocks, our stock A and our stock B. These are the same two stocks we've been working with. A has a beta of 1.0 and alpha, our prediction of +1%. B has a beta of 2.0 and a forecast alpha of negative 1%. So we want to go long on A and short on B. The question is what should the weights be so that we can minimize or eliminate market risk.


#### Answer
Okay, so we want to find two weights, A and B, such that when you multiply them by their betas, the sum turns out to be 0. Now keep in mind that we're going to short B, so this one needs to be negative. And we're going to long A, so this one needs to be positive. Just keep that in mind as we go forward. So, let's solve for A initially here. We know that the weight of A should be equal to -2 times the weight of B. We also know that the sum of A and B, well, the sum of the absolute values of A and B, should be equal to 1. If we plug this minus 2 weight of B and for weight of A, we get this, or long story short, the absolute value of the weight of B equals 1/3. So, I know the weight of B has to be negative, so we get -1/3 for the weight of B. And coming all the way back up here, we know that the weight of A is equal to negative two times the weight of B. So, we get this. So finally, the answers are: 2/3 for the weight of A, and -1/3 for the weight of B.

## How does it work


#### Calculated Weights and Their Application

Okay, we've calculated these weights. Let's see how they work on the examples we've been looking at. So again our weight for stock A is going to be .66 and for stock B is going to be negative .33. And we're going to look at this scenario where the market goes up 10%.

#### CAPM Expansion

We'll pull out our old trusty CAPM and expand it for these two stocks. So for stock A we have the weight of stock A, times its beta times the return on the market, plus the alpha component. So these are the two parts that relate to the return on the market, and we'll bring them together. So for stock A we have 0.66, and our beta is 1.0. And for stock B we've got -0.33 times 2 times the return on the market.

#### Expected Return

So because of all that work we did to figure out these values, we know already that this is going to become 0. We'll carry down our two alpha components, so for stock A, our alpha expectation is 1%, and our weighting is 0.66. For stock B, our weighting is negative one third, times -1, our expectation is just going to go down 1.0%. So combining these two, 0.66 plus 0.33 gives us a 1.0% expected return. Whichever way the market goes.

#### Market Risk Elimination

Remember, we eliminated the return on the market. So, whichever way the market goes, we can expect to get 1% return. Now, need to add a lot of caveats here. These betas aren't necessarily fully guaranteed to continue into the future, and these alphas aren't guaranteed, either. These are just estimates that we computed based on information we thought we had, so this is not a guaranteed thing by any means, but it is a way to use long/short investing to reduce exposure to the market overall and to focus on those alpha components where we do have information.

## CAPM for hedge funds summary
#### Using CAPM in Hedge Funds

Let's bring it all together now, how hedge funds can use CAPM effectively. Assuming we have some sort of actionable information that we can convert into a forecast alpha, in other words, a prediction for a particular stock i, about which way it's going to go. And also the beta of that stock with regard to the market.

#### Minimizing Market Risk

We can do the following. We can minimize market risk by finding a beta for our portfolio that's equal to zero. And we can do that by finding the appropriate weights on each individual stock.

#### Portfolio Construction with CAPM

So, CAPM can be a really valuable tool in terms of portfolio construction because it can enable you to build these portfolios that are less exposed to market risk. And this is where the whole idea of long short trading came about. You know, CAPM really enables you to refine that.

All right, that is it for now. We'll see you again soon. Thank you.