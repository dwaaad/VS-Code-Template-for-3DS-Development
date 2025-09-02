# VS Code Template for devkitPro 3DS Development 
Premade VS Code configuration files to aid in devkitPro 3DS development.

If you've been struggling with setting up VS Code with devkitPro, such as devkitPro libraries not picking up etc, this should solve all your issues assuming you installed devkitPro with the official Windows [installer](https://github.com/devkitPro/installer/releases/latest).

# Setup
> [!NOTE]
> This assumes you have already setup devkitPro for Windows OS. A small guide I'd like to recommend is this [Nintendo 3DS Homebrewing - Getting Started Guide By Drake Rochelle](https://gbatemp.net/threads/3ds-homebrew-development-getting-started-guide.666095/)

The config files will prompt VS Code to automatically build *(using "make")* and run the resulting `.3dsx` file in a 3DS emulator, which you have to link yourself in the [`launch.json`](https://github.com/dwaaad/VS-Code-Template-for-3DS-Development/blob/main/template/.vscode/launch.json) file.
Put your path to `.exe` there and you should be good to go!


If VS Code still doesn't recognise the libraries, you can edit the [C/C++ extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) `settings.json` to include:
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
