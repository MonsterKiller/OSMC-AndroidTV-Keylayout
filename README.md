# OSMC Android TV Key layout file
This is a simple Android key layout file to allow all the OSMC RF remote control buttons to work with Kodi on Android TV as by default the 'info' and 'menu' buttons did nothing.
This also makes the 'home' button on the remote go to the Android TV home screen.


## Important
This was only an issue on and I have only tried this on a build of Android TV for the Pine64 from http://forum.pine64.org/showthread.php?tid=2861
it may not work for everyone, I uploaded it mainly for reference purposes.
This also does require you have root privilages to copy the file into the key layout directory.


## Installation
The .kl file should be copied into `/system/usr/keylayout/`, as per https://source.android.com/devices/input/key-layout-files.html the file is named by device vendor ID and product ID, like so: `Vendor_XXXX_Product_XXXX.kl`
(I found this by doing `cat /proc/bus/input/devices` and the device was called `HBGIC Technology Co., Ltd. USB Keyboard Mouse`)

You also need to ensure the file has the correct permissions, so use: `chmod 644 Vendor_2252_Product_1037.kl`

Once you have done this, simply unplug and reattach the receiver and you should be good to go.

## Did it work?
You can ensure it loaded the correct key layout by running `dumpsys input`, finding the device name near the top of the dump and checking the `KeyLayoutFile` value. 
For example:

```
    23: HBGIC Technology Co., Ltd. USB Keyboard Mouse
      Classes: 0x80000001
      Path: /dev/input/event3
      Descriptor: 604eb149107bf9d63309a31598f6ba31593e75d0
      Location: usb-sunxi-ohci-1/input0
      ControllerNumber: 0
      UniqueId:
      Identifier: bus=0x0003, vendor=0x2252, product=0x1037, version=0x0110
      KeyLayoutFile: /system/usr/keylayout/Vendor_2252_Product_1037.kl
      KeyCharacterMapFile: /system/usr/keychars/Generic.kcm
      ConfigurationFile:
      HaveKeyboardLayoutOverlay: false
```
