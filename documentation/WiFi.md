# WiFi

- [Internet Connectivity Galileo](https://software.intel.com/en-us/internet-connectivity-galileo)
  - Ethernet Connectivity
  - Integrated WiFi
    - Connecting to a WiFi Network
    - Providing an Access Point  

```sh
root@galileo:~# ifconfig
enp0s20f6 Link encap:Ethernet  HWaddr 98:4F:EE:01:77:6D
          inet6 addr: fe80::9a4f:eeff:fe01:776d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:280 (280.0 B)
          Interrupt:50 Base address:0xc000

enp0s20f6:avahi Link encap:Ethernet  HWaddr 98:4F:EE:01:77:6D
          inet addr:169.254.7.44  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:50 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:121600 (118.7 KiB)  TX bytes:121600 (118.7 KiB)
```

```sh
root@galileo:~# dmesg
[  398.670181] usb 1-1: new high-speed USB device number 3 using ehci-pci
[  398.980186] usb 1-1: reset high-speed USB device number 3 using ehci-pci
[  399.187909] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[  399.304607] systemd-udevd[279]: renamed network interface wlan0 to wlp0s20f3u1
```

```sh
root@galileo:~# connmanctl
connmanctl> enable wifi
connmanctl> [  632.756490] IPv6: ADDRCONF(NETDEV_UP): wlp0s20f3u1: link is not ready
Enabled wifi
connmanctl> scan wifi
Scan completed for wifi
connmanctl> services
    POSADA DE LA MONEDA  wifi_e84e06099fef_504f53414441204445204c41204d4f4e454441_manag                      ed_psk
    Cineteca             wifi_e84e06099fef_43696e6574656361_managed_psk
    Mision Zacatecas     wifi_e84e06099fef_4d6973696f6e205a6163617465636173_managed_non                      e
    Sala_Prensa          wifi_e84e06099fef_53616c615f5072656e7361_managed_psk
connmanctl> agent on
Agent registered
connmanctl> services
    POSADA DE LA MONEDA  wifi_e84e06099fef_504f53414441204445204c41204d4f4e454441_managed_psk
    Mision Zacatecas     wifi_e84e06099fef_4d6973696f6e205a6163617465636173_managed_none
    Cineteca             wifi_e84e06099fef_43696e6574656361_managed_psk
    Sala_Prensa          wifi_e84e06099fef_53616c615f5072656e7361_managed_psk
aged_psktl> connect wifi_e84e06099fef_504f53414441204445204c41204d4f4e454441_man
Agent RequestInput wifi_e84e06099fef_504f53414441204445204c41204d4f4e454441_managed_psk
  Passphrase = [ Type=psk, Requirement=mandatory, Alternates=[ WPS ] ]
  WPS = [ Type=wpspin, Requirement=alternate ]
Passphrase? 6912345678
connmanctl> [  739.164070] wlp0s20f3u1: authenticate with c0:56:27:89:7e:57
[  739.176405] wlp0s20f3u1: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[  739.235203] wlp0s20f3u1: send auth to c0:56:27:89:7e:57 (try 1/3)
[  739.248570] wlp0s20f3u1: authenticated
[  739.270195] wlp0s20f3u1: associate with c0:56:27:89:7e:57 (try 1/3)
[  739.283578] wlp0s20f3u1: RX AssocResp from c0:56:27:89:7e:57 (capab=0x431 status=0 aid=6)
[  739.309207] wlp0s20f3u1: associated
[  739.312999] IPv6: ADDRCONF(NETDEV_CHANGE): wlp0s20f3u1: link becomes ready
Connected wifi_e84e06099fef_504f53414441204445204c41204d4f4e454441_managed_psk
connmanctl> quit
root@galileo:~# 
```

```sh
root@galileo:~# ifconfig
enp0s20f6 Link encap:Ethernet  HWaddr 98:4F:EE:01:77:6D
          inet6 addr: fe80::9a4f:eeff:fe01:776d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:280 (280.0 B)
          Interrupt:50 Base address:0xc000

enp0s20f6:avahi Link encap:Ethernet  HWaddr 98:4F:EE:01:77:6D
          inet addr:169.254.7.44  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:50 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:271360 (265.0 KiB)  TX bytes:271360 (265.0 KiB)

wlp0s20f3u1 Link encap:Ethernet  HWaddr E8:4E:06:09:9F:EF
          inet addr:192.168.1.131  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea4e:6ff:fe09:9fef/64 Scope:Link
          inet6 addr: fd24:7f3c:145:1a00:ea4e:6ff:fe09:9fef/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13836 (13.5 KiB)  TX bytes:9501 (9.2 KiB)
```

```sh
root@galileo:~# opkg update
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
```

```sh
root@galileo:~# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s20f6: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 98:4f:ee:01:77:6d brd ff:ff:ff:ff:ff:ff
    inet 169.254.7.44/16 brd 169.254.255.255 scope link enp0s20f6:avahi
    inet6 fe80::9a4f:eeff:fe01:776d/64 scope link
       valid_lft forever preferred_lft forever
4: wlp0s20f3u1: <BROADCAST,MULTICAST,UP,LOWER_UP8000> mtu 1500 qdisc mq qlen 1000
    link/ether e8:4e:06:09:9f:ef brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.131/24 brd 192.168.1.255 scope global wlp0s20f3u1
    inet6 fd24:7f3c:145:1a00:ea4e:6ff:fe09:9fef/64 scope global dynamic
       valid_lft 6995sec preferred_lft 3395sec
    inet6 fe80::ea4e:6ff:fe09:9fef/64 scope link
       valid_lft forever preferred_lft forever
```

```sh
root@galileo:~# cat /var/lib/connman/wifi_e84e06099fef_504f53414441204445204c41204d4f4e454441_managed_psk/settings
Name=POSADA DE LA MONEDA
SSID=504f53414441204445204c41204d4f4e454441
Frequency=2462
Favorite=true
AutoConnect=true
Modified=2015-05-29T21:27:03.729537Z
Passphrase=6912345678
IPv4.method=dhcp
IPv4.DHCP.LastAddress=192.168.1.131
IPv6.method=auto
IPv6.privacy=disabled
```

## Not Used

```sh
root@galileo:~# wpa_passphrase "POSADA DE LA MONEDA" 6912345678 > /etc/wpa_supplicant.conf
root@galileo:~# cat /etc/wpa_supplicant.conf
network={
        ssid="POSADA DE LA MONEDA"
        #psk="6912345678"
        psk=c61b827aabeaa0703825b7b6f14c7d8201671b429b206617490eeb590efd8468
}
root@galileo:~# cat /etc/network/interfaces
cat: /etc/network/interfaces: No such file or directory
root@galileo:~# vi /etc/network/interfaces
auto wlan0
root@galileo:~# cat /etc/network/interfaces
auto wlan0
```

