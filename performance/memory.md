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
- `java -jar [Equilinox jar] -Xmx 1024`

## Steps to Fix Performance: The Guide

### Step 1: Install Java

Equilinox is a game made with Java. It comes with its own version of Java, but that version won't work for this guide. You will need a standalone version of Java 8 from Oracle. Make sure you get the 64-bit version. (unless your OS is 32-bit, but that is highly unlikely). If you already have installed standalone Java, you should be good to go.

The version of Java recommended above is a safe choice. Depending on your needs, you may have success installing a different version of Java. This carries its own risks, and is beyond the scope of this guide, but is discussed in the Appendix.

### Step 2: Locate Java and Equilinox

You will need to know the full file paths for your currently installed version of Java and Equilinox in order to use them later.

### Step 3: Choose bash or Powershell

From this step forward, you will need to decide what command line program to use.

If you are on Linux/Mac, the default command line program comes with bash, which is covered by this guide.

This guide also covers Powershell, which is one of the default command line programs shipped with Windows.

Figure out how to run your command line program of choice, then close the program and move on to the next step.

### Step 4: Create a Tool to Run Equilinox with More Memory

In the folder where your Equilinox program is located, create a file called "Equilinox_launch.sh" if you are using bash, or "Equilinox_launch.bat" if you are using Powershell.

Open the new file in a text editor and type one of the following:

**Equilinox_launch.sh (bash):**

~~~
export PATH="/path/to/java/installation":$PATH
java -jar EquilinoxWindows.jar -Xmx 1024
~~~

**Equilinox_launch.bat (Powershell):**

~~~
SET PATH=P:\ath\to\java\installation;%PATH%
java -jar EquilinoxWindows.jar -Xmx 1024
~~~

Replace `path/to/java/installation` with the folder containing the Java program (java.exe on Windows).

Replace `EquilinoxWindows.jar` as applicable for your Equilinox installation.

Once you have typed this, save the file.

What does this file do? The first line temporarily helps your command line find Java. The second line tells Java to run Equilinox with up to 1024 megabytes of RAM, rather than the 256 megabytes maximum Equilinox usually uses. Other values to consider are 512 for machines with little RAM to spare, or 1536 if Equilinox's memory usage is still hovering near the max.

So, why might Equilinox need more RAM? Java programs like Equilinox use garbage collection to manage memory usage. The lower the max RAM, the harder the garbage collector must work to keep RAM usage under the max value, which can cause lag spikes and increased CPU usage. In addition, there may be situations where Equilinox simply needs more than 256 megabytes of RAM to run.

### Step 5: Run the game

This step should be done each time you want to run Equilinox.

Open your command line program of choice. If you are on Windows and have dedicated graphics (AMD/Nvidia), you should open the command line program in a special way: by right-clicking on the command line program and selecting "Run With Graphics Processor" > AMD or Nvidia. This will cause the command line program, and any programs originating from it, to use that graphics processor.

Next, you should navigate your command line to your Equilinox folder, by typing the following command and pressing enter:

**Go to Equilinox Folder (bash and Powershell):**

~~~
cd path/to/equilinox
~~~

On Powershell, the path must have backslashes, not forward-slashes.

As a sanity check, see if you are in the right folder.

**See Equilinox Folder directory contents (bash and Powershell)**

~~~
ls
~~~

Your command line should output EquilinoxWindows.jar (or the equivalent for Mac or Linux), the Equilinox_launch file you created, and some other Equilinox-related files and folders.

Finally, run Equilinox using your tool.

**Run Equilinox_launch.sh (bash)**

~~~
./Equilinox_launch.sh
~~~

**Run Equilinox_launch.bat (Powershell)**

~~~
./Equilinox_launch.bat
~~~

When in your world, you should see RAM usage for Equilinox be above 256, but below the max value you have set. In Task Manager or equivalent, the program will not be called Equilinox, and instead will just be called Java.

## Appendix

### Alternative Version of Java

An Equilinox mod developer recommends using OpenJDK, with Java 11. OpenJDK is effectively the same as Oracle's official Java, but may contain additional fixes:

https://github.com/EquilinoxModKitProject/Equilinox-Mod-Kit/wiki/Installing-Java

Discussion of an alternative Java 8 version, using OpenJ9, in the Modded Minecraft community. It has risks, but may improve performance:

https://www.reddit.com/r/feedthebeast/comments/as6p87/java_vms_and_you_how_to_reduce_your_ram_and_cpu/

### Java on your system path

If you have permanently added Java to your system PATH, you can omit the first line in your Equilinox_launch tool. Note that you can only do this with one Java version.
