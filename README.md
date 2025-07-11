# melonHD 🍈

 ## Purchase melonHD on [Flashfi.re](https://flashfi.re)
 
 melonHD is a video converter module based around Lontium Semiconductor's LT6711A. It accepts an HDMI 2.0 input signal (up to 2160p) and outputs USB-C DisplayPort 1.2 Alt Mode. 

 <img src="https://github.com/mackieks/melonHD/blob/main/images/module_top.jpg" width=300>  <img src="https://github.com/mackieks/melonHD/blob/main/images/module_bot.jpg" width=300>

 The module is designed to allow [portablizers](https://bitbuilt.net/forums/index.php) to add USB-C video output to DIY handheld video game systems, and therefore does not expose the HDMI DDC connections. As such, compatibility with PCs and other HDMI sources which rely on EDID is not guaranteed. 
 
 For legal reasons, the melonHD module itself is not open source. It's available for purchase on [Flashfire](https://flashfi.re), my webstore. This repository contains documentation, usage guidelines, and an open source carrier board reference design.

 <img src="https://github.com/mackieks/melonHD/blob/main/images/carrier.jpg" width=500>

 ## Features

- [x] Super compact 17 x 13mm 0.8mm-thick castellated PCB
- [x] 480p - 2160p HDMI 2.0 input and USB-C DP 1.2 Alt Mode output
- [x] Pin-strappable VBUS PDO selection: 5V/3A, 9V/3A, 12V/3A, or 15V/3A
- [x] Powered directly from 5V - 15V VBUS with onboard voltage regulators
- [x] HPD (hotplug detect) output pin: high for DP Alt Mode contracts, low for power-only contracts

 <img src="https://github.com/mackieks/melonHD/blob/main/images/dimensions.jpg" width=400>

## Usage

melonHD is powered by the downstream-facing port. This can be a little confusing if you're unfamiliar with the USB-C protocol. Basically, your USB-C monitor needs to be able to provide power to melonHD, while melonHD sends it video data. Most DP Alt Mode sinks support this mode of operation.

The reason melonHD works this way is so it can request power to charge your portable's batteries while your portable is docked. This is identical to how a Nintendo Switch works. Please see the diagram for a more detailed breakdown.

<img width="1593" height="603" alt="image" src="https://github.com/user-attachments/assets/74091fad-8b42-4f46-91a8-fea91a221f41" />

One key feature of melonHD is the customized LT6711A firmware, which allows the user to select what VBUS voltage the module requests from the downstream-facing port. Based on how you pinstrap the module, you can request 5V/3A, 9V/3A, 12V/3A, or 15V/3A. This lets you charge your portable's batteries quickly without sacrificing DP Alt Mode output. Of course, whether you can get higher voltages depends on the capabilities of the downstream port you connect to.

<img width="519" height="244" alt="image" src="https://github.com/user-attachments/assets/a499fba0-e5af-4911-a78a-3967b568499b" />

Also, the melonHD module has an "HPD" output pin. This pin is low when melonHD negotiates for a power-only contract, such as when you plug a charger into the USB-C port. But when you plug in a USB-C monitor, melonHD will negotiate a DP Alt Mode contract and the HPD pin will go high. This is useful for enabling GCVideo DVI only when a USB-C monitor is connected, and not when a charger is connected. You could also use it to turn off your portable's screen when an external display is connected, just like a Nintendo Switch.

<img width="506" height="104" alt="image" src="https://github.com/user-attachments/assets/92e24d00-beb3-4e47-8351-4f6e2394b44c" />


## License
Carrier board is licensed under Solderpad Hardware License v2.1
