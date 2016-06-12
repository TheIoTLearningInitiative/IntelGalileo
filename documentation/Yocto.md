# Yocto

```sh
xe1gyq@jessie:~/Galileo$ git clone git://git.yoctoproject.org/poky
Cloning into 'poky'...
remote: Counting objects: 322331, done.
remote: Compressing objects: 100% (78519/78519), done.
remote: Total 322331 (delta 238233), reused 321932 (delta 237835)
Receiving objects: 100% (322331/322331), 123.57 MiB | 611.00 KiB/s, done.
Resolving deltas: 100% (238233/238233), done.
Checking connectivity... done.
xe1gyq@jessie:~/Galileo$ cd poky
xe1gyq@jessie:~/Galileo/poky$ git checkout -b krogoth origin/krogoth
Branch krogoth set up to track remote branch krogoth from origin.
Switched to a new branch 'krogoth'
xe1gyq@jessie:~/Galileo/poky$ 
```

```sh
xe1gyq@jessie:~/Galileo/poky$ git clone git://git.yoctoproject.org/meta-intel
Cloning into 'meta-intel'...
remote: Counting objects: 12302, done.
remote: Compressing objects: 100% (3779/3779), done.
remote: Total 12302 (delta 7080), reused 12275 (delta 7053)
Receiving objects: 100% (12302/12302), 3.96 MiB | 608.00 KiB/s, done.
Resolving deltas: 100% (7080/7080), done.
Checking connectivity... done.
xe1gyq@jessie:~/Galileo/poky$ cd meta-intel/
xe1gyq@jessie:~/Galileo/poky/meta-intel$ git checkout -b krogoth origin/krogoth
Branch krogoth set up to track remote branch krogoth from origin.
Switched to a new branch 'krogoth'
xe1gyq@jessie:~/Galileo/poky/meta-intel$ 
```

```sh
xe1gyq@jessie:~/Galileo/poky$ source oe-init-build-env
You had no conf/local.conf file. This configuration file has therefore been
created for you with some default values. You may wish to edit it to, for
example, select a different MACHINE (target hardware). See conf/local.conf
for more information as common configuration options are commented.

You had no conf/bblayers.conf file. This configuration file has therefore been
created for you with some default values. To add additional metadata layers
into your configuration please add entries to conf/bblayers.conf.

The Yocto Project has extensive documentation about OE including a reference
manual which can be found at:
    http://yoctoproject.org/documentation

For more information about OpenEmbedded see their website:
    http://www.openembedded.org/


### Shell environment set up for builds. ###

You can now run 'bitbake <target>'

Common targets are:
    core-image-minimal
    core-image-sato
    meta-toolchain
    meta-ide-support

You can also run generated qemu images with a command like 'runqemu qemux86'
```

```sh
xe1gyq@jessie:~/Galileo/poky/build$ bitbake-layers add-layer "$HOME/Galileo/poky/meta-intel"
xe1gyq@jessie:~/Galileo/poky/build$ echo 'MACHINE = "intel-quark"' >> conf/local.conf
xe1gyq@jessie:~/Galileo/poky/build$ 
```

```sh
xe1gyq@jessie:~/Galileo/poky/build$ bitbake core-image-minimal
Parsing recipes: 100% |#########################################| Time: 00:01:20
Parsing of 886 .bb files complete (0 cached, 886 parsed). 1317 targets, 48 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies

Build Configuration:
BB_VERSION        = "1.30.0"
BUILD_SYS         = "i686-linux"
NATIVELSBSTRING   = "Debian-8.3"
TARGET_SYS        = "i586-poky-linux"
MACHINE           = "intel-quark"
DISTRO            = "poky"
DISTRO_VERSION    = "2.1"
TUNE_FEATURES     = "m32 i586-nlp"
TARGET_FPU        = ""
meta              
meta-poky         
meta-yocto-bsp    = "krogoth:8f51f6153a09f8048fb4c4ce9cf4a19655240de4"
meta-intel        = "krogoth:58b8e0f2e6c4f6566983baf4bc980a86592398ad"

NOTE: Fetching uninative binary shim from http://downloads.yoctoproject.org/releases/uninative/0.95/i686-nativesdk-libc.tar.bz2;sha256sum=5f27d7e0f4dd2ed80a7ff6a0d88af107b08e00765b31ed3aa180cc5ce15b0811
NOTE: Preparing RunQueue
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
Currently 2 running tasks (65 of 2378):
0: libtool-native-2.4.6-r0 do_configure (pid 27070)
1: gcc-source-5.3.0-5.3.0-r0 do_fetch (pid 27129)
...
NOTE: Fetching uninative binary shim from http://downloads.yoctoproject.org/releases/uninative/0.95/i686-nativesdk-libc.tar.bz2;sha256sum=5f27d7e0f4dd2ed80a7ff6a0d88af107b08e00765b31ed3aa180cc5ce15b0811
NOTE: Preparing RunQueue
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
NOTE: Tasks Summary: Attempted 2378 tasks of which 15 didn't need to be rerun and all succeeded.
```

