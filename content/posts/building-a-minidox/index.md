+++
title = "Building a MiniDox"
author = ["Fernando Jascovich"]
date = 2019-07-19
lastmod = 2019-07-20T01:02:11-03:00
tags = ["minidox", "keyboard", "qmk"]
draft = false
weight = 2001
layout = "single"
+++

I built my first mechanical keyboard, a [MiniDox](<https://github.com/That-Canadian/MiniDox%5FPCB>).

{{< figure src="assets/minidox-complete-01.jpg" >}}

---


## Motivation {#motivation}

-   It was easy? nope.
-   I already had experience doing something similar? nope.
-   I had even held a solder for one second before? nope.
-   I knew somthing about keyboards before (besides using one, of course)? nope.

So... why?
Well, to be completely honest, for fun mainly. I got my first comments about something called mechanical keyboard thanks to [geekymartian](<https://github.com/bfagundez>), he built an [ErgoDox](<https://www.ergodox.io/>) and then others (two MiniDoxs and counting). Then I started to read about it, about the tools involved, about an endless world of possibilities about key mappings and functions, about typing in a real more comfortable way.
Another reason could be my "[Emacs pinky](<https://en.wikipedia.org/wiki/Emacs#Emacs%5Fpinky>)", now I have Ctrl and Alt right under my thumb.

{{< figure src="assets/laptop-ctrl.jpg" caption="Figure 1: Here is a picture of my laptop's keyboard which I think is self-explanatory about emacs-pinkyness" >}}

It was after started building it when I started to realize or to have an aproximate clue about the posiblities behind being able to program your own keyboard.


## Gathering things togheter {#gathering-things-togheter}

For building this keyboard I need two sets of things: tools and pieces.


### Tools {#tools}

{{< figure src="assets/lab.jpg" caption="Figure 2: My \"lab\"" >}}

-   Soldering station with adjustable temperature ~40W
-   Rosin core solder 0.5mm
-   Soldering paste: for soldering smd diodes
-   Syringe with needle: for putting soldering paste right on the required place.
-   Desoldering wick: life saver
-   Magnifying glass with tweezers
-   Anti-static tweezers kit for electronics
-   Toothpicks: for holding smd diodes
-   Isopropyl alcohol: cleaning pcb
-   Multimeter with diode test capabilities: You'll want to measure every soldered diode just after soldering it.


### Pieces {#pieces}

I bought [PCB](<https://shop.profetkeyboards.com/product/minidox-pcb-set>) and [electronic components](<https://shop.profetkeyboards.com/product/minidox-pcb-set>) from [Profet](<https://shop.profetkeyboards.com/>), but this is the list of required components:

-   PCB or hand-wire
-   2 ProMicros: atmega32u4
-   2 Switches for reset
-   2 TRRS ports
-   36 diodes: it could be smd (SOD 123) or through-hole (1N4148)
-   36 key switches: I used [Gateron Brown](<https://www.switchtop.com/product/gateron-switches>)
-   36 key caps: In my case, Cherry compatible
-   Mount plate and case: I printed [this model](<https://github.com/fernando-jascovich/minidox-case>)
-   TRRS male-to-male cable


## Getting your hands dirty {#getting-your-hands-dirty}

I was able to build this thanks to [this great and detailed building guide](<https://imgur.com/a/vImo6>).

{{< figure src="assets/minidox-building-01.jpg" caption="Figure 3: Mouting reset button" >}}

{{< figure src="assets/minidox-building-02.jpg" caption="Figure 4: Soldering first key switches" >}}

{{< figure src="assets/minidox-building-03.jpg" caption="Figure 5: ProMicro mount" >}}

Not everything is soldering and roses, after putting my keyboard together I had the following issues:

-   Some keys from right hand started to malfunction. When I pressed a key from second row, all that row was sended as input. It happens that my plate (the one on which keyswitches are laid) is too thick and this causes some improper levelling at PCB which produces this kind of malfunctioning. I fixed this by putting some supports (cardboard) between plate and pcb and avoiding pcb bending in any way.

-   First column on right hand worked weird too, sometimes no keystroke was registered. I took me a while to discover this but, finally, I detected (by using a multimeter) that keystrokes weren't reaching ProMicro's pin. So a bridge fixed this problem.

{{< figure src="assets/minidox-bridge.jpg" caption="Figure 6: Brige to pin" >}}

-   An intermittently dead key. This was caused by a bad swich, just replacing it fixed the problem (note here, buy a couple more key switches just in case).


## Firmware {#firmware}

After finishing both sides, you have to install firmware. There are a couple of options around, I only used [qmk](<https://qmk.fm/>) which comes with a [docker environment](<https://github.com/qmk/qmk%5Ffirmware/blob/master/Dockerfile>)  which works perfectly (yes, you have to run it in privileged mode).

{{< highlight bash >}}
KEYBOARD=minidox
KEYMAP=example

docker run -ti --privileged \\
       -v /dev:/dev \\
       -v "$PWD":/qmk\_firmware \\
       qmk-build make "$KEYBOARD":"$KEYMAP":avrdude
{{< /highlight >}}

With qmk there are a lot of posibilities and tweaks available for every key on your keyboard. This is my [current keymap](<https://github.com/fernando-jascovich/qmk%5Ffirmware/tree/fernando-jascovich%5Fminidox%5Flayout/keyboards/minidox/keymaps/fernando%5Fjascovich>) for reference, but I think that this is a really personal thing. For example, I wanted to have ctrl in my thumb mainly because I'm a Emacs user, I doubt that a vimmer would have the same requirement.


## Using it {#using-it}

It took me a couple of months to being able to write decently with this layout, it was my first time with a split keyboard. First discovering where are the keys, then writting and coodinating movements of the two hands, it was fun.

Once you get your hands in the keyboard, there no way back, I feel "at home" with my MiniDox.
