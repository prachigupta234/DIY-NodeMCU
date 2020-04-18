# NodeMCU
For introduction to NodeMCU and setting it up, [visit here](https://github.com/prachigupta234/NodeMCU/blob/master/NodeMCU.md).
## Project-GEOLOCATION
### Index
### Introduction of project
In this project we will print the latitude and longitude of the device on an OLED Display with the help of a NodeMCU. For this we will use a NodeMCU, OLED display for the hardware part and ipstack geolocation API, Aurdino IDE for the software part.
### Getting the prerequisites
Using these OLEDs with Arduino sketches requires that two libraries be installed: Adafruit_SSD1306, which handles the low-level communication with the hardware, and Adafruit_GFX, which builds atop this to add graphics functions like lines, circles and text.The method of the installation of these libraries can be found in the file mentioned ablove.

### Hardware
#### NodeMCU:
NodeMCU is a system on a chip (SoC) design with components like the processor chip. The processor has around 16 GPIO lines, some of which are used internally to interface with other components of the SoC, like flash memory.

Since several lines are used internally within the ESP8266 SoC, we have about 11 GPIO pins remaining for GPIO purpose.

Now again 2 pins out of 11 are generally reserved for RX and TX in order to communicate with a host PC from which compiled object code is downloaded.

Hence finally, this leaves just 9 general purpose I/O pins i.e. D0 to D8.

![Nodemcu](/images/NodeMCU.PNG)

#### OLED:
The OLED we use here is a 0.96" 128x64 display. It has 4 pins-
1. **Power:**  It is used to power up the OLED,connected to the 3.3V pin on the NodeMCU.
2. **Ground:**  It is connected to the ground pin in the NodeMCU.
3. **SCL:**  It is a serial clock pin for OLED-NodeMCU interface.
4. **SDA:** It is a serial data pin for OLED-NodeMCU interface.
#### 

![OLED](/images/oled.PNG)
### Software
#### Setting Up The API
1. Open [ipstack](https://ipstack.com/).
2. Click on **SIGN UP FREE** then click on **GET FREE API KEY**.

![sign up](/images/A.png)

![free api](/images/B.png)
3. Fill the form and click on **Sign Up**.

![free api](/images/C.png)

![free api](/images/D.png)

4. Copy the API access key.

![free api](/images/E.png)
#### Main Code
1. Copy the code from [this file](/geolocation.md).
2. Write your wifi name in place of 'SSID' and your wifi password in place of 'PASS'.
3. Replace 'YOUR_API_KEY' by the API key copied.

**Now connect your laptop with NodeMCU using a USB cable and upload the code.**
