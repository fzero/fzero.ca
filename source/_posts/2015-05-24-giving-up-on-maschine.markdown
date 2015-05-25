---
layout: post
title: "Giving up on Maschine"
date: 2015-05-24 18:58
comments: true
published: true
categories: 
  - geek
  - audio
  - music
---

It took almost four years and a major software update, but I'm finally ready to admit [NI Maschine](http://www.native-instruments.com/en/products/maschine/) isn't for me.

<img src="/post_images/maschine.jpg" class="center"/>

I'm a bit surprised, really. I come from a sampling background and my first productions were made using trackers running on DOS (Remember the 90s? I was there). I bought an [Akai MPC2000](http://www.vintagesynth.com/akai/mpc2000.php) when I was ready to bring my tracks to the stage and I pushed it to its absolute limits, so I feel completely at home with a lovely array of 16 rubberized pads.

<img src="/post_images/mpc2000.jpg" class="center"/>

Knowing that, it's obvious I got interested on Maschine when I first heard of it. An MPC-like design with all the convenience of editing samples, programs and sequences on the computer? Shut up and take my money! But the theory doesn't always work in practice. Maschine is indeed very straightforward and quick to get a groove going, but once you reach a certain point you can't help but wish you had a full DAW at your disposal. Even NI knows this - that's why Maschine also runs as a plugin. And that's where your problems start.

## Double the sequencers, double the fun?

For all practical purposes, Maschine acts as an "external" box MIDI-synced to your DAW. Only it isn't a *box*, but a whole new pattern-based sequencer running inside a plugin. This means you get double everything: there's a second arrangement (scenes containing patterns), a second mixer and second set of effect buses.

Since sequencing grooves in Maschine is pretty much the whole point, your workflow quickly becomes a huge mess. Any pattern currently selected on Maschine will start playing immediately whenever you press play on the DAW, regardless of where you are in the arrangement. I've lost count of how many times I had the groove for the chorus playing on top of a breakdown and vice-versa. It's extremely confusing and annoying.

There are two ways to fix this, and both suck. One is creating scenes on Maschine, assigning MIDI notes or control changes to them and remembering to fire them from the arrangement. This is the *bad stuff* from the MPC times and precisely what everyone hoped to avoid when working with a computer.

The second way is exporting audio for every pattern in every group using Maschine's drag and drop feature - which works, but it's a pain in the ass - or sending the plugin's outputs to multiple channels and recording them to regular audio channels. Your arrangement will be all audio from that point on, which means you'll have to re-record the whole thing if you wish to change a groove later. In other words: it sucks.

## Wait but why?

Is it all bad? No, not really. It just doesn't fit well on my setup. And if you use [Ableton Live](https://www.ableton.com/en/live/) as your main DAW (or [Bitwig](http://www.bitwig.com/), for that matter) it probably isn't for you either.

The truth is Live does *everything* Maschine does in a saner and more integrated way. The [drum rack](https://www.youtube.com/watch?v=2PGdfIK5K9Y) device alone does *way more* than Maschine's groups will ever do, with the added benefit of being able to drag bits and pieces from the session directly into each drum pad. Then you can use the session view to create clips and scenes without worrying about copying all tracks to a new pattern all the time (again, a consequence of Maschine trying too hard to feel *just like hardware*). Each clip can have a different time signature too, something that simply isn't possible on Maschine.

<img src="/post_images/live_drum_rack.png" class="center"/>

Speaking of controllers: sure, Maschine big selling point is providing a way to put keyboard and mouse away, but Live has [Push](https://www.ableton.com/en/push/) and the whole [APC line](http://www.akaipro.com/category/ableton-controllers). It also talks to virtually anything you can plug into a USB or plain old MIDI port. Any controller with pads will work automatically with Drum Rack, so you can do your finger drumming just the same (and plug the same controller on your iPad afterwards).

On the other hand, Maschine only works with Maschine. There's a General MIDI mode and a few other control templates, but the controller **always** requires a Mac or PC to do anything useful - and forget about Linux. It isn't even class-compliant, so you can't use it to control any iOS music apps (including NI's own iMaschine, somewhat ironically).

To top it off: my controller is still the monochrome version - no cute RGB pads for me. **Of course** NI doesn't offer the option to buy just the hardware. If you want to pound the rainbow there's no other option but paying for a brand new software license. Ah, the joys of vendor lock-in!

## If your DAW is boring, go for it

But yeah, let's say you're stuck with a boring old linear DAW like ProTools or Logic. In that case, Maschine will feel revolutionary! A sizeable number of features all cool kids have been playing with for the last decade will be finally available to you. Hell, you might even love the fact Maschine mostly works like an external piece of hardware.

The included sample library and plugins are also well worth it. That's actually the only thing stopping me from selling it, especially since they're available without having to fire up Maschine. 

(On the other hand, this means I should have gotten Komplete and a good pad controller instead, but that's another story.)

## Fixing it

It turns out there's a way to bypass Maschine's internal sequencer entirely [using Live's drum racks to control everything](http://tekmonki.com/2014/01/22/sequencing-maschine-drum-tracks-with-ableton-push-controller-update/). It's a  long-winded solution, but it makes using those sweet drum synthesizers less painful. Then again, this makes the Maschine controller dispensable - you can control drum racks with anything after all.

The bottom line is: if you're not stuck with a boring DAW and want to make more than beats, do your homework. You might already have what you need, or you can get there spending close to nothing. It also pays to buy hardware that won't lock you to a single software. Ableton tried that with the first APC line and failed; now Push and the APC MKII are fully class compliant. Open and hackable hardware is always the way to go.
