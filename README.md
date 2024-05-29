<h1 align="center">
  <br>
  pcids: Get PCI Bus IDs for video cards
  <br>
</h1>

## What is it?

`pcids` displays PCI Bus IDs suitable for [use in `xorg.conf`](https://man.archlinux.org/man/xorg.conf.5.en#BusID).
If you use NixOS, you might use these IDs in the following settings:
* `hardware.nvidia.prime.amdgpuBusId`
* `hardware.nvidia.prime.intelBusId`
* `hardware.nvidia.prime.nvidiaBusId`

## Why not just use `lspci`?

You can, of course; in fact, this tool uses `lspci` underneath.
However, `lspci` outputs IDs in hex:

```
$ lspci -nn -d '*:*:03xx'
2d:00.0 VGA compatible controller [0300]: Intel Corporation DG2 [Arc A770] [8086:56a0] (rev 08)
```

whereas `pcids` produces a more directly usable format:

```
PCI:45:0:0	Intel Corporation [8086]	DG2 [Arc A770] [56a0]
```

## Usage

```sh
nix --experimental-features "flakes nix-command" run github:eclairevoyant/pcids
```
