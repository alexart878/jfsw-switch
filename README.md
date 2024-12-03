# JFSW for Nintendo Switch

This is port of [Jonathon Fowler's SW](https://github.com/jonof/jfsw), and firstly, i would like to thank him, as well as 2 people, without whose work this project would not have been possible:
- [Rinnegatamante](https://github.com/Rinnegatamante) for his fix of polymost rendering bug in his [PS Vita port](https://github.com/Rinnegatamante/jfsw-vita)
- [MrHuu](https://github.com/MrHuu) for his [3DS port](https://github.com/MrHuu/jfsw-3ds), which was my point of inspiration

## Key differences

- Switch custom controls reading system, as sdl, for some reason, can't produce input events
- "Hotplug" switch between OG game and WD addon (still need restart game, though)
- Support for Polymost and OpenGL rendering (true 3d with option to use classic 8bpp)
- While using SwitchBrew's [libnx](https://github.com/switchbrew/libnx), keyboard inputs (save) and (un)dock mode supported
- Modified build files and scripts, to bring fluid devkit toolchain integration

## Controls

I used most comfortable layout (IMHO, can be remapped through game's controls menu):

- Left stick: moving
- Right stick: camera control
- A: fire
- B: crouch
- X: jump
- Y: interact
- L1/R1: switch weapons
- L2: jump
- R2: fire
- L3: none
- R3: none
- Minus: map
- Plus: game menu
- Dpad up: use inventory item
- Dpad down: holster weapon
- Dpad left/right: switch inventory items

NOTE: axis scale and saturation can be set in game's controller menu

## Installation

- Go to releases page, and grab latest .nro executable
- Obtain legal copy of Shadow Warrior (i used Steam version), files in:
```
"Steam\steamapps\common\Shadow Warrior Classic\gameroot\classic"
```
- Create "jfsw" folder somewhere on your SD card
- Place "sw.grp", "wt.grp" and TrackXX.ogg from MUSIC to it
- Place "jfsw.nro" in that folder, too
- I recommend to launch game in non-applet mode, because otherwise worked, but not tested
- OPTIONAL: if you want to create forwarder DO NOT USE video capture - it causes CPU Boost bug after closing app

## Build

Those, who want improve something, or just compile by their own, should follow next steps:

- Setup switch homebrew enviroment, more info: [link](https://devkitpro.org/wiki/Getting_Started)
- Download switch-sdl2 packages
- For make:
```
cd jfsw-switch
make -f Makefile.switch
```
- For clean:
```
cd jfsw-switch
make -f Makefile.switch clean
```
- Also, if you want to modify shaders, or use another tools, you can (bin2c example):
```
cd jfsw-switch
/usr/bin/g++ $JFTOOLS/bin2c.cc -o bin2c
./bin2c -text $JFSRC/polymost_fs.glsl default_polymost_fs_glsl > $JFSRC/polymost_fs.c 
```
