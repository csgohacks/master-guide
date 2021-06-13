# Osiris

Osiris is an open-source legit cheat for CS:GO. It is commonly used as a base for pasted cheats. In this guide by BaconatorPizza, is going to teach how to compile osiris from source.

***

## Step 1: Downloading Needed Items

Download the [Osiris source](https://github.com/danielkrupinski/Osiris). Osiris is one of the most stable open source cheats with the most features.

Download [SigBench](https://www.unknowncheats.me/forum/anti-cheat-bypass/167449-sigbench-test-binary-signature-scans.html), we will use it to compare signatures.

Download any source code obfuscator that works decently well for C++.

Lastly, download [the VMProtect demo](https://vmpsoft.com/purchase/buy-online/).

***

## Step 2: Setting Up

Extract the .ZIP file you downloaded with the Osiris source inside of it. Double click the .sln file inside of the folder you extract. This will open Visual Studio.

![Failed to load image](https://preview.redd.it/1ec9jyqmthi51.png?width=658&format=png&auto=webp&s=6f354cdbff8ddc923a9bea990ad43305fa0feeb4)

Right click the text that says 'Osiris' on the sidebar, and click Properties. Click on the arrow next to C/C++, click on Optimization, and set Optimization to 'Disabled (/Od)'.

Click OK.

![Failed to load image](https://preview.redd.it/7uc4dzumr8y31.png?width=846&format=png&auto=webp&s=a98d79a9cdd273c142cfe4c6101f10ab63119835)

Then, in the top bar, change Debug to Release, and change the thing next to it to x86 (it should be x86 by default though).

![Failed to load image](https://preview.redd.it/pyn1lr6yuhi51.png?width=320&format=png&auto=webp&s=627d3c4b81f3390e18a3457039f18872eec24e93)

Press Local Windows Debugger (or whatever it says for you), and wait for it to build. Then go into your project folder again, and then into Release, you should see a file called Osiris.dll. Copy that file and paste it in another directory for later, like your Desktop.

***

## Step 3: Removing VMT Hooking

On the sidebar, you will see a folder called Hooks, open that up and delete VmtSwap.cpp, VmtSwap.h, VmtHook.cpp and VmtHook.h.

Next go into Header Files, and open Hooks.h. You will see 2 lines towards the top:

```cpp
#include "Hooks/VmtHook.h"

#include "Hooks.VmtSwap.h"
```

Delete these 2 lines.

You will also see a line saying using `using HookType = VmtSwap;`, delete that line too.

You are done removing VMT hooking! Onto the next step.

***

## Step 4: Removing Features

Go into the folder called hacks, and delete all the files for features you will not use. Delete the .cpp and .h files. If you aren't too much of a skid, you can go into Visuals.cpp and delete the functions for visuals you will not use.

Next go into Source Files, and open up Config.cpp. You should have a ton of errors. Simply delete the lines that are causing the errors. (ex. If you have an error on line 15, delete line 15).

Go into Hooks.cpp, and do the same. Lastly, do the same for GUI.cpp.

Press Local Windows Debugger again, because sometimes (or at least for me), certain errors don't show up until you compile. Also, if it says the error is in GUI.obj, Hooks.obj or etc, open up file-with-error.cpp. If it does not show the error in there, open up file-with-error.h.

You are done removing features! Onto the next step.

***

## Step 5: Renaming Features

Of course, every file/feature has a name. VAC however, can scan your cheats code and check for those names (and just other aspects of the code). If it matches known cheat code (which it will, Osiris and other open source cheats are most definitely detected), it will ban you.

So what we must do, is rename things to combat this. This won't totally solve our problem, but it still helps a bit. On top of that, it will change up the signature a little bit, which is nice!

For example, rename Backtrack.cpp and Backtrack.h to AimRewind (or something like that). Keep in mind you must also change this in all references to the file, like when another file is doing `#include <Hacks/Backtrack.cpp>`.

In places like GUI.cpp, the string containing what it will actually display as the name doesn't need to have it's value modified. However, it's a smart idea to rename the variable itself.

Once you have done this for most things in the cheat, move onto the next step!

***

## Step 6: Modifying Code

You know of how I said VAC scans your cheat against known cheat code? Well renaming things on it's own isn't enough. We need to do more!

Even doing little things such as replacing `currentTargetXPos = 52.234` with `currentTargetXPos = 50 + 2.234` (or something like that lol, just an example I came up with) will not only change the signature, but combat VAC detection!

So go around doing this. It will probably take a while. However, if you do it enough, it will help a lot with making your paste undetected.

Once you have done this for most things in the cheat, move onto the next step!

***

## Step 7: Compiling

This last step will help you compile your cheat.

First of all, if you did decide to use a source code obfuscator, make sure you use that first before you compile because it probably wont work on your finished build of the cheat. Once you have ran it, press Local Windows Debugger to compile.

Next, go into your project folder, Release, and rename the DLL inside to whatever you want your cheat to be called (ex. RainbowWare).

If you decided to get VMProtect, run that on your DLL. Take the outputted one, and now we will test the signatures!

Open up SigBench. In the first slot, input the original DLL from earlier. In the second slot, input your new one. Press benchmark.

There should be a pretty big difference in signatures, and it should look something like this: ![https://imgur.com/6kOpTCv](https://i.imgur.com/6kOpTCv.png)

You are now done!

***

## Step 8: Injecting

Find any decent injector (like [Extreme Injector](http://www.extreme-injector.com/#:~:text=Extreme%20Injector%20is%20a%20small,the%20hacking%20of%20computer%20games.), [Xenos](https://www.unknowncheats.me/forum/general-programming-and-reversing/124013-xenos-injector-v2-3-2-a.html) or the [GH Injector](https://guidedhacking.com/resources/guided-hacking-dll-injector.4/), really anything with manual mapping). Select your finished DLL, and inject!

I also reccomend you use the [VAC Bypass Loader](https://matt12945.gitbook.io/csgo-subreddit/free-and-pastes/vacbypass) as it will also greatly reduce your chances of being banned with any cheat.

Don't share the cheat with very many people or VAC may start detecting it. Also, do these steps again every now and then to change the signature and get any new updates your source may have.

Enjoy!
