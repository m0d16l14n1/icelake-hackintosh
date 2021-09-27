# icelake

## Graphics related issues

| Bug | Description | Details |
| ------ | ------ | ------ |
| 1. 5 seconds black screen glitch | LINK | Not fixed |
| 2. No HDMI | LINK | Not fixed |
| 3. Issues with “default” ig-platform-id value | Link | WA |
| 4. HiDPi issues | LINK | Fixed/WA |
| 5. Black screen after wake up | LINK | Fixed/WA > -noDC9 |

## USB-TB wa

| Bug | Description | Details |
| ------ | ------ | ------ |
| 1. Thunderbolt 3 > no drivers or patches available | LINK | (working if you plug device before boot) |
| 2. USB mapping on macOS may / may not work properly | LINK | > better to map in Windows using THAT tool |

## Sleep/power issues / wa

| Bug | Description | Details |
| ------ | ------ | ------ |
| 1. Hibernation is not working | stuck on booting, garbled screen | ?? |
| 2. Sleep issues (wake-up problem) | Some Ice Lake machines have AOAC enabled (can’t be disabled in most part of laptops because of “locked” BIOS) | * |
	* 1) Use daliansky patches/SSDTs (LINK) > not so stable: battery life is low, some machines can't wake even with that patches
	* 2) Unlock BIOS settings > disable AOAC (Low power S0 idle) > the most hard way, but the most "stable"
	* 3) Patch FACP (still not properly tested) > patching FACP with OC > ACPI > Patch seems 
	to be not working for some reason (patching has no effect at all). 
	But it seems it's possible to do patching (disabling AOAC) with the help of that efi driver > LINK

### Collection of kernel panics / wa

| Bug | Description | Details |
| ------ | ------ | ------ |
| 1. EL[0] | Need to enable Apple GuC firmware | (Whatevergreen) |
| 2. AppleGFXHDA |  No-gfx-hda or patch AppleALC yourself | LINK |
| 3. -noDC9 | Black screen after wake (graphics related issue) | LINK |
