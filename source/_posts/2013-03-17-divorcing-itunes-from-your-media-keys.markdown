---
layout: post
title: "Divorcing iTunes from your media keys"
date: 2013-03-17 13:24
comments: true
published: true
categories: geek 
---

You've been there. Maybe you're listening to your favourite song on Rdio, or maybe checking your Soundcloud stream. You reach for the play/pause key on your keyboard and *BAM*, motherfucking iTunes comes up. Don't you hate that? I do.

Luckily, there's a way to fix it. Open your terminal and type:

    launchctl unload -w /System/Library/LaunchAgents/com.apple.rcd.plist

Voilà, iTunes no longer responds to the media keys. The only downside is that now iTunes doesn't respond to the media keys _at all_. I couldn't care less, but if you're a crazy person who actually *likes* iTunes (poor you!), you can reattach the keys at any time with:

    launchctl load -w /System/Library/LaunchAgents/com.apple.rcd.plist

One could conceivably run the _detach_ script at login and write a small AppleScript launcher to reattach the keys and then launch iTunes. I'll leave this as an exercise to the reader.

