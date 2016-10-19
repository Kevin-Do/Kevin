---
layout: post
title: "Android Application Concepts"
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

# Android Coding One
---
![process](http://i.imgur.com/y7yyFiM.png)

* Android Studio
  * SDK - Target and Minimum
  * Emulators vs. Real Devices
  * Gradle
  * Application
  * Activity
  * Fragment
  * Views and ViewGroups
  * Views and XML layouts
  * ListView
  * ArrAdapter

Weight Value
---
The weight value is a number that specifies the amount of remaining space each view should consume, relative to the amount consumed by sibling views. This works kind of like the amount of ingredients in a drink recipe: "2 parts soda, 1 part syrup" means two-thirds of the drink is soda. For example, if you give one view a weight of 2 and another one a weight of 1, the sum is 3, so the first view fills 2/3 of the remaining space and the second view fills the rest. If you add a third view and give it a weight of 1, then the first view (with weight of 2) now gets 1/2 the remaining space, while the remaining two each get 1/4.

The default weight for all views is 0, so if you specify any weight value greater than 0 to only one view, then that view fills whatever space remains after all views are given the space they require

Activity Call Backs
---

The call getIntent() grabs the intent that started the activity. Every Activity is invoked by an Intent, regardless of how the user navigated there. The call getStringExtra() retrieves the data from the first activity.


![activity call backs](https://developer.android.com/images/training/basics/basic-lifecycle.png)

When the user selects your app icon from the Home screen, the system calls the onCreate() method for the Activity in your app that you've declared to be the "launcher" (or "main") activity. This is the activity that serves as the main entry point to your app's user interface.

You can define which activity to use as the main activity in the Android manifest file, AndroidManifest.xml, which is at the root of your project directory.

The main activity for your app must be declared in the manifest with an <intent-filter> that includes the MAIN action and LAUNCHER category. For example:

{% highlight yaml %}
<activity android:name=".MainActivity" android:label="@string/app_name">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
Note: When you create a new Android project with the Android SDK tools, the default project files include an Activity class that's declared in the manifest with this filter.
{% endhighlight %}

If either the MAIN action or LAUNCHER category are not declared for one of your activities, then your app icon will not appear in the Home screen's list of apps.

Create a Fragment Class
---
To create a fragment, extend the Fragment class, then override key lifecycle methods to insert your app logic, similar to the way you would with an Activity class.

One difference when creating a Fragment is that you must use the onCreateView() callback to define the layout. In fact, this is the only callback you need in order to get a fragment running.
Fragment is modular container within an activity.

Layouts
---
Linear Layout, Relative Layout, Grid Layout can dynamically adapt to any screen *(absolute is evil)*

|Layout Type | Great for... |
|---|---|
|Frame | Useful for simple layouts with a single or stack of views that fills entire content area|
| Linear | Stacking views vertically or horizontally|
|Relative | Sophisticated layout that allows relative positioning |

Scroll View: Allow scrolling through items

### Question:
50 items in list, and only 10 are visable at a time, what is minimum number of views needed to scroll through the list?

5, 10, and 50 are wrong, 12 views will allow for extra elements on either side

The ListView is a specialized control that is optimized for displaying long lists of items. It's very efficient in how it creates, recycles, and displays views, and is optimized to scroll very smoothly. It's also designed to simplify the process of adding, removing, and editing items that are to be displayed in the list -- as you'll learn in more detail later in this lesson.
(AdaptedView descendant)

match_parent does up the chain of parents for length/width

Adapters
---
Takes raw data and builds list item layout and don't create layouts until its needed.
Bind to ListView and then adapter will check for quantity and items. ListView starts at position zero and asks for the layout at position zero. Adapter creates and returns the item.

| Initialize | Parameters |
| --- | --- |
| Array Adapter | context, list item layout ID, text view ID, list of data |

Context - global information about the app environment, access to system services and resources. Use fragments containing activity as the context.
* call: getActivity()
* R.layout.list_item_parkinglot (xml file)
* R.layout.list_item_parkinglot_textview (text view to fill out)
* parkingLots (array list containing explicit data list)

![View Hierarchy](http://i.imgur.com/1Nb8hYk.png)

[Tips & Tricks](https://drive.google.com/file/d/0B1kaWbepsXZxYV9pUVJOYUcxZGc/view)
