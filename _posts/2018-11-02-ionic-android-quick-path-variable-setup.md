---
layout: post
title:  "Fastest Android Setup for Ionic"
date:   2018-11-02
comments: true
categories: Development Ionic Android Apps Linux 
---
### THE *absolute* fastest way to build your Ionic v3/v4 app (for Android)
Ionic 4 is out *horray*, and I am testing out a new distro (shocker). Let's find out the absolute minimal steps to get Android Stuido installed and our env variables set so we can run `ionic cordova build android`.

I'm writing this down so hopefully I can write a short script to automate it.

When I last set up my local development environment to build this I remember losing over an hour. I think I can get it set up quickly this time.

# first get ionic
If you havent already done so, install `Ionic` globally. For ionic projects, you can use the system version of nodejs, but I have found using [NVM]() helps keep versions consistent across distros and throws less errors.

```
npm i -g ionic cordova
```

## Flatpak & Snap make it easy
[Snaps](https://snapcraft.io) are an awesome way to install applications in a contained space and not muck up all your dependencies. Android Studio can be isntalled as a snap, and I want to see if I can use this to build our app since installing Android Studio is large, messy, and uncontained.
```
sudo snap install android-studio --classic
ionic add platform android

```
[Similarly, Android Studio is available via Flatpak as well. In either event, once installed, run it once and install the latest Android SDK. If you need to install an earlier version, when this is all done, you can re-launch Android Studio and open the SDK manager to install older versions of the SDK.

## Set Your Env Variables
```
# Set Java 
export PATH=/snap/android-studio/current/android-studio/jre/bin/:$PATH
### Set Android SDK variable after first launch of Android Studio and SDK is installed
export ANDROID_HOME=/home/`whoami`/Android/Sdk
```
## A note on Gradle:
For some reason, the version of Gradle in the snap wasnt working for me so I installed it, and didn't need to mess with a path variable anymore.


# SUCCESS







