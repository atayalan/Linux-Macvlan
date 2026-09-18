# Linux-Macvlan
Macvlan Linux driver to embed the stripped VLAN header information in to SKB

## v0.0.2

This branch supports building the module for Ubuntu kernel `7.0.0-31-generic`.
Build it on a host running the target kernel:

```sh
make clean
make
```

The Makefile uses the running kernel's headers through `uname -r`.
