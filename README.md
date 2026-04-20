# Linux Kernel Modules Collection

This repository is a cleaned publication snapshot for a Linux kernel module
recovery/build workspace.

The repository intentionally keeps only:

- published `.ko` binaries in the repository root
- recovered source trees in [`sources/`](sources/README.md)
- lightweight documentation in [`docs/`](docs/BUILD_NOTES.md)

Large binary modules are tracked with Git LFS. Build caches, temporary trees,
and offline source mirrors are excluded from version control.

## Build Baseline

Published binary modules were built against:

- Kernel: `5.15.0-139-generic`
- Toolchain: `gcc-9 (Ubuntu 9.4.0-1ubuntu1~20.04.2)`

Published `.ko` binaries in the repository root:

- `amdgpu.ko`
- `ast.ko`
- `drm.ko`
- `e1000.ko`
- `e1000e.ko`
- `fm10k.ko`
- `gfs2.ko`
- `i40e.ko`
- `i915.ko`
- `igb.ko`
- `igc.ko`
- `nouveau.ko`
- `nvidia.ko`
- `ttm.ko`
- `xfs.ko`

Recovered source-only entries:

- `sources/ext4`
- `sources/fat`
- `sources/nfs`

## Repository Layout

- Root: published `.ko` artifacts
- [`sources/`](sources/README.md): recovered per-module source trees with
  generated build artifacts stripped out
- [`docs/BUILD_NOTES.md`](docs/BUILD_NOTES.md): build baseline, source
  provenance, and local compatibility notes

## Notes

- `drm.ko` is represented by the DRM core source files under `sources/drm`.
  Driver-specific DRM trees such as `amdgpu`, `i915`, `nouveau`, and `ttm`
  are published separately.
- `nvidia.ko` source recovery is published under `sources/nvidia/` from the
  NVIDIA open GPU kernel module source snapshot used in the local workspace.
- `ext4`, `fat`, and `nfs` are kept as recovered source trees only; they are
  not published as root-level `.ko` files in this cleaned snapshot.

## Usage

Load a published module on a matching kernel with:

```bash
sudo modprobe <module_name>
```

Kernel modules must match the running kernel ABI. Loading incompatible modules
may fail or destabilize the target system.
