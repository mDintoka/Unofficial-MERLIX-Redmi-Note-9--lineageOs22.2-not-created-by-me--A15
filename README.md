# Unofficial-MERLIX-Redmi-Note-9--lineageOs22.2-A15
This is an unofficial build of LineageOS 22.2 based on Android 15 for the device Merlix. It aims to provide a clean, stable, and bloat-free experience while bringing the latest Android 15 features and security patches to the platform
LineageOS 22.2 for Merlinx (Unofficial)
Disclaimer
This software is provided "as is" without any warranty. Flashing custom ROMs involves risks. This project is not created by me; I am sharing this build so that everyone can have it for free instead of paying for private builds.

Important Information
Base Requirement: You MUST be on MIUI 12.5 (Android 11) firmware before flashing. If you are on Android 10 or Android 12+ stock, the ROM will not function correctly.

Face Unlock: Not available (Hardware/Blob limitations).

GApps: Only Core GApps (NikGapps Core recommended) are supported. The system partition size on Merlinx is not large enough for "Basic" or "Full" packages.

Security: Face Unlock is disabled, but Fingerprint and Pin/Pattern work perfectly.

1. Prerequisites & Downloads
Drivers & Tools
You must install these to ensure your PC communicates with your device:

ADB & Fastboot Drivers: Download Platform Tools

MTK VCOM Drivers: Essential for SP Flash Tool.

SP Flash Tool (v5.1916 or newer): 
# ALL THE SP-FLASH AND THE MOST IMPORTAND MEDIATEK ECL BYPASS TOOL AVAILABLE IN OTHER REPOSITRY

Files Needed
MIUI 12.5 Fastboot ROM: (Ensure it is for merlinx).

LineageOS 22.2 Zip

Recovery Image: (TWRP or Lineage Recovery).

GApps: NikGapps (Core)

2. Step-by-Step Installation
Step A: Flash MIUI 12.5 Base (SP Flash Tool)
Open SP Flash Tool.

In "Download-Agent," select MTK_AllInOne_DA.bin.

In "Scatter-loading file," choose the MT6768_Android_scatter.txt from your MIUI 12.5 firmware folder.

Crucial: Ensure "Download Only" is selected. Do not use "Format All + Download" as it will wipe your IMEI (NVRAM/NVDATA).

Click Download, turn off your phone, and hold Volume Down while connecting the USB cable.

Step B: Unlock & Disable Security (Fastboot)
Once MIUI is installed and the bootloader is unlocked, boot into Fastboot Mode (Power + Volume Down) and run these commands:

Bash
# 1. Disable vbmeta verification (Mandatory to prevent bootloops)
fastboot --disable-verity --disable-verification flash vbmeta vbmeta.img

# 2. Flash the Recovery
fastboot flash recovery recovery.img

# 3. Reboot to Recovery
# (Hold Power + Volume Up immediately after running the reboot command)
fastboot reboot
Step C: Flashing the ROM
In your recovery (TWRP/Lineage):
(I tested using only the lineage reovery given in the files)
# FOR TWRP
Go to Wipe > Format Data > Type yes.

Go to Install and select the LineageOS 22.2 Zip.

DO NOT REBOOT YET.

Go back to Install and select NikGapps-Core.

Reboot System.
# FOR LINEAGE RECOVERY
ADB Command Reference
If you prefer installing via ADB Sideload from your PC:
1:Click format data and wipe everything one by one
2:Click apply update and then apply update from adb

Bash
# Enter Sideload mode in Recovery, then:
adb sideload LineageOS_22.2_merlinx.zip

# Then sideload GApps
adb sideload NikGapps-core-arm64-15.zip

# Important:
if it show error during installing click yes and keep going

# When everything is done reboot into system and Bravo!
What's Working?
[x] Smooth UI (Android 15)

[x] Wi-Fi / Bluetooth / Hotspot

[x] Audio / Video Playback

[x] RIL (Calls/Data)

[x] Fingerprint Scanner

[x] Camera

Known Issues
[ ] Face Unlock: Not supported.

[ ] Partition Space: Do not attempt to flash Large GApps; it will fail with Error 1.

Credits
LineageOS Team

Merlinx Community Developers

NikGapps Project

Special thanks to the original builders for keeping this device alive. This build is shared freely for the community.
