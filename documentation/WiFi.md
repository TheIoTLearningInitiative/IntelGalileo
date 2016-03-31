WiFi
==

```sh
root@galileo:~# wpa_passphrase "POSADA DE LA MONEDA" 6912345678 > /etc/wpa_supplicant.conf
root@galileo:~# cat /etc/wpa_supplicant.conf
network={
        ssid="POSADA DE LA MONEDA"
        #psk="6912345678"
        psk=c61b827aabeaa0703825b7b6f14c7d8201671b429b206617490eeb590efd8468
}
root@galileo:~#     
```

