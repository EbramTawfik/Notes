# Options

Sure, here's the organized transcript with headers and divided into paragraphs. I've removed the timestamps as per your instructions:

#### Introduction

Hi, I'm Dave Bird, a research scientist here at Georgia Tech who primarily studies tiny series machine learning. I'm also the head TA for the class you're taking right now, CS 7646 machine learning for trading. I also teach the class sometimes on campus when Dr. Mulch is not available.

#### Previous Experience

Last summer when I taught the class, I gave a sort of impromptu basic options lecture in response to questions from students. It was very well received and so Dr. Belch asked if I would please record a version of that lecture to permanently include in the online version of the class. That's what you're going to get here today.

#### Lecture Content

Do you expect me to cover a bare-bones introduction assuming you don't know anything about exchange-traded options? So, I'll cover what they are, what it means, how to read an options chain, what are call and put options, what are some basic strategies that you can employ with options, what's the purpose, how do you price options, and how can you combine different options contracts in order to get more advanced strategies.

#### Advanced Strategies

These strategies let you take a specific position in the market based on a very specific opinion that you have about what's going to happen. That can go well beyond just long or short. Please don't expect us to get into any kind of advanced topics like the details of the Black Scholes model or how to trade a volatility smile or how to manage your positions over time, rolling out and down if your position goes against you.


We won't get into any topics like that, but hopefully, this will give you a good quick broad cover of the basics and you'll walk away from it at least knowing what exchange-traded options are and how you might want to consider approaching it from a machine learning perspective to see if you could include it into your bag of tricks. Alright, I'll get started and I hope you find this useful.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/1.png)

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/2.png)



#### Meaning of "Option"

The word "option" is used to mean several different things and I want to start by distinguishing that anytime I say the word "option" during this talk, I'm referring to exchange-traded options. At no point will we be talking about employee stock options such as you might get when you go off to your fancy tech company. That's a completely different beast, it's not something we can publicly trade in on the market and therefore not what we're after in this class. So here, "option" will mean an exchange-traded stock option such as on the CBOE or Chicago Board of Exchange.

#### Definition of an Option

An option is a legal contract which gives you, as the buyer, the right but not the obligation to buy the underlying stock at a specific price on or before a specific expiration date. For this first part of the talk, I'm going to assume we're talking about buying call options only, which means buying the right to buy the stock. We'll get into some of the other details later but just to be unambiguous right now, we're buying call options which is buying the right to buy the stock.

#### Caveats in the Definition

I have a few caveats in the definition here. There are options on many other underlying assets besides stocks. There are options on future contracts and commodities, options on currencies, all kinds of other things. When we say we're going to be able to buy the stock at a specific price, we call that the strike price. And when we say "on or before the expiration date", we're talking specifically about U.S. style stock options. In European-style options, we can execute the option on the expiration date only. Under Euro style, you cannot choose to exercise your option prior to the expiration date, but in U.S. style, you can.

#### Looking at an Option Chain

So with those caveats, let's actually look at an option chain to try to make all of this real so that we have kind of a common position to go forward with.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/3.png)


#### Option Chain for Call Options

So, this is the option chain for call options on Apple stock. I took this picture the day before I originally gave a lecture in the classroom in November, and it was for the December expiration date.

#### Interpreting the Options Chain

We can look through the options chain example that I have here and see what some of the different data points mean and how we can interpret it. The first column here is the expiration date, so all of these options expire December 16, 2016. If you were to buy one of these options, that would be the date by which you would have to use or exercise the option or else it just simply goes away.

The second column is the route column. Route here is just jargon that means the underlying security, in our case a stock, that this option is tied to. Strike is that strike price we mentioned. This is the price that you will be guaranteed to be able to buy the stock at if you choose to exercise the option.

The key to these options is you can choose to buy at this strike price no matter what the real price of the route security is on the day you exercise the option. That's kind of where the power and flexibility comes from.

The last column is because I took this after market closed on that day, so it's showing the last price that each of these options traded at on that day as the market closed. Net is simply showing the change from the previous time period.

#### Market Closed

Bid, ask, and bid size and ask size are all zero because the market was closed, so of course there were no open orders at that moment. If you look at this during the day, you would see some order book information here about what the current best bid and best ask price were for each one of these.

#### Open Interest

