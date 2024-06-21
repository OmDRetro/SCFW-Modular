#  SCFW: Bleeding-edge modular kernel branch

This branch is primarily for those who'd like to test out/play with new revisions of the kernel that have yet to be pushed to the main branch.

## Installation
1 - Download the current release and copy the scfw folder to the root of your SD card.  
2 - That's it! You can now use the kernel by loading scfw/kernel.gba from the official firmware.  
> **_NOTE:_** You can also select the firmware.frm file from within the kernel to flash SCFW to the Supercard's firmware. Because the firmware is minimal and the kernel is loaded from the SD card, updates to the firmware should be rare. You can enjoy kernel updates without updating the firmware.  

## Prerequisites for emulator use
For Game Boy / Game Boy Color, you need to download your preferred Goomba fork/binary and rename it to:
- gbc.gba
    - For Game Boy Color emulation
- gb.gba
	- For Game Boy emulation

For NES/Famicom, you need to download your preferred PocketNES fork/binary and rename it to:
- nes.gba

For Sega Master System, Game Gear, and Sega Game 1000 (Sega 1000), you need to download your preferred SMSAdvance fork/binary and rename it to:
- smsa.gba

For NEC PC-Engine/TurboGrafx-16, you need to download your preferred PCEAdvance fork/binary and rename it to:
- pcea.gba

Once you have those files, transfer these to the scfw folder.
You should find the ff. files within the scfw folder:
- kernel.gba
- gb.gba
- gbc.gba
- nes.gba
- smsa.gba
- pcea.gba

## Observed emulator quirks
System | Emulator | Quit to firmware | Soft reset | Modular
:-:|:-:|:-:|:-:|:-:
Game Boy | Goomba / Super Goomba / Goomba Color | ✔ | ✔ | ✔
Game Boy Color | Jagoomba Color / Goomba Color | ✔ | ✔ | ✔
Nintendo Entertainment System / Family Computer | PocketNES | ⚠ | ✔ | ✔
Sega Master System | SMSAdvance | ❌ | ✔ | ✔
Sega Game Gear | SMSAdvance | ❌ | ✔ | ✔
Sega Game 1000 / Sega 1000 | SMSAdvance | ❌ | ✔ | ✔
NEC PC-Engine / TurboGrafx-16 | PCEAdvance | ❌ | ❌ | ✔
> **_LEGEND:_**
> > * ⚠ ~ Varies per fork / version. Use with caution
> > * ❌ ~ Unsupported / Not functioning as intended
> > * ✔ ~ Supported / Works as intended
>
> **_NOTE:_**  Emulator binaries can be improved upon and can be made compatible with the kernel just like Goomba.
> * IF QUIT TO FIRMWARE DOESN'T WORK, USE THE SOFT RESET METHOD TO QUIT TO FIRMWARE.
>     * Soft reset key combination: **START** ➕ **SELECT** ➕ **A** ➕ **B**

## Current features
- Can browse files
- Can load a GBA ROM
- Can flash a Supercard firmware.
- Automatic SRAM, waitstate, and prefetch patching (buggy)
- Automatic SRAM loading & saving
- Manual SRAM management
- SDHC
- Soft reset patch
- PCEAdvance support ✅
	- Loads PC-Engine/TurboGrafx-16 games (*.pce)
- SMSAdvance support ✅
    - Loads Sega Master System games (*.sms)
	- Loads Game Gear games (*.gg)
	- Loads Sega Game 1000 / Sega 1000 games (*.sg)
- PocketNES support ✅
    - Loads NES / Famicom games (*.nes)
    - Automatic ROM region detection (PAL / NTSC timing)
- Goomba support ✅
    - Loads Game Boy games (*.gb)
    - Loads Game Boy Color games (*.gbc)
	 
## Planned features
- NGPGBA
- WasabiGBA
	
## NOTES
- ⚠Some GBAOAC devices such as the EXEQ Game Box SP don't play nice with flash carts as it doesn't have the same wait time. Thus, ROMs boot faster and the flash cart does not have enough time to prepare. Try to toggle "Boot games through BIOS" each time you exit a GBC/GB game.
    - Alternative method for GBAOC devices: Create a ROM compilation using "goombafront" and sideload the gba file. This process is tedious, but it works best for clones like these.
- ⚠WARNING: The cart **appears** to not have enough time to properly load both emulator and ROM if you skip the BIOS. It's better to leave that kernel option "Boot games through BIOS" as 1 (on).

## Links
[GBATemp Bleeding-edge kernel thread](https://gbatemp.net/threads/scfw-bleeding-edge-modular-kernel-branch.656629/)

## Credits
[metroid maniac](https://github.com/metroid-maniac) - Main developer  
[Archeychen](https://github.com/ArcheyChen) - Early development into another loader, SDHC support  
[OmDRetro](https://github.com/OmDRetro) - Kernel enhancements, more supported filetypes  
[RocketRobz](https://github.com/RocketRobz) - Twilightmenu++ "gbapatcher" code for patching Supercard ROMs  
[SiliconExarch](https://github.com/SiliconExarch) - Finding an old DevkitARM release with a functioning Supercard SD drive  