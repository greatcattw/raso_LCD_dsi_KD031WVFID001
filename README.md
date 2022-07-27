# LCD
www.startek-lcd.com/

KD031WVFID001

rasp 3B

linux 5.10.103

![pic](https://github.com/greatcattw/rpi_dsi_driver_KD031WVFID001/blob/main/pic/demo2.jpg)

![circuit](https://github.com/greatcattw/rpi_dsi_driver_KD031WVFID001/blob/main/circuit/kd031_circuit_2.png)


# pin of touch screen

1 GND

2 VDDIO - 3v3

3 VDD -3v3

4 SCL - rasp#5

5 SDA - rasp#3

6 INT - rasp#13 / GPIO27

7 RST - rasp#7 / GPIO4

8 GND


# Usage:
sudo cp kd031dsi.ko /lib/modules/5.10.103-v7+/

sudo depmod

sudo cp gcatlcd0a.dtbo /boot/overlay/

sudo cp gcat_kd031ts.dtbo /boot/overlay/



## modify /boot/config.txt

#for uart console

enable_uart=1

dtoverlay=pi3-disable-bt

dtoverlay=gcat_kd031ts




#for kd031dsi

ignore_lcd=1

dtoverlay=vc4-kms-v3d,noaudio

dtoverlay=gcatlcd0a


# Check
fbset                                                         
                                                                                
$mode "480x800"                                                                  
    geometry 480 800 480 800 16                                                 
    timings 0 0 0 0 0 0 0                                                       
    accel true                                                                  
    rgba 5/11,6/5,5/0,0/0                                                       
endmode

$lsmod | grep kd031                                            
kd031dsi               16384  0                                                 
drm                   520192  5 vc4,kd031dsi,drm_kms_helpe

# rotate screen

Preference / Screen Configuration 

Configure / Screens / DSI-1 / Orientation / left

Configure / Apply
