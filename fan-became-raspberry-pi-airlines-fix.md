<h3>Imagine this:</h3>
You got a Raspberry Pi 5, and started using it, but then, 2 months later, your dumb ass fan becomes an airline and doesn't wanna stop being loud?

# I have experienced it too.
Here is how to fix it:

First of all, open up the config TXT file:

```bash
sudo nano /boot/firmware/config.txt
```

Once you're in, find the `[all]` section. If you don't see it, add it.

Now, add this below `[all]`:

`dtparam=cooling_fan=on`

After you're done, save the file.

# Now, reboot your Raspberry Pi 5 and your fan should be quiet when it finishes booting!

# Resources:
https://forums.raspberrypi.com/viewtopic.php?p=2292362&hilit=fan#p2292362
