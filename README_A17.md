# Android 17 (LineageOS 24.0) for malachite (POCO X7 / Redmi Note 14 Pro 5G)

This branch is the Android 17 port of the malachite device tree. Android 17 port, fixes and release builds: HUNTER[RKJAAT] (MalachitePro).
Support: https://t.me/Malachite_Pro

## Credits
- The Android 16 (LineageOS 23.2) device tree is from malachite-project, puhboo, mt6878-devs and cmdr-chara. Thanks to them, their commits are kept in this history.
- LineageOS team for the base.
- Prebuilt kernel: https://github.com/malachite-project/kernel_manifest-6.1 (GPLv2)

If you use this tree for your own ROM, please keep these credits.

## Build
Add a local manifest in `.repo/local_manifests/malachite.xml`:

```xml
<manifest>
  <remote name="mp" fetch="https://github.com/MalachitePro" />
  <remote name="upstream" fetch="https://github.com/malachite-project" />
  <project path="device/xiaomi/malachite" name="android_device_xiaomi_malachite" remote="mp" revision="lineage-24.0" />
  <project path="vendor/xiaomi/malachite" name="proprietary_vendor_xiaomi_malachite" remote="mp" revision="lineage-24.0" />
  <project path="hardware/xiaomi" name="android_hardware_xiaomi" remote="mp" revision="lineage-24.0" />
  <project path="device/xiaomi/malachite-kernel" name="android_device_xiaomi_malachite-kernel" remote="upstream" revision="lineage-23.2" />
</manifest>
```

Then `repo sync`, `breakfast malachite user` and `mka bacon`. Use the `user` variant for release builds.
