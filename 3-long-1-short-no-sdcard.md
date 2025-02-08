# `raspi-config` fucked with your EEPROM and now your Pi isn't booting? You also have no SD card to fix it?
Here is how to fix it!

You'll need:
- A Linux PC/Laptop
- USB-C cable with data transfer capatibility
- Any storage device (USB drive/SSD/HDD/NVMe) with the EEPROM .bin file

First, install Git on your PC. This varies on the distro you're using, so find the command for your package manager.

After that's done, clone the `usbboot` repository:
```bash
git clone https://github.com/raspberrypi/usbboot
```

Then change-directory into it:
```bash
cd usbboot
```

After you're in, you have to use `make` to get the binary:
```bash
make
```

Now, we can start our Raspberry Pi's recovery process.

Unplug everything from the Raspberry Pi, then connect your storage device to the Raspberry Pi followed by the micro HDMI cable (we need an output device connected), then plug it into your PC while holding down the power button.

If everything goes with plan, you should be stuck on a red light. That's what we want!

Now boot the Raspberry Pi:
```bash
sudo ./rpiboot
```

You should now be in a Linux instance. Mount the storage device if needed, then use the `flashrom` command to write to the EEPROM:
```bash
flashrom -p linux_spi:dev=/dev/spidev10.0,spispeed=16000 -w PATH/TO/YOUR/EEPROM.BIN
```

# After that's done, just unplug everything from your Raspberry Pi, and it should be good to boot.
