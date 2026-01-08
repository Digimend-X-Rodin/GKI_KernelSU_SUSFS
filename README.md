### This is an automated GKI kernel build repository

> For non-GKI devices, you can try resources from [SukiSU Cloud](https://alist.shirkneko.top), does not support OnePlus ColorOS14, 15
>
> For first-time use, **please read** the following content carefully, don't waste others' time due to laziness!
>
> Recent updates: 1. OnePlus 8 ELITE processor can use 6.6 kernel (untested), 2. Fixed compilation errors for these GKI versions——[5.10.(66、81、101)、5.15.(74、94、104)]
### Download
You can [download](https://github.com/zzh20188/GKI_KernelSU_SUSFS/releases) your resources here
1. For Anykernel3.zip, download and use directly!
- Then use flashing software, such as [HorizonKernelFlasher](https://github.com/libxzr/HorizonKernelFlasher/releases) to flash the kernel
2. For boot.img, download the one that matches your kernel format (uncompressed, gz, lz4), [refer to](https://kernelsu.org/zh_CN/guide/installation.html#install-by-kernelsu-boot-image) **Find the suitable boot.img** section
- Flash using [FASTBOOT](https://magiskcn.com/), or use flashing software to flash to the boot partition of the ROOT slot (e.g., iWanJi, Kernelflasher)

### Features
| Feature | Description |
| --- | --- |
| [KernelSU](https://kernelsu.org/zh_CN/) | Including **Official, MKSU, SUKISU, NEXT** |
| [SUSFS4](https://gitlab.com/simonpunk/susfs4ksu) | Kernel-level functionality patch to assist KSU hiding |
| [BBR](https://blog.thinkin.top/archives/ke-pu-bbrdao-di-shi-shi-me) | TCP congestion control algorithm, makes network faster? |
| [Wireguard](https://zh.wikipedia.org/wiki/WireGuard) | Refer to the wiki link on the left |
| [LZ4KD](https://github.com/ShirkNeko/SukiSU_patch/tree/main/other) | Reportedly a ZRAM algorithm from HUAWEI source, patch ported by [Cloud Maple](http://www.coolapk.com/u/24963680) |

<details>

<summary>Also supports these algorithms, can switch in scene's ZRAM</summary>

### LZ4K, LZ4HC, deflate, 842, ~~zstdn~~, lz4k_oplus

</details>

### KSU Manager
After compilation is complete, you will see a file like `Next-Manager(12600)`, simply put this is the ***latest manager*** uploaded together with the kernel.
![Example](./assets/get_manager.gif)
Similarly, in [Release](https://github.com/zzh20188/GKI_KernelSU_SUSFS/releases) also contains the ***latest manager***!
![release](./assets/release_manager.gif)

### Emergency Recovery Guide

> [!IMPORTANT]
> **Trigger Conditions**  
> Recovery needs to be performed when the device cannot boot due to:  
> - Flashing incorrect/incompatible kernel
> - Kernel version adaptation exception (e.g., flashing version 233 kernel on 5.10.66)
1. Enter FASTBOOT mode

- Physical key combination: Power + Volume Down or ADB command: `adb reboot bootloader`

2. Execute flash command
```bash
$ fastboot flash boot <full boot.img filename>
```
### Methods to Obtain Original Images
1. Extract from existing firmware

- OTA package: Extract using [payload-dumper tool](https://magiskcn.com/payload-dumper-go-boot.html) after decompression

- Fastboot package: Extract boot.img directly after decompression

2. Obtain from external resources

- Community platform search: device model + original boot (e.g., XDA/Coolapk)

- [Mobile online extraction and remote acquisition](https://magiskcn.com/payload-dumper-compose.html)

> [!TIP]
> ### Kernel Version Compatibility Instructions
> 
> **1. Cross Sub-version Flashing Rules**  
> When the phone GKI major version is 5.10.x (e.g., 5.10.168), you can flash kernels with higher sub-versions of the same major version (e.g., 5.10.198).  
> Regarding **X-lts** version, taking `android12-5.10.X-lts-AnyKernel3.zip` as an example:
> - **X-lts** represents Long Term Support version (maximum sub-version number, currently 5.10.236 in this example)
> - As GKI source code updates, LTS compilation version number will continue to increase (other versions like 198 are permanently fixed)
> - ⚠️ Note: Although LTS is the latest, **latest version ≠ most stable** (e.g., 6.6.x has auto-restart BUG)
> 
> **2. Kernel Version Spoofing Method**  
> Execute in MT Manager terminal:
> ```bash
> uname -r | sed 's/^[^-]*//'
> ```
> After obtaining, copy directly, fill this version number into the Action compilation panel to achieve kernel version spoofing.
> 
> **3. Compilation Optimization Suggestions**  
> Modify [configuration file](.github/workflows/kernel-a12-5.10.yml) (e.g., kernel-a12-5.10.yml):
> - ▶️ Delete/comment out unnecessary GKI version configurations (**speeds up compilation**)
> - ➕ Add specified GKI version (refer to [customization guide](https://www.coolapk.com/feed/62820671?shareKey=OGMxYmZmNTk0YzIxNjgxNzM1MzI~&shareUid=11253396&shareFrom=com.coolapk.market_15.2.2))
> - 📅 For kernel build time, refer to the **`comments around line 490`** in [gki-kernel.yml](.github/workflows/gki-kernel.yml) file for modifications

### More Content
You can mention your suggestions... I will try!