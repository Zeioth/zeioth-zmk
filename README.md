# Zeioth zmk-config
My wireless keyboard firmware

## How to flash (Linux)

* Shortcut the pins grd/rst twice in < 500ms to enter flash mode. A blue led will turn on on the board. 
* A new device should have appeared in your computer.
* On terminal, as sudo, copy your FS2 file, and delete everything else.

Note that FS2 files are currently generated using github actions, so you can find them there.

## Commands to re-flash the bootloader
Under normal circumstances this should not be necessary, but it can be done with

    pip3 uninstall --user adafruit-nrfutil
    sudo adafruit-nrfutil --verbose dfu serial --package nice_nano_bootloader-_s140_6.1.1.zip -p /dev/ttyS0 -b 115200 --singlebank --touch 1200


## Docs 

* https://docs.nicekeyboards.com/#/nice!nano/troubleshooting
* https://zmk.dev/docs/user-setup
