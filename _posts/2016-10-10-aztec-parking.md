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

**Progress BLOG**  
[Timeline Updates!](https://docs.google.com/document/d/18Eg5EOx2ETNyla-LXG4DLTckIDiXMzJWi56QPfMXA_8/edit?usp=sharing)
{: .btn .btn_success}


## The Plan
---
The effective way to calculate open parking spots is to instead account for **% total percent** capacity of a parking lot. This can simply be done by:

<div class="notice">
(initialCars + {entries - departures}) / totalCapacity = loadFactor
</div>

Instead of posting sensors at every single parking spot or floor, we can instead post single *camera + arduino programmed units* at the entrances of the parking lots.

<figure>
	<a href="https://github.com/Kevin-Do/Aztec-Parking-Guidance"><img src="http://i.imgur.com/OXw4ISt.jpg"></a>
	<figcaption> I mapped out all the entrances and parking lots on campus </figcaption>
</figure>

## Software
---
We will be utilizing [OpenCV](http://opencv.org/), an open source computer vision library. Free to use for all purposes, it has great documentation and historical results.  
<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/z1Cvn3_4yGo" frameborder="0" allowfullscreen></iframe>  
</center>

### Software pushes to: [Github](https://github.com/Kevin-Do/Aztec-Parking-Guidance){: .btn .btn_success}
<a class="github-button" href="https://github.com/kevin-do/Aztec-Parking-Guidance" data-style="mega" aria-label="Star kevin-do/Aztec-Parking-Guidance on GitHub">Star</a>

## Materials


| Bill of Materials | Purpose | Cost: |
|---|---|---|
| Raspberry Pi Computer Units  | Runs main program, computations and calculations  | **TBA**  |
| Camera/Sensors  | Monitors parking lot entrances and uses [OpenCV](http://opencv.org/) | **TBA**   |
| Network Adapters  | Transmits data regarding capacity and current conditions    | **TBA**   |
| External Materials  | (*Waterproof Case, Ethernet, Power Cords*)   | **TBA**   |

**Prototype Bill of Materials:** [Spread Sheet](https://docs.google.com/spreadsheets/d/1F0OX3I4pIi6qh72riP2w0rrSMLZh6Gi5A-4ApnPeVbI/edit?usp=sharing)

## External Factors
---

**Faculty Vehicles**:
---  
Vehicles that belong to administrators, teachers and faculty members cannot be distinguished from student cars. The only varying difference is the **green colored** permit whereas students have the **red colored** permit. We might also face problems with specialty edge case vehicles like large service trucks or trailers. *ie: 80% capacity does not guarantee 20% vacant student parking spots.*
{: .notice_danger}  

Some parking lots have completely sectioned off faculty areas. Out of 8 floors, the bottom 3 floors may be entirely faculty only. This makes accounting for faculty cars completely doable if we plant **additional units** at those areas!  
{: .notice_success}

**Night Time**:
---  
OpenCV image analysis may be faulty or impossible to operate at low light.
Outfit our units with **night vision**. Our software may need to have configurations to automatically switch over to night vision at certain time periods.  
{: .notice_info}

**Remote Control Access**:
---  
We'll complete trial runs with unit tests and create remote control access for fixing calibration. Use Haar Training to steadily improve accuracy as the unit progresses.  
{: .notice_info}



<iframe src="https://docs.google.com/document/d/18Eg5EOx2ETNyla-LXG4DLTckIDiXMzJWi56QPfMXA_8/pub?embedded=true"></iframe>
