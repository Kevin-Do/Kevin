---
layout: post
title: "Android AI Mapping Application"
image: "https://farm3.staticflickr.com/2101/2372486734_175bd3c55e_b.jpg"
categories:
  - IEEE
  - projects
  - mobile
tags:
  - Android
  - Mobile
  - Java
  - GoogleMapsAPI
---

# Android Coding
---
```

The weight value is a number that specifies the amount of remaining space each view should consume, relative to the amount consumed by sibling views. This works kind of like the amount of ingredients in a drink recipe: "2 parts soda, 1 part syrup" means two-thirds of the drink is soda. For example, if you give one view a weight of 2 and another one a weight of 1, the sum is 3, so the first view fills 2/3 of the remaining space and the second view fills the rest. If you add a third view and give it a weight of 1, then the first view (with weight of 2) now gets 1/2 the remaining space, while the remaining two each get 1/4.

The default weight for all views is 0, so if you specify any weight value greater than 0 to only one view, then that view fills whatever space remains after all views are given the space they require

```
---
```
The call getIntent() grabs the intent that started the activity. Every Activity is invoked by an Intent, regardless of how the user navigated there. The call getStringExtra() retrieves the data from the first activity.
```

![activity call backs](https://developer.android.com/images/training/basics/basic-lifecycle.png)

When the user selects your app icon from the Home screen, the system calls the onCreate() method for the Activity in your app that you've declared to be the "launcher" (or "main") activity. This is the activity that serves as the main entry point to your app's user interface.

You can define which activity to use as the main activity in the Android manifest file, AndroidManifest.xml, which is at the root of your project directory.

The main activity for your app must be declared in the manifest with an <intent-filter> that includes the MAIN action and LAUNCHER category. For example:
```
<activity android:name=".MainActivity" android:label="@string/app_name">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
Note: When you create a new Android project with the Android SDK tools, the default project files include an Activity class that's declared in the manifest with this filter.
```
If either the MAIN action or LAUNCHER category are not declared for one of your activities, then your app icon will not appear in the Home screen's list of apps.
