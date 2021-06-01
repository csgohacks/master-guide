# VAC-bypass

VAC bypasser is a VAC bypass module that blocks VAC from running. This could allow any detected cheats \(i.e: OTC v3\) to be injected to the game witout the risk of getting VAC detection banned.

## How does it work?

According to the github description, it's trying to make the function `Utils_getSystemInformation` inside VAC to return `false`, so it will stop scanning for cheats.

## How to install it?

* Warning: Installing VAC-bypass requires compiling the source code from your own! Please install Visual Studio 2019 with Visual C++ toolchain first.
* Also antivirsus software will report a false alarm on your compiled program. You can ignore as it is safe to use. However this only applies to the program you compiled from the github source.

First, head to the VAC-bypass loader's [github page](https://github.com/danielkrupinski/VAC-Bypass-Loader):

Then download the project to youre folder. After that, fire up the .sln file:

Once the project is fully loaded, change build configuration on top of the menu bar to Release \| x86UI.AddCheckbox\( \[ path \], name \);

Finally, simply press Build solution on solution explorer.

Once the compile is successfully, head to the Release folder on your downloaded project file:

Then click on "VAC-bypass-loader.exe". Make sure you have closed steam before opening it due to the program will inject the module into steam.

Once it is successful, you will see a window pop up that says "VAC-bypass loaded successfully!". Simply click on enter and steam login window will show up. Enter your username and password as usual.

And vollia! You an inject any VAC-detected cheats as you want. However once you shut down steam, you have to re-run the loader again.

