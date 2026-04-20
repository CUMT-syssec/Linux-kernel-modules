# Build Notes

## Baseline

The published binary modules in the repository root were built against:

- Kernel: `5.15.0-139-generic`
- Toolchain: `gcc-9 (Ubuntu 9.4.0-1ubuntu1~20.04.2)`

Published root-level `.ko` files:

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

## Source Provenance

Linux module source recovery was published from the local Ubuntu kernel source
workspace at `.cache/ubuntu-5.15.0-139-src`.

`nvidia.ko` source recovery was published from the local NVIDIA open kernel
module workspace at `.cache/nvidia-open`.

Only the recovered source trees were copied into `sources/`. Generated build
artifacts such as `.o`, `.ko`, `.cmd`, `Module.symvers`, and `modules.order`
were stripped during publication.

## Local Compatibility Notes

The cleaned `sources/` tree preserves the compatibility edits that were used in
the local workspace:

- `sources/i40e/i40e_main.c`
  Maps `irq_update_affinity_hint()` to `irq_set_affinity_hint()` for the local
  Ubuntu `5.15.0-139` headers.
- `sources/nfs/internal.h`
  Adds fallback definitions for `NFS_CAP_CASE_INSENSITIVE`,
  `NFS_FSDATA_BLOCKED`, and `nfs_fhandle_hash()` while attempting local NFS
  module builds.

## Source-Only Modules

The cleaned snapshot keeps the following recovered source trees without
publishing matching root-level `.ko` binaries:

- `sources/ext4`
- `sources/fat`
- `sources/nfs`

These stayed source-only because the local publication target was reduced to the
useful built module set, and the original root placeholders were zero-byte
stubs rather than real binaries.
