# joe Linux

An independent distribution built from source. glibc, systemd, a usr-merged
btrfs file system and GNOME on Wayland.

Boring, on purpose.

The parts you touch are ordinary. Three things underneath are not.

## Upgrades roll back by themselves

An upgrade is applied to a btrfs snapshot as the machine shuts down and takes
effect on reboot. If the new system does not boot, the machine returns to the
previous one by itself. The running root stays an ordinary writable file
system, and `/home` and `/var` are shared by every version of it.

## dave

The package manager, written in Zig around that update model, with a PubGrub
solver. It shows the plan before changing anything, and when a request cannot be
met it says why, in sentences.

## Root runs only signed code

A kernel security module lets privileged processes run only code the
distribution has signed, refuses memory made executable at run time, and holds
each program to the operations it declares. On an installed system it logs what
it would refuse. Starting the kernel with `joe=enforce` turns that into refusal.

## Repositories

- [joe-linux](https://github.com/theJoeLinuxFoundation/joe-linux): dave, the
  package recipes, the security module, image specs, the installer, the tests.
- [.github](https://github.com/theJoeLinuxFoundation/.github): this page.

## Status

Alpha. Today it builds from source into a console system and a GNOME desktop
that boot in a virtual machine, passes end to end tests for upgrade, rollback,
power loss and recovery, and builds a live ISO whose installer can put joe in
free space beside Windows or across a whole disk.

Not yet: real hardware beyond a handful of machines, Secure Boot, disk
encryption, and per-service security declarations. The full list is in the
[joe-linux README](https://github.com/theJoeLinuxFoundation/joe-linux#not-done-yet).

Please do not put it on a machine you rely on.

## Contributing

Issues are welcome, and hardware reports are the most useful kind: the model,
the CPU, the GPU, the Wi-Fi chipset, and what broke. Pull requests run dave's
unit tests in CI. Start from the
[joe-linux README](https://github.com/theJoeLinuxFoundation/joe-linux#readme).

---

The upgrade model was inspired by
[Arch-silverblue](https://github.com/sinisterMage/Arch-silverblue). joe's own
code is MIT licensed; the security module is GPL-2.0-only, being part of the
kernel.
