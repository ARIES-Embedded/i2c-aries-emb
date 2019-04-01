Linux I2C Driver for MX10 and SpiderSoM
---------------------------------------

This repository contains a kernel module driver enabling the host to access the I2C bus on MX10 and SpiderSoM.  
I2C driver and protocol derived from [i2c-tiny-usb](https://github.com/harbaum/I2C-Tiny-USB).

### Installation
* Clone the sources.
```
$ git clone https://github.com/ARIES-Embedded/i2c-aries-emb.git i2c-aries-emb
```
* Build the kernel module.
```
$ cd i2c-aries-emb
$ make
```
* Insert module.
```
$ sudo insmod i2c-aries-emb.ko
```

### Usage
When connecting an MX10 or SpiderSoM this driver will create a **/dev/i2c-x** device node, which can be used by default i2c tools.
Example with an RTCC (0x6f) including EEPROM (0x57) connected:
```
$ i2cdetect -l
    ...
    i2c-10  unknown  i2c-aries-emb at bus 001 device 010     N/A
$ sudo i2cdetect -y 10
        0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
    00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
    10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
    20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
    30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
    40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
    50: -- -- -- -- -- -- -- 57 -- -- -- -- -- -- -- -- 
    60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 6f 
    70: -- -- -- -- -- -- -- --   
```
