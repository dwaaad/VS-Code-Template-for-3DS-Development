# VS Code Template for devkitPro 3DS Development 
Premade Visual Studio Code configuration files to aid in devkitPro 3DS development.

If you've been struggling to get devkitPro correctly setup with VS Code, this template will do that and more!

# Features 
- It will solve devkitPro libraries not picking up
- Automatically build from source and then emulate
- Automatically build and run on hardware.

# Setup
> [!IMPORTANT]
> This assumes you have already setup devkitPro for Windows OS. A small guide I'd like to recommend is this [Nintendo 3DS Homebrewing - Getting Started Guide By Drake Rochelle](https://gbatemp.net/threads/3ds-homebrew-development-getting-started-guide.666095/)

To use the template, all you gotta do is download the folder and rename it from "template" to your chosen project name. This will solve the libraries not being recognised. If you don't want the other automation features, you can delete both the `launch.json` and `task.json` files.

## Library Detection
Libraries should be recognised without any need to setup. However, if VS Code still doesn't recognise the libraries, you can edit the [C/C++ extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) `settings.json` to include:
```json
{
    "C_Cpp.default.includePath": [
        "${workspaceFolder}\\**",
        "C:\\devkitPro\\**",
        "C:\\devkitPro\\libctru\\include\\**",
        "C:\\devkitPro\\devkitARM\\include\\**",
        "C:\\devkitPro\\devkitARM\\arm-none-eabi\\include\\**",
        "C:\\devkitPro\\devkitARM\\lib\\gcc\\arm-none-eabi\\**",
        "C:\\devkitPro\\portlibs\\3ds\\include\\**"
    ],
}
```

## Emulation
The emulation launch task will prompt VS Code to automatically build *(using "make")* and run the resulting `.3dsx` file in a 3DS emulator, which you have to link yourself in the [`launch.json`](https://github.com/dwaaad/VS-Code-Template-for-3DS-Development/blob/main/template/.vscode/launch.json) file.
Put your path to `.exe` there and you should be good to go!

## 3DS Link
There is another configuration which will make testing on real hardware much faster. This will automate the use of the 3dslink tool which comes bundled with devkitPro's 3ds-dev environment.

### Setting the environment variable

In order to get this working I highly suggest you make the tool a system wide path variable so that it may be used from any location on the terminal.

> [!NOTE]
> If you don't want to do this for some reason, you'll have to edit the "3dslink" command to "C:\devkitPro\tools\bin\3dslink.exe" in the `launch.json`

Let's break it down:
1. First add `3dstool.exe` as an environment variable. I did this as in my User Path. The fastest way to get there is to press <kbd>🪟 Win</kbd> + <kbd>R</kbd> on your keyboard and paste `SystemPropertiesAdvanced`
3. Then press the <kbd>Environment Variables</kbd> button
4. A new window will pop up. Under "User variables for...", double click on the "Path" variable
5. Another window should open with a list of user path variables, double click on the blank space under the list and paste C:\devkitPro\tools\bin to add it to your Path
6. Press OK on all aforementioned windows
7. You can check you've done it correctly by typing in any cmd "3dslink" and hitting enter. It should output the version number with the help commands

### Usage

Now that we can actually use the tool, we must edit the `launch.json` to include our own 3DSs IP Address.
1. You can get this by opening the homebrew menu app on your modded 3DS and pressing Y (or X). You must do this everytime you would like to use 3dslink.
2. Go to the launch.json and replace `3ds.ip.address.123` with your actual IP
3. Save file changes and smile, because we're done :)

Now when we try run the project we can safely choose the option "3dslink: Build & Run on Hardware".

## Example
From here on out you can do whatever you like with these files, get creative with it and make more configs. I personally have one for my emulator of choice, one for linking to my New 2DS XL and another for my New 3DS LL: <WIP-insert-screenshots-include-little-writing-underneath-ss-with-vscodetheme>

# Licence
WIP but basically just credit me where you can please and thanks :)
