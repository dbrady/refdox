# New Linux Machine Setup (VirtualBox VM)

Last Updated On: 2026-10-15

Ubuntu running as a VirtualBox guest on the Windows 11 box (e.g. toothache),
so build123d work doesn't mean rebooting into Linux. Do the general setup in
new_linux_machine_setup.ubuntu.md; this file is just the VM-specific bits.

## VM settings (VirtualBox, on the host)

Settings → Display:
- Graphics Controller: VMSVGA (the default for Linux guests)
- Video Memory: 128 MB. A 4K screen needs more than the default.

## Guest Additions: makes the screen resize with the window

Without these, the guest is stuck at 1280x800 (about a third of a 4K monitor)
no matter how big the window is. The kernel driver ships with Ubuntu, but the
services that listen for "window resized" and change the resolution don't.

$ sudo apt install virtualbox-guest-utils virtualbox-guest-x11
$ sudo reboot

These are Ubuntu's packages (7.0.x). If auto-resize still doesn't work after
the reboot, the host's VirtualBox is probably too far ahead of them. Install
the exactly matching version from the host's ISO instead:
Devices → Insert Guest Additions CD image, then

$ sudo sh /media/$USER/VBox*/VBoxLinuxAdditions.run

## Getting full resolution

In the VirtualBox window:
- View → Auto-resize Guest Display (Host+G), then maximize or full screen (Host+F)
- Or, to stretch a fixed resolution instead: View → Scaled Mode (Host+C)

At native 4K the text will be tiny. Scale it inside Ubuntu (Settings →
Displays → Scale, 200%, or turn on fractional scaling for 150/175%). That
gives sharper text than VirtualBox's own Settings → Display → Scale Factor.
