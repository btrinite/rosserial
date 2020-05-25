# rosserial

[![Build Status](https://travis-ci.org/ros-drivers/rosserial.svg?branch=melodic-devel)](https://travis-ci.org/ros-drivers/rosserial)

Please see [rosserial on the ROS wiki](http://wiki.ros.org/rosserial) to get started.

# Modification (compared to original repo) :
- Server : Increased buffer for serial communication (since I'm using it to transmit MJPEG frame)
- Arduino : 
    - directive ROSSERIAL_BAUD to control baud value (default 57600), to define before including ros.h (optionnal)
    - directive ROSSERIAL_OVERRIDE_SERIAL_CLASS to verride serial port object used, to define before including ros.h (optionnal)
    - directive ROSSERIAL_RXD_PIN and ROSSERIAL_TXD_PIN to define specific PIN to be used for serial link, to define before including ros.h (optionnal)

Exemple of directive in an Arduino sketch (esp32) :
    ```
    #define ROSSERIAL_BAUD 1500000
    #define ROSSERIAL_OVERRIDE_SERIAL_CLASS Serial1
    #define ROSSERIAL_RXD_PIN 18
    #define ROSSERIAL_TXD_PIN 19

# additonal node on hoz to use high speed :
    If you have trouble using rosserial on high speed UART (like me trying to use 1500000 baud uart link with esp32), Please read http://programmersought.com/article/95921196958/
    