Then the open interest column is kind of interesting. This shows how many total positions of this option are open and in the market right now. So, one thing you'll notice about this that's kind of interesting is humans like nice round numbers. The interest is much higher for no really special reason necessarily in all of the prices that end in a multiple of five. Just a little bit of humans being humans there.

Sure, here's the organized transcript with headers and divided into paragraphs. I've removed the timestamps as per your instructions:

#### Option Contracts

So, what are we doing with these Option contracts? an option contract controls a hundred shares of the underlying stock. It's always 100, never more, never less. But when I look at these prices, options contracts are always priced per share. I don't know if that's just a historical artifact or if it's salesmanship to make options look cheaper, but this is how it's always been done.

#### Strike Price

So if I look at this $110 strike price for Apple and I see that it costs two dollars and 73 cents, what that means is if I buy a single 110 call option on Apple, that option will control 100 shares of Apple stock and my actual price that I pay for the option will be 2 dollars and 73 cents times the 100 shares. So this option will actually cost me two hundred and seventy-three dollars if I wish to buy it.

#### Buying the Option

So I can buy one contract of the Apple December 16, 2016 call option at 115 dollars strike price for 273 dollars which is 2.73 cents a share then anytime the market and here then I mean typically the Chicago Board of exchange is open before December 16th I can choose to exercise this option.

#### Exercising the Option

If I exercise the option, whoever sold me the option is obligated to sell me a hundred shares of Apple stock at exactly a hundred and ten dollars a share no matter what the price of Apple stock is on that day. So by itself, buying this call option amounts to a bet on my part that Apple stock will rise to at least a hundred and ten dollars by the expiration date.

#### Calculating the Break-even Price

Almost, I actually paid money for the option and when I'm calculating my breakeven price I really should factor in the money that I paid to buy this option because that is a lost expense I don't get that money back. So what I really need is I need for Apple to rise to a hundred and twelve dollars and 73 cents per share so that I earn back the hundred and ten dollars that I would spend buying the stock if I exercised the option and the two dollars and 73 cents a share that I spent to get the option in the first place.

#### Making Profit

And then if the price of Apple on that day is 112-73 I break even and if it's anything above that I make money by exercising option.

#### Ignoring Trading Fees

I am ignoring trading fees here, which I'll do throughout the lecture because that complicates things in unnecessary ways.

#### The Point of Buying the Option

So, what's the point of buying the option? Why wouldn't I just buy the stock? It's a perfectly reasonable question to ask. Why would I buy an option when I could just buy the underlying stock directly?


#### Advantages and Disadvantages

There are some disadvantages that we'll talk about in a sec. So, what's the advantage? Why would I do this?



![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/4.png)
#### Specific Scenario

It will help to look at a specific scenario. So, I'll look at Apple stock again and I'll use that same one ten strike price with a $2 and 73 cent value. On the day that I first prepared this presentation, Apple stock was trading at 111 57.

#### Considering Options

So, Apple on some day is 111 57 and we're considering what to do. We think that Apple stock will go up in the near future. We could buy a hundred shares of Apple stock today. It's a nice round lot, your broker will like you. That's how you minimize your commissions and that will cost us eleven thousand one hundred and fifty-seven dollars. That money disappears from our account, it's gone, and we get a hundred shares of Apple stock in exchange.

#### Potential Profit

Let's say that the price of Apple does go up like we hope and it rises to one hundred and twenty dollars a share sometime on or before the theoretical expiration date of the options that we're talking about. By this time, we just bought the stock. Then we could sell our stock for twelve thousand dollars. Even if we don't sell it, that's still the paper amount that we're worth and we can still calculate a paper gain. Then we have a profit on this particular trade of eight hundred and forty-three dollars minus trading expenses, which again I'm going to ignore. That's pretty good for holding the stock for something like two-three weeks.


#### Option Contract

Instead, we could have bought an option contract. The option contract we looked at was the one ten call and that would cost us two hundred and seventy-three dollars to buy. Now, in the same situation, if the Apple stock rises to one hundred and twenty dollars a share by the expiration date, then we could choose to exercise our stock option which allows us to buy a hundred shares of Apple stock at the 110 strike price that we agreed on when we bought the contract.

#### Immediate Sale

So, buying that stock on that day cost us eleven thousand dollars and then we can immediately sell the stock the same day at the open market price for twelve thousand dollars. So doing that, our profit is only seven hundred and twenty-seven dollars. It's a little bit less, but we got to participate in most of the upside move in the stock.

