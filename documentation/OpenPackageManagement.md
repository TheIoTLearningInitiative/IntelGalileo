# Open Package Management

- [AlexT's Galileo & Edison pages](http://alextgalileo.altervista.org/package-repo-configuration-instructions.html)

```sh
root@galileo:~# cat /etc/opkg/base-feeds.conf
root@galileo:~# vi /etc/opkg/base-feeds.conf
```

```sh
src/gz all http://repo.opkg.net/galileo/repo/all
src/gz clanton http://repo.opkg.net/galileo/repo/clanton
src/gz i586 http://repo.opkg.net/galileo/repo/i586
```

```sh
root@galileo:~# opkg update
Downloading http://repo.opkg.net/galileo/repo/all/Packages.gz.
Inflating http://repo.opkg.net/galileo/repo/all/Packages.gz.
Updated list of available packages in /var/lib/opkg/all.
Downloading http://repo.opkg.net/galileo/repo/clanton/Packages.gz.
Inflating http://repo.opkg.net/galileo/repo/clanton/Packages.gz.
Updated list of available packages in /var/lib/opkg/clanton.
Downloading http://repo.opkg.net/galileo/repo/i586/Packages.gz.
Inflating http://repo.opkg.net/galileo/repo/i586/Packages.gz.
Updated list of available packages in /var/lib/opkg/i586.
Downloading http://iotdk.intel.com/repos/1.5/iotdk/all/Packages.
Updated list of available packages in /var/lib/opkg/iotdk-all.
Downloading http://iotdk.intel.com/repos/1.5/iotdk/i586/Packages.
Updated list of available packages in /var/lib/opkg/iotdk-i586.
Downloading http://iotdk.intel.com/repos/1.5/iotdk/quark/Packages.
Updated list of available packages in /var/lib/opkg/iotdk-quark.
Downloading http://iotdk.intel.com/repos/1.5/iotdk/x86/Packages.
Updated list of available packages in /var/lib/opkg/iotdk-x86.
Downloading http://iotdk.intel.com/repos/1.5/intelgalactic/Packages.
Updated list of available packages in /var/lib/opkg/mraa-upm.
root@galileo:~#
```

