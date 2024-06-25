![SkylineUI](https://github.com/SkylineUI/manifest/raw/aosp-14/SkylineUIBanner.png)

# Manifest SkylineUI #

### Install Git LFS ###

It is necessary to install Git LFS to avoid problems with gapps and repositories that are uploaded with Git LFS.

*Avoid this step if you already have Git LFS installed*.

```bash
sudo apt install git-lfs
git lfs install
```

### Sync SkylineUI Source ###

```bash
# Initialize local repository

mkdir SkylineUI
cd SkylineUI
```

- Repo Init Source
```bash
repo init -u https://github.com/SkylineUI/manifest -b aosp-14 --git-lfs
```

Now we proceed with the synchronization of the source with the following command:
```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```
**Note:** To save space and reduce download time during the synchronization process, you can also pass `--depth 1` to the `repo sync` command. However, using `--depth 1` will result in the repositories being synced without any commit history.

### Build ###

```bash

# Set up environment
$ . build/envsetup.sh

# Choose a target
$ lunch aosp_$device-ap2a-userdebug

# Build the code
$ mka bacon -j$(nproc --all)
```

# Build Flags
It will be your decision and if the device supports it `true/false` any of the following flags

`You must add these flags in aosp_$device.mk`

| Flag                          |Function                       |
|-------------------------------|-------------------------------|
TARGET_BOOT_ANIMATION_RES := 1080 | Specifies the resolution of the boot animation |
TARGET_FACE_UNLOCK_SUPPORTED := true | To use Face Unlock |
TARGET_CALL_RECORDING_SUPPORTED := true | To record calls on the Google dialer |
PRODUCT_NO_CAMERA := false | Use `false` to remove Aperture |

# Credits:

| Projects                      |
|-------------------------------|
| **Android Open Source Project** |
| [**PixelOS**](https://github.com/PixelOS-AOSP) |
| [**LineageOS**](https://github.com/LineageOS) |
| [**DerpFest**](https://github.com/DerpFest-AOSP) |
| [**YAAP**](https://github.com/yaap) |
