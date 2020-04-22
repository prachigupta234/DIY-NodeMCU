# NodeMCU
For introduction to NodeMCU and setting it up, [visit here](https://github.com/prachigupta234/NodeMCU/blob/master/NodeMCU.md).
## Project- GEOLOCATION
### INDEX
1. [Introduction of project](https://github.com/prachigupta234/DIY-NodeMCU/blob/master/diy.md#introduction-of-project)
2. [Getting the prerequisites](https://github.com/prachigupta234/DIY-NodeMCU/blob/master/diy.md#getting-the-prerequisites)
3. [Hardware](https://github.com/prachigupta234/DIY-NodeMCU/blob/master/diy.md#hardware)
   - [NodeMCU](https://github.com/prachigupta234/DIY-NodeMCU/blob/master/diy.md#nodemcu-1)
   - [OLED Display](https://github.com/prachigupta234/DIY-NodeMCU/blob/master/diy.md#oled-display)
   - [Circuit](https://github.com/prachigupta234/DIY-NodeMCU/blob/master/diy.md#circuit)
4. [Software](https://github.com/prachigupta234/DIY-NodeMCU/blob/master/diy.md#software)
   - [Setting Up The API](https://github.com/prachigupta234/DIY-NodeMCU/blob/master/diy.md#setting-up-the-api)
   - [Sending Data to Spreadsheet](https://github.com/prachigupta234/DIY-NodeMCU/blob/master/diy.md#sending-data-to-spreadsheet)
   - [NodeMCU Code](https://github.com/prachigupta234/DIY-NodeMCU/blob/master/diy.md#main-code)
   
### INTRODUCTION OF PROJECT
In this project we will print the latitude and longitude of the network host on an OLED Display with the help of NodeMCU. For this, we will use a NodeMCU, an OLED display as the hardware components and ipstack geolocation API,  Aurdino IDE for the software components.
### GETTING THE PREREQUISITES
Using these OLEDs with Arduino sketches requires two libraries to be installed: Adafruit_SSD1306, which handles the low-level communication with the hardware, and Adafruit_GFX, which builds atop this to add graphics functions like lines, circles and text.The method of the installation of these libraries can be found in the inroductory section of the project.

### HARDWARE
#### NodeMCU:
NodeMCU is a system on a chip (SoC) design with components like the processor chip. The processor has around 16 GPIO lines, some of which are used internally to interface with other components of the SoC, like flash memory.

Since several lines are used internally within the ESP8266 SoC, we have about 11 GPIO pins remaining for GPIO purpose.

Now again 2 pins out of 11 are generally reserved for RX and TX in order to communicate with a host PC from which compiled object code is downloaded.

Hence finally, this leaves just 9 general purpose I/O pins i.e. D0 to D8.

![NodeMCU](/images/NodeMCU.PNG)

#### OLED Display:
The OLED we use here is a 0.96" 128x64 display. It has 4 pins-
1. **Power:**  It is used to power up the OLED,connected to the 3.3V pin on the NodeMCU.
2. **Ground:**  It is connected to the ground pin in the NodeMCU.
3. **SCL:**  It is a serial clock pin for OLED-NodeMCU interface.
4. **SDA:** It is a serial data pin for OLED-NodeMCU interface.

![OLED Display](/images/oled.PNG)
#### Circuit
### SOFTWARE
#### Setting Up The API
1. Open [ipstack](https://ipstack.com/).
2. Click on **SIGN UP FREE** then click on **GET FREE API KEY**.

![sign up](/images/A.png)

![free api](/images/B.png)

3. Fill the form and click on **Sign Up**.

![free api](/images/C.png)   ![free api](/images/D.png)

4. Copy the API access key.

![free api](/images/E.png)
#### Sending Data to Spreadsheet
For instructions on how to setup the google spreadsheet-NodeMCU communication refer to [this link](https://github.com/prachigupta234/NodeMCU/blob/master/NodeMCU.md).
The code for the spreadsheet can be found in [this file.](/spread.md)

#### NodeMCU Code
1. Copy the code from [this file](/geolocation.md).
2. Write your host name in place of 'SSID' and your password in place of 'PASS'.
3. Replace 'YOUR_API_KEY' by the API key copied( see the process of setting up the api in the previous section).

**Now connect your laptop with NodeMCU using a USB cable and upload the code.**
## CITATION
- https://github.com/prachigupta234/NodeMCU/blob/master/NodeMCU.md
- https://www.electronicsforu.com/electronics-projects/gps-geolocation-using-esp8266-projects
