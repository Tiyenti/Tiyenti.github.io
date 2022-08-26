---
title: "Tiyenti Tech Troubles: Trying to get an official IIDX Entry Model controller to function"
category: "tiyenti-tech-troubles"
---

Alright, so I guess it's time for another episode of Tiyenti Tech Troubles. A "series" that never
really was on *here* since I barely use this place, but I somewhat regularly have made massive
tweet threads about technical issues whenever they've cropped up, and realistically a blog is
a better place for that kind of long-form content. So I'll save my Twitter followers the tweet
spam. Here's what's currently up with me trying to get the IIDX Entry Model controller I just
bought a couple weeks ago and recieved today.

<div markdown="1" style="margin-left: 20px; margin-right: 20px;">
## **Issue Status:** **<span style="color: red;">Unsolved</span>** (as of 2022-08-26)

This post has last been updated on 2022-08-26.

If I find any solutions or test any more things, I will either be tweeting about them or
I might possibly update this post with further attempted solutions. If I do find a proper
solution, I will update this post with it as a reference for any future Internet folks
who come accross the same issue. {% include footnote.html footnote="There is nothing worse than discovering an obscure problem that noone else seems to have that noone's published any fix for. Even worse if it's an obscure item with very little information about it, at least in the places I would expect there to be on the anglophone Internet (such as on /r/bemani)." %}
</div>

<!--more-->

{% include img.html src="https://pbs.twimg.com/media/FbHGAllUEAEWIZh.png" alt="Image of my avatar character, Mssaku, smashing her head into a desk." caption="*sigh* Here we go again..."%}

## The Basic Overview

So, I ended up getting one of those official "entry model" IIDX controllers, but while I mostly like it externally, I have discovered an unfortunate problem: it seems to refuse to work with my computer.

**The Issue:** When I connect it to my PC, the controller is recognised, but no inputs are detected. In addition, the blue light that indicates Bluetooth mode will start flashing after a short time. Despite the fact the Bluetooth switch is off, and there are no batteries inserted.
To be specific about the way the light is functioning, it seems to follow the following pattern:

