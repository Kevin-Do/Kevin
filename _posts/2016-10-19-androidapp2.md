---
layout: post
title: "Android Application Concepts Two"
image: "https://i.ytimg.com/vi/Q1Od7_6FDY0/maxresdefault.jpg"
categories:
  - projects
  - Learning
tags:
  - Android
  - Mobile
  - Java
  - StudyNotes
  - Concepts
  - ViewControl
  - Design
---

# Android Coding Two
---
API Calling:
---

JSON Query Example (Weather):  
http://api.openweathermap.org/data/2.5/forecast/daily?zip=92127,us&mode=JSON&units=metric&cnt=7&appid=APIKEYHERE  

Parameters:  
* 7 day forecast
* JSON
* Metric units
* 92127, USA
* My personal API Key

### HTTP Request

1. Make Request
2. Read response
3. Clean and log errors

Two clients available: HttpUrlConnection or HttpClient

*adb logcat* prints errors and also exists on the Android Device Monitor
Can filter out error tags in DM

Error Logging
---
| Log Levels | Log API |
| --- | --- |
| Error | Log.e(String tag, String msg) |
| Warn | Log.w (...) |
| Info | Log.i (...) |
| Debug | Log.d (...) |
| Verbose | Log.v (...) |

Threads
---
Main Thread
* UI thread + user input and output
* Cannot run network requests

Background Thread
* Long running work
* Read and write from/to databases

Android uses the **AsyncTask** class to simply background thread creation and UI thread synchronization
