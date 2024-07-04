#  SCFW-Modular: A modular kernel with extra features

This is an experimentation repository before contributing to the main SCFW project.

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

For Watara/Quickshot Supervision, you need to download your preferred WasabiGBA fork/binary and rename it to:
- wsv.gba

For Neo Geo Pocket / Color, you need to download your preferred NGPGBA fork/binary and rename it to:
- ngp.gba

For Home Video Computer Advance, builds require additional work - but after doing so you can rename the binary to:
- hvca.gba
    * The base.bin file of hvca requires gbafix and an addiontal step:
        * _"Like retail games, this emulator tries to increase the ROM speed which supercard is not compatible with, I just disabled that"_ - Metroid Maniac

For SwanGBA, you need to download OR build your preferred SwanGBA fork/binary along with the needed dependencies and rename it to:
- bwsc.gba

Once you have those files, transfer these to the scfw folder.
You should find the ff. within the scfw folder:
- bwsc.gba
- gb.gba
- gbc.gba
- hvca.gba (Custom built version by metroid-maniac)
- kernel.gba
- nes.gba
- ngp.gba
- pcea.gba
- smsa.gba
- wsv.gba
- ./hvca/ (folder)
- ./hvca/mapr/ (folder)

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
Watara/Quickshot Supervision | WasabiGBA | ⚠ | ✔ | ✔
Neo Geo Pocket / Color | NGPGBA | ⚠ | ✔ | ✔
Famicom Disk System / NSF Player | HVCA | ❌ | ❌ | ‼
Bandai WonderSwan/WonderSwan Color / Benesse Pocket Challenge V2 | SwanGBA | ❌ | ✔ | ✔
> **_LEGEND:_**
> > * ‼ ~ Requires some technical know-how to get working / Modular to an extent, but requires additional work.
> > * ⚠ ~ Varies per fork / version OR works with some caveats(buggy). Use with caution
> > * ❌ ~ Unsupported / Not functioning as intended
> > * ✔ ~ Supported / Works as intended
>
> **_NOTE:_**  Emulator binaries can be improved upon and can be made compatible with the kernel just like Goomba.
> * IF QUIT TO FIRMWARE DOESN'T WORK, USE THE SOFT RESET METHOD TO QUIT TO FIRMWARE.
>     * Soft reset key combination: **START** + **SELECT** + **A** + **B**

## Current features
- Can browse files
- Can load a GBA ROM
- Can flash a Supercard firmware.
- Automatic SRAM, waitstate, and prefetch patching (buggy)
- Automatic SRAM loading & saving
- Manual SRAM management
- SDHC
- Soft reset patch
- Goomba support ✅
    - Loads Game Boy Color games (*.gbc)
    - Loads Game Boy games (*.gb)
- PCEAdvance support ✅
	- Loads PC-Engine/TurboGrafx-16 games (*.pce)
- PocketNES support ✅
    - Loads NES / Famicom games (*.nes)
    - Automatic ROM region detection (PAL / NTSC timing)
- SMSAdvance support ✅
	- Loads Game Gear games (*.gg)
	- Loads Sega Game 1000 / Sega 1000 games (*.sg)
    - Loads Sega Master System games (*.sms)
	- Custom BIOS loading support
- WasabiGBA support ✅
    - Loads Watara/Quickshot Supervision games (*.sv)
	- Custom BIOS loading support
- NGPGBA support ✅
    - Loads Neo Geo Pocket games (*.ngp)
	- Loads Neo Geo Pocket Color games (*.ngc)
	- Custom BIOS loading support
- HVCA support ✅
    - Loads Famicom Disk System games (*.fds)
	- Loads Nintendo Sound Files (*.nsf)
- SwanGBA support ✅
    - Loads Benesse Pocket Challenge V2 games (*.pc2)
	- Loads WonderSwan games (*.ws)
	- Loads WonderSwan Color games (*.wsc)

	
## NOTES
- ⚠Some GBAOAC devices such as the EXEQ Game Box SP don't play nice with flash carts as it doesn't have the same wait time. Thus, ROMs boot faster and the flash cart does not have enough time to prepare. Try to toggle "Boot games through BIOS" each time you exit a GBC/GB game.
    - Alternative method for GBAOC devices: Create a ROM compilation and sideload the resulting gba file. This process is tedious, but it works best for clones like these.
- ⚠WARNING: The cart **appears** to not have enough time to properly load both emulator and ROM if you skip the BIOS. It's better to leave that kernel option "Boot games through BIOS" as 1 (on).

## Links
[GBATemp Bleeding-edge kernel thread](https://gbatemp.net/threads/scfw-bleeding-edge-modular-kernel-branch.656629/)

## Credits
[metroid maniac](https://github.com/metroid-maniac) - Main developer  
[Archeychen](https://github.com/ArcheyChen) - Early development into another loader, SDHC support  
[OmDRetro](https://github.com/OmDRetro) - Kernel enhancements, significantly more supported filetypes  
[RocketRobz](https://github.com/RocketRobz) - Twilightmenu++ "gbapatcher" code for patching Supercard ROMs  
[SiliconExarch](https://github.com/SiliconExarch) - Finding an old DevkitARM release with a functioning Supercard SD drive  