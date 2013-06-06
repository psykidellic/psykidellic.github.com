---
layout: post
published: true
title: "Installing and developing Android applications on command line in OS X"
date: "Tue Jul 03 21:40:43 -0700 2012"
---

Who wants Eclipse when you can use vim like a `vimmer`. This document will help
you get ready and develop Android applications from command line.

As usual, without saying - if you have not yet, [Get
Homebrew](http://mxcl.github.com/homebrew/). This post also assumes that you
have installed the command line tools from XCode and
[Ant](http://ant.apache.org/).

Steps
=====

Install Android SDK
-------------------

`brew install android-sdk`

{% highlight console %}
==> Downloading http://dl.google.com/android/android-sdk_r20-macosx.zip
######################################################################## 100.0%\
==> Caveats
Now run the `android' tool to install the actual SDK stuff.

The Android-SDK location for IDEs such as Eclipse, IntelliJ etc is:
  /usr/local/Cellar/android-sdk/r20

 you will have to install the platform-tools and docs every time this formula
 updates. if you want to try and fix this then see the comment in this formula.

 you may need to add the following to your .bashrc:
   export ANDROID_SDK_ROOT=/usr/local/Cellar/android-sdk/r20
   ==> Summary
   /usr/local/Cellar/android-sdk/r20: 444 files, 70M, built in 2.1 minutes
{% endhighlight %}

This will only install the _Android SDK Manager_. None of the actual SDK or
anything is installed.

As suggested by Homebrewa, add the lines to your `.bashrc`. You can start the
manager by typing `android`. Generally, I like to install a version from every
major release (so that I can quickly debug things out if necessary). You can
choose whichever version you want.

Bootstrap your project for specific target
------------------------------------------

Remember, we had installed multiple version of SDK. We have to setup an Android
Virtual Device for it and setup the project for the target.

`android list target`

{% highlight bash %}
Available Android targets:
id: 1 or "android-10"
     Name: Android 2.3.3
     Type: Platform
     API level: 10
     Revision: 2
     Skins: HVGA, QVGA, WQVGA400, WQVGA432, WVGA800 (default), WVGA854
     ABIs : armeabi
id: 2 or "android-13"
     Name: Android 3.2
     Type: Platform
     API level: 13
     Revision: 1
     Skins: WXGA (default)
     ABIs : armeabi
id: 3 or "android-15"
     Name: Android 4.0.3
     Type: Platform
     API level: 15
     Revision: 3
     Skins: HVGA, QVGA, WQVGA400, WQVGA432, WSVGA, WVGA800 (default), WVGA854, WXGA720, WXGA800
     ABIs : armeabi-v7a
id: 4 or "android-16"
     Name: Android 4.1
     Type: Platform
     API level: 16
     Revision: 1
     Skins: HVGA, QVGA, WQVGA400, WQVGA432, WSVGA, WVGA800 (default), WVGA854, WXGA720, WXGA800, WXGA800-7in
     ABIs : armeabi-v7a
{% endhighlight %}

`android create avd --target 1 --name yourprojectname`

{% highlight bash %}
$: android create avd --target 1 --name param
Auto-selecting single ABI armeabi
Android 2.3.3 is a basic Android platform.
Do you wish to create a custom hardware profile [no]
Created AVD 'param' based on Android 2.3.3, ARM (armeabi) processor,
with the following hardware config:
hw.lcd.density=240
vm.heapSize=24
hw.ramSize=256
{% endhighlight %}

Now if its a new project, you can bootstrap one by using something like:

{% highlight bash %}
android create project --name HelloWorld --activity HelloWorld --path ./
--package com.examples.helloworld --target 1
{% endhighlight %}

If you already have an Eclipse build project and you want to start doing it
right. Set it up using `android update project --target 1 --path .`

Now you can build it using `ant debug` or `ant release` and corresponding
`.apk` file will be created.

Running in the emulator
=======================

Lets start up the avd that we created before. Assuming, you named your project
"awesome", we can start the emulator `emulator -avd awesome`.

Now we can install the above built packager using the `Android Debug Bridge or
adb` by running `adb install bin/awesome-debug.apk`.

You should now see your new app in the applications list.

References
==========

* [Android Developer Site](http://developer.android.com/tools/building/building-cmdline.html)
* [http://www.aplusbi.com/?p=164](http://www.aplusbi.com/?p=164)
* [http://blog.standalonecode.com/?p=269](http://blog.standalonecode.com/?p=269)
* [http://incise.org/android-development-on-the-command-line.html](http://incise.org/android-development-on-the-command-line.html)
