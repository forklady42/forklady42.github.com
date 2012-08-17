---
layout: post
title: 9.63 seconds
published: true
comments: true
excerpt: The past couple of weeks have been filled with jaw-dropping aerials, hair-splitting hundredths of a second, and feats of endurance. Now, the summer Olympics are winding down. Some of my favorite coverage of the London Olympics has been The New York Times data analysis in their "One Race, Every Medalist Ever" series.
---

The past couple of weeks have been filled with jaw-dropping aerials, hair-splitting hundredths of a second, and feats of endurance. Now, the summer Olympics are winding down. Some of my favorite coverage
of the London Olympics has been The New York Times' "One Race, 
Every Medalist Ever" series.

In the <a href="http://www.nytimes.com/interactive/2012/08/05/sports/olympics/the-100-meter-dash-one-race-every-medalist-ever.html">men's 100 meter sprint</a>,
Usain Bolt topped his 2008 time by six hundredths of a second to finish the race in a mere 9.63 seconds.

Looking at the graph of the 100 meter sprint men's medalists since 1896 (20 second mark), 
it appears to be exponential. Of course, it you throw out 1896, a linear fit 
would be possible. The difference in times does seem to have diminished recently. However, 
that doesn't necessarily mean that we've reached an asymptote. There are 
several points on the graph where it appears to level out until someone breaks 
that barrier. Usain Bolt has started a new tier on the graph and if he continues 
to run, I imagine that the time will continue to shrink. Plus, there is no theoretical reason
to suspect a non-linear fit.

Three seconds is not insignificant in the 100 meter sprint. 9.6 seconds is
almost a 25% improvement over 12.6 seconds, the slowest time of any of the
medalists. Still, as The New York Times points out that difference is only
3 seconds. All of these medalists are incredibly fast, even now. Every 
Olympian is a highly skilled athlete whether or not they make it onto the 
podium. 9.63 seconds or 12.6 seconds is truly impressive.

<hr />
EDIT: Now that I've returned from vacation, I've played around 
with the data to get a better sense of the regression.

The two clear choices are a linear or negative logarithm model.
As mentioned above, the linear model is simpler. In this case, 
it is easy to overfit the data based on past times. Although the 
R-squared value for the logarithmic model is 0.90 while the R-squared value
for the linear model is 0.78, the linear model may still be the 
better choice. Sports analysis is not likely to perfectly follow a 
model unlike physical laws.

<img class="scale-with-grid" src="/images/olympic_linear.png" width=600px>

<img class="scale-with-grid" src="/images/olympic_log.png" width=600px>

However, there is one part of the logarithmic model that I prefer.
Both models have the 100 meter sprint times continue to fall, which seems
reasonable. Given all of the records humans have broken in just the past century, I doubt that we've 
reached the boundary of our abilities yet. If the linear model holds true, the gold
medalist in the 2708 Olympic Games will finish the race in 0 seconds.
I realize that those games are 700 years away, while the model is only based
on 116 years of data. Yet 700 years is not that long. The Olympics have already existed for 3000 years.

Alternatively, the logarithmic model does not have a medalist finishing in 0 seconds
until the 2654388 games. I can entertain the idea that humans (well, our descendents) could evolve to teseract
within 2652376 years, and I am sure that both of these models will be thrown out well before
then.