#### Benefits of Options

You can already see one of the benefits that we obtained by using the option instead of buying the stock, and that is we only tied up two hundred and seventy-three dollars in our account and the rest of the cash was still there in the account available to use. Compared with if we had bought the stock, we would actually have to tie up the full eleven thousand one hundred and fifty-seven dollars and it would not be available to do anything else with during that time.

#### Leverage Aspect of Options

So this is the leverage aspect of options and one reason that we like them because you can control more money using less money.


![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/5.png)


#### Considering the Downside

The other case to consider is what if the stock doesn't go the way we expect. So, let's run through that same exercise again. Apple stock today is one hundred and eleven fifty seven. We could buy a hundred shares for the same cost as we talked about before. Now, we're saying, what if Apple stock falls to some amount, let's say a hundred dollars a share by December sixteenth. Whether we sell it or not, we still have the same paper loss.

#### Potential Loss

So, we can treat it as a sale. Now, our stock is only worth ten thousand dollars. That means we've got a current loss of eleven hundred and fifty-seven dollars. That's a pretty big loss for just a few weeks. Apple stock price may not actually move this much, but it's an interesting and illustrative example.

#### Option in Case of Loss

Now, what would happen if we bought the option? If we buy that 110 call for two hundred and seventy-three dollars and then we assume again that Apple falls to a hundred dollars a share and it stayed there until the option expires, we simply don't exercise the stock option. Remember, this is an option. That's the entire point. We're buying the right but not the obligation to buy the stock.

#### Minimizing Damage

So, we don't have to use it if we don't want to. And if we're below our breakeven price, we won't. We'll just let the option expire and at least it won't do any further damage to us. So, in that case, our loss is just the two hundred and seventy-three dollars that we spent buying the call option. No matter how low Apple stock price falls.

#### Extreme Scenario

If you want to make the numbers even more extreme, imagine that something terrible happens and Apple goes out of business. Then, if you bought the stock, you lose every single dollar that you had in it. If you bought an option, you lose exactly the premium that you paid for the option. And it doesn't matter what happens to the stock after that.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/6.png)

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/7.png)



#### Reasons to Like Options

So, these are some of the reasons that we like options. First, you cannot lose more than the premium that you paid for that option upfront. No matter how far it moves against you, you can't possibly come out worse than losing the premium you pay for it.

#### Leverage and Potential

Second, we like it because of leverage. We still get most of the upside potential if the stock goes the right way, not quite all, but most. And in exchange, we've capped our downside to the premium and we've tied up a lot less money in our account.

#### Diversification

So, we could go out and take more bets and diversify our opinion about the market in more directions.

#### Not All Good

Now, it's obviously not all good. If it were just this, then you would say, "Well, so why should I ever buy a stock instead of just always trading in options?" And there are some people who do that.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/8.png)


![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/9.png)


![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/10.png)


#### Downsides to Options

There are downsides to options. A couple of them are:

**Lost Premium**

First, the premium is lost money. It's gone. You pay it immediately to another person when you acquire the option contract, and you don't get it back no matter what happens to the stock.

**Expiration Dates**

Second, options have expiration dates. This is big. You're adding a layer to the bet that you're making in the stock market. If I just go buy some stock, I'm betting that that stock will go up eventually. I'd like it to go up sooner rather than later, but it's okay if it doesn't. I can just hang on to the stock and forget about it, and someday in the future when the market goes back up, I can sell the stock at a profit. Yes, I've tied up money for longer, yes, I couldn't close out the position maybe when I wanted to because it was in the red, but I never have to sell it. I can just hold on and hope for the best. With an option, you can't do that. Options have a built-in time bomb. You're now taking a bet that the stock will move in a specific direction by a specific amount or more and in a specific, usually pretty short, time period. So there's a lot of benefits, but you're also now making a much more specific bet that's more likely to be wrong because you've got timing and all these other elements that you don't have if you just buy the stock.

**Ownership**

And then the third thing, of course, is you don't own the stock. Now that sounds kind of trivial, but there are implications to the fact that when you buy an option to buy the stock, you've not yet bought the stock. So the person who sold you that stock option still owns the stock until you choose to exercise it. And that means while the stock price is going up before you exercise the option, they have the voting rights that might come from that stock, not you. And they are collecting the dividends and any other benefits of ownership of the stock, not you.



![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/11.png)


