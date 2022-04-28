<p align="center">
  <img 
    width=50%
    height=50%
    src="https://i.imgur.com/b04QAsB.png"
  >
</p>

# Raspberry Pi-Static IP Address-Setup
### Raspberry Pi Static ip  and Router static setup 



![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white)![Raspberry Pi](https://img.shields.io/badge/-RaspberryPi-C51A4A?style=for-the-badge&logo=Raspberry-Pi)![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)![Mac OS](https://img.shields.io/badge/mac%20os-000000?style=for-the-badge&logo=macos&logoColor=F0F0F0)![IOS](https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=ios&logoColor=white)![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)
### What is Static IP Address vs Dynamic Address?
Most router use dynamic IP addresses to connect the devices, which are assigned by the router when they connect and change over time.

  A static IP address is simply an address that doesn't change. Once your device is assigned a static IP address, that number typically stays the same until the device is decommissioned or your network architecture changes. Static IP addresses generally are used by servers or other important equipment.
  
  In raspberry pi, if you have ssh and vnc enabled this will help a lot.
  
 ![This is the image](https://i.imgur.com/VFepxv6.png)
### How to set a Raspberry Pi with a static ip address?
**First method is Setting up DHCP Configuration in Raspberry Pi itself**.

**Second method is setting up DHCP Configuration in Router**.

## 1. Method DHCP Configuration in Raspberry Pi
I ordedr to change Raspberry Pi to boot same static IP address each time, you will need to modify the configuration file for the DHCP client daemon, dhcpcd.conf.

Before that, you will need some information on your current network setup

- The type of network connection. This is either **wlan0** if your Raspberry Pi is connected to the router **Wirelessly**, or **eth0** if it’s connected using an **Ethernet cable**.

- The Raspberry Pi’s currently assigned IP address. I am going to same ip addrees assigned by router. Since its free.

- Default Gateway. That is your Router IP address.

1. Type this command in terminal or putty
```sh
ifconfig
```

![This is image](https://i.imgur.com/9zqJrro.jpg)

In here **eth0** stands for ethernet.If you are coonected to raspberry through wirelessly, it shows **wlan0**.

192.168.1.156 is my IP address assigned by the router for PI (Dynamic).
 2. NextWe need  Default Gateway. For that type
 ```sh
 sudo route -n
 ```

![This is image](https://i.imgur.com/DhgiZXz.jpg)

In here 192.168.1.1 is my default gateway.
