# GRiSP 2 Support

[![CircleCI](https://circleci.com/gh/fhunleth/nerves_system_grisp2.svg?style=svg)](https://circleci.com/gh/fhunleth/nerves_system_grisp2)[![Hex version](https://img.shields.io/hexpm/v/nerves_system_grisp2.svg "Hex version")](https://hex.pm/packages/nerves_system_grisp2)

This might be the base Nerves System configuration for the [GRiSP
2](http://grisp.org/). I haven't had a chance to work on it and last time I did,
I was using a [PHYTEC
phyBOARD-Segin](https://phytec.com/product/phyboard-imx6ul-segin/).

To do:

- [ ] Update Linux kernel to 5.10
- [ ] Bring up WiFi
- [ ] See if U-Boot works since this will be easier than porting to Barebox
- [ ] Check that A/B firmware updates work
- [ ] Verify RGB LEDs
- [ ] Verify DIP switches
- [ ] Enable 1-Wire and test
- [ ] Verify SPI
- [ ] Verify MicroSD card works
- [ ] Verify ATECC608B
- [ ] Check that `TARGET_GCC_FLAGS` are right
- [ ] Create example app that uses GRiSP2? Perhaps Nerves Livebook?

![GRiSP 2 image](assets/images/grisp2.jpg)

| Feature              | Description                     |
| -------------------- | ------------------------------- |
| CPU                  | NSP iMX6UL, ARM ARM Cortex-A7 @ 696 MHz |
| Memory               | 128 MB DRAM                     |
| Storage              | 4 GB eMMC Flash and MicroSD     |
| Linux kernel         | 4.14 w/ Phytec patches          |
| IEx terminal         | ttyS0                           |
| GPIO, I2C, SPI       | Yes - [Elixir Circuits](https://github.com/elixir-circuits) |
| ADC                  | -                               |
| PWM                  | -                               |
| UART                 | ttyS0-ttyS4                     |
| Camera               | None                            |
| Ethernet             | Yes                             |
| WiFi                 | Will be enabled when GRiSP 2 is available  |
| HW Watchdog          | i.MX6 watchdog enabled on boot. Be sure to enable `heart` in your vm.args or the device will reboot |

## Using

The most common way of using this Nerves System is create a project with `mix
nerves.new` and to export `MIX_TARGET=grisp2`. See the [Getting started
guide](https://hexdocs.pm/nerves/getting-started.html#creating-a-new-nerves-app)
for more information.

If you need custom modifications to this system for your device, clone this
repository and update as described in [Making custom
systems](https://hexdocs.pm/nerves/systems.html#customizing-your-own-nerves-system)

## Preparing the PHYTEC phyBOARD-Segin

The phyBOARD-Segin defaults to booting off an integrated NAND Flash. The
GRiSP 2 will have an eMMC Flash instead, so support for NAND has been disabled.
In the interim, this system only supports booting off the MicroSD card slot. To
enable this, place a jumper across J1.

## Console access

The console is configured to output to `ttyS0` by default.

TODO: Change to a UART that's doesn't require the debug daughter board.

## Provisioning devices

TODO: The GRiSP 2 includes an ATECC608A so provisioning the board for use with
NervesHub can be done without setting U-Boot environment variables.

## Linux and U-Boot versions

*TBD*

We're currently using PHYTEC's Linux kernel fork from
[git.phytec.de/linux-mainline](git://git.phytec.de/linux-mainline).