#### Moneyness of Options

Let's talk for a second about the "moneyness". This is one of those words that you don't tend to hear in casual conversation and I'm not totally sure it's proper English, but it is a common financial term.

#### Option Pricing

Why are some options so much more expensive than others? If you look back here at the option chain that we're studying, for example, down at the bottom of the page, we've got the 117-118 options that are only 20 cents, 23 cents per share. But then up at the top, the 102 strike price option is currently trading at nine dollars and five cents. So, if you were to buy that for your hundred shares you're controlling, that would cost you nine hundred and five dollars for one contract, whereas the 117 would only cost you twenty-three dollars for a contract on a hundred shares.


#### Intrinsic Value

Why is that? The answer is right now, as of the day that I did this, Apple is trading at 111.57. So, Apple is trading right there in the middle of the table between those 111 and 112 strike prices. If I were to buy that 110 call option that we keep looking at for two dollars and 73 cents a share, I could exercise that option right now, one moment after I buy it, for a profit of $1 and 57 cents a share. Because Apple today, right now, already is trading a dollar and 57 cents above that 110 strike price. So, the option is obviously not going to be priced less than that dollar and 57 cents a share that I could get if I bought the option, exercised it, and sold the stock immediately all in one go. That is what we call the intrinsic value.


![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/12.png)

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/13.png)


#### Intrinsic Value and Time Value

The **intrinsic value** of the stock is the difference between an option's strike price and the current underlying spot price for an in-the-money option. All we mean by "in the money" is that it's an option that currently has a non-negative intrinsic value, so you could make money immediately by buying the option, exercising it, and then selling the stock.

Something that doesn't have intrinsic value is called an **out-of-the-money** option, meaning currently you could not exercise that option at a profit because of where the stock price is right now. And then if you're right on the border between those two, you can be **at the money** or **near the money**.

So, we said intrinsic value right now is a dollar fifty-seven cents a share for that 110 strike price because that's what we could get if we sold it right now immediately after buying it. But it's not priced at a dollar fifty-seven cents a share, it's 273. So, what is the rest of that price?

The 110 costs 273 and has an intrinsic value of dollar 57. The 115 has an intrinsic value of zero because Apple is trading less than that right now, so it's not currently worth anything in the sense of exercising the option, but it still costs 53 cents a share or 53 dollars for the contract. So, there must be some other component to this, and the other component is what we call the **time value** of the option.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/14.png)


#### Time Value of the Option

The other component is what we call the **time value** of the option. The more time there is between now and the option's expiration, the better the chance there is that the stock will reach the strike price before it expires, and so the higher the time value will be.

We can say the excess premium cost, that's beyond whatever the intrinsic value of the option is, is attributed to its time to expiration. You can think of that as the amount of time that the stock has got to move the right way before the option expires. Of course, the further you are from the expiration date, the bigger that time value will be. And then as you get closer to the expiration date, the time value shrinks and shrinks, especially rapidly in the last few days and really the last few hours before the expiration, as it becomes nearly impossible that the stock will reach each strike price.

#### Trading Options

Now, you're not stuck with options once you buy them. These are not something that you buy and then there's no market for it to sell. It's second hand. These can be bought and sold just like stocks. So, if you change your mind on the option after you bought it, you can sell it on to someone else via an exchange like the Chicago Board of Exchange. But you'll probably lose money if the stock hasn't gone your way fast enough because of **time decay**.


![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/15.png)

#### Time Decay and Theta

As you hold this option and the price is not moving or it's not moving in the correct direction, the time value of the option will be decreasing because there's less time before the expiration date for it to make that move that you need. An out-of-the-money option is also called **theta**. It's one of the Greeks that I said I wouldn't talk about much. There's a lot of Greek letters that are used to describe different secondary characteristics and derivatives and second derivatives of various factors of options related to stocks if you get really into trading.

Theta or time decay is the rate at which an option is losing its time value, which is to say it's the first derivative of that time value over time. The time value changes more rapidly as the expiration date arrives and the time decay goes up. And then when you get to the expiration date, of course, time value approaches zero and all of the option prices will approach their intrinsic value because you would have to buy it, exercise it, and sell it immediately at that point. It's just about to expire. The last two weeks are when time decay goes the fastest.

#### Trading Options and Time Decay

