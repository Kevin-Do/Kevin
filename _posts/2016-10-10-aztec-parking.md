---
layout: post
title: "Aztec Parking Guidance"
image: "https://farm3.staticflickr.com/2101/2372486734_175bd3c55e_b.jpg"
categories:
  - IEEE
  - projects
  - PGS
tags:
  - Python
  - OpenCV
  - Arduino
  - ImageAnalyzing
---

# Aztec Parking Guidance Project
---

At SDSU, there is a ton of traffic that stuffs up all of the surrounding streets. During the morning rush and afternoon exodus, traffic is simply jammed and parking spots are also extremely hard to find during the common hours.


Other modern facilities in malls and universities have these systems already in place with sensors on every parking spot or floor. This is very costly and I believe it can be done way cheaper and much more efficiently.

## The Plan
---
The effective way to calculate open parking spots is to instead account for **% total percent** capacity of a parking lot. This can simply be done by:

'''
    {total current cars\over total maximum capacity}
'''
