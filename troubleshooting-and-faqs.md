<div id="top"></div>

<!-- Shields/Logos -->
[![License][license-shield]][license-url]
[![Issues][issues-shield]][issues-url]
[![Discord][discord-shield]][discord-url]
[![Reddit][reddit-shield]][reddit-url]
[![Telegram][telegram-shield]][telegram-url]

<!-- Project Logo -->
<p align="center">
  <a href="https://github.com/sebanc/brunch" title="Brunch">
   <img src="./images/settings_icon-512.png" width="128px" alt="Logo"/>
  </a>
</p>
<h1 align="center">Troubleshooting and FAQs</h1>
  
# Common Issues

<details>
  <summary> Click to learn about common issues </summary>
  
  ***
<!-- This *** line creates a divider so that the dropdown looks nice. 
Empty lines between everything in <angle breackets> is intentional due to markdown issues -->
  
  ### The instructions are too difficult to follow!
* ChromeOS is based on linux, most troubleshooting will require some familiarity with basic linux commands. It is strongly suggested that users are comfortable with linux before attempting an installation. If you are strugging with a specific step or would like to suggest changes to the guide, please reach out to our communities for assistance.

[![Discord][discord-shield]][discord-url]
[![Reddit][reddit-shield]][reddit-url]
[![Telegram][telegram-shield]][telegram-url]
  
  ### I followed a video tutorial, now I'm having issues.
  * Video guides are very frequently out of date or use potentially dangerous scripts. For the most up to date information and guides, be sure to read over this github page thouroughly *before* asking for help. 
  
  ### My computer will not boot a Brunch USB, and I've followed all of the instructions correctly!
  * Some devices (notably Surface Go) will not boot a valid USB flash drive / SD card with secure boot on even if the shim binary is signed. For those devices, you will need to disable secure boot in your bios settings and use the legacy EFI bootloader by adding the `-l` parameter when running the chromeos-install.sh script.
  
  ###  The first boot and the ones after a framework change or an update are incredibly long! 
  * Unfortunately, the Brunch framework has to rebuild itself by copying the original rootfs, modules and firmware files after each significant change. The time this process takes depends mostly on your USB flash drive / SD card write speed. You may try with one that has better write speed or use the dual boot method to install it on your HDD.

  ### ChromeOS reboots randomly!
  * This can in theory be due to a lot of things. However, the most likely reason is that your USB flash drive / SD card is too slow. You may try with one that has better write speed or use the dual boot method to install it on your HDD.

  ### Some apps, like Netflix, do not appear on the playstore or don't run properly!
  * In order to have access to the ChromeOS shell, ChromeOS is started in developer mode by default. If you have a stable enough system, you can manually remove `cros_debug` from grub.cfg on the 12th partiton and then do a Powerwash (ChromeOS mechanism which will wipe all your data partition) to disable developer mode. This will remove access to the Crosh shell and certain other features though.
  
  ### Some android apps on the Playstore show as incompatible with my device!
  * Some Playstore apps are not compatible with genuine Chromebooks so this is probably normal. ChromeOS is not Android, so some apps and games are not optimized or avaliable.
  
  ### A new update is avaliable, is it safe to update?
  * ChromeOS updates can be unpredictable, especially on Brunch devices. Even if it's declaired safe by other users, you should *always* have backups ready in case there is an issue while updating or if the update has serious bugs on your hardware. 
  
  ### My Touchpad, Touchscreen, Wifi or other hardware is not working properly!
  * ChromeOS is not optimized for every device. Brunch has several avaliable framework options and multiple customized kernels avaliable further down on this page to help with these issues. If you're still having issues, you can reach out to other users on one of our communities for help.

[![Discord][discord-shield]][discord-url]
[![Reddit][reddit-shield]][reddit-url]
[![Telegram][telegram-shield]][telegram-url]

  
</details>

# Brunch Configuration Menu

<details>
  <summary> Click to learn about the Brunch Configuration Menu, Kernels, Framework Options and more! </summary>
  
***
  