1. The light will remain solid blue for a short time. (According to the user manual which I Google Translated given that they're all in Japanese and I am but a monolingual anglophone, this apparently means Bluetooth mode is initializing.)
2. The light will turn off for several seconds. (Indicating that it's connected via USB, but as already mentioned, no inputs are recognised by my PC when connected in this manner.)
3. The light will turn back on, but this time flashing slowly. (Supposedly indicating it's searching for the official mobile app so it can pair with a phone.)

**My Theory:** The controller is, for some reason, not properly detecting the USB data connection, and is somehow only receiving power. This prompts it to start bluetooth mode to connect to a phone for *IIDX ULTIMATE MOBILE*, but, obviously, this is not what I want; I'm
wanting to connect it to my PC for use with BMS simulators or *INFINITAS*.

## Attempted to fix the problem via a USB controller adapter

I think I'm just going to have to try a bunch of weird shit to get it to work, so I tried to use a controller adapter I have lying around - the Mayflash MAGIC-NS USB adapter I use with my thnikk Fightboard to play Tetris on Switch - in hopes that maybe that would make it work
properly. It didn't, but it did change the behaviour of the issue somewhat. To recap
what I just said above, the normal pattern of the bluetooth light appears to be the following:

1. Solid for a moment
2. Remains off for several seconds
3. Starts flashing slowly

However, when I connect it via the controller adapter, it changes to something else.

1. The light flashes quickly for several seconds.
2. The light turns solid for several seconds.
3. The light begins flashing slowly like it normally does.

Based on some other information about the IIDX Entry Model controller from the machine translated manual, the quick flashing apparently means something else to do with the Bluetooh mode, I think that indicates it's attempting to pair with something but I don't exactly remember. I should probably check... Either way, I think this could perhaps be due to the fact the MAGIC-NS  adapter apparently itself has Bluetooth support, and can identify Bluetooth devices by plugging them into the USB port. There's some more information about this as well but I want to go over some other things first since that's relevant to understand the context here.

While this could be a potential lead to solve this problem given that it is very clearly 
altering how the controller is interfacing with my system (and has other info I'll get to
in a bit), I do wonder if it's *just* the Bluetooth support on the adapter causing that
behavioural change, and just using a different adapter might not work. I'd also need to
find an adapter that functioned, which might take time and money.

## Other attepted fixes, and trying to see if the controller even worked
I did attempt some other potential solutions that I could think of, but none of these did
anything:

Anyway, next I decided to try some other things to see if the controller even *worked*, given
that some further context here is that I bought my unit used off of eBay. It's possible it could
have been defective, so I did want to see if it at least functioned in other scenarios.

The first thing I attempted was trying to connect the controller to my phone via a USB C OTG
cable. This actually worked partially; I was getting turntable inputs, but the buttons weren't
working at all. That was at least some progress, though it did make me worry that the controller
might just straight up be defective given that the buttons weren't working. But it wasn't, which
I will get to in a sec. To try and get the buttons to work, I decided to try and use the 
controller adapter with my phone, but this ended up giving the same (non-functional) results
as trying to use the adapter with my PC. It's clearly changing the interfacing somehow,
which does still give me *some* hope that this might lead me to a similar solution that actually
works.

I decided to try using that OTG cable on some other things, like my Steam Deck (which I also
received recently) - this also didn't work and gave me similar problems to connecting it
directly to my PC. I also tried to just try random crap at this point; I used that OTG cable
plugged into my PC's USB-C port (didn't change anything), as well as using a USB passthrough
I had from my Steam Controller (also didn't change anything.)

At this point I was obviously starting to get pretty worried I might have just wasted money,
but one of my family members suggested trying to use a laptop that we have lying around, and
I found that with that laptop, the controller actually works *perfectly*, and it's *consistent.*
So the controller at least *works*. It just, for some reason, doesn't like the other devices I
have.

Later on, I also decided to check to see how the controller adapter worked with the laptop;
it gave the same results as every other device; the quick flashing, followed by solid,
followed by slow flashing, and no inputs are recognised. So the adapter is still behaving
consistently across devices, but the controller itself is not.

## Unfortunately, this could be the end of the road
I have heard from someone talking in a Discord I lurk in that official
Konami controllers such as the IIDX Entry Model can apparently have difficulty
functioning properly on AMD systems. So far, this information is adding up;
my main PC has an AMD Ryzen 5600x, and obviously the Steam Deck is AMD-based as
well. The two devices that the controller at least partially worked on so far - my
phone and that laptop - are Snapdragon and Intel, respectively. So it's entirely
possible that the controller will just never work with my PC at all, given that
circumstance, and, well, that would suck...

So, this could be the reason why it's not working for me. My phone at least partially worked,
and while that *could* be a chipset problem, I'm personally more thinking along the lines that
my phone just doesn't provide enough USB power to the controller, so only the turntable works.
I'd have to test with a powered USB hub, but I don't have one on me right now to test.

I still perhaps have some hope that I could find a solution, but I don't have the necessary
equipment to test things right now, which is... unfortunate. At the moment, I primarily want
to see if using a USB hub of some kind might get the controller to work for me, but as I just
said, I don't have one on hand to test. My monitor does have an in-built USB hub, but I don't
seem to have the USB 3.0 A to B cable that's required to actually use it anymore, so I can't
test with that right now either. I might have to see if anyone around me has one I could 
borrow for testing purposes, or maybe I'll just have to go buy one off of Amazon or something
just to see if that works. Either that, or maybe a different controller adapter would work,
albeit possibly with some latency which could be a problem given that IIDX is a rhythm game
and therefore requires pretty consistent timing. I've heard that can be an issue on old PS2 KOCs.

Another method would just be to see if I could just use the Bluetooth mode, but I did try to
pair it with my phone and it doesn't seem to allow you to pair to it directly. It sounds like
it only actually accepts pairing if it's being done from the official app, which isn't available
on the international Google Play / App Store and the only easy way to get it (i.e., won't need
to make a new Google account) would be from some other store that looks... uhh, sketchy to me,
to be honest, so can't really use that either.

At the extreme level of "I really want to find some way to get this to work", I wonder if
there is at least value in the idea of seeing if I use some other device (Raspberry Pi?) that
it plays nicely with as an intermediary, and use that as a middleman to tranfer data to my
main PC that way. I have no idea if such a thing would even be possible, or... well, easy,
probably too complicated for me to do that myself unless someone's already made a solution
for that specific problem. This sounds like a really janky idea, but it *could* work.
Ideally, this would not be the solution and something simpler would end up working just fine,
but... who knows at this point. It might be the only way short of just gutting the controller
completely and replacing the internals with something else, but I don't have the electronics
expertise for that kind of job.

## Conclusion for now
The controller isn't completely worthless given that it does at least work on some devices.
I can use it on that laptop fine, and theoretically if I did want to I could probably get it to
work on IIDX mobile and use it there (although no keysounds means it wouldn't be the full
experience, and having to use my phone kind of sucks).

Worst comes to worst I guess I could maybe see if I can throw together a dedicated
beatmania machine, but that would require even more money. I hope I'm able to find a solution
to this issue somehow, given that not being able to use a USB device on a PC due to processor
incompatibility sounds like the kind of thing that should've died out 10 or 20 years ago,
yet here we are. Computers were a mistake.

If you're reading this and have any ideas, leads, or potential solutions here, go @ me
on Twitter at [@TiyentiSR](https://twitter.com/TiyentiSR), cause I would obviously really
like to get this thing working lmao. If you come across this and don't know yourself
but perhaps knows someone who could help, I would also appreciate it if you could
share it I guess. Perhaps there is a way.

Anyway until I either find a USB hub or buy one I don't really have anything else I can try
so for the time being, that's it for now. Hopefully I find some kind of solution soon?