```sh
xe1gyq@jessie:~/Galileo/poky/build$ ls
bitbake.lock  cache  conf  downloads  sstate-cache  tmp
xe1gyq@jessie:~/Galileo/poky/build$ ls tmp/deploy/images/intel-quark/
bzImage
bzImage--4.4.3+git0+9ab4787fe2_076cc85486-r0-intel-quark-20160612054437.bin
bzImage-intel-quark.bin
core-image-minimal-initramfs-intel-quark-20160612054437.rootfs.cpio.gz
core-image-minimal-initramfs-intel-quark-20160612054437.rootfs.manifest
core-image-minimal-initramfs-intel-quark.cpio.gz
core-image-minimal-initramfs-intel-quark.manifest
core-image-minimal-intel-quark-20160612054437.hddimg
core-image-minimal-intel-quark-20160612054437.iso
core-image-minimal-intel-quark-20160612054437.rootfs.ext4
core-image-minimal-intel-quark-20160612054437.rootfs.manifest
core-image-minimal-intel-quark.ext4
core-image-minimal-intel-quark.hddimg
core-image-minimal-intel-quark.iso
core-image-minimal-intel-quark.manifest
gummibootia32.efi
microcode_20151106.cpio
microcode.cpio
modules--4.4.3+git0+9ab4787fe2_076cc85486-r0-intel-quark-20160612054437.tgz
modules-intel-quark.tgz
README_-_DO_NOT_DELETE_FILES_IN_THIS_DIRECTORY.txt
xe1gyq@jessie:~/Galileo/poky/build$ 
```

```sh
dd if=/dev/zero of=/dev/sdf bs=1M count=512
../meta-intel-iot-devkit/scripts/wic_monkey create -e core-image-minimal ../meta-intel-iot-devkit/scripts/lib/image/canned-wks/iot-devkit.wks
```

```sh

```

## Not Working