The Brunch Configuration menu is a new feature avaliable in Brunch 93 and higher, this menu will allow users to set and controll options easily without needing to manually edit files themselves. The Brunch Configuration Menu can be accessed directly from Grub using the "ChromeOS (settings)" boot option or while logged into ChromeOS using the `sudo edit-brunch-config` command in the crosh shell.
  * To access the crosh shell, press **Ctrl + Alt + T** and type `shell` at the invite.

  
## Kernels
  
<details>
<summary> Click to learn about kernels </summary>
  
*** 

Several kernels can be enabled throught the configuration menu:
- kernel 5.4: Default kernel which is considered to be the most stable.
- kernel 5.10: Most recent kernel, needed for Intel Gen 10+ and AMD Ryzen Gen 4+ devices.
- kernel 4.19: Previous brunch kernel.
- kernel chromebook-5.4: Kernel with the best support for chromebooks.
- kernel chromebook-4.4: Kernel compatible with some older chromebooks models.
- kernel macbook: 5.10 kernel with specific patches for different generations of macbooks

WARNING: Changing kernel can prevent you from logging into your ChromeOS account, in which case a powerwash is the only solution (**Ctrl + Alt + Shift + R** at the login screen). Therefore, before switching to a different kernel, make sure you have a backup of all your data.

 </details>
  
## Framework Options
  
<details>
<summary> Click to learn about framework options </summary>
  
*** 

Some device specific options can be enabled through brunch configuration menu:
- "enable_updates": allow native ChromeOS updates (use at your own risk: ChromeOS will be updated but not the Brunch framework/kernel which might render your ChromeOS install unstable or even unbootable),
- "pwa": use this option to enable the brunch PWA 
  - You can install it from https://sebanc.github.io/brunch-pwa/ or see a preview [on the wiki][brunch-pwa-info],
- "android_init_fix": alternative init to support devices on which the android container fails to start with the standard init,
- "mount_internal_drives": allows automatic mounting of HDD partitions in ChromeOS 
  - Android media server will scan those drives which will cause high CPU usage until it has finished, it might take hours depending on your data),
  - Partition label will be used if it exists,
- "broadcom_wl": enable this option if you need the broadcom_wl module,
- "iwlwifi_backport": enable this option if your intel wireless card is not supported natively in the kernel,
- "rtl8188eu": enable this option if you have a rtl8188eu wireless card/adapter,
- "rtl8188fu": enable this option if you have a rtl8188fu wireless card/adapter,
- "rtl8192eu": enable this option if you have a rtl8192eu wireless card/adapter,
- "rtl8723bu": enable this option if you have a rtl8723bu wireless card/adapter,
- "rtl8723de": enable this option if you have a rtl8723de wireless card/adapter,
- "rtl8723du": enable this option if you have a rtl8723du wireless card/adapter,
- "rtl8812au": enable this option if you have a rtl8812au wireless card/adapter,
- "rtl8814au": enable this option if you have a rtl8814au wireless card/adapter,
- "rtl8821ce": enable this option if you have a rtl8821ce wireless card/adapter,
- "rtl8821cu": enable this option if you have a rtl8821cu wireless card/adapter,
- "rtl88x2bu": enable this option if you have a rtl88x2bu wireless card/adapter,
- "rtbth": enable this option if you have a RT3290/RT3298LE bluetooth device,
- "ipts": enable support for Surface devices touchscreen with kernel 5.4 / 5.10 
  - Thanks go to the linux-surface team, especially StollD,
- "goodix": improve goodix touchscreens support,
- "invert_camera_order": use this option if your camera order is inverted,
- "no_camera_config": if your camera does not work you can try this option which disables the camera config,
- "oled_display": enable this option if you have an oled display (use with kernel 5.10),
- "acpi_power_button": try this option if long pressing the power button does not display the power menu,
- "alt_touchpad_config": try this option if you have touchpad issues,
- "alt_touchpad_config2": another option to try if you have touchpad issues,
- "disable_intel_hda": some Chromebooks need to blacklist the snd_hda_intel module, use this option to reproduce it,
- "internal_mic_fix": allows to forcefully enable internal mic on some devices,
- "asus_c302": applies asus c302 specific firmwares and fixes,
- "baytrail_chromebook": applies baytrail chromebooks specific audio fixes,
- "sysfs_tablet_mode": allow to control tablet mode from sysfs 
  - `echo 1 | sudo tee /sys/bus/platform/devices/tablet_mode_switch.0/tablet_mode` to activate it or use 0 to disable it,
