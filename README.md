# GRiSP 2 Support

[![CircleCI](https://circleci.com/gh/fhunleth/nerves_system_grisp2.svg?style=svg)](https://circleci.com/gh/fhunleth/nerves_system_grisp2)[![Hex version](https://img.shields.io/hexpm/v/nerves_system_grisp2.svg "Hex version")](https://hex.pm/packages/nerves_system_grisp2)

This might be the base Nerves System configuration for the [GRiSP
2](http://grisp.org/).

*This is a work in progress. It may change in backwards incompatible ways and the documentation might be lacking.*

To do:

- [x] Bring up Ethernet
- [x] Bring up WiFi (currently requires unreleased VintageNetWiFi)
- [x] Verify RGB LEDs
- [ ] Verify DIP switches
- [ ] Enable 1-Wire and test
- [ ] Verify SPI
- [x] Verify MicroSD card works
- [ ] Verify ATECC608B
- [ ] Verify HW watchdog
- [ ] Add ramoops support
- [ ] Review GRiSP2 specs to see what else there is to verify
- [x] Check that `TARGET_GCC_FLAGS` are right
- [x] Update Linux kernel to 5.10
- [x] Update Nerves Toolchain 1.5.0 version
- [x] Implement A/B firmware updates work
- [ ] Create example app that uses GRiSP2? Perhaps Nerves Livebook?
- [ ] Review Linux kernel options and compare with other systems
- [ ] Clean up debug and low hanging items to improve boot time
- [ ] Clean up changes to GRiSP repositories and send PRs

![GRiSP 2 image](assets/images/grisp2.jpg)

| Feature              | Description                     |
| -------------------- | ------------------------------- |
| CPU                  | NXP iMX6ULL, ARM Cortex-A7 @ 696 MHz |
| Memory               | 512 MB DRAM                     |
| Storage              | 4 GB eMMC and optional MicroSD  |
| Linux kernel         | 5.10 w/ Phytec patches          |
| IEx terminal         | ttymxc0                         |
| GPIO, I2C, SPI       | Yes - [Elixir Circuits](https://github.com/elixir-circuits) |
| LEDs                 | Yes - grisp-rgb[12]-(red or blue or green) via `sys/class/leds` |
| ADC                  | -                               |
| PWM                  | -                               |
| UART                 | ttymxc0-ttymxc5                 |
| Camera               | None                            |
| Ethernet             | Yes                             |
| WiFi                 | Yes - 2.4GHz                    |
| HW Watchdog          | i.MX6 watchdog enabled on boot  |

## Using

The most common way of using this Nerves System is create a project with `mix
nerves.new` and to export `MIX_TARGET=grisp2`. See the [Getting started
guide](https://hexdocs.pm/nerves/getting-started.html#creating-a-new-nerves-app)
for more information.

If you need custom modifications to this system for your device, clone this
repository and update as described in [Making custom
systems](https://hexdocs.pm/nerves/systems.html#customizing-your-own-nerves-system)

## Boot notes

This system isn't ready for general use. If you know how to build a Nerves
system, then it will probably be a little frustrating, but you'll get something
to boot.

1. Build the system
2. Create a test Nerves project or modify `circuits_quickstart` to use it. Until
   the Linux kernel is updated, you'll have to delete all other Nerves systems
   to avoid dependency conflicts on the toolchain.
3. Build the project with `mix firmware`. Then run `mix firmware.image` to get
   an image file.
4. gzip the image file and copy to a FAT-formatted MicroSD card
5. Boot the GRiSP2, but press a key to break into the bootloader.
6. Run:

    ```
    uncompress /mnt/mmc/myfirmware.img.gz /dev/mmc1
    reset
    ```
7. Now you should be able to use `mix upload` or `./upload.sh` for subsequent
   updates. The firmware is set to auto-validate.

## Console access

The console is configured to output to `ttymxc0` by default.

TODO: Change to a UART that's doesn't require the debug daughter board.

## Provisioning devices

TODO: The GRiSP 2 includes an ATECC608A so provisioning the board for use with
NervesHub can be done without setting U-Boot environment variables.

## Linux versions

*TBD*

We're currently using PHYTEC's Linux kernel fork from
[git.phytec.de/linux-mainline](git://git.phytec.de/linux-mainline).
