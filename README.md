Modified from Adafruit for ST7735

SPI connection

Display            | RPi
-------------------|--------
GND                |GND
VCC                |3.3V
SCL                |GPIO 11
SDA                |GPIO 10
RES(Reset)         |GPIO 27
DC(Data/Command)   |GPIO 25
BLK(Backlight)     |GPIO 24

```
class ST7789(object):
    """Representation of an ST7789 IPS LCD."""
    def __init__(self, spi, mode=3, rst=27, dc=25, led=24, gpio=None, width=ST7789_TFTWIDTH,
        height=ST7789_TFTHEIGHT):
```        
        
# Python_ST7789
Python library for using ST7789-based IPS LCD with Raspberry Pi
(240x240 pixels, SPI interface, 7 pins without CS pin)
