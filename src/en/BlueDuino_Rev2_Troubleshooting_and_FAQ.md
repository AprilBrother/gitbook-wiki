[← BlueDuino Rev2 Main Page](BlueDuino_rev2.md)

## Troubleshooting

### How to Revive a “Bricked” BlueDuino Rev2

Incorporating all of the USB tasks on a single chip is an awesome
feature that makes the BlueDuino and boards like it truly unique. But it
also places more stress on a single chip, and if anything goes wrong
with that chip, the board becomes nearly unusable. It’s not uncommon for
BlueDuino’s to become “bricked” and unprogrammable. But, in most cases,
the bricking is reversible\!

The most common source of BlueDuino “bricking” is uploading code to it
with an incorrectly set board.

To revive the BlueDuino, you’ll need to find a way to upload a sketch to
it with the board option correctly set. We can do this with a little
help from the bootloader.

First, you’ll need to set the serial port to the bootloader. But that
port is only visible when the board is in bootloader mode, so pull the
reset line low twice quickly to invoke the bootloader reset feature
discussed above. You can quickly press the reset button twice. While the
BlueDuino is in the bootloader mode change the ‘Tools \> Serial Port’ menu to the
bootloader COM port. Quick\! You’ve only got eight seconds. On Windows,
the bootloader’s COM port number is usually one number higher than the
BlueDuino’s regular port number.

## FAQ

### Why Does my ATMega32U4 Board Show up Twice in Device Manager?

Both the bootloader and the sketch have their own VID/PIDs. When you
plug in a board the bootloader starts running for a few seconds, and you
will see the board show up in Device Manager based on those VID/PIDs.
After a few seconds, the sketch will start running, and you will see
Device Manager disconnect from the bootloader and connect to the sketch.
