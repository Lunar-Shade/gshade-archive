# How To Move To ReShade From GShade
*(a guide by [rika](https://twitter.com/lostkagamine) (@lostkagamine). tested, should work fine.)*
*Snatched from https://gist.github.com/ry00001/3e2e63b986cb0c673645ea42ffafcc26 for archival purposes*

([Korean version / 한국어 버전](https://gist.github.com/hibiyasleep/142bfe45c85824d255ad098a63bd8780))

**If you are having issues like the screen turning black, read the mini-FAQ at the bottom of this document!**

## 0. Don't uninstall GShade yet!
Uninstalling GShade removes the `gshade-shaders` folder which contains all the content. It does not remove GShade's executable file. This guide will help you do that.  

You can uninstall it right before installing ReShade. Uninstalling it after will break ReShade!

## 1. Identify your `game` folder, and open it in Windows Explorer.
This is where you installed FFXIV. It contains `ffxiv_dx11.exe`. If you can't find it, look at the FAQ.

## 2. Back up the `C:\Program Files\GShade\gshade-shaders` and `game\gshade-presets` folder.
This contains GShade's shaders and presets, obviously. If you have lost it, [download a backup of the full shader and preset package here.](https://kagamine.tech/shade/gshade.zip)

## 3. Delete `dxgi.dll` in the `game` folder. (If there's a file called `d3d11.dll` there, delete that too.)
***DO NOT DELETE THIS FILE IF IT'S IN THE `C:\Windows` FOLDER! IF YOU ONLY HAVE A `dxgi.dll` OR `d3d11.dll` FILE THERE, SKIP THIS STEP! YOU MUST BE IN THE `game` FOLDER! <ins>DELETING THE WRONG FILE WILL CAUSE WINDOWS TO STOP WORKING!</ins>***

**Note: this file might appear as just `dxgi` or `d3d11`. <ins>If it's present within the FFXIV `game` folder</ins>, you are safe to delete it.**

This is GShade's executable file. The uninstaller does not delete this file, which is mildly suspicious, as it will continue to load into your game after uninstallation.

You can uninstall GShade at this point, if you have backed up its folders.

## 4. [Install ReShade](https://reshade.me) to `ffxiv_dx11.exe`.
**You must install the version with full add-on support. The regular build of ReShade will not work with FFXIV.**

**Do not tick the options to install the shader packs from vanilla ReShade during the install process. Only make sure to install the ReShade default shaders.**

If that link is still dead when you read this, [use this file](https://cdn.discordapp.com/attachments/1072202729692340245/1072204165004152942/ReShade_Setup_5.6.0_Addon.exe). It's the exact same file as the one you would download from ReShade. <sup>[1]</sup>  
It will pop up a scary-looking message box warning of bans when you first launch. Just ignore it; ReShade can get you banned just as much as GShade can, aka it can't.  
Don't install into `ffxiv.exe`, as that's the DirectX 9 version of the game.

## 5. Replace the contents of the `reshade-shaders` folder with `gshade-shaders`'s contents.
If you don't have a `reshade-shaders` for some reason, copy and paste `gshade-shaders` and rename it to `reshade-shaders`.

## 6. Copy and rename the `gshade-presets` folder to `reshade-presets` in the `game` folder.
This is to make presets work again. Despite what GShade team might have told you, you don't need GShade for presets.

## 7. Download [this ZIP file](https://kagamine.tech/shade/fixed_shaders.zip), extract it, and move all of those .fx/.fxh files into your `reshade-shaders\Shaders` folder.
**Remember to overwrite files if it asks.**

This will fix compatibility issues, add new tools (notably `FFKeepUI` and `FFRestoreUI`) and make some shaders compile.

## 8. You're done. Launch the game.
Enjoy not using software full of malware, and enjoy never updating again. If you find this useful, [please throw me something](https://paypal.me/ry00001), I don't have much money at all.

## Mini-FAQ

### There's no `gshade-shaders` folder. What do I do?
It's `Program Files\GShade\gshade-shaders`. If you have uninstalled GShade, [download a backup of the full shader and preset package here.](https://kagamine.tech/shade/gshade.zip)

### Where's the `game` folder?
It's probably in `C:\Program Files (x86)\SquareEnix\FINAL FANTASY XIV - A Realm Reborn\game`, and if you're on Steam, it's `Steam\steamapps\common\FINAL FANTASY XIV Online\game`.

### I'm looking for `reshade-shaders` but I can't find it.
If ReShade's installer did not create it, just copy-paste `gshade-shaders` and rename it to `reshade-shaders`.

### `dxgi.dll` is not next to the game executable!
You might have already uninstalled GShade. Ignore and continue, but GShade might be required to construct an appropriate `reshade-shaders` folder.

### How do I open the ReShade menu?
Maybe press <kbd>Home</kbd>. ReShade will tell you when you run the game.

The <kbd>Home</kbd> key may be labeled <kbd>Pos1</kbd> (in German) or <kbd>Inicio</kbd> (in Spanish). It's the same key.

### But I don't have a <kbd>Home</kbd> key on the keyboard!
If you're on a laptop, try pressing <kbd>Fn</kbd> and <kbd>←</kbd> at the same time.

### Do GShade presets work?
They should. If they don't, we can't know for certain why, because GShade is closed-source.
Project Crystal presets appear to be especially problematic right now, and thus may not function.

### My screen is going black when using Project Crystal presets / There are no (shaders/presets) listed.
Add - verbatim - `.\reshade-shaders\Shaders\**` to the shader search path in ReShade settings, and your texture search path to `.\reshade-shaders\Textures\**`. You can use the ReShade file explorer to load your presets.

### The screen's colours look super weird! / There are two of each shader in the list!
Replace the entire contents of `reshade-shaders` with the contents of `gshade-shaders`, leaving nothing behind, and then re-apply the `fixed_shaders.zip` file you downloaded in Step 7.

### Why do some shaders not compile?
Please report these shaders in [this Discord server](https://discord.gg/9kQTCB5Xwh), linking the .fx file **and the full text of the error message.**

### Bard, Astrologian, Monk and Dancer's job gauges look weird!
This is a known issue. There is no fix for it at this time. Use the simple mode gauges.

### Project Crystal presets are far too dark.
You will need to place Technicolor 2 in the middle of the shader stack, and tweak it to your liking.

## References
1: MD5sum of `ReShade_Setup_5.6.0_Addon.exe`: `16bbf254d1a6df02bede993725ad680c`. SHA256sum of the same file: `855a118eed4838b7522450ffed21a0b1b7e20dbee4eb2295766cbfd229947b3b`.

## Special Thanks
 - [NotNite](https://NotNite.com) for starting all of this in the first place.
 - [crosire](https://patreon.com/crosire) for the [ReShade project](https://reshade.me).
 - [The ReShade Discord server](https://discord.gg/PrwndfH) for all the help.