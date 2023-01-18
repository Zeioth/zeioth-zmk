# Zeioth zmk-config

My wireless keyboard firmware.

## How to flash

* Shortcut the pins grd/rst twice in < 500ms to enter flash mode.
  A blue led will turn on on the board.
* A new device should have appeared in your computer.
* Copy your FS2 file into it, and wait until it finishes.
* Your file browser will close automatically. And the device will be unmounted.
  This is normal, it means all is ok. You can now try to pair the device with
  your phone.

Note that FS2 files are currently generated using github actions, so you can
find them there.

## Commands to re-flash the bootloader

Under normal circumstances this should not be necessary, but it can be done by
entering bootloader mode and running

    pip3 uninstall --user adafruit-nrfutil
    sudo adafruit-nrfutil --verbose dfu serial --package nice_nano_bootloader-_current_version.zip -p /dev/ttyS0 -b 115200 --singlebank --touch 1200

You can find the latest version [here](https://nicekeyboards.com/docs/nice-nano/troubleshooting).

## REQUIREMENTS

This firmware is for spanish. Your system's keyboard distribution must be
spanish querty. The firmware will convert it in real time to spanish COLEMAK DH layout.

## LAYERS

* **Default**: Colemak-dh layout + spanish ñ + dedicated key for tilde.
* **Super**: Full integration with I3/SWAY keybinds (default ones, and some extras).
* **Lower**: Characters + numbers. Because all characters you can achieve with RALT
         already exist in this layer, we don't have RALT key at all.
* **Raise**: On the right side, Movement/pagination keys (also mouse keys when
         implemented). On the left side VIM macros.
* **Hyper**: Programs
* **Arrow mode**: A mode that only has arrow keys in different positions.
                  Comfortable for reading!
* **Config**: Configures the keyboard. Currently, only has bluetooth profiles
              and a shortcut to launch this firmware manual (and my vimrc's).
* **Android**: Android doesn't allow customizing keyboard shortcuts (yet?), so
               we need this layer to control it.

## Troubleshooting

* **I can't see my bluetooth keyboard from my device**: Well you should.
ZMK makes itselft available all the time without you needing to do anything.
That's why as security measurement, a profile cannot be re-paired  until
cleared (see next point). Make sure your device or receiver support BLE technology.
* **I can't re-pair the keyboard**: You must make the device forget about the
keyboard. And then in the keyboard config layer, you must choose the paired
layer and press the CLEAR key. Now you should be able to re-pair both.
* **After I flash the firmware, if I reconnect the controller to the PC I only
see the default files**: Again, this is for security, so no one can modify your
firmware once flashed (easily).
* **My file browser doesn't close automatically after copying the firmware**:
  Try to copy the file a second time without resetting, it should auto-close
  this time. Reported to happen in some versions of thunar.

## Docs

* https://docs.nicekeyboards.com/#/nice!nano/troubleshooting
* https://zmk.dev/docs/user-setup

## Credits
This firmware uses the helper [zmk-nodefree-config](https://github.com/urob/zmk-nodefree-config) by urob, to avoid boilerplate.
