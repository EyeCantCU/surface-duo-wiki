# Convert AT&T Surface Duo into the global variant

## Prerequisites

- Your AT&T Surface Duo recovery image (https://support.microsoft.com/en-us/surface/recover-surface-duo-if-it-won-t-start-1e6fb3cf-4e24-92a8-bc05-4984274bc6a4#ID0EDD=Surface_Duo). 
- A global Surface Duo recovery image (https://forum.xda-developers.com/t/android-11-ota-link-zip-file-img-files-unlocked.4393341/).
- [Root](https://forum.xda-developers.com/t/root-guide-updated.4266095/).
- Unlocked bootloader (including critical).
- 'USB Debugging' enabled.

## WARNING

Only continue with this process if your battery is charged and you're using a reliable USB cable without quirks. Your device could die during the process potentially leaving you with a brick, or a faulty cable could result in data corruption.

Apps that rely on SafetyNet (some banking apps, some media apps, etc.) will not work unless you relock your bootloader after this process completes. Alternatively, you can root the device again and install kdrag0n's SafetyNet fix (https://github.com/kdrag0n/safetynet-fix).

While this process has worked on other devices, it might not on yours for various reasons that I take no responsibility for.

It is totally likely this method stops working in the future, specifically with the release of Android 12L. Partition images that need to be written may change.

__I am not responsible for bricked devices, devices without working SIM cards or eSIM, devices that don't work in any specific way, or devices that gain a mind of their own and seek out world domination. You have been warned.__

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
