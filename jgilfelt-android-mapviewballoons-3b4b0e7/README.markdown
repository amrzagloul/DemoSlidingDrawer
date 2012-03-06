Android MapView Balloons
========================

This project provides an easy way to annotate map overlay items with a simple information balloon when using the Android Maps external library (`com.google.android.maps`). It consists of `BalloonOverlayView`, a view representing the balloon that is displayed over your `MapView` and `BalloonItemizedOverlay`, an abstract extension of `ItemizedOverlay`.

![Balloon](http://jeffgilfelt.com/mapviewballoons/device-balloon1.png "Balloon")&nbsp;
![Balloon Pressed](http://jeffgilfelt.com/mapviewballoons/device-balloon2.png "Balloon Pressed")&nbsp;
![hdpi](http://jeffgilfelt.com/mapviewballoons/device-balloon-hdpi.png "hdpi")

The presentation of the balloons was mostly reverse engineered from Google's Places Directory application. 

Basic Usage
-----------

Create a subclass of `BalloonItemizedOverlay` in the same way you would do for the base `ItemizedOverlay` class. Rather than overriding `onTap()` (which is already implemented and final in the subclass to invoke the balloon view display for each item tap), you override `onBalloonTap()` to handle a screen tap event on the balloon itself.

The data displayed in each balloon is mapped to the title and snippet arguments you provide to the constructor of each `OverlayItem`.

The repository contains a working sample application project which fully demonstrates its usage.

Custom Layouts
--------------

![custom](http://jeffgilfelt.com/mapviewballoons/device-balloon-custom.png "custom")

You can create your own balloon look & feel and custom data mapping by creating a subclass of `BalloonOverlayView` with a generic type that extends `OverlayItem`. Override the `setupView(Context context, final ViewGroup parent)` method and inflate your own XML layout using `parent` as the root of its view hierachy.

One caveat with custom layouts is that you MUST include a layout container that represents the clickable action area of your balloon whose id property is `android:id="@id/balloon_inner_layout"`.

An example custom layout and data mapping which downloads an image from the internet and displays it in an ImageView is included in the sample application project.

Implementation
--------------

As of version 1.1, android-mapviewballoons is an Android Library project. Refer to **Referencing a library project** in [this document](http://developer.android.com/guide/developing/projects/projects-eclipse.html#ReferencingLibraryProject) for instructions on how to include it in your own Android project. Ensure you have the latest Android SDK, tools and Eclipse plugin installed.

To install the library and sample project in Eclipse:

- Select **File, Import, Existing projects into workspace...**
- Select the root folder where you cloned/downloaded the repository to import both projects.
- Use **Project - Clean** if there are any errors.

Whats Missing?
--------------

* Long press support
* Trackball/cursor support

Credits
-------

Author: Jeff Gilfelt

The code in this project is licensed under the Apache Software License 2.0.
<br />
Copyright (c) 2011 readyState Software Ltd.
