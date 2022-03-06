# Changelog

## v0.2.2

* Changes
  * Enable the `ramoops` driver to capture log messages right before an
    unexpected reboot.
  * Turn off unused kernel options and adjust for faster boot times and smaller
    images.

## v0.2.1

This release has various Linux device tree and option updates to bootup warnings
and allow more hardware to be accessed in Elixir.

* Changes
  * Use the serial number printed on the GRiSP board

* Updated dependencies
  * [nerves_system_br v1.18.5](https://github.com/nerves-project/nerves_system_br/releases/tag/v1.18.5)

## v0.2.0

This is a very early port to the GRiSP2. It runs off eMMC, supports A/B firmware
updates like other Nerves devices, and basics like WiFi look like they work.

* Dependencies
  * [nerves_system_br v1.18.4](https://github.com/nerves-project/nerves_system_br/releases/tag/v1.18.4)
  * Erlang 24.2.1
  * Linux 5.10.76 with PHYTEC kernel patches

## v0.1.0

* Dependencies
  * [nerves_system_br v1.7.1](https://github.com/nerves-project/nerves_system_br/releases/tag/v1.7.1)
  * Erlang 21.2.7
  * Linux 4.14.93 with PHYTEC kernel patches

