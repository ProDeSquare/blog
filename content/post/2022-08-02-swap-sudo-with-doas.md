---
title: "Archlinux swap sudo with doas"
excerpt: As there are many problems with sudo it is always better to search for an alternative. Guess what, now you can use opendoas instead of sudo
date: 2022-08-02T02:24:55+05:00
draft: false
hero: /images/posts/swap-sudo-with-doas/hero.webp
authors:
    - Hamza Mughal
---

## Why consider switching

As there are many known issues with `sudo` it is wise to switch to something that is not bloat or has little or no known issues. In this case `opendoas` is the best choice.

## Installation

`doas` is available in the [AUR \(Arch User Repository\)](https://aur.archlinux.org). There are following ways to install:

- AUR helper
- Make from git repo

In this case we are directly going to install it with the help of an **AUR helper** like `paru` or `yay`. Run the following command from the commandline:

```shell
$ paru -S doas
```

Install it normally and continue.

## Setup

`doas` is already installed, now you need to set it up. Edit `/etc/doas.conf` with your text editor of choice, in my case it's `neovim`

```shell
$ sudo nvim /etc/doas.conf
```

`doas` could be configured in many ways but the most simple one is to permit the `wheel` group which is most commonly used.

```shell
# /etc/doas.conf
# uncomment/add either one of them based upon your liking

permit :wheel # with password confirmation
permit nopass :wheel # remove password confirmation
```

## Removing sudo

Congratulations, now you have successfully installed and setup `doas`. So now you can remove `sudo` because an alternative is present. But it could lead to some issues and we will see how to fix them. First let's remove sudo.

```shell
$ sudo pacman -R sudo
```

Our system is now cleansed from the evil of `sudo`. But there are programs that require sudo to be installed in the system to work properly. We are going to trick them to use `doas` instead of `sudo`.

```shell
$ which sudo
zsh: command sudo not found
$ ln -s /usr/bin/doas /usr/bin/sudo
$ which sudo
/usr/bin/sudo
```

What we did is checked the location where `sudo` is installed, as we recently uninstalled it, it was not found in our system. We made a **symbolic link** of `/usr/bin/doas` to `/usr/bin/sudo` so we can have `doas` to be called whenever some program calls `sudo`. This is to prevent many issues with the programs in the future.

## Resources

This article is available in the video form, check it out [here](https://youtu.be/zNy_FfCgmm0).