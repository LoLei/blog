---
layout: post
title: Half-Life 2 release counter
author: Lorenz Leitner
categories: Creations
---

So far this blog has been really meta, this will be the first post which
actually addresses something outside of the blog itself.

Some years ago (I think 2), during my mandatory community service, I made
a website which counts the days that passed since the release of the game
Half-Life 2: Episode 2, which is the latest installment of the Half-Life
series.

Fans have been waiting for years for the next release, because (mild spoiler:)
Half-Life 2: Episode 2 ends on a cliffhanger.

The counter does not help to ease the pain waiting, it has almost been 3000
days.

Anyways, check out the counter [here](http://lolei.github.io/hl2-counter).

I also made a counter with the same concept about the Game Of Thrones books,
alias "A Song Of Ice And Fire". You can view this website
[here](http://lolei.github.io/got-counter).

---

A little insight on how it works:
The script gets the release date I pulled from Wikipedia, and compares it
to the current date. The result is in milliseconds. This then gets calculated
back into days, which is also split up into year, month and days using some
modulo operations.

Below is the code snippet of the script, but you can view the entire source
code on [GitHub](https://github.com/LoLei/hl2-counter).

<pre><code class="hljs javascript">// Set the two dates
var ep2 = new Date(2007, 9, 10); // Y/M/D, Month is 0-11
today = new Date();
// Get 1 day in milliseconds
var one_day = 1000*60*60*24;

// Calculate difference in milliseconds btw the two dates, and convert to days
document.write(Math.ceil((today.getTime() - ep2.getTime()) / (one_day)) +
  " days since Half Life 2: Episode 2");
var time = Math.ceil((today.getTime() - ep2.getTime()) / (one_day))

// Split into Year, month and day
function calc(x) {
	var y = 365;
	var y2 = 31;
	var remainder = x % y;
	var casio = remainder % y2;
	year = (x - remainder) / y;
	month = (remainder - casio) / y2;
	var result = "Or " + year + " years, " + month + " months and " + casio +   "days";

	return result;
}</code></pre>
