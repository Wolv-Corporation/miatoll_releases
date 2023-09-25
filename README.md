## Miatoll Kernel Releases
* Updated frequently with latest Linux, AOSP and Qualcomm changes.
* Linux Kernel Version: `v4.14.275`
* Qualcomm TAG: `LA.UM.9.1.r1-11900-SMxxx0.0`
* Supported Android Version: `11-12`
* Latest release codename: `Permafrost`
* ZIP flashable file in `Github Releases`
## Built-in drivers
It is known that Xiaomi shipped their kernel without `WIFI` and `AUDIO` drivers. These drivers can be acquired from **Codelinaro** git repository.
These drivers are built-in inside the kernel, and they are updated with latest changes from `QUALCOMM` for maximum ***PERFORMANCE*** and ***STABILITY***
## Data Drivers from Qualcomm
**RMNET** performance drivers are included too, which optimize and improve mobile data speed drastically.
## Built-in modules
* [QCACLD-3.0](https://git.codelinaro.org/clo/la/platform/vendor/qcom-opensource/wlan/qcacld-3.0)
* [FW-API](https://git.codelinaro.org/clo/la/platform/vendor/qcom-opensource/wlan/fw-api)
* [QCA-WIFI-HOST-CMN](https://git.codelinaro.org/clo/la/platform/vendor/qcom-opensource/wlan/qca-wifi-host-cmn)
* [AUDIO-KERNEL](https://git.codelinaro.org/clo/la/platform/vendor/opensource/audio-kernel)
* [RMNET-PERF-KERNEL](https://git.codelinaro.org/clo/la/platform/vendor/qcom-opensource/data-kernel)
* [Qualcomm Android Base Kernel](https://wiki.codelinaro.org/en/clo/la/release)

You need to know your current kernel Qualcomm TAG, you can find it in OEM github by checking commit history. After you know the base tag, you can then upstream to newer version.

### **EXAMPLE** 
* LA.UM.9.1.r1-11900-SMxxx0.0
* `LA = LinuxAndroid`
* `UM = Random 2-WORD declared by Qualcomm`
* `9.1.r1 = Android Version 9, release QPR1`
* `11900 = Qualcomm PATCHLEVEL`
* `SMxxx0.0 = Qualcomm Chipset Code`

You can also build these drivers as modules, but it is hard to add them to vendor partition on MIUI system because these partitions are read-only, and cannot be edited except by editing whole super partition.
On AOSP, this is not the case, so you can remount read-write the vendor partition, and add module **.ko** files to `/vendor/lib/modules`.

After building the kernel, run `make INSTALL_MOD_STRIP=1 modules_install`. You can then find the module files in `vX.XX.XXX` folder, this folder name is the same as the kernel version.
