nrfprog.sh
==========

This is a loose shell port of the nrfjprog.exe program distributed by Nordic.
It relies on JLinkExe (from https://www.segger.com/jlink-software.html) to
interface with the JLink hardware.

The generated scripts were basically lifted from the Makefiles distributed with
the [nrf51-pure-gcc-setup](https://github.com/hlnd/nrf51-pure-gcc-setup)
project, so much thanks to @hlnd.

usage:

```
nrfjprog.sh <action> [hexfile]
```

where action is one of:
 * `--info`
 * `--reset`
 * `--pin-reset`
 * `--erase-all`
 * `--flash`
 * `--flash-softdevice`
 * `--flash-bootloader-bin`
 
## Un-bricking Particle Mesh Boards

This script has been modified specifically to un-bork Particle Mesh boards. Instructions to un-bork are the following:

1. Run `./nrfjprog.sh --flash-softdevice /path/to/s140_nrf52_6.0.0_softdevice.hex`
1. Then, run `./nrfjprog.sh --flash-bootloader-bin /path/to/xenon-bootloader@1.3.0-rc.1.bin 0xf4000`

As of this writing, the latest firmware is `xenon-bootloader@1.3.0-rc.1.bin` and the boot loader start location is `0xf4000`. This parameter **may change** in future revisions.
