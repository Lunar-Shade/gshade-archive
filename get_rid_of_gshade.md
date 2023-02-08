# A step by step guide to get rid of gshade

Because the original author and owner of GShade decided to be cringe and not only introduce malware, but make it realistically impossible to uninstall without deleting files manually because the uninstaller is dogwater. This is a step by step guide to get rid of GShade.

By the way, I have a fork of a gist file I found that will help you transition from GShade to Reshade. You can find it under [gshade_to_reshade.md](https://github.com/Lunar-Shade/gshade-archive/blob/master/gshade_to_reshade.md)

## A. Uninstall GShade Root Files

*Oh a side note, uninstall GShade will get rid of the Gshade presets and shaders, so make sure you have a backup of them somewhere if you plan to use them later :)*

Since the actual uninstaller of GShade is actually just the installer (so there isnt an uninstaller, how nice of them!) you will have to delete the files manually. To do this, open up your file explorer and go to the following directories and remove them: 

- %ProgramFiles%\GShade
- %ProgramData%\GShade
- %Public%\GShade Backups
- %Public%\GShade Custom Shaders

## B. Uninstall GShade From Games

You will have to repeat this step for every game you had GShade installed in. Convient eh?

- gshade-addons
- gshade-presets
- gshade-shaders
- d3d10.dll
- d3d10core.dll
- d3d11.dll
- d3d12.dll
- d3d9.dll
- dinput8.dll
- dxgi.dll
- GShade.ini
- GShade.log

⚠️ **WARNING:** Do not remove any of the `.dll` if they are **OUTSIDE** of a game that GShade installed. You **__WILL__** break Windows!

If you are using a game launcher like Steam, Origin, Epic Games, etc. I recommend running a file integrity check on the game to make sure you got all the files and didn't accidentally delete any important files.

## C. Remove GShade From Registry

Well GShade apparently needs to set values in registry and not a config file, because why not. Anyways, you will need to open the registry editor. 
To do that, press the Windows key AND `R` at the same time (WIN+R) and type in "regedit" and press enter. You will be asked for permission to open the registry editor, click yes.

**WARNING**! The registry editor is not a toy. Do not mess around with anything but removing the GShade registry keys. If you mess up, you can break your computer. If you are not sure what you are doing, do not mess with the registry editor.

To remove the GShade registry keys, go to the following directory: `HKEY_LOCAL_MACHINE\SOFTWARE\GShade` and delete the folder and keys. 
This is what the folder should look like: 
![](https://img.eramsorgr.me/userdata/regedit_CRrjhyal0Q.png)

Delete the folder as shown in the image below:
![](https://img.eramsorgr.me/userdata/regedit_XxxOvHYbPN.png)

Confirm the deletion by clicking yes on the popup window.

## Congratulations!

You have successfully removed GShade from your computer. Now go use Reshade instead, it's better and doesn't have malware.

Check out the file [gshade_to_reshade.md](https://github.com/Lunar-Shade/gshade-archive/blob/master/gshade_to_reshade.md) that will help you transition from GShade to Reshade.
