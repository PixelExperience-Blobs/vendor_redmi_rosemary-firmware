# Firmware tree for `rosemary`

## What is this?

A firmware tree to...ship firmware with builds for the
Redmi Note 10S and 11 SE?

# Getting started

First of all, ensure you have cloned this into
`vendor/redmi/rosemary-firmware`.

Manifest:

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <remote name="yourremote" fetch="https://gitlab.pixelexperience.org/android/vendor-blobs" revision="thirteen" clone-depth="1" />
    <project name="vendor_redmi_rosemary-firmware" path="vendor/redmi/rosemary-firmware" remote="yourremote" />
</manifest>
```

Device tree dependencies file:

```
[
  {
    "remote": "yourremote",
    "repository": "vendor_redmi_rosemary-firmware",
    "target_path": "vendor/redmi/rosemary-firmware",
    "branch": "thirteen",
    "clone_depth": "1"
  }
]
```

Manual cloning:

```bash
git clone https://gitlab.pixelexperience.org/android/vendor-blobs/vendor_redmi_rosemary-firmware -b eleven vendor/redmi/rosemary-firmware --depth=1 --no-tags --single-branch
```

> These are example entries, you need to replace the relevant stuff
> with your own case.

After that, ensure your tree's BoardConfig inherits this tree's BoardConfigVendor:

```makefile
include vendor/redmi/rosemary-firmware/BoardConfigVendor.mk
```

> These kinds of includes are typically placed along with other
> inherits at the beginning of BoardConfig or at the end of
> BoardConfig, along with other includes if any.

And lastly, build:

```bash
source build/vendorsetup.sh
lunch rom_codename-variant
m otapackage
```

> Of course replace `rom_codename-variant` and `otapackage` with the
> relevant stuff from ROM manifest/guide.

# Additional information for geeks

## Firmware

**ROM**: MIUI

**Version**: 12.5.19.0.RKLINXM

## Compatibility

**Android version compatibility**:
* All Android 11 ROMs
* Android 12 ROMs based on MIUI 12.5.x.x.RKL..XM blobs
* Android 13 ROMs based on MIUI 12.5.x.x.RKL..XM blobs

**Recovery compatibility**:
* All TWRP variants
* All OrangeFox variants
* Custom ROMs' own recoveries

**MIUI version compatibility**: Any MIUI version.

**Variant compatibility**:
* `rosemary` (Redmi Note 10S Global/NFC)
* `secret` (Redmi Note 10S/11 SE India)
* `maltose` (Redmi Note 10S Latin America)
