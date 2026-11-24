# Linux-Macvlan
Macvlan Linux driver to embed the stripped VLAN header information in to SKB

## v0.0.2

This branch builds the module for the Ubuntu 24.04 kernels: GA 6.8
(`6.8.0-149-generic`) and HWE 7.0 (`7.0.0-31-generic`, `7.0.0-43-generic`).
`macvlan.c` is Ubuntu's `drivers/net/macvlan.c` with the Ataya change; the
6.8 and 7.0 API differences are selected with `LINUX_VERSION_CODE`.

The Ataya change puts the stripped 802.1Q tag back into received frames, only
for macvlan devices whose name contains `xdp` (the BESS XDP devices), as the
5.15 module on `v0.0.1` does.

Build it on a host running the target kernel:

```sh
make clean
make
```

The Makefile uses the running kernel's headers through `uname -r`. To build for
another installed kernel, pass its version and the compiler that built it:

```sh
make KVERSION=7.0.0-43-generic CC=x86_64-linux-gnu-gcc-13
```
