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


### Downsides to Options

There are downsides to options. A couple of them are:

**Lost Premium**

First, the premium is lost money. It's gone. You pay it immediately to another person when you acquire the option contract, and you don't get it back no matter what happens to the stock.

**Expiration Dates**

Second, options have expiration dates. This is big. You're adding a layer to the bet that you're making in the stock market. If I just go buy some stock, I'm betting that that stock will go up eventually. I'd like it to go up sooner rather than later, but it's okay if it doesn't. I can just hang on to the stock and forget about it, and someday in the future when the market goes back up, I can sell the stock at a profit. Yes, I've tied up money for longer, yes, I couldn't close out the position maybe when I wanted to because it was in the red, but I never have to sell it. I can just hold on and hope for the best. With an option, you can't do that. Options have a built-in time bomb. You're now taking a bet that the stock will move in a specific direction by a specific amount or more and in a specific, usually pretty short, time period. So there's a lot of benefits, but you're also now making a much more specific bet that's more likely to be wrong because you've got timing and all these other elements that you don't have if you just buy the stock.

**Ownership**

And then the third thing, of course, is you don't own the stock. Now that sounds kind of trivial, but there are implications to the fact that when you buy an option to buy the stock, you've not yet bought the stock. So the person who sold you that stock option still owns the stock until you choose to exercise it. And that means while the stock price is going up before you exercise the option, they have the voting rights that might come from that stock, not you. And they are collecting the dividends and any other benefits of ownership of the stock, not you.