People who want to actively trade options, as opposed to hoping to exercise them and get the stock, usually try to close out their open option positions at least two weeks before the expiration date. So, the smart money is really not in there at the last second trying to do option trades that are about to expire. They're buying those options a month or two months out and then selling them as you get to four, three, two weeks away from expiration on to somebody else who actually wants to make that bet about whether the stock will end up in the right place and they'll get to exercise the option.

#### Black-Scholes Model

If all of this part about the Greeks and time decay is really interesting to you, you may want to go look at the **Black-Scholes model**. While it's not machine learning related, it is one of the very common financial models that's used to decide what should the price of an option be at any given moment and a lot of people use deviations from that model to try to do arbitrage on options where they moved away from the expected price and you might expect some reversion to the mean.



#### Assumptions and Relaxations

So far, the discussion has been based on the assumption that you are buying a **call option**. A call option is equivalent to a long position. It's going to profit if the underlying stock goes up. You have been buying it, which means you're buying the right to buy the stock.

#### Other Types of Options

But there are several other basic things you can do with options, even before we get to the complex strategies. As I introduce each one, I want to show you a common profit and loss curve that we look at in options.

#### Profit and Loss Curve

This curve makes it very easy, once you get accustomed to looking at it, to understand exactly what an option strategy is doing and particularly to understand exactly when it will make money and when it will lose money. It's a really helpful visualization tool in the world of options trading.

![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/16.png)



#### Profit and Loss Curve for Call Options

When you buy a call option, you're paying some premium upfront. This is money that you're in the hole immediately as soon as you buy the option. Then you need for the stock to rise to some amount above the strike price that represents that extra premium that you paid before you've actually broken even and recovered all of the money that you spent plus been able to sell the stock and get back to zero.

If we look at the Profit & Loss (P&L) curve for a standard buy call, we start over here at the left end with the spot price well below the strike price. So, in other words, the stock price going down doesn't matter how much it just went down quite a bit below the strike price and no matter how far down it goes, you've lost a dollar amount that exactly correlates to the premium that you paid. This is the risk you take when buying a call option. The maximum loss is the premium paid for the option, regardless of how much the stock price falls. 

On the other hand, the potential profit is theoretically unlimited, as the stock price could continue to rise. However, you need the stock price to rise above the strike price plus the premium paid to start making a profit. This is why the P&L curve for a long call option slopes upwards to the right (representing increasing stock prices) and is flat to the left (representing decreasing stock prices). The point where the curve shifts from flat to sloping upwards is the break-even point, which is at the strike price plus the premium paid.That’s going to be the case until I get to the strike price.


#### Reaching the Strike Price

As soon as I hit the strike price, I'm still losing money, but I'll start losing less because once I hit that strike price, I will exercise the option. I'll make at least a little bit of money exercising it, buying the stock at the cheaper price that I have, and then selling it at a market price. In fact, that'll leave one dollar for one dollar for every dollar that we go above the strike price.

#### Profit and Loss

I'll make a dollar per share of profit, not counting that premium. This is just a simple linear relationship, and then once I have exceeded the strike price by the premium, I finally reach my actual P&L break-even point where now I've been made whole on this entire trade. I've got back to zero, and I haven't lost any money, and as I continue to rise above that, I'm actually finally in a truly profitable position having bought this call option.

#### Exploring Other Options

But buying calls is far from the only thing you can do, and kind of the further away we get from it, the more interesting it will be. So, I want to talk about some of the other things that we can do with options. As I go through each one, I'll also note just as a point of interest what is the maximum profit and the maximum loss that we could experience for each strategy.

#### Final Thoughts

That's one useful thing to think about, and here on the bike, all it's very simple, but do notice the maximum loss I could possibly experience is my premium amount which we had said before. The maximum profit from buying a call is theoretically unlimited because there's no amount where the spot price of the underlying stock would have to stop going up. It could go up any amount, and I profit dollar-for-dollar along with it with this position once I exceed my break-even point.



![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/17.png)


#### The Basics of Put Options

The other basic type of exchange traded stock option that you need to know about is the put option. The put option is essentially the opposite of a call option. You'll buy it just the same and you'll pay a premium when you buy it just the same. But now, instead of buying the option to buy the stock, you're buying the option to sell the stock.

#### Exercising the Put Option

You don't have to own the stock to be able to do this because you're probably going to have a margin account if you are playing with options anyway. You can short the stock as part of your exercising of it and then immediately buy it back to close out the position.

