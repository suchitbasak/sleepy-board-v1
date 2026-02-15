# Sleepy Board (v1)

The Sleepy Board can be used to capture temperature, humidity, sound (loudness) and ambient light (brightness) data. Data is read from sensors connected to a microcontroller unit (MCU), which is then transmitted to a database over wifi. I live right next to a main road and wanted to know what my room looks like once I have fallen asleep.

Sleepy Board (v0) started off as my one weekend project and turned out to be a decent proof of concept.

## Feedback from Sleepy Board (v0)
I analysed at the sensor data gathered by Sleepy Board (v0) and observed the following:
1. Temperature and relative humidity stay more or less constant throughout. Will continue taking one reading every one minute. Can also reduce this frequency if needed.
2. All brightness data stayed at zero once the lights were off. However, I do see car headlights reflecting off my walls, which means it could be more useful to wall mount the board.
3. Must incorporate sound data as well. I will be attaching an I2S mic to the MCU. Sound will be recorded whenever the loudness is above a certain threshold.

## Duel-MCU Architecture
- I want to use an I2S microphone. RaspberryPi Pico does not have decicated I2S hardware. I do not wish to bit-bang I2S for the sake of using a Pico. I have an STM32 G0 board that will be used for reading sensor data.
- The data read by the STM32 will be transmitted to the Pico 2W, which will send it to the server over WiFi.

### Advantages
- The parts are readily available and using readily available parts is the cheapest option at this stage.
- I can see myself using the same architecture in another project - where a lot of the data processing is done by a more powerful MCU (like an STM32F) and the data transmission is done by a simpler ESP32-style MCU.

### Disadvantages
- Two sets of firmware to maintain.
- Final BOM could be more expensive.
- Flashing the board would be a two step process.


(TBC..)