## Concepts and components

### Microcontroller

A microcontroller (sometimes abbreviated MCU) is a small computer on a single integrated circuit
containing a processor core, memory, and usually from several to dozens of general purpose input/output pins (GPIO). 
GPIO pins are software configurable to either an input or an output state. 
When GPIO pins are configured to an input state, they are often used to read sensors or external signals.
Configured to the output state, GPIO pins can drive external devices such as LEDs or motors, 
often indirectly, through external power electronics.

Read more on [Wikipedia](https://en.wikipedia.org/wiki/Microcontroller)

Interesting MCUs for a hobbyist include at least the Atmega328 that's used in Arduinos, the ESP8266 that
includes in integrated Wifi circuit.

### Arduino

Arduino is family of microcontroller boards, many of which contain the Atmega328 MCU. In addition to the
MCU, the Arduino boards typically feature a voltage regulator (see below) and an USB port for easy communications
with a host computer. The Arduino boards typically also act as "breakout boards" for easily connecting the MCU
GPIO pins to your periphrals of choice. My first Arduino board was the Arduino Uno, pictured below.

![https://upload.wikimedia.org/wikipedia/commons/3/38/Arduino_Uno_-_R3.jpg]

Arduino IDE is a programming environment that you can use to upload a "sketch" onto an Arduino board. The
sketches are programmed in C++. In addition to actual Arduinos, you can use the Arduino IDE and related
host of additional libraries for some other microcontrollers, such as the ESP8266 via "plugins".

### Breadboard

A breadboard is a construction base for prototyping of electronics. It allows you to plug electronic components
together using jump wires, without having to solder anything together.

![https://en.wikipedia.org/wiki/Breadboard#/media/File:Breadboard.JPG]

### Voltage

I assume you understand the concepts of voltage, current and power already, so I'll cover those
from a perspective that's practical from the IoT hobbyiests point of view.

Your devices will typically need some DC power to work. Voltage is key; if you don't supply
enough voltage, your device won't work. If you supply too much, it'll probably heat up and
go out in flames. So pay attention to the minimum/maximum voltage specs of your devices. Typically,
digital components like microcontrolller operate at 3.3 or 5 volt and have some tolerance with regard
to voltage. For example, the ESP8266 microcontroller operates at 3.3 volts but practically runs just
fine with 2 AA batteries that provide 3 volts in total.

### Voltage regulators

A voltager regulator is a component that takes a range of input voltages (say, 6 to 12 volts) and outputs
a steady output voltage (say, 5 volts). The Arduino boards feature a voltage regulator, so they are not
so picky about input voltage.

### Current

Your components will draw some amount of current from their power source. For instance an Arduino
might draw 30 mA (milliamperes) at 5 volts. From this you can calculate the power consumption of about
150 milliwatts.

TODO: mAhs, maximum output currents of things

### Resistance and resistors

### Up, down, floating

In digital logic circuits a pin (let's say a GPIO pin on your arduino) can be in 3 different states:

1. Up: the pin has a voltage above the "high" threshold of you MCU. In a typical Arduino setup, a pin
that's said to be "up", is at 5 volts
2. Down: the pin is pulled down, i.e. connected to ground
3. Floating: the pin is connected to neither "high" or ground. When your input GPIO pin is floating, there's
no guarantee on the value you can read from it.

So, if your reading a digital value from a GPIO pin, make sure it's not floating. You can do this by applying
a pull-up or pull-down resistor.

### LEDs

### Push buttons

### Sensors

### FTDI

## Platforms

| Platform                | Specs             | Voltage | mA    | Battery life |
|-------------------------|-------------------|---------|-------|--------------|
| Raspbberry Pi           | 1Ghz, any flash   | 3.3v    | 400mA | 3AA, ?       |
| Arduino                 | 16Mhz, 32kb flash | 5v      | 33mA  | 4AA, ?       |
| Bare Arduino            | 16Mhz, 32kb flash | 3v      | 10mA  | 2AA, ?       |
| Bare Arduino deep sleep |                   | 3v      | 10uA  | 2AA, years   |
| ESP8266 / ESP01         | 80Mhz, 512kb flash| 3v      | 70mA  | 2AA, ?       |
| ESP8266 deep sleep      |                   | 3v      | 30uA  | 2AA, 1 year  |

So if you're looking at making a battery-powered device that's always on, you'll probably
need a platform that can go to a deep-sleep mode. That will work for, for instance, sensors
that transmit something once in 5 minutes or so.

If, on the other hand, you can plug into AC power, you can use a Raspberry Pi and enjoy
the power of a full-fledged Linux machine, yet with GPIO capabilities for interacting with
sensors and other devices.

## Communications

### Wifi

### Zigbee

### Custom 433Mhz radio

### Enocean

## Practical considerations

Here are some things that you'll have to take into account when designing your device.

### Power supply

### Heat dissipation

### Software update

### Boxing
