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
3. Next is DNS. Your router’s DNS (Domain Name System) IP address. This is typically the same as its gateway address, but may be set to another value to use an alternative DNS – such as 8.8.8.8 for Google, or 1.1.1.1 for Cloudflare. But here i am  using gateway address that is 192.168.1.1
4. it’s time to edit the dhcpcd.conf configuration file to add the settings you need to set up a static IP address for your Raspberry Pi
5. Type this command on terminal
```sh
sudo nano /etc/dhcpcd.conf
```
6. add the following lines at the bottom

![This is image](https://i.imgur.com/P1RwDiO.jpg)

**interface eth0**
**static ip_address = 192.168.1.156**
**static routers = 192.168.1.1**
**static domain_name_servers = 192.168.1.1**

| Command | Description |
| --- | --- |
| Interface |your network connection type  eth0 (Ethernet) or wlan0 (wireless) |
| static ip_address  | the static IP address you want to set for the Raspberry Pi | 
| static routers  | the gateway IP address for your router on the local network |
| static domain_name_servers | the DNS IP address (typically the same as your router’s gateway address) |

## 2. Method DHCP Configuration in Router

I am using Tplink AX1500 Wi-Fi 6 Router. Steps will be different.
1. Go to ip address of router and login
2. Go to advance settings

![This is image](https://i.imgur.com/IXM7Yu5.jpg)

3. Click DHCP
4. Then Click add, This will Reserve IP addresses for specific devices connected to the router

![This is image](https://i.imgur.com/DZp02tV.jpg)

5. Click the view connected devices and select the device from the list.

![This is image](https://i.imgur.com/qQIn32J.jpg)

![This is image](https://i.imgur.com/K1Xi5BK.jpg)

![This is image](https://i.imgur.com/XPhQUSl.jpg)

6. Click Save :electron:
