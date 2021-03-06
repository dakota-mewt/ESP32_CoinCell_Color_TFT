# ESP32_CoinCell_Color_TFT
![kit](https://user-images.githubusercontent.com/4991664/97461608-ab616e80-191c-11eb-923d-81e30eafeb2a.jpg)
![Top](https://user-images.githubusercontent.com/4991664/97198353-75da4b00-178d-11eb-99a8-423e4afa3d99.png)
![Bottom](https://user-images.githubusercontent.com/4991664/97198461-930f1980-178d-11eb-9ccb-2a1128894bd0.png)

Video: https://youtu.be/O6SoF_0fP20

This ESP32 internet of things dev board with has an accelerometer, 80x160 pixel 0.96" color TFT LCD display, RGB led, temperature/humidity sensor, laser range sensor and LiPo battery protection. The very bottom edge has four capacitive touch sensors for menu navigation and is powered by a rechargeable LIR2450 coin cell, external LiPo battery or micro usb cable. When a battery is connected and you plug in the micro usb cable, it charges the battery. It was not made for any specific purpose and was really more of a design challenge to try and make it as small as possible with plenty of sensors. The design files and parts list are provided on my Github site if you would like to assemble your own. Each board is hand assembled by myself using a soldering iron and hot air wand. Hand assembly is complicated. Components except for the sensors and display are placed, tested and then the board is washed, sensors are placed, tested and cleaned again, then the display is soldered into place and tested.

As expected, battery using a rechargeable 2450 coincell is very, very poor so I've added a connector for a larger LiPo battery. Current draw awake with the ESP32 awake, the tft, accelerometer, temp/humidity and range sensor on is around 70mA and only lasts around 10 minutes. Wifi current draw is significantly more. In sleep mode current draw is around 220uA and waking every 10 minutes to grab sensor data, use wifi and turn on the display it on the screen lasts around 12 hours or so. Using a larger external LiPo battery is highly recommended.

Hardware design instead of software is my strength so at this state the only a few simple Arduino sketches are available that test out the hardware.

**Hardware on this dev board is:<br/>**
-temperature/humidity sensor (HDC1080DMBT)<br/>
-Laser range sensor (VL53L0CXV0DH)<br/>
-accelerometer (LIS3DHTR)<br/>
-LiPo protection (DW01A)<br/>
-80x160 TFT LCD (ER-TFT0.96-1)<br/>
-3.3V LDO (HT7833)<br/>
-LiPo charger (SL4054ST25P)<br/>
-USB interface (CP2104N)<br/>

If  you decice to purchase this project from Tindie https://www.tindie.com/products/miker/esp32-iot-color-coincell/ you get an assembled and tested board with coin cell holder not soldered in place along with a microJST cable to use with an external battery.

**Board setup instructions:<br/>**
-install the latest Arduino IDE<br/>

![Preferences](https://user-images.githubusercontent.com/4991664/97713183-4170d280-1a9e-11eb-82ad-8573fa191bb2.png)<br/>


-File/Preferences in Additional Boards Manager URLs add: https://dl.espressif.com/dl/package_esp32_index.json<br/>
-Tools/Board/Board Manager install esp32<br/>
-Tools/Board/ESP32 Arduino select ESP32 Dev Board

**Com Port Setup (Windows)<br/>**
-using a microUSB cable, plug the board into your computer<br/>
-in the Arduino IDE Tools/Port<br/>
-select the new com port for your board<br/>
-if the com port does not appear in Windows type Device Manager<br/>
-right click on CP2104 USB to UART Bridge Controller and Properties<br/>


![port](https://user-images.githubusercontent.com/4991664/97712525-500aba00-1a9d-11eb-99e5-8d06dfd3c323.png)<br/>


-click Driver, Update Driver, Browse my computer for driver software<br/>
-find your installed Arduino IDE location. ie C:\XXXX\Arduino-1.8.13\arduino-1.8.13\drivers The drivers folder is the one you want<br/>
-click next<br/>
-in the Arduino IDE the com port should now appear<br/>


'![port_1](https://user-images.githubusercontent.com/4991664/97712616-70d30f80-1a9d-11eb-9eb3-bb4c536409b7.png)<br/>

**Powering the board<br/>**
The board can be powered over usb, a LIR2450 rechargable coincell or an external LiPo battery. By default the charger resistor R4 has a 43K soldered in place that delivers 25mA for charging the coincell.<br/>

![bat1](https://user-images.githubusercontent.com/4991664/97786295-537b6f80-1b89-11eb-98f8-4ae383f3db22.jpg)<br/>
![bat2](https://user-images.githubusercontent.com/4991664/97786292-52e2d900-1b89-11eb-8338-011f999aaecd.jpg)<br/>
![bat3](https://user-images.githubusercontent.com/4991664/97786293-537b6f80-1b89-11eb-87bd-dc4ca9a4fef4.jpg)<br/>
![charger](https://user-images.githubusercontent.com/4991664/97786294-537b6f80-1b89-11eb-9efa-a9e21272d6ee.png)<br/>

It is recommended to replace R4 with a different value depending on the capacity of your battery calculated with this equation.<br/>
![resistor](https://user-images.githubusercontent.com/4991664/97786558-25972a80-1b8b-11eb-983f-9bfc1c6ad737.png)<br/>
If you are a developer and require a custom board of a different size of require different sensors then just let me know at 0miker0@gmail.com<br/>




