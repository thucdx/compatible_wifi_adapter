List of compatible USB wifi in Linux
------

### 1. [TP Link Archer T4U v3 1300 Mpbs USB Wifi Adapter](https://www.amazon.com/TP-Link-Archer-T4U-1300Mbps-Wireless/dp/B01MR6M8EC/ref=sr_1_1?dchild=1&keywords=TP-Link+Archer+T4U+AC1300&qid=1605434896&sr=8-1)
- Support 5GHz & 2.4GHz
- Product: https://www.amazon.com/TP-Link-Archer-T4U-1300Mbps-Wireless/dp/B01MR6M8EC/ref=sr_1_1?dchild=1&keywords=TP-Link+Archer+T4U+AC1300&qid=1605434896&sr=8-1
- Tested OS: `Ubuntu 20.04`
- Driver: `88x2bu`
    - Driver repository can be found here: https://github.com/EntropicEffect/rtl8822bu
    - Follow instruction to build and install driver.
    - Notes: If driver is not automatically loaded on boot, try adding 
        ```
        88x2bu
        ```
        to `/etc/modules`

### 2. [TP Link Archer T2U](https://www.tp-link.com/us/home-networking/usb-adapter/archer-t2u-plus/)
- Support 2.4 GHz
- Product: https://www.tp-link.com/us/home-networking/usb-adapter/archer-t2u-plus/
- Tested OS: `Ubuntu 20.04`
- Driver: `88xxau`
    - Driver repo can be found here: https://github.com/aircrack-ng/rtl8812au
    - Notes: If driver is not automatically loaded on boot, try adding
        ```
        88xxau
        ```
        to `/etc/modules`

### 3. [TL-WN722N](https://www.tp-link.com/us/home-networking/usb-adapter/tl-wn722n/)
- Support 2.4 GHz
- Product: https://www.tp-link.com/us/home-networking/usb-adapter/tl-wn722n/
- Tested OS: `Ubuntu 20.04`, `Ubuntu 18.04`
- Driver: `8188eu`, can be found here: https://github.com/aircrack-ng/rtl8188eus

### 4. [TL-WN725N](https://www.amazon.com/TP-Link-wireless-network-Adapter-SoftAP/dp/B008IFXQFU)
- Product: https://www.amazon.com/TP-Link-wireless-network-Adapter-SoftAP/dp/B008IFXQFU
- Tested OS: `Ubuntu 20.04`, `Ubuntu 18.04`
- Driver: `8188eu`, can be found here: https://github.com/aircrack-ng/rtl8188eus

Install instruction for Ubuntu

```
// Update and installed prerequisite components
sudo apt update
sudo apt-get install build-essential
sudo apt install bc
// Remove old module 
sudo rmmod r8188eu.ko
sudo rmmod 8188eu.ko

// Build module from source
git clone https://github.com/aircrack-ng/rtl8188eus
cd rtl8188eus

make
sudo make install

// Load module to kernel
sudo modprobe 8188eu

// Load kernel at boot time (just to make sure the module is loaded)
sudo vim /etc/modules => add 8188eu  => save

sudo reboot
```





