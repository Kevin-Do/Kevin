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

```
    {totalCurrentCars \ totalMaximumCapacity} = currentCapacity (%)
    or
{initialLoad + (totalEntries - totalDepartures)} \ {totalLotSize} = loadFactor (.n)
```

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

# Software pushed to:

[Github](https://github.com/Kevin-Do/Aztec-Parking-Guidance){: .btn .btn_success}


## External Factors
---
There will definitely problems that arise when our initial prototypes and implementations.  
Here are things we need to account for:

* **Faculty Vehicles**:
  * Problem:
    * Vehicles that belong to administrators, teachers and faculty members cannot be distinguished from student cars. The only varying difference is the **green colored** permit whereas students have the **red colored** permit.
  * Short Term:
    * Parking capacities will simply have to reflect that open parking spots may or may not belong to faculty only. *ie*: **80% capacity** does not guarantee **20% of purely open student parking spots.**
  * Long Term:
    * Some parking lots have completely sectioned off faculty areas. Out of 8 floors, the bottom 3 floors may be entirely faculty only. This makes accounting for faculty cars completely doable if we plant **additional units** at those areas!  
{: .notice_danger}
* **Faculty Vehicles**:
    * Problem:
      * Edge case vehicles like trailer, special equipment vehicles, and temporary service vehicles.

* **Night Time**
  * Problem:
    * OpenCV image analysis may be faulty or impossible to operate at low light.
  * Solutions:
    * Outfit our units with **night vision**. Our software may need to have configurations to automatically switch over to night vision at certain time periods.  
{: .notice_danger}
* **Detection Rate**
  * Problem:
    * What happens if a car is miscounted or if slight mistakes occur? This can result in entirely **skewed total capacities** until the unit is recalibrated. How can we recalibrate mistakes in the detection rate?
  * Solution:
    * Make accurate software! Complete trial runs with unit tests and remote control access for fixing calibration. Use Haar Training to steadily improve accuracy as the unit progresses!
{: .notice_danger}
