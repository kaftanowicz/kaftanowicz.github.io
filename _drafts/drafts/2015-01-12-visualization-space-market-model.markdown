---
author: admin
comments: true
date: 2015-01-12 20:37:49+00:00
excerpt: '[:en]A formal model of space market equilibrium dynamics and cyclicality,
  from "Commercial Real Estate Analysis and Investments" by Geltner and Miller, written
  in R as a Shiny app.[:]'
layout: post
link: http://kaftanowicz.com/visualization-space-market-model/
slug: visualization-space-market-model
title: (English) Visualization of space market model
wordpress_id: 174
---

[:en]I'm currently reading _Commercial Real Estate Analysis and Investments_ by Geltner and Miller. I'll write a full review later; right now I'll focus on section 6.2, titled _Formal model of space market equilibrium dynamics and cyclicality_.

A reader gets warned (by a footnote and an asterisk before section number) that this part is more advanced and difficult. This post is my attempt at making it easier by using more diagrams, more visualization and less scary looking Greek letters (I'll switch to suggestively named variables instead). I hope that my different approach will make this topic easier to understand for at least some people.

<!-- more -->We are trying to make a simple mathematical model of some space market, for example the market for office space in some city. In year 1 there is the stock of office space ready to be leased for a particular rent. There is also some need for office space, represented by the number of office workers. This need caused demand. Some space gets occupied, the rest stays vacant. Let's assume that no construction occurs in the first year.

What happens in following years?
(I) Developers take a look at rents that were a few years ago. (How many years exactly is dictated by so-called construction lag). If rents were higher than some trigger rent, developers build more office space. 
(II) This new construction is added to stock ready to be leased. 
(III) The amount of occupied space changes, satisfying the demand from previous year. 
(IV) Vacancy rate changes. 
(V) Rent changes, too - if vacancy rate is higher than some natural vacancy rate prevailing in this particular market, rents will fall, otherwise they will rise. 
(VI) Need increases as the city and the number of its office workers grows. 
(VII) Demand changes to reflect increased need and change in rent.
These steps are then repeated specified number of times.

If we can write it, maybe we can draw it, too?

[![Space Market Flowchart](http://kaftanowicz.com/wp-content/uploads/2015/01/Space-Market-Flowchart.png)](http://kaftanowicz.com/wp-content/uploads/2015/01/Space-Market-Flowchart.png)

Now it looks much more clearly. We see the main cycle, representing the demand side of the market: demand -> occupied space -> vacancy rate -> rent -> demand, with input from need influencing demand. We also see additional cycle of supply side: rent -> construction -> stock -> vacancy rate. They are joined by vacancy rate, influenced both by occupied space and stock, and rent, which influences both demand and construction activity.

We can write it out as equations, too:

`if (Rent[t-construction.lag] > trigger.rent){
  Construction[t] = supply.sensitivity*(Rent[t-construction.lag]-trigger.rent) 
}else{
  Construction[t] = 0} # (I)
Stock[t] = Stock[t-1] + Construction[t] # (II)
OccupiedSpace[t] = min(Demand[t-1], Stock[t]) # (III)
VacancyRate[t] = (Stock[t] - OccupiedSpace[t])/Stock[t] # (IV)
Rent[t] = Rent[t-1]*(1-rent.sensitivity*(VacancyRate[t] - NaturalVacancyRate)/NaturalVacancyRate) # (V)
Need[t] = Need[t-1]*(1+need.growth.rate) # (VI)
Demand[t] = demand.intercept -demand.sensitivity*Rent[t] +demand.per.need*Need[t] # (VII)
`

Something[t] means the value of something in year t. Numerals are there to help relate equations to sentences from a few paragraphs before.

Those equations tell us more than a diagram, but are harder to visualize. It would be great to see how market dynamics changes when we change some parameters, would't it?

[Here's an app](https://kaftanowicz.shinyapps.io/SpaceMarketModel/) doing exactly this that I've written in R, using the Shiny framework. We can play with parameters and observe their influence on model. [Here is the code](https://github.com/kaftanowicz/spacemarketmodel). 

This model is very simple and based on strong assumptions - and by "strong", I mean "questionable" - such as:
- neither developers nor space users nor landlords can predict changes in rent and only react to its current or past values,
- occupied space changes every year so that all demand from previous year gets satisfied,
- no office space available on the market ever gets removed from the market; the stock can only stay the same or increase thanks to construction works.
It is, hovewer, interesting model and as book's authors note, it is useful for getting the general idea of real estate market dynamics.

Initial values are those that the authors have chosen, with few improvements (supply and demand sensitivity should be 0.3*10^6, not 0.3 - otherwise we won't get that nice graphs with fluctuating construction activity, rent and vacancy rates; also, trigger rent was not specified in the book). However, by tweaking some of the parameters, we can model even more interesting market behaviour. Try it yourself![:]
