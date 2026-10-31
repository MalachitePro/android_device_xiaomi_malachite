# Android 17 (LineageOS 24.0) for malachite (POCO X7 / Redmi Note 14 Pro 5G)

Android 17 port of the malachite device tree. Port, fixes and release builds: HUNTER[RKJAAT] (MalachitePro).
Support: https://t.me/Malachite_Pro

## Credits
- Device tree history (kept in this repo): claxten10, cmdr-chara, ArianK16a, Mashopy, bengris32, luk1337 and others, via malachite-project (maintained by noamtu123). Also puhboo and mt6878-devs, who worked on the Android 16 tree.
- Kernel and vendor blobs: cmdr-chara (Chara), malachite-project. Kernel source: https://github.com/malachite-project/kernel_manifest-6.1 (GPLv2)
- Fingerprint / UDFPS HAL (hardware/xiaomi): SebaUbuntu, bgcngm, ArianK16a, Demon000, luk1337 and the LineageOS Xiaomi contributors.
- LineageOS team for the base.
- Android 17 port, fixes and release builds: HUNTER[RKJAAT] (MalachitePro).

If you use this tree for your own ROM, please keep these credits.

## Build
Local manifest in `.repo/local_manifests/malachite.xml`:

```xml
<manifest>
  <remote name="mp" fetch="https://github.com/MalachitePro" />
  <remote name="upstream" fetch="https://github.com/malachite-project" />
  <project path="device/xiaomi/malachite" name="android_device_xiaomi_malachite" remote="mp" revision="lineage-24.0-v1.2" />
  <project path="vendor/xiaomi/malachite" name="proprietary_vendor_xiaomi_malachite" remote="mp" revision="lineage-24.0-v1.2" />
  <project path="hardware/xiaomi" name="android_hardware_xiaomi" remote="mp" revision="lineage-24.0-v1.2" />
  <project path="device/xiaomi/malachite-kernel" name="android_device_xiaomi_malachite-kernel" remote="upstream" revision="lineage-23.2" />
</manifest>
```

Run `repo sync`, then apply the patches for the LineageOS sources from the root of the source tree (Wi-Fi, face unlock and Android 17 build fixes):

```
for pair in external_libmnl:external/libmnl frameworks_base:frameworks/base frameworks_hardware_interfaces:frameworks/hardware/interfaces \
            packages_apps_Glimpse:packages/apps/Glimpse packages_apps_Settings:packages/apps/Settings system_tools_hidl:system/tools/hidl \
            hardware_mediatek:hardware/mediatek; do
  git -C "${pair#*:}" apply "$PWD/device/xiaomi/malachite/patches/${pair%%:*}.patch"
done
```

Then `breakfast malachite user` and `mka bacon`. Use the `user` variant for release builds.
