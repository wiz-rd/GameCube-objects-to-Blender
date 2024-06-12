# How to open (some) GameCube files in Blender

## Get your ISO

Get the ISO of the game you would like to dump ready. Put it wherever you would like the dump to occur. If you have the game in any other format, you should be able to use Dolphin to convert it to ISO, which is what this will assume you have.

## Dump your ISO

My recommended program to extract or dump your ISO files is [wit](https://wit.wiimm.de/). Then run the following:

`wit X <iso filename> <output location>`

*Note: on my machine, I put wit in my /usr/local/bin/ folder so that I can run it anywhere. I'm unsure if it defaults to installing machine-wide or not, but if not, make sure to run the file directly.*

I recommend outputting it to a folder.

## Ensure you have Rarcdump setup

[Rarcdump](https://github.com/mrysav/szstools) (this is the only URL I can find it at, although I'm unsure if that's where I obtained mine) is a tool used to extract .arc files to their components (.bmd, .bti, .bol, and so on). You need this to access the .bmd files that you will import into Blender.

The primary issue or hiccup you could experience with this is that rarcdump is only made for Windows, however tweaking the .cpp file will allow you to compile it for Linux. I'll try and include the .cpp file and my compiled program alongside this file.

Should my compiled script not run for you, running `g++ rarcdump_LINUX.cpp` should compile it for your system.

## Extract the files

Use Rarcdump to extract the files. On my Linux machine, I put it in the my bin, so I can run just `rarcdump %filename%.arc` and it will extract all data into a folder.

## Convert to .DAE

You'll now need to convert the newly-extracted .bmd files to .dae files so Blender can open them. There are probably other ways of doing this, but this is the best, cross-platform way I can find.

*Note: this does not seem to work with textures, however. I will need to research it further to find out why and how to work around it. [This](https://github.com/RenolY2/SuperBMD) is supposed to be a newer version of SuperBMD however it does not seem to export it as .dae files for me for some reason. Potentially because I'm on Linux, but all other file exports (the images, that is) seem to work fine (not to mention the older version of SuperBMD does work anyway), so I don't know why this is the case.*

- Windows
  
  Use [SuperBMD.exe](https://github.com/Sage-of-Mirrors/SuperBMD) (through the commandline)
  
  `SuperBMD.exe <input file>`

- Linux
  
  Use [SuperBMD.exe](https://github.com/Sage-of-Mirrors/SuperBMD) through Wine (also commandline)
  
  `wine SuperBMD.exe <input file>`



The files will be outputted to the same directory as the input file. It's kind of annoying, I know, but I tried putting `-i <input file> -o <output folder>` but that did not work, at least for me on Linux.

## Open .DAE with Blender

Just open [Blender](https://www.blender.org/), click **import**, and select **.dae**.

There's a very high chance you'll have to scale down the model dramatically in order to be able to see it. Press "**.**" on your numpad to zoom up to it (this will not work if it's too large).

# Resources

- [SZS Tools](https://github.com/mrysav/szstools), where Rarcdump is located.

- [SuperBMD - old](https://github.com/Sage-of-Mirrors/SuperBMD) the older, working version.

- [SuperBMD - new](https://github.com/RenolY2/SuperBMD) the newer, but broken (for me) version.

- [Wiimm](https://wiimm.de/) has some super useful resources.
