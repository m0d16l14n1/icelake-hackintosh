# icelake

## Graphics related issues

| Bug | Description/Details | Status |
| ------ | ------ | ------ |
| 1. 7-10 seconds black screen glitch after boot | [LINK](https://github.com/acidanthera/bugtracker/issues/1329) | FIXED/WIP - [details](https://github.com/acidanthera/bugtracker/issues/1805)|
| 2. **No HDMI support** | [LINK](https://github.com/Ardentwheel/OpenCore-Hasee-X57S1/issues/3#issuecomment-711080776) | **NOT FIXED** |
| 3. Issues with “default” ig-platform-id value | With default value (injected by WEG) in most cases laptop can't properly wake from sleep (result is a black screen and no panic/logs) | WA > Check 0x8A510002 (it's default value from MacBookAir9,1 which is working properly) |
| 4. HiDPi issues | [LINK](https://github.com/Ardentwheel/OpenCore-Hasee-X57S1/issues/3#issuecomment-790013456) | FIXED/WA > add AAPL,GfxYTile to iGPU device properties |
| 5. Black screen after wake up with kernel panic after | [LINK](https://github.com/acidanthera/bugtracker/issues/1207) | FIXED/WA > add "-noDC9" boot-arg |
| 6. **Screen backlight dimming** | Some of Lenovo laptops have that issue. Brightness is much lower than on Windows before a sleep-wake cycle. | **Currently no WA available / No fix or patch** |

## USB-TB WA

| Bug | Description/Details | Status |
| ------ | ------ | ------ |
| 1. Thunderbolt 3 > no drivers or patches available | "No drivers" in System report | Still working, if you plug device before boot |
| 2. USB mapping on macOS may / may not work properly due to TXHC | Randomly it will fail to map it properly (TXHC) | Better to map in Windows using [THAT](https://github.com/USBToolBox/tool) tool |
| 3. **Type-C to HDMI is not working on some of Ice Lake laptops (for example some of Dell laptops)** | Maybe because there is no Thunderbolt 3 support on that laptops > but it's working with video output on Linux (*Ubuntu*) | **Currently no WA available / No fix or patch** | 

## Sleep/power issues / WA

| Bug | Description/Details | Status |
| ------ | ------ | ------ |
| 1. **Hibernation is not working at all** | Stuck on booting or garbled screen right after selecting "macOS" drive in Boot Picker (OC) | Behavior is seems to be the same as it's mentioned [here](https://dortania.github.io/hackintosh/updates/2021/04/24/rocket-lake.html) in **"Power Cycle" part** |
| 2. Sleep issues (wake-up problem) | Some Ice Lake machines have **AOAC enabled** (can’t be disabled in most part of laptops because of “locked” BIOS) | * |

***
1) Use daliansky patches/SSDTs [LINK](https://github.com/alkindivv/OC-Little-English/tree/main/OC-Little-English/01-About%20AOAC%20) > Isn't so stable: battery life is low, some machines can't wake even with that patches
2) Unlock BIOS settings > disable AOAC (Low power S0 idle or any S0ix stuff) > It's the most hard way, but the most "stable"
3) !!!Patch FACP table!!! (still not properly tested) > It seems it's possible to do patching (disabling AOAC) with the help of that efi driver > [LINK](https://github.com/m0d16l14n1/Hasee-KingBook-X57S1/blob/master/Tools/AcpiPatcher.efi.zip). Patcher was found on some reddit topic. Credit goes to [datasone](https://github.com/datasone)
***

### Collection of kernel panics / wa

| Bug | Description/Details | Status |
| ------ | ------ | ------ |
| 1. EL[0] was invalidated!! | [LINK](https://github.com/acidanthera/bugtracker/issues/1343) | Need to enable GuC firmware loading > use device property for iGPU or boot-arg "igfxfw=2" |
| 2. AppleHDA panic if you connect external screen with speakers | [1](https://github.com/acidanthera/bugtracker/issues/1616), [2](https://github.com/acidanthera/bugtracker/issues/1551), [3](https://github.com/acidanthera/bugtracker/issues/1283) | Add "No-gfx-hda" to iGPU device properties or [patch AppleALC yourself](https://github.com/acidanthera/bugtracker/issues/1283#issuecomment-824802110) |