- [Creating a Yocto Image for Inteñ® Galileo Board Using Split Layers](https://software.intel.com/en-us/blogs/2015/03/04/creating-a-yocto-image-for-the-intel-galileo-board-using-split-layers)

```sh
xe1gyq@jessie:~/Galileo$ git clone git://git.yoctoproject.org/poky iotdk
Cloning into 'iotdk'...
remote: Counting objects: 322331, done.
remote: Compressing objects: 100% (78519/78519), done.
Receiving objects: 100% (322331/322331), 123.57 MiB | 354.00 KiB/s, done.
Resolving deltas: 100% (238233/238233), done.
Checking connectivity... done.
xe1gyq@jessie:~/Galileo$ cd iotdk/
```

```sh
xe1gyq@jessie:~/Galileo/iotdk$ git clone git://git.yoctoproject.org/meta-intel-quark
Cloning into 'meta-intel-quark'...
remote: Counting objects: 439, done.
remote: Compressing objects: 100% (257/257), done.
remote: Total 439 (delta 142), reused 428 (delta 131)
Receiving objects: 100% (439/439), 813.81 KiB | 467.00 KiB/s, done.
Resolving deltas: 100% (142/142), done.
Checking connectivity... done.
xe1gyq@jessie:~/Galileo/iotdk$ 
```

```sh
xe1gyq@jessie:~/Galileo/iotdk$ git clone git://git.yoctoproject.org/meta-intel-iot-middleware
Cloning into 'meta-intel-iot-middleware'...
remote: Counting objects: 1113, done.
remote: Compressing objects: 100% (611/611), done.
remote: Total 1113 (delta 560), reused 957 (delta 406)
Receiving objects: 100% (1113/1113), 5.62 MiB | 745.00 KiB/s, done.
Resolving deltas: 100% (560/560), done.
Checking connectivity... done.
xe1gyq@jessie:~/Galileo/iotdk$ 
```

```sh
xe1gyq@jessie:~/Galileo/iotdk$ git clone git://git.yoctoproject.org/meta-intel-galileo
Cloning into 'meta-intel-galileo'...
remote: Counting objects: 160, done.
remote: Compressing objects: 100% (98/98), done.
remote: Total 160 (delta 50), reused 151 (delta 41)
Receiving objects: 100% (160/160), 180.42 KiB | 233.00 KiB/s, done.
Resolving deltas: 100% (50/50), done.
Checking connectivity... done.
```

```sh
xe1gyq@jessie:~/Galileo/iotdk$ git clone git://git.yoctoproject.org/meta-intel-iot-devkit
Cloning into 'meta-intel-iot-devkit'...
remote: Counting objects: 224894, done.
remote: Compressing objects: 100% (57451/57451), done.
remote: Total 224894 (delta 162433), reused 224748 (delta 162287)
Receiving objects: 100% (224894/224894), 108.63 MiB | 984.00 KiB/s, done.
Resolving deltas: 100% (162433/162433), done.
Checking connectivity... done.
xe1gyq@jessie:~/Galileo/iotdk$ 
```

```sh
xe1gyq@jessie:~/Galileo/iotdk$ git clone http://github.com/openembedded/meta-openembedded.git meta-oe
Cloning into 'meta-oe'...
remote: Counting objects: 61741, done.
remote: Compressing objects: 100% (300/300), done.
remote: Total 61741 (delta 129), reused 18 (delta 18), pack-reused 61409
Receiving objects: 100% (61741/61741), 26.24 MiB | 939.00 KiB/s, done.
Resolving deltas: 100% (35595/35595), done.
Checking connectivity... done.
xe1gyq@jessie:~/Galileo/iotdk$ 
```

```sh
xe1gyq@jessie:~/Galileo/iotdk$ source oe-init-build-env

You had no conf/local.conf file. This configuration file has therefore been
created for you with some default values. You may wish to edit it to, for
example, select a different MACHINE (target hardware). See conf/local.conf
for more information as common configuration options are commented.

You had no conf/bblayers.conf file. This configuration file has therefore been
created for you with some default values. To add additional metadata layers
into your configuration please add entries to conf/bblayers.conf.

The Yocto Project has extensive documentation about OE including a reference
manual which can be found at:
    http://yoctoproject.org/documentation

For more information about OpenEmbedded see their website:
    http://www.openembedded.org/


### Shell environment set up for builds. ###

You can now run 'bitbake <target>'

Common targets are:
    core-image-minimal
    core-image-sato
    meta-toolchain
    meta-ide-support

You can also run generated qemu images with a command like 'runqemu qemux86'
xe1gyq@jessie:~/Galileo/iotdk/build$ 
```

```sh
xe1gyq@jessie:~/Galileo/iotdk/build$ ls
conf
xe1gyq@jessie:~/Galileo/iotdk/build$ nano conf/bblayers.conf 
```

```sh
# POKY_BBLAYERS_CONF_VERSION is increased each time build/conf/bblayers.conf
# changes incompatibly
POKY_BBLAYERS_CONF_VERSION = "2"

LCONF_VERSION = "6"

BBPATH = "${TOPDIR}"
BBFILES ?= ""

BBLAYERS ?= " \
  /home/xe1gyq/Galileo/iotdk/meta \
  /home/xe1gyq/Galileo/iotdk/meta-poky \
  /home/xe1gyq/Galileo/iotdk/meta-yocto-bsp \
  /home/xe1gyq/Galileo/iotdk/meta-oe/meta-oe \
  /home/xe1gyq/Galileo/iotdk/meta-oe/meta-filesystems \
  /home/xe1gyq/Galileo/iotdk/meta-intel-quark \
  /home/xe1gyq/Galileo/iotdk/meta-intel-galileo \
  /home/xe1gyq/Galileo/iotdk/meta-intel-iot-middleware \
  /home/xe1gyq/Galileo/iotdk/meta-intel-iot-devkit \
  "
```

```sh
xe1gyq@jessie:~/Galileo/iotdk/build$ nano conf/local.conf
```
