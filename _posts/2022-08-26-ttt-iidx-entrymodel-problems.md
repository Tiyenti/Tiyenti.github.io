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
## **Issue Status:** **<span style="color: darkgoldenrod;">Workaround Found</span>** (as of 2022-08-28)

This post has last been updated on 2022-09-18.

I have another update on this situation; [last update](/tiyenti-tech-troubles/2022/08/26/ttt-iidx-entrymodel-problems.html#update-as-of-2022-08-28-an-extremely-janky-workaround-that-im-disgusted-actually-works), which I published on 2022-08-28, I mentioned that I had found a functional workaround to get
the controller working, that being I decided to use a Steam Link in a virtual machine combined
with GlosSI on my host to get the controller working, but since then I have discovered that
this limits the polling rate to about 60Hz, which is abysmal.

Since I couldn't find any other program that allowed me to send controller inputs over
a network that would give me a better polling rate, I decided to just write my
own code, since I remembered I knew how to do that. This has improved my workaround so that,
while still being somewhat inconvenient, it feels *much* better to play the game now and in
theory should feel about as good as just having the controller plugged in directly. You can
view the latest update [here]() or if you just want to see my code, I've published that on
my GitHub [here](https://github.com/Tiyenti/iidx-con-hack).

This still isn't ideal, so I would still prefer to have a proper solution, of course.
Lemme know if you've got any ideas for a fix; I will update this post with it as a reference for any future Internet folks
who come accross the same issue if I do manage to find one. {% include footnote.html footnote="There is nothing worse than discovering an obscure problem that noone else seems to have that noone's published any fix for. Even worse if it's an obscure item with very little information about it, at least in the places I would expect there to be on the anglophone Internet (such as on /r/bemani)." %}
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

## Other attempted fixes, and trying to see if the controller even worked
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

## UPDATE AS OF 2022-08-28: An extremely janky workaround that I'm disgusted actually works
So, a bit after I had initially posted this I had tried something that I had also found from
the tweets made by someone that seemigly had the same issue I had, as mentioned above: I tried
to pass the controller through to a guest virtual machine. And... in what I can only describe
as sheer, absolute insanity, when I do this, **it works perfectly fine**. Depsite the fact
it's plugged into the ***SAME DAMN COMPUTER.*** For some reason, it just refuses to work
with my PC under normal circumstances, but apparently it *does* happen to like VirtualBox's
USB emulation, I guess, so this gave me a new potential lead as to how I could at the very
least circumvent the problem.

Essentially, if the controller works in a VM, perhaps there's some way that I could get the
guest VM to connect to my host machine, to get the controller working there, probably over some
kind of network connection. If I could manage to do that, then this would probably get the
controller working, with hopefully minimal latency as the network connection would obviously
be, well. It's just going to be an internet adapter talking to itself, really, so as far as 
latency is concerned I didn't think it'd be *too* bad.

I spent some time trying to figure out a method to get that remote connection. I was thinking
about Steam Remote Play, but I initially ran into problems with that given that on my phone,
whenever I went back to the desktop (which is where I was going to be running a gamepad test
website), I couldn't send any controller inputs. Somewhere along that road I found out about
and was looking into USB/IP and wanting to see if that would work, but eventually I did manage
to get that installed on a live system and it didn't seem to allow me to bind the controller
in the VM, so, eh.

So eventually I did just end up having to try the Steam Link linux client;
I also ended up wasting a lot of time here trying to get it to install on a live ISO
instead of just properly installing the OS to the VM, which admittedly was mostly due
to the fact that I had tried a proper install earlier and it failed and was unbootable.
Just running the Ubuntu installer again (since that's the distro I was using at least for
testing purposes) fixed that problem and after another reinstall to give myself more virtual
disk space to install everything, I was able to get the Steam Link app running to see if this
would work, and it did mostly function and I could bind the controller and all, but it still
wouldn't work globally throughout my system. I would prefer a solution that didn't need me
to run every game through Steam to get the controller to work, especially for something
like *INFINITAS* which has its own web-based launcher as far as I'm aware that might not
work if added as a non-Steam game.

The solution to that problem is just to use [GlosSI](https://github.com/Alia5/GlosSI); I
downloaded it, installed the prerequisite drivers, and then added `GlosSITarget.exe` to
Steam as a shortcut; running this successfully allowed me to use the controller in a 
web browser, and has officially "solved" my issue with getting the thing to function
in... what is honestly the most improvised with duct-tape and hot glue solution
I feel there possibly could be, but, I mean, it *works*. Even if it does feel like
it could break apart at any moment.

Now I will admit I'm writing this at like 4 in the morning after only having just
gotten this bullcrap to actually function somewhat well, so I apologise if I've gotten
a bit rambly here. I've gotta add though that at the moment I've obviously not tested this
*super* heavily; I've mostly just been using it in some web-based BMS player, where
it seems to work alright at least. I've not tested this with a PC client like *Beatoraja*
or, of course, the official *IIDX INFINITAS* PC release - I'm admittedly somewhat worried about
*INFINITAS* given that I'm not sure how good its controller support really is, but as far as
I can tell GlosSI does have the option to emulate DS4 instead of XInput, which I assume means
DirectInput (what the official controllers are meant to be using to begin with), so hopefully
if I do eventually get around to playing the official PC verison with and I still have to use
this hack, I should be able to get it to work. 

In terms of input latency, I haven't *noticed* any significant lag, but
I haven't actually tested it, so it's possible there could maybe be a small amount.
I'm not sure what the best method to test it would be to be honest but at least it
wasn't immediately apparent. I think through the use of offset calibration it would
hopefully be possible to account for whatever small amont of input lag there is, 
but it would maybe take some time to set that up.

All in all, this is... really screwed up that it's actually kind of working like this,
but I mean, I am happy that the controller I bought *is* actually able to be used on
my main PC, even if I have to resort to strange methods like this. I still probably
will want to try just using a USB hub since that would probably be a more clean solution,
but this hopefully will work as at least a temporary solution until I can find a more
permanent fix (but we all know that "placeholder" is just Programmer for "permanent" anyway).
Just... what the hell is even happening here, though. It doesn't work unless I use it in a
VM... I have no idea what in the world would cause *that* kind of behaviour, but I guess
maybe it just doesn't like my USB controller...? I would try with a USB 2.0 port if I still
had one on my motherboard, but, yeah.

For now, that's everything. I hope that either you enjoyed this technology ramble,
or if you're one of the 0 other people who have bought this controller and have
come across the same problem, maybe this will be helpful, although this is definitely
not something I expect someone who isn't at least something of a tech nerd to be able
to even follow... either way, maybe it provided some useful advice. Now, in the interest
of my sleep schedule, I'm gonna stop writing this update. Goodbye for now.

## UPDATE AS OF 2022-09-18: Improving the workaround and flaws with the original method
So, I've got another update to this saga. Previously, I had mentioned that using Steam
Link combined with GlosSI created a functioning workaround, but I hadn't fully tested it,
and I'm here to report that after longer than it probably should've taken me, I finally
decided to actually test the latency of this method by binding the buttons in Etterna,
and running the audio calibration test there - largely because I was trying to figure out
why my timing was so horrible with this workaround. As far as I knew, beatoraja - what I
was playing on - has 40ms PGREAT window (±20ms), but I was struggling pretty hard to actually hit
it consistently, which bothered me a lot since Etterna's Marvelous window is apparently around the same as that (though at the time I thought it was actually smaller), and playing that on keyboard
gave me significantly less timing problems.

I was wondering if my workaround was adding some latency - but as far as I can tell, there is not
a significant amount of extra input latency that is being added through this solution. However,
there was one thing that I started to notice: the standard deviation was sometimes going up to 18ms, and this started to concern me in regards to a *different* issue that this workaround could
be exacerbating: polling rate. Using [XInputTest](https://github.com/chrizonix/XInputTest) as a reference, I was able to determine what I was fearing: the input polling rate of Steam Link is
an astronomically low 60Hz. That's some extremely specific information that I wasn't able to
find on the Internet before I tested it myself, so if anyone else was looking for the same
info - there you go, I'm the one other crackhead around who actually needed to find that out.
You're welcome.

Either way, this was going to be a problem, given this is... *not* a good polling rate. While
60Hz input polling might work for some games, for a rhythm game like IIDX or BMS, that is
unacceptable; this likely explains why my timing felt so inconsistent, since there would be a lot of times where I just missed the input poll window and the input had to occur around *16 to 17 milliseconds* later, which would definitely be enough to miss the PGREAT window if I hit on the outer edges. Polling rate is really important for rhythm games!

So, I had to find a different solution. I wasn't able to find a different program that seemed
to do what I needed to do, that being sending controller inputs over a network connection.
This was frustrating... but then I remembered, oh wait, I know how to code. So I decided to go
and figure out how to just write my own damn program. The value of knowing programming increases
exponentially to how niche your interests get, since sometimes you'll run into a problem like
this where there is literally nothing that does what you want, but then you can just make it
yourself!

The result of this effort is a simple client and server program written in Python, that uses
[ViGEmBus](https://github.com/ViGEm/ViGEmBus) to create a virtual DualShock 4 from inputs
sent over from the virtual machine, and from my testing so far, this has been *much* better
in terms of timing. Running XInputTest again with this new method confirmed that this new
solution I made myself seemingly shows the controller polling at 200-220Hz or so, which I
assume just means it's polling at roughly whatever the rate the controller does normally.
Awesome.

Now, I also haven't thorougly tested this new program, and I already encoutered one apparent
bug where a key started holding itself down, but I think I know why that happened and have
already updated the code to hopefully prevent that. {% include footnote.html footnote="I was only checking 1 byte of the recieved data at the time, so the input probably just arrived at the same time as something else and got dropped. I'm using TCP for this, which isn't apparently is not message based, so assuming that every 1 byte sent will corrospond to 1 byte receieved was foolish of me. I've since updated the protocol to actually be message based to patch that particular hole." %} I'm not sure if this solution will work with *IIDX INFINITAS* since I
am using an emulated DS4, but I assume that means it will support DirectInput so hopefully
it'd work. There's always [this program](https://github.com/wcko87/bm-input-display) that can apparently keybind a controller for use
with *INFINITAS* as well, so I guess we can just slap workarounds on top of workarounds and
hopefully that would work lmao

Anyway, I've decided to publish my code on my GitHub, which you can view [here](https://github.com/tiyenti/iidx-con-hack) if you're either just interested, or have come across this page
in the near or far future in search of a solution to this exact problem and need to use what
I use. Just keep in mind that as of right now this is still not 100% confirmed to work right
and may not be suitable for high level IIDX/BMS play, but even just at a beginner level I can
tell that this is working much better than my previous solution. 

Not really much else to say other than that; this is still not an *ideal* solution
given that it still adds the extra processing overhead of having to use a VM to get
the controller working, but there is an advantage in that this solution no longer
requires a GUI, so I can probably alleviate some load by disabling/switching to
another Linux distribution that doesn't have a desktop environment. It's still
inconvenient having to remember to start this up every time I wanna play the game,
but it's better than the controller just straight up not working. There are other
problems with this controller like buttons double tapping sometimes, which I wonder
if doing a JKOC-style coin/cardboard mod would help with, but hopefully with this
solution in place I'll at least get some decent use out of this one until the time
comes where I can justify spending more on a better controller some time down the line.

That's it for now. If there's any signficiant updates on this situation later on, I'll
probably update this post again, or at least tweet about it.