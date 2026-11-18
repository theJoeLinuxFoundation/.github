<div align="center">

# joe Linux

### Boring, on purpose.

*Open your laptop. Do your thing. Close your laptop.*

[![Status: alpha](https://img.shields.io/badge/status-alpha-c98361?style=for-the-badge)](https://github.com/theJoeLinuxFoundation/joe-linux#not-done-yet)
[![Latest: J1-7.3.1-0.2.2-alpha4](https://img.shields.io/badge/latest-J1--7.3.1--0.2.2--alpha4-24362c?style=for-the-badge)](https://github.com/theJoeLinuxFoundation/joe-linux#releases)
[![Unit tests](https://img.shields.io/github/actions/workflow/status/theJoeLinuxFoundation/joe-linux/unit-tests.yml?branch=main&style=for-the-badge&label=unit%20tests)](https://github.com/theJoeLinuxFoundation/joe-linux/actions/workflows/unit-tests.yml)
[![License](https://img.shields.io/github/license/theJoeLinuxFoundation/joe-linux?style=for-the-badge&color=24362c)](https://github.com/theJoeLinuxFoundation/joe-linux/blob/main/LICENSE)
[![Stars](https://img.shields.io/github/stars/theJoeLinuxFoundation/joe-linux?style=for-the-badge&color=c98361)](https://github.com/theJoeLinuxFoundation/joe-linux/stargazers)

![Zig 0.17.1](https://img.shields.io/badge/Zig-0.17.1-f7a41d?style=flat-square&logo=zig&logoColor=white)
![Linux 7.3.1](https://img.shields.io/badge/kernel-7.3.1-24362c?style=flat-square&logo=linux&logoColor=white)
![GNOME on Wayland](https://img.shields.io/badge/GNOME-Wayland-4a86cf?style=flat-square&logo=gnome&logoColor=white)
![systemd-boot](https://img.shields.io/badge/boot-systemd--boot-24362c?style=flat-square)
![btrfs snapshots](https://img.shields.io/badge/btrfs-snapshots-24362c?style=flat-square)
![fs-verity seals](https://img.shields.io/badge/fs--verity-sealed-24362c?style=flat-square)
![PubGrub solver](https://img.shields.io/badge/solver-PubGrub-c98361?style=flat-square)
![Built from source](https://img.shields.io/badge/built%20from-source-c98361?style=flat-square)

</div>

---

The joe Linux Foundation maintains **joe Linux**, an independent distribution
built from source whose goal is to be as boring as possible for the person
using it. The parts you touch are ordinary: glibc, systemd, a usr-merged file
system and GNOME on Wayland, laid out the way most people already expect. The
interesting work lives underneath, where it belongs.

## Interesting underneath

- **Upgrades that undo themselves.** An upgrade is applied to a btrfs
  snapshot at shutdown and takes effect on reboot. If the new system does not
  boot, the machine returns to the previous one by itself. The running root
  stays an ordinary, writable file system.
- **Meet dave.** A package manager written in Zig with a PubGrub solver,
  designed around that update model from day one. It shows you the plan
  before it changes anything, and tells you exactly why when something cannot
  be done.
- **Root has rules, too.** A kernel security module lets privileged
  processes run only code the distribution has signed, refuses code generated
  at run time, and holds each program to the operations it declares.

## A taste of dave

```console
$ sudo dave install gimp
Install
  babl  0.1.128-r1  (dependency)
  gegl  0.4.72-r2   (dependency)
  gimp  3.2.8-r2

3 to install. 27.0 MiB to download; 112.4 MiB more disk space will be used.
Continue? [Y/n]
```

```console
$ sudo dave upgrade     # prepared now, applied when the machine shuts down
$ sudo dave rollback    # the previous system, from the next boot onward
$ dave why zlib         # the shortest chain from something you asked for
```

## Repositories

| Repository | What's inside |
|------------|---------------|
| [**joe-linux**](https://github.com/theJoeLinuxFoundation/joe-linux) | The distribution itself: dave, every package recipe, the security module, image specs, the installer and the test suites. |
| [**.github**](https://github.com/theJoeLinuxFoundation/.github) | This profile page. |

## Where things stand

joe Linux is **alpha**. Today it:

- builds from source into a console system and a GNOME desktop that boot in a virtual machine
- passes end to end tests for upgrade, rollback, power loss and recovery
- builds a live ISO whose installer puts joe beside Windows in free space, or on a whole disk
- has been tried on only a few real machines, with no Secure Boot or disk encryption yet
- still gives services broad declarations while narrower, per-service ones are written

The full list lives in [Not done yet](https://github.com/theJoeLinuxFoundation/joe-linux#not-done-yet).
Please hold off on putting it on a machine you rely on.

## Get involved

- **Found something exciting?** That's a bug. [Open an issue](https://github.com/theJoeLinuxFoundation/joe-linux/issues/new).
- **Pull requests are welcome.** GitHub Actions runs dave's unit tests on every one.
- **Start reading** with the [README](https://github.com/theJoeLinuxFoundation/joe-linux#readme); the sources it points to are commented for readers.
- **Follow along** by starring [joe-linux](https://github.com/theJoeLinuxFoundation/joe-linux).

## Tags

[`linux`](https://github.com/topics/linux)
[`linux-distribution`](https://github.com/topics/linux-distribution)
[`operating-system`](https://github.com/topics/operating-system)
[`linux-from-scratch`](https://github.com/topics/linux-from-scratch)
[`atomic-upgrades`](https://github.com/topics/atomic-upgrades)
[`btrfs`](https://github.com/topics/btrfs)
[`systemd-boot`](https://github.com/topics/systemd-boot)
[`fs-verity`](https://github.com/topics/fs-verity)
[`linux-security-module`](https://github.com/topics/linux-security-module)
[`lsm`](https://github.com/topics/lsm)
[`package-manager`](https://github.com/topics/package-manager)
[`pubgrub`](https://github.com/topics/pubgrub)
[`zig`](https://github.com/topics/zig)
[`gnome`](https://github.com/topics/gnome)
[`qemu`](https://github.com/topics/qemu)

---

<div align="center">

<sub>Snapshot upgrades without immutability were inspired by
[Arch-silverblue](https://github.com/sinisterMage/Arch-silverblue).
joe Linux's own code is MIT licensed; the security module is GPL-2.0-only, as part of the kernel.</sub>

**Here's to nothing out of the ordinary.**

</div>
