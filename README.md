## NOTE: Manjaro Sway Community edition doesn't work with this script!(It's _not_ a Wayland issue, scroll down for more info)

# Manjaro to Arch conversion script(only for x86_64, UEFI, IPv4)

This is a script to convert a Manjaro installation to an Arch installation with a single command.<br>The original version is [this gist](https://gist.github.com/mariuszkurek/bff8a821076f5406b15fe9be528957b6/) which did work but wasn't seamless, and this script follows the GPLv2 license in the original script.<br>Personally I wanted to use the MIT or BSD-2 clause license.

## Why did I write this?

A few months ago, I was using Manjaro just because I liked the green theme, and I just wanted to compile [paru](https://github.com/Morganamilo/paru).<br> The `libalpm` library and `pacman`, which had a major update to v6.0.0, weren't updated in Manjaro's mirrors, but `paru` already had an implementation of the updated versions.<br>I did manage to compile it by switching to an old tag, but it was very inconvenient, and I decided to switch to Arch while using my userspace. Online guides of it were wrong in many ways, and I finally found a working _script_ which _did_ work, but was incomplete. I decided to improve it, and the result is this.

## How this script works

The main difference of pure Arch and Manjaro is that they use different mirrors. Manjaro uses slightly old versions of a package for testing, so changing it to Arch mirrors is the first step.<br>Then the script deletes Manjaro-specific packages and Pacman configurations, and enables the multilib repository if it's commented out.<br>After that, the script performs a `pacman -Syyuu` so that the packages are updated and installs an Arch kernel.<br>Finally GRUB is updated to have Arch's theme and the distributor name is changed to `Arch`.<br>Finally DE-specific operations are performed to give a better polished result.

## Unsupported Editions

### Sway Daily Community edition

The screen goes gray after rebooting after running this script.<br>As far as I have experimented it's definetely not a Wayland issue, it's an issue in Sway. Please DO NOT USE THIS IF YOU'RE ON SWAY!

## TODO

- [ ] Check if UEFI or CSM

- [ ] Choose a different editor other than ${EDITOR}

- [ ] Ask reboot after run

- [ ] Check if x86_64 or AArch64

- [ ] Check if IPv4 or IPv6

- [ ] Manjaro Sway community edition support

- [ ] Ask which kernel version is to be installed