#### Profit and Loss with Put Options

So, if we look at a buy put, we would expect the P&L curve to be opposite in some sense, and indeed it is. Because now, we're making a bet that the stock will go down and we'll be able to sell it or short sell it at the strike price and then immediately buy it back to close the option position and the stock position at whatever the price is on that day. So, we'll be able to sell it for more and then immediately buy it back for less and pocket the difference.

#### Understanding the Cost Curve

Our cost curve is going to be almost exactly the opposite. If the stock closes above the strike price, we will experience our maximum loss which will be the premium that we paid for this put option. If we get down to the strike price, then we'll start recovering some of our money again. One dollar for one dollar, every dollar that the underlying spot price goes below the strike price will earn back a dollar of our premium that we spent until we finally get up to a true breakeven point where we've recovered the full premium.

#### Earning Profits

Then for every dollar that the stock falls below that, we'll earn a dollar profit per share that's covered by our option contract. There's one important difference to note though, and that is with a put option, we actually have an axis over here to run into. So, our maximum loss is still limited to our premium but our maximum profit is no longer unlimited because the lowest that the stock could go is zero dollars a share. So there is going to be some limit which will essentially be the strike price minus the premium that will be our maximum profit because again we can't hope for the stock to do worse than go to zero, stop trading in the company go out of business and that will limit the maximum profit we could make.


![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/18.png)

#### The Basics of Writing Options

There are a couple of other things that you can do even with basic options. Everything so far has assumed that we're buying an option, but if we're buying options, someone must be selling options. There's no reason that we could not be the person selling the option instead of buying it. Typically in options, this is called writing the options contract.

#### Understanding the Cost Curves

Let's look at what happens to the cost curves if we write options instead of buying options. To explain writing a call for a moment, it is the exact opposite in the other way between a call and a put. When I write an option contract, I am selling someone the option. Then, until the expiration date, they can force me to buy or sell them the stock at the strike price whether or not I want to and no matter what the price of the underlying stock is on that day.

#### Writing a Call Option

For example, with a call, I am selling someone a call option. I collect that premium payment immediately and I get to keep it no matter what. But then, until the expiration date, they can buy my stock away from me at the strike price no matter what. Now, in the best case, they won't exercise that option. I got their premium, I keep it, and I keep my stock. But of course, the downside is I might be forced to make a very unprofitable trade at some point prior to the expiration date if things don't work out well.

#### Profit and Loss Curve

Here, you might expect that the profit and loss curve will end up upside down of where the buy call curve was, and you'd be pretty much exactly right. If we write a call, we flip that cost curve over. The first thing that happens is we now collect the premium for writing this call option, and that's cash in our pocket. So, as long as the stock expires below the strike price, meaning it would be unprofitable to exercise the option for the person who bought it from us, we have a profit equal to that premium we collected, and they will let the option expire. Once we get up to the strike price, then the person who bought the option is earning a dollar for dollar because now they will exercise the option since it's above the strike price and they're gaining a little bit back dollar for dollar and we're now losing dollar for dollar because they're going to exercise that call and take our stock away from us at a disadvantageous price. But we're still sort of okay until the stock price gets to the strike price plus the premium and then at that point we are actually overall losing money on having written this option because now the person at the other end is going to exercise it, take it away from us at a very disadvantageous price compared to the current price of the stock and our premium we collected was not enough to make up the difference. Writing calls which by the way are called naked calls if this is your sole position and you're just doing it without any other strategy attached to it and that's meant to suggest that it's probably a bad idea. And here's why our maximum profit is now limited to the premium there's no way we can make more money than the premium now that could be okay if the odds of that happening are very very high but here's the slightly scary part of it our maximum loss is now unlimited this axis down here doesn't really count for putting a floor because it is just the profit and loss axis we're not saying the stock price goes to zero this is our loss so now the stock price could theoretically go up without any limit and the more it goes up the more money we lose so we have to manage a strategy like this very carefully to ensure that we don't lose essentially some arbitrary unlimited amount of money.




![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/19.png)


#### The Potential of Writing Put Options

Writing a put actually does not have that same unlimited loss potential because we'll flip the cost curve back the other way. So, it'll be left to right opposite of writing a call and it will be top to bottom opposite of buying a put. If we write a put, we've now got a floor under the stock which can't go down any lower than zero. So when we write a put, we give someone else the option to sell us the stock at the strike price should they choose to do so.

