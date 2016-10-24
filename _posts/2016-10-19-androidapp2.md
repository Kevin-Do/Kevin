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

**Error Logging**

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
[Documentation](https://developer.android.com/reference/android/os/AsyncTask.html)  
The three types used by an asynchronous task are the following:

* Params, the type of the parameters sent to the task upon execution.
* Progress, the type of the progress units published during the background computation.
* Result, the type of the result of the background computation.  

Not all types are always used by an asynchronous task. To mark a type as unused, simply use the type Void:

 private class MyTask extends AsyncTask<Void, Void, Void> { ... }
doInBackground() is required but onPreExecute(), onProgressUpdate(), onPostExecute() are not required.

When an asynchronous task is executed, the task goes through 4 steps:

1. onPreExecute(), invoked on the UI thread before the task is executed. This step is normally used to setup the task, for instance by showing a progress bar in the user interface.
2. doInBackground(Params...), invoked on the background thread immediately after onPreExecute() finishes executing. This step is used to perform background computation that can take a long time. The parameters of the asynchronous task are passed to this step. The result of the computation must be returned by this step and will be passed back to the last step. This step can also use publishProgress(Progress...) to publish one or more units of progress. These values are published on the UI thread, in the onProgressUpdate(Progress...) step.
3. onProgressUpdate(Progress...), invoked on the UI thread after a call to publishProgress(Progress...). The timing of the execution is undefined. This method is used to display any form of progress in the user interface while the background computation is still executing. For instance, it can be used to animate a progress bar or show logs in a text field.
4. onPostExecute(Result), invoked on the UI thread after the background computation finishes. The result of the background computation is passed to this step as a parameter.

With the ability to send messages to server and run background tasks, there is no need for a refresh button. That should only be for debugging purposes.
If thread is determined by UI activity it can interrupted and the data transfer can be stopped by a simple orientation flip.{: .notice_danger}

Because of this, AsyncTask should only be used for tasks tied to the host activity and only run for a few seconds. In the real world, network access is unlikely to run in perfectly little time. Therefore, its better to use a **service**.

Services
---
An application component without a UI that's less likely to be interrupted. Android has a specialized solution known as a Sync Adapter designed to schedule your background data syncs as efficiently as possible. You can also use Google Cloud Messenger that notifies the Sync Adapter on the server side. So there will only be updates when you know for a fact there are things to be updated.

Menu Options
---
Override the methods onCreate and OptionsMenu in order to instruct commands on how to inflate views we created in .xml and actions after buttons are clicked.

{% highlight yaml %}
public void onCreate(Bundle savedInstanceState) {
       super.onCreate(savedInstanceState);
       // Add this line in order for this fragment to handle menu events.
       setHasOptionsMenu(true);
   }

   @Override
   public void onCreateOptionsMenu(Menu menu, MenuInflater inflater) {
       inflater.inflate(R.menu.forcastfragment, menu);
   }

   @Override
   public boolean onOptionsItemSelected(MenuItem item) {
       // Handle action bar item clicks here. The action bar will
       // automatically handle clicks on the Home/Up button, so long
       // as you specify a parent activity in AndroidManifest.xml.
       int id = item.getItemId();
       if (id == R.id.action_refresh) {
           return true;
       }
       return super.onOptionsItemSelected(item);
   }
{% endhighlight %}

Permissions
---
[Security Section](https://developer.android.com/guide/topics/security/permissions.html)  
[Permission List](https://developer.android.com/reference/android/Manifest.permission.html)  

Which of the following activities can only be done after declaring a user-permission in the manifest?
* Taking a photo
* Making a phone call
* Accessing contact data
* Retrieving current location

**The answer is:  Retrieving current location**  
The other activities rely on other applications *(phone, contacts, camera)* and the user can cancel this action. Current location comes from the UI thread and requires explicit user permission.

What permission must you add to the manifest in order to declare the Internet permission?  
**The answer is: android.permission.INTERNET**
