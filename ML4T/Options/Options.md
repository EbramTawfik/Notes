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