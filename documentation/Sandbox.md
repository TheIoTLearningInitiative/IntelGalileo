# Sandbox

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
