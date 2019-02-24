
```
sudo python3 setup.py install
python3 examples/clock_EN.py
python3 examples/sensor_clock_EN.py
```

sensor_clock works with BME280 module.
For connection to RPi, see https://github.com/Naohiro2g/bme280

Adafruit BME280 requires:
-  Adafruit BM280 https://github.com/Naohiro2g/Adafruit_Python_BME280
-  Adafruit GPIO https://github.com/Naohiro2g/Adafruit_Python_GPIO

I2C address should be changed from 0x77 to 0x76
`i2cdetect -y 1`

```
BME280_I2CADDR = 0x76
```

```
class BME280(object):
    def __init__(self, t_mode=BME280_OSAMPLE_1, p_mode=BME280_OSAMPLE_1, h_mode=BME280_OSAMPLE_1,
                 standby=BME280_STANDBY_250, filter=BME280_FILTER_off, address=BME280_I2CADDR, i2c=None,
                 **kwargs):
```



Modified from Adafruit for ST7735

### SPI connection
OLED Pin  |Name  |Remarks       |RPi Function
----------|------|--------------|---------------
1 Brown   |GND   |Ground        |GND
2 Red     |VCC   |+3.3V Power   |3V3
3 Orange  |SCL   |Clock         |GPIO 11 (SCLK)
4 Yellow  |SDA   |MOSI          |GPIO 10 (MOSI)
5 Green   |RES   |Reset         |GPIO 27 -> 25
6 Blue    |DC    |Data/Command  |GPIO 25 -> 24
7 Purple  |BLK   |Backlight     |GPIO 24 -> 8

```
class ST7789(object):
    """Representation of an ST7789 IPS LCD."""
    def __init__(self, spi, mode=3, rst=27, dc=25, led=24, gpio=None, width=ST7789_TFTWIDTH,
        height=ST7789_TFTHEIGHT):
```        
             
### Wiring to Rpi Pins (pin compatible with SD1306 128x64 display)

Left   |BCM   |BCM   |Right
-------|------|------|-------
Red    |3.3   |24    |Blue
Yellow |10    |GND   |Brown
`---`  |9     |25    |Green
Orange |11    |8     |Purple
 






# Python_ST7789
Python library for using ST7789-based IPS LCD with Raspberry Pi
(240x240 pixels, SPI interface, 7 pins without CS pin)
