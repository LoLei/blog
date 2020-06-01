---
layout: post
title: How to fix SteelSeries Arctis 5 Balancing
author: Lorenz Leitner
categories: Tutorials
---

If all of a sudden your SteelSeries Arctis 5 headphones are not balanced anymore,
for example if the sound comes out louder from one ear than the other, here's the fix.

---

This issue only happens on Windows (figures) therefore the instruction to fix it is also for Windows.

1. Control panel
2. Sound
3. Playback > Arctis 5 Game
4. Properties
5. Levels
6. Balance
7. Set the off-balanced side to 100 again

<a href="{{ site.baseurl }}/images/ssarctis5fix.png" data-lightbox="arctis5-fix" data-title="The crime scene">
  <img src="{{ site.baseurl }}/images/ssarctis5fix.png" title="The problem and solution">
</a>

What a great driver. Why does it randomly set the balancing of one side lower?
No wonder reverse-engineering this for Linux hasn't proved to be an easy task [[1](https://github.com/LoLei/arctis-ctl), [2](https://github.com/LoLei/sibctrl)],
considering how broken it is on Windows already.

---
Credit goes to [AlvardReynolds on Reddit](https://www.reddit.com/r/steelseries/comments/bgrjea/arctis_5_louder_in_left_ear/elndgqg/).  
This comment is unfortunately buried under a lot of other non-working solutions and threads, so I posted it here as well.
Mainly for myself so I can find how to navigate the Windows control panel more easily again.
