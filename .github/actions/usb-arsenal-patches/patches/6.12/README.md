# patches/6.12 — USB-Arsenal set for android16-6.12 (target: 6.12.92, 2026-09)

Selected from upstream https://github.com/ravindu644/USB-Arsenal `kernel-patches/`,
minus patches already upstream at 6.12.92 (those are omitted, never forced).
Applied in filename-sort order via `patch -p1` from `kernel/common`.
Verified with `patch --dry-run` against the in-tree 6.12.92 sources
(`kernels/android16-6.12/common`).

| File | Upstream origin | Note |
|---|---|---|
| 0001-usb-gadget-android_configfs_uevent-unregister-the-ga.patch | `kernel-patches/6.6/0001` (cross-version carry-forward; byte-identical to `patches/6.6/0001`) | applies, offset -4 |
| 0002-pikvm-msd-dvd-support.patch | `kernel-patches/6.12/0001` (renumbered 0001→0002 to keep configfs-first order) | applies, offset -3 |

Intentionally ABSENT (already upstream in 6.12.92, do not re-add):

- `kernel-patches/6.6/0003` (f_hid move-list/spinlock inits): inits already live
  in `hidg_alloc()` in this tree; no `cdev_init()` in the bind path either, so
  the 6.6 `0004` cdev_init fix is upstream too.
- No writable-bInterval patch exists upstream for 6.12 (`bInterval` stays
  hardcoded with FIXME in `f_hid.c`), so `hid --interval` warns. Expected
  limitation.
