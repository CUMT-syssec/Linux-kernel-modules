# Kernel Module Source Collection

This directory contains the cleaned, materialized source trees corresponding to
the kernel module workspace in the repository root.

## Provenance

Linux module sources were extracted from the local Ubuntu HWE kernel source tree
for `5.15.0-139`:

- Source base: `.cache/ubuntu-5.15.0-139-src`
- Kernel family: `5.15.0-139-generic`

`nvidia.ko` was extracted from the local NVIDIA open GPU kernel module source
workspace:

- Source base: `.cache/nvidia-open`

All copied source trees were filtered to remove generated build artifacts such
as `.o`, `.cmd`, `.ko`, `Module.symvers`, `modules.order`, and temporary build
directories.

## Local Index

| Binary / target | Published source path | Source base path | Status |
| --- | --- | --- | --- |
| `amdgpu.ko` | `sources/amdgpu` | `drivers/gpu/drm/amd/amdgpu` | binary + source |
| `ast.ko` | `sources/ast` | `drivers/gpu/drm/ast` | binary + source |
| `drm.ko` | `sources/drm` | `drivers/gpu/drm` core files | binary + source |
| `e1000.ko` | `sources/e1000` | `drivers/net/ethernet/intel/e1000` | binary + source |
| `e1000e.ko` | `sources/e1000e` | `drivers/net/ethernet/intel/e1000e` | binary + source |
| `ext4` | `sources/ext4` | `fs/ext4` | source only |
| `fat` | `sources/fat` | `fs/fat` | source only |
| `fm10k.ko` | `sources/fm10k` | `drivers/net/ethernet/intel/fm10k` | binary + source |
| `gfs2.ko` | `sources/gfs2` | `fs/gfs2` | binary + source |
| `i40e.ko` | `sources/i40e` | `drivers/net/ethernet/intel/i40e` | binary + source |
| `i915.ko` | `sources/i915` | `drivers/gpu/drm/i915` | binary + source |
| `igb.ko` | `sources/igb` | `drivers/net/ethernet/intel/igb` | binary + source |
| `igc.ko` | `sources/igc` | `drivers/net/ethernet/intel/igc` | binary + source |
| `nfs` | `sources/nfs` | `fs/nfs` | source only |
| `nouveau.ko` | `sources/nouveau` | `drivers/gpu/drm/nouveau` | binary + source |
| `nvidia.ko` | `sources/nvidia` | `kernel-open/nvidia`, `src/nvidia`, `src/common` | binary + source |
| `ttm.ko` | `sources/ttm` | `drivers/gpu/drm/ttm` | binary + source |
| `xfs.ko` | `sources/xfs` | `fs/xfs` | binary + source |

## Notes

- `sources/drm` intentionally contains the DRM core files only. Driver-specific
  DRM subtrees are published under their own directories such as `amdgpu`,
  `i915`, `nouveau`, and `ttm`.
- `sources/i40e` and `sources/nfs` include the local compatibility shims that
  were used while building against the installed Ubuntu `5.15.0-139` headers.
- The `source only` entries are kept because they were part of the recovery
  workflow, but their root-level placeholder `.ko` files were dropped from this
  cleaned repository snapshot.
