WiFi
==

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

