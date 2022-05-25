# Changelog

This project does NOT follow semantic versioning. The version increases as
follows:

1. Major version updates are breaking updates to the build infrastructure.
   These should be very rare.
2. Minor version updates are made for every major Buildroot release. This
   may also include Erlang/OTP and Linux kernel updates. These are made four
   times a year shortly after the Buildroot releases.
3. Patch version updates are made for Buildroot minor releases, Erlang/OTP
   releases, and Linux kernel updates. They're also made to fix bugs and add
   features to the build infrastructure.

## v0.3.0

This release updates to Buildroot 2022.02.1 and OTP 25.0. While this should be
an easy update for most projects, many programs have been updated. Please review
the changes in the updated dependencies for details.

* Updated dependencies
  * [nerves_system_br v1.19.0](https://github.com/nerves-project/nerves_system_br/releases/tag/v1.19.0)
  * [Buildroot 2022.02.1](http://lists.busybox.net/pipermail/buildroot/2022-April/640712.html). Also see [Buildroot 2022.02](http://lists.busybox.net/pipermail/buildroot/2022-March/638160.html)
  * [Erlang/OTP 25.0](https://erlang.org/download/OTP-25.0.README)

## v0.2.3

This release bumps Erlang to 24.3.2 and should be a low risk upgrade from the
previous release.

* Changes
  * Pull in upstream Linux SquashFS patch to improve file system performance
  * Switch back to using kernel modules for WiFi drivers to avoid needing to
    build regulatory information into the kernel.

* Updated dependencies
  * [nerves_system_br v1.18.6](https://github.com/nerves-project/nerves_system_br/releases/tag/v1.18.6)

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

