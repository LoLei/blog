---
layout: post
title: Blurry lock screen with i3lock
author: Lorenz Leitner
categories: Tutorials
---

This is a tutorial on how to get a lock screen like this:

<div><center><iframe width="560" height="315" src="http://webm.land/media/C3FA.webm" frameborder="0" allowfullscreen></iframe></center></div>
---

## Prerequisites
- [Some Linux distribution](http://distrowatch.com/)
- [i3lock](http://i3wm.org/i3lock/)
- [scrot](https://en.wikipedia.org/wiki/Scrot)
- [imagemagick](https://en.wikipedia.org/wiki/ImageMagick)
- An icon ([examples](http://www.flaticon.com/search/lock))

To install the package prerequisites, depending on your Linux distribution
you can use the package manager.

For example on Ubuntu based distros:  
`sudo apt-get install i3lock scrot imagemagick`

## The script
The major workload is done by this script:
<pre><code>#!/bin/bash
scrot /tmp/screen.png
convert /tmp/screen.png -scale 10% -scale 1000% /tmp/screen.png
[[ -f $HOME/Pictures/Icons/lock.png ]] && convert /tmp/screen.png $HOME/Pictures/Icons/lock.png -gravity center -composite -matte /tmp/screen.png
dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Stop
i3lock -u -i /tmp/screen.png</code></pre>

## Actual steps
0. Make sure you have the prerequisites, see above.

1. Copy this script to your home folder, call it lock.sh (for example).  
`curl http://lolei.github.io/blog/assets/post_files/lock.sh >> ~/lock.sh`

2. Add permissions so it can be executed  
`chmod +x ~/lock.sh`

3. Get an icon and save it somewhere. If you use a different folder or icon name you'll have to change it in the script too.  
`mkdir -p ~/Pictures/Icons && curl https://i.imgur.com/qY1nKlP.png >> ~/Pictures/Icons/lock.png`

4. Now you can run the script.  
`~/lock.sh`

5. Create an alias to have a dedicated command for the script.  
`alias lock="~/lock.sh"`

6. You can also create a keyboard shortcut. Go to your keyboard settings, shortcuts, create a custom shortcut, as command enter the script name and location again.  
`~/lock.sh`

And in case you don't know, i3lock can be unlocked just by typing your
password when it is active and pressing `Enter`.

## Finish
There you go, you have your own blurry lock screen.

If you think you're funny like me (`/s`), use a hilarious icon, click [here](http://lolei.github.io/blog/assets/post_files/illuminati.png) for the one I made.

---
How it looks on my Laptop with Arch Linux:
<div><center><iframe width="720" height="480" src="http://webm.land/media/C3FA.webm" frameborder="0" allowfullscreen></iframe></center></div>

How it looks on my desktop PC with Elementary OS:
<div><center><iframe width="720" height="480" src="http://webm.land/media/hXSh.webm" frameborder="0" allowfullscreen></iframe></center></div>

## Sources
I found out about this script on [Reddit](https://www.reddit.com/r/unixporn/comments/3358vu/i3lock_unixpornworthy_lock_screen).

The instructions I got from user [/u/TotallyNotAnAlien](https://www.reddit.com/r/unixporn/comments/3358vu/i3lock_unixpornworthy_lock_screen/cqib37h).
