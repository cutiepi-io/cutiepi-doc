### Initial install

If you setup a new system there are two steps you need to do

1) a recovery image
https://dl.omnirom.org/tmp/rpi4/omni-rpi4-cutiepi-recovery.img.zip

2) a recovery flashable zip of the build you want to install eg
`https://dl.omnirom.org/tmp/rpi4/omni-12-<date>-<type>.zip` (ex. https://dl.omnirom.org/tmp/rpi4/omni-13-20221126-rpi4-MICROG.zip - see https://dl.omnirom.org/tmp/rpi4/ for a list).

Step 1 - flashing TWP
-unzip recovery image downloaded from 1 and flash to your new system storage device SD
-boot from that storage device - it will enter TWRP by default
-resize userdata by running install -> up one level -> resize_userdata.zip

Step 2 - flashing build with TWRP
-copy recovery flashable zip downloaded from 2 to USB stick
-insert USB stick and flash by running install -> select storage -> select USB stick
-after flash is done -> reboot system

### OTA updates

Open app Control Center -> System updates
-> Check - if new build is available
-> Download - recovery flashable zip will be stored in internal storage /sdcard/OpenDelta
-> Flash - device will reboot into TWRP flash the update and will reboot back into the ROM

Optional you can set automatic checks to get notified for new builds

### manual TWRP updates

Download recovery flashable zip of the build from 2 and either copy to
external USB stick or to internal storage in /sdcard/OpenDelta using adb
Follow step 2 above from initial install

### known issues

- camera image rotated
- on charging battery always shows 99% and will not change
- batter status updates happens every 30s only eg plug and unplug
- cutoff power not supported
- wireless adb is enabled by default using <ip>:5555
- with 2GB memory its generally not reecommended to use GAPPS builds