- "force_tablet_mode": same as above except tablet mode is enabled by default on boot,
- "suspend_s3": disable suspend to idle (S0ix) and use S3 suspend instead,
- "advanced_als": [default ChromeOS auto-brightness][auto-brightness] is very basic, 
  - This option activates more auto-brightness levels (based on the Pixel Slate implementation).

 </details>

## Kernel command line parameters
  
<details>
<summary> Click to learn about kernel line parameters </summary>
  
*** 

The most common kernel command line parameters are listed below:
- "enforce_hyperthreading=1": improve performance by disabling a ChromeOS security feature and forcing hyperthreading everywhere (even in crositini).
- "i915.enable_fbc=0 i915.enable_psr=0": if you want to use crouton (needed with kernel 5.4).
- "psmouse.elantech_smbus=1": fix needed for some elantech touchpads.
- "psmouse.synaptics_intertouch=1": enables gestures with more than 2 fingers on some touchpad models.

Additional kernel parameters can also be added manually from the configuration menu.
  
</details>

## Brunch Bootsplashes
  
<details>
<summary> Click to learn about Brunch bootsplashes </summary>
  
  ***
  
Brunch Bootsplashes can be selected using the Brunch Configuration Menu, these determine the logo visible while Brunch is booting. (before the ChromeOS logo appears) You can preview the different bootsplashes by switching the branch of this repository to your brunch version and browsing the folder named "bootsplashes".

</details>

</details>

# Updates
  
<details>
<summary> Click to learn about updates </summary>
  
  ***
  
It is currently recommended to only update ChromeOS when the matching version of the Brunch framework has been released, however it's not a strict requirement that Brunch and ChromeOS be the same version. 

 
 ## How to update Brunch and ChromeOS together
  
<details>
<summary> Click to learn how to update Brunch and ChromeOS together</summary>
  
  ***
 
 The easiest way to update Brunch and ChromeOS is to use the [Brunch PWA][brunch-pwa-info], although it's also possible to update manually.
 
 To manually update Brunch and ChromeOS together: 
 * Download the [latest Brunch release][latest-release]
 * Download the [latest recovery][cros-tech] matching your install and extract the bin.
 * Open the Crosh Shell with **Crtl + Alt + T** and enter `shell` at the prompt.
 * Run the built in command to update Brunch.
   * Replace `brunch_archive.tar.gz` with the file's actual filename.
   * Replace `recovery.bin` with the file's actual filename.

