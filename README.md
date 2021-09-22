# icelake

## Graphics related issues

1. 5 seconds black screen glitch (not fixed)
2. No HDMI (not fixed)
3. Issues with “default” ig-platform-id value (wa)
4. HiDPi issues (fixed/wa)
5. Black screen after wake up (fixed/wa) > -noDC9

## USB-TB wa

1. Thunderbolt 3 > no drivers or patches available (working if you plug device before boot)
2. USB mapping on macOS may / may not work properly > better to map in Windows using that tool

## Sleep/power issues / wa

1. Hibernation is not working > stuck on booting, garbled screen
2. Some Ice Lake machines have AOAC enabled (can’t be disabled in most part of laptops because of “locked” BIOS):
	* Use daliansky patches/SSDTs > not stable, battery life is low
	* Unlock BIOS settings > disable AOAC (Low power idle) > check
	* Patch FACP (still not properly tested)

### Collection of kernel panics / wa

1. EL[0] > need to enable Apple GuC firmware (Whatevergreen)
2. AppleGFXHDA > No-gfx-hda or patch AppleALC yourself
3. -noDC9 > black screen after wake (don’t mix that issue with black screen after wake up because of AOAC
