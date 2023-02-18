# ASUS-USB-C2500
ASUS USB-C2500

No need of any aditional drivers for Ubuntu 22.04 Jammy

On plug the default driver is assigned to it.
```
[Sat Feb 18 15:53:02 2023] usb 6-1.1: new SuperSpeed USB device number 9 using xhci_hcd
[Sat Feb 18 15:53:02 2023] usb 6-1.1: New USB device found, idVendor=0b05, idProduct=1976, bcdDevice=31.05
[Sat Feb 18 15:53:02 2023] usb 6-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=6
[Sat Feb 18 15:53:02 2023] usb 6-1.1: Product: USB 10/100/1G/2.5G LAN
[Sat Feb 18 15:53:02 2023] usb 6-1.1: Manufacturer: Realtek
[Sat Feb 18 15:53:02 2023] usb 6-1.1: SerialNumber: 5013000001
[Sat Feb 18 15:53:02 2023] cdc_ncm 6-1.1:2.0: MAC-Address: 04:42:1a:3c:6a:7a
[Sat Feb 18 15:53:02 2023] cdc_ncm 6-1.1:2.0: setting rx_max = 16384
[Sat Feb 18 15:53:02 2023] cdc_ncm 6-1.1:2.0: setting tx_max = 16384
[Sat Feb 18 15:53:02 2023] cdc_ncm 6-1.1:2.0 eth0: register 'cdc_ncm' at usb-0000:06:00.4-1.1, CDC NCM, 04:42:1a:3c:6a:7a
[Sat Feb 18 15:53:02 2023] cdc_ncm 6-1.1:2.0 enx04421a3c6a7a: renamed from eth0
[Sat Feb 18 15:53:05 2023] IPv6: ADDRCONF(NETDEV_CHANGE): enx04421a3c6a7a: link becomes ready
```

The devise is conencted to another device NAS.
To assigne it a IP address

/etc/network/interfaces
```
..
allow-hotplug enx04421a3c6a7a
iface  enx04421a3c6a7a inet static
        address 169.254.1.4/24
```

or manually 
```
ip addr flush dev enx04421a3c6a7a
ip addr add 169.254.1.4/24 dev enx04421a3c6a7a
ip link set enx04421a3c6a7a up

```

The 2 dvices have to be connested at 2500Mbps now. 
The download speed from wget command is 280MB/s


The latest drivers for this chipset are coming with an udev rule that doesn't mention the ASUS one. 
The ASUS support ws not able to provide any additional information how to apply the dedidcated driver.
