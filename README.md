![Arch Logo](https://www.archlinux.org/static/logos/archlinux-logo-dark-90dpi.ebdee92a15b3.png)

# My desktop configuration for Arch Linux

My [Manjaro](https://manjaro.org/) installation recently broke,
so I decided to replace it with [Arch](https://www.archlinux.org/) at reinstallation.

I also realized this fresh start was a good opportunity to describe my system configuration
as an [Ansible](https://www.ansible.com/) playbook.
This way reinstallation should be swift in case of another system failure.

## Things not covered in this playbook

- Base Arch Linux installation from install media
- Boot loader (e.g. Grub) installation
- Creation and/or mounting of local filesystems
- Installation of Ansible itself &mdash; and `sudo`
- Per-user configuration
  - I have `/home` on a separate partition which remains untouched between
    system reinstalls. (It is also regularly backed up, of course.)

### Packages needed for this playbook to function

`# pacman -S sudo ansible`

You should be able to run this as soon as you have booted into your
fresh Arch installation and your network connection is up.

Afterwards add yourself to sudoers by running `visudo`.

(Ansible might actually work without `sudo`, but I have never tested this.)

## Things (hopefully!) omitted in this repository

- IP addresses or hostnames of my private computers
  - in particular the files in `secret_vars/`
- Usernames, passwords or other credentials

## How to run the playbook

Ansible is often run on a separate controller host,
but not in this case.
This playbook directly targets `localhost`,
so type this on the computer you wish to perform the installation on:

`ansible-playbook install-system.yml -K`

## Why put this on GitHub?

1. Why not? It could be useful to someone?
2. Kind of as part of my portfolio as an Ansible demo.
3. I am planning on writing an article on Ansible for
[Skrolli](https://skrolli.fi) magazine and plan to link here from the article.

## License

This playbook is distributed under the terms of the MIT license.
See [`LICENSE.md`](LICENSE.md) for details.