#### The Goal of Writing Put Options

So now we want the price of the stock to go down because we don't want the person to choose to sell us the stock because if they do that, it will mean they're winning and we're losing. So as long as it stays above the strike price, then we've got the premium that we charged in our pocket as profit and that is our maximum profit.

#### Understanding Profit and Loss with Put Options

Once the stock falls below the strike price, we start losing money dollar for dollar. We break even when it's the strike price minus the premium and then we start actually losing money. The trade at least has a floor at some point if the stock hits zero and we can no longer lose any money beyond that point. So our maximum loss here will be the strike minus the premium if the stock goes all the way to zero.

#### The Good News About Writing Options

The good news about writing options is 90 percent of stock options that are bought are not exercised. So while it may seem strange to take these trades where you've got potentially large losses and small fixed profits that are your premiums, you have to realize that the odds of these situations happening are not equal. Most options expire unexercised which means most of the time with writing an option, you'll put that premium in your pocket and that's the end of the deal.

#### The Risk of Writing Options

The option will never be exercised but you really got to watch out for that small percentage of the time when it is exercised because you could lose your shirt. Now this is just the four basic things you can do with a single options contract. You can buy a call, you can write a call, you can buy a put, you can write a put.




But the real power of options is not in doing these naked calls or naked puts or even just buying or selling puts. It’s putting these things together with some other strategy to let you take a more complex position or to hedge your bets or to make a very precise bet on what you think is going to happen in the market. Now I want to talk about just a couple of those before I wrap up.



![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/20.png)


#### Covered Call Strategy 

One of the most basic strategies that's considered one of the most safe things you can do with options and in fact many brokers will allow you to do it even in a cash account when you haven't been approved for margin is the covered call. The covered call is a very simple strategy that combines one option position with a position in the underlying stock. So to enter a covered composition what you would do is buy a stock and then write a call on that same stock. So you're giving someone else the privilege to be able to buy away from you a stock that you do actually own. We should look at the possible outcomes of this to understand the purpose of the strategy.


#### The Outcomes of a Covered Call Strategy

There are three basic possibilities. 

#### Stock Ends Up Above the Strike Price

The first is that the stock ends up above the strike price before the expiration date. This is not really ideal but it's not so bad. If that happens, then our stock will be called away, meaning that the person on the other end of that call option will exercise it and buy our stock from us below the current market price. 

##### Selling the Stock

So we'll be obligated to sell our stock at the strike price, which means we miss out on any of the profit above that strike price if the stock continues to move because now we don't own it, the other person owns it. 

##### Profit and Loss

So our total profit in that case is the strike price minus the original purchase price of the stock plus the premium that we collected when we wrote that call. This is not the end of the world. We still made money, but we didn't make as much money as we would have if we had just bought the stock and not written the call because then we would have gotten to fully participate in that profit if the stock moved up. 

##### The Problem with Covered Call Strategy

The other problem is, of course, we don't have the stock anymore, and so if we really wanted to be in that stock, we think it's going to continue up, now we have to go buy it again.



![](https://raw.githubusercontent.com/EbramTawfik/Notes/main/ML4T/Options/images/21.png)


#### The Second Outcome: Stock Goes Up But Not Enough

The second outcome is that the stock could go up, but not up enough to hit the strike price of the option that we wrote. This is actually the perfect thing that we want to happen. Because now, the option will not be exercised because we're below the strike price and the person on the other end would lose money by exercising the option. 

##### The Perfect Position

We're in the perfect position now because the stock went up so we've gained money on our position in the stock and we still have the stock and can write another call or anything else that we want. We collected a premium that has accelerated our return on the stock that ended up not costing us anything. 

##### Calculating Profits

So our profits so far on this stock that we still own is the current price of the stock minus the purchase price that we paid for the stock plus the premium that we collected for selling the option that was never used. 

##### The Ideal Situation

This is where you would love to be with a covered call. You'd like to be in this middle range where you never actually have to sell the stock. So you end up making the full same amount of money as if you had just bought the stock and done nothing with options, holding the stock the whole time that goes up. 

##### Juicing the Returns

Except periodically, you're juicing those returns and getting more money than you would otherwise because you're writing calls and collecting premium that's just extra money to you. And then hopefully, it's not exercised and the stock keeps going up slowly, never hitting those strike prices, and the premiums are just extra money that you put in your pocket the whole time.