```sudo chromeos-update -r ~/Downloads/recovery.bin -f ~/Downloads/brunch_archive.tar.gz```
 * Restart ChromeOS after the update finishes.
  
  Brunch and ChromeOS can also be updated with the [BiteDasher's Script][bite-dasher]
  
  </details>
  
 ## How to update Brunch
  
<details>
<summary> Click to learn how to update Brunch </summary>
  
  ***
 
 The easiest way to update Brunch is to use the [Brunch PWA][brunch-pwa-info], although it's also possible to update manually.
 
 To manually update Brunch: 
 * Download the [latest Brunch release][latest-release]
 * Open the Crosh Shell with **Crtl + Alt + T** and enter `shell` at the prompt.
 * Run the built in command to update Brunch.
   * Replace `brunch_archive.tar.gz` with the file's actual filename.

```sudo chromeos-update -f ~/Downloads/brunch_archive.tar.gz```
 * Restart ChromeOS after the update finishes.
  
  Brunch can also be updated with the [Brunch Toolkit][brunch-toolkit]
  
  </details>
  
  </details>

<!-- Reference Links -->
<!-- Badges -->
[license-shield]: https://img.shields.io/github/license/sebanc/brunch?label=License&logo=Github&style=flat-square
[license-url]: ./LICENSE
[forks-shield]: https://img.shields.io/github/forks/sebanc/brunch?label=Forks&logo=Github&style=flat-square
[forks-url]: https://github.com/sebanc/brunch/fork
[stars-shield]: https://img.shields.io/github/stars/sebanc/brunch?label=Stars&logo=Github&style=flat-square
[stars-url]: https://github.com/sebanc/brunch/stargazers
[issues-shield]: https://img.shields.io/github/issues/sebanc/brunch?label=Issues&logo=Github&style=flat-square
[issues-url]: https://github.com/sebanc/brunch/issues
[pulls-shield]: https://img.shields.io/github/issues-pr/sebanc/brunch?label=Pull%20Requests&logo=Github&style=flat-square
[pulls-url]: https://github.com/sebanc/brunch/pulls
[discord-shield]: https://img.shields.io/badge/Discord-Join-7289da?style=flat-square&logo=discord&logoColor=%23FFFFFF
[discord-url]: https://discord.gg/x2EgK2M
[telegram-shield]: https://img.shields.io/badge/Telegram-Join-0088cc?style=flat-square&logo=telegram&logoColor=%23FFFFFF
[telegram-url]: https://t.me/chromeosforpc
[reddit-shield]: https://img.shields.io/badge/Reddit-Join-FF5700?style=flat-square&logo=reddit&logoColor=%23FFFFFF
[reddit-url]: https://www.reddit.com/r/Brunchbook

<!-- Outbound Links -->
[croissant]: https://github.com/imperador/chromefy
[swtpm]: https://github.com/stefanberger/swtpm
[linux-surface]: https://github.com/linux-surface/linux-surface
[chromebrew]: https://github.com/skycocker/chromebrew
[intel-cpus]: https://en.wikipedia.org/wiki/Intel_Core
[intel-list]: https://en.wikipedia.org/wiki/List_of_Intel_CPU_microarchitectures
[atom-cpus]: https://en.wikipedia.org/wiki/Intel_Atom
[atom-list]: https://en.wikipedia.org/wiki/List_of_Intel_Atom_microprocessors
[amd-sr-list]: https://en.wikipedia.org/wiki/List_of_AMD_accelerated_processing_units#%22Stoney_Ridge%22_(2016)
[amd-ry-list]: https://en.wikipedia.org/wiki/List_of_AMD_Ryzen_processors
[recovery-rammus]: https://cros.tech/device/rammus
[recovery-volteer]: https://cros.tech/device/volteer
[recovery-grunt]: https://cros.tech/device/grunt
[recovery-zork]: https://cros.tech/device/zork
[cros-tech]: https://cros.tech/
[cros-official]: https://cros-updates-serving.appspot.com/
[vboot-utils]: https://aur.archlinux.org/packages/vboot-utils
[auto-brightness]: https://chromium.googlesource.com/chromiumos/platform2/+/master/power_manager/docs/screen_brightness.md
[brunch-toolkit]: https://github.com/WesBosch/brunch-toolkit
[bite-dasher]: https://github.com/BiteDasher/brcr-update

<!-- Images -->
[decon-icon-24]: ./images/decon_icon-24.png
[decon-icon-512]: ./images/decon_icon-512.png
[terminal-icon-24]: ./images/terminal_icon-24.png
[terminal-icon-512]: ./images/terminal_icon-512.png
[settings-icon-512]: ./images/settings_icon-512.png
[windows-img]: https://img.icons8.com/color/24/000000/windows-10.png
[linux-img]: https://img.icons8.com/color/24/000000/linux--v1.png

<!-- Internal Links -->
[cpu-wiki]: https://github.com/sebanc/brunch/wiki/CPUs-&-Recoveries
[windows-guide]: ./install-with-windows.md
[linux-guide]: ./install-with-linux.md
[troubleshooting-and-faqs]: ./troubleshooting-and-faqs.md
[compatibility]: ./README.md#supported-hardware
[changing-kernels]: ./troubleshooting-and-faqs.md#kernels
[framework-options]: ./troubleshooting-and-faqs.md#framework-options
[releases-tab]: https://github.com/sebanc/brunch/releases
[latest-release]: https://github.com/sebanc/brunch/releases/latest
[mbr-patch]: https://github.com/sebanc/brunch/raw/master/mbr_support.tar.gz
[brunch-der]: https://github.com/sebanc/brunch/raw/master/brunch.der
[secure-boot]: ./install-with-linux.md#secure-boot
[brunch-pwa-info]: https://github.com/sebanc/brunch/wiki/Brunch-PWA-Guide