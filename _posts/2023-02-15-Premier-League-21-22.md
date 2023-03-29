---
layout: post
title:  "py - Premier League Analysis 21/22 season"
date:   2023-02-15 00:00:50 -0500
categories: Python
---

21/22 season is over but we can learn from premier league teams last year, in this post:

1. How was the road for Manchester City title?
2. What were the key matches who decided the champions?
3. How was the road for the relegated teams?

We're gonna use the usual libraries:

{% highlight python %}

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns 
import numpy as np
from scipy.stats import norm

{% endhighlight %}

Let's check at the overview of the table at the end of the season:



Pos|Team                    |Pld|W |D |L |GF|GA|GD  |Pts
---|------------------------|---|--|--|--|--|--|----|---
1  |Manchester City         |38 |29|6 |3 |99|26|73  |93 
2  |Liverpool               |38 |28|8 |2 |94|26|68  |92 
3  |Chelsea                 |38 |21|11|6 |76|33|43  |74 
4  |Tottenham Hotspur       |38 |22|5 |11|69|40|29  |71 
5  |Arsenal                 |38 |22|3 |13|61|48|13  |69 
6  |Manchester United       |38 |16|10|12|57|57|0   |58 
7  |West Ham United         |38 |16|8 |14|60|51|9   |56 
8  |Leicester City          |38 |14|10|14|62|59|3   |52 
9  |Brighton and Hove Albion|38 |12|15|11|42|44|\-2 |51 
10 |Wolverhampton Wanderers |38 |15|6 |17|38|43|\-5 |51 
11 |Newcastle United        |38 |13|10|15|44|62|\-18|49 
12 |Crystal Palace          |38 |11|15|12|50|46|4   |48 
13 |Brentford               |38 |13|7 |18|48|56|\-8 |46 
14 |Aston Villa             |38 |13|6 |19|52|54|\-2 |45 
15 |Southampton             |38 |9 |13|16|43|67|\-24|40 
16 |Everton                 |38 |11|6 |21|43|66|\-23|39 
17 |Leeds United            |38 |9 |11|18|42|79|\-37|38 
18 |Burnley                 |38 |7 |14|17|34|53|\-19|35 
19 |Watford                 |38 |6 |5 |27|34|77|\-43|23 
20 |Norwich City            |38 |5 |7 |26|23|84|\-61|22 


In the table we can see the positions after 38 games, **Machester City** and **Liverpool**, clearly dominated the entire season, Manchester City won again a championship by one point difference with 93 points, to have a context, there are 114 available points each season, to have a performace like Manchester City won **+81.58%** of disputed points throught the year, that is 2.447 out of 3 points for 38 matches!

The average team in the 21/22 premier league:

|Team           |W   |D   |L   |GF   |GA   |GD|Pts
|---------------|----|----|----|-----|-----|--|---
|Average team   |14.6|8.8 |14.6|53.55|53.55|0 |52.6 

A team with that amount of points will be placed at 8th only behind West Ham to dispute the middle of the table. Europe competitions are 17 points away to get to the Europe League and 19 points to play in the Champions League.



# 1. How was the road for Manchester City title?

Pos|Team                    |Pld|W |D |L |GF|GA|GD  |Pts
---|------------------------|---|--|--|--|--|--|----|---
1  |Manchester City         |38 |29|6 |3 |99|26|73  |93 
2  |Liverpool               |38 |28|8 |2 |94|26|68  |92 

There were only 2 runners up, Manchester City and Liverpool. 

Manchester City with 29 victories out of the 38 possible, 6 draws and only 2 loses, 73 goals of difference. 

{:refdef: style="text-align: center;"}
<img src="{{site.baseurl}}/images/steps.jpeg">
{: refdef}

Here is how the season went for both teams:

Liverpool was leader until round 11, when Liverpool lost the invict of 11th matches in premier league against West Ham in an away game, 

|Date         |Home Team        | Result | Away Team   |
|-------------|-----------------|------- |-------------|
|07-Nov-2021  |West Ham United  | 3:2    |Liverpool    |



{% highlight python %}

plt.barh(df['Team'], df['W'], color='g', label='Wins' )
plt.barh(df['Team'], df['D'], left=df['W'], color='y', label='Draws')
plt.barh(df['Team'], df['L'], left=df['W+D'], color='r', label='Loses')
plt.legend(loc='lower center', bbox_to_anchor=(0.5, -0.1), ncol=3)
plt.tick_params(bottom=False, left=False, labelbottom=False)
plt.box(False)

{% endhighlight %}

{:refdef: style="text-align: center;"}
<img src="{{site.baseurl}}/images/points.jpeg">
{: refdef}

