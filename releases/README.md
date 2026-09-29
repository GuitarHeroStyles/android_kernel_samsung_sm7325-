# Flashable builds

## SukiSU-Ultra_SUSFS-v2.3.0_a52sxq_A528BXXSAGYA2_20260929.zip

TWRP-flashable zip for Galaxy A52s (SM-A528B, a52sxq), built from branch
`sep-17/SukiSU-Ultra` of this repo: **SukiSU-Ultra (builtin) + SUSFS v2.3.0**
on top of QGKI 5.4, repacked against firmware base **A528BXXSAGYA2**.

Contains a repacked `boot.img` (new kernel `Image`), `vendor_boot.img`
(new DTB), and stock `dtbo.img` -- all three sourced from the
A528BXXSAGYA2 firmware itself.

**Before flashing:**
- Confirm your device is running firmware A528BXXSAGYA2 (Settings ->
  About phone -> Software information).
- Back up your current boot/dtbo/vendor_boot partitions in TWRP first.
- Not yet flash-tested on real hardware -- verified only by a full clean
  cross-compile + link (zero errors) with the AOSP prebuilt
  clang-r383902b1 toolchain.
- Vendor kernel modules (wifi/camera/etc DLKMs) are left untouched by the
  installer; it does not repackage `/vendor/lib/modules`.
- `CONFIG_KSU_SUSFS_OPEN_REDIRECT` is disabled (its VFS hook wasn't
  safely portable to this kernel's older `path_openat()`/`do_last()`).
