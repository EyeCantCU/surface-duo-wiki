# Convert AT&T Surface Duo into the global variant

## Prerequisites

- Your AT&T Surface Duo recovery image (https://support.microsoft.com/en-us/surface/recover-surface-duo-if-it-won-t-start-1e6fb3cf-4e24-92a8-bc05-4984274bc6a4#ID0EDD=Surface_Duo). 
- A global Surface Duo recovery image (https://forum.xda-developers.com/t/android-11-ota-link-zip-file-img-files-unlocked.4393341/).
- [Root](https://forum.xda-developers.com/t/root-guide-updated.4266095/).
- Unlocked bootloader (including critical).
- 'USB Debugging' enabled.

## WARNING

While this has been tested on my personal device, I cannot confirm that it will work for yours. SIM card support might be broken (though it worked on my Swedish network). **I am not responsible for any damage that might occur to your device.**

Banking and similar (SafetyNet) apps should still work but might require you to re-lock the bootloader afterwards since we'll just be running stock firmware.

## Steps

1. Extract 'payload.bin' from the global Surface Duo recovery image.
2. Use payload_dumper from the rooting guide to extract the partition images.
3. Copy all the partition images to `/sdcard/duo` on the target Surface Duo.
4. Download [globalify.sh](globalify.sh) and save it as `globalify.sh` on the root of the target Surface Duo.
5. Open a terminal with adb and run the following
   1. `adb shell`
   2. `su`
   3. `cd /data/local/tmp`
   4. `mv /sdcard/globalify.sh ./`
   5. `chmod +x globalify.sh && ./globalify.sh`
6. Exit adb shell and run `adb reboot recovery`. You might have to press Volume Up + Power to get past the "No Command" screen.
7. Pick the "sideload through adb" option.
8. Then run `adb sideload name_of_duo_global_ota.zip`. This might fail at 94-98%; but should still work. If not, just boot into recovery and retry from step 6.
9. Reboot.
10. Profit!!!!
