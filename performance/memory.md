# Method to Fix Lag Spikes/Crashes in Equilinox

Link to Equilinox: https://equilinox.com/

## Introduction

Are you experiencing the following issues when playing Equilinox?:

- The game freezes or slows down at regular intervals, especially on larger worlds
- The game crashes, especially on larger worlds
- The game crashes only some of the time, with no apparent explanation

If so, this guide may be able to help!

This guide will show you how to launch Equilinox in a way that makes it faster and more stable, by increasing the Java memory allocation. There are a few downsides:

- If you bought Equilinox through Steam, Steam features (for example, recording number of hours played) may not work.
- You need to do a bit more work to run Equilinox to use high performance AMD/Nvidia graphics. Currently this guide only covers how to fix this on Windows (contributions welcome, assuming Mac/Linux have that issue)

This guide has been tested on Equilinox 1.6.0, but should in principle work with any version. No mods are required. When using this launch technique, you will see higher RAM usage when Equilinox is running.

## Summary

- Install standalone Java if you don't have it
- Run your command line, making it use your dedicated GPU if possible
- Change Equilinox Steam properties to `"C:\your-path-to-java\bin\javaw.exe" -jar EquilinoxWindows.jar %command%`

## Steps to Fix Performance: The Guide

### Step 1: Install Java

Equilinox is a game made with Java. It comes with its own version of Java, but that version won't work for this guide. There are multiple sources available for the most recent Java version, but the current recommended one is AdoptOpenJDK to be found at https://adoptium.net/. Make sure you get the 64-bit version. (unless your OS is 32-bit, but that is highly unlikely). If you already have installed standalone Java, you should be good to go.

The most recent Java version is a much newer version than the old one that Equilinox uses, but should cause no issues when running the game. In case it does, it's pretty simple to revert to that version again.

### Step 2: Locate Java

You will need to know the full file path for the version of Java you just installed.

### Step 3: Change Equilinox' properties in Steam

Right-click Equilinox in the list of games in your Steam library, and select "Properties". A new window will open which should have a text field with the label "Launch options" in the middle. In this text field, enter the following text, replacing the path to Java that you determined in the step before: `"C:\your-path-to-java\bin\javaw.exe" -jar EquilinoxWindows.jar %command%`

### Step 3.1: (Optional) Give Equilinox access to more memory

This is a slightly advanced step and shouldn't normally be necessary. By default, the newer Java versions use 25% of your computers memory. As long as you have 4GB or more RAM, you should have more than enough to run Equilinox with that. So don't worry if you have 4GB or more. However, on certain low-end machines with less RAM, you may want to increase the RAM dedicated to Equilinox to something larger than 25% of your total memory.

To do that, navigate to Equilinox install directory. Open the file `EquilinoxWindows.jar` with 7zip. Navigate to the `META-INF` folder inside the zip. Select `MANIFEST.MF` and right-click -> Edit. Where it says `Launcher-VM-Args: `, add `-Xmx1024m`, so that the line looks like `Launcher-VM-Args: -Xmx1024m`, then save the file. 7zip should now ask you if you want to update the file in the zip, say yes.

You can also change the 1024 to any amount of memory you want to allocate to Equilinox.

### Step 4: Start Equilinox

You can simply start Equilinox as normal through Steam, and the new Java version you specified should be used instead, hopefully greatly increasing performance.
