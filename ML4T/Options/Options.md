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