# Code for the Project


```

#include <SPI.h>
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
#include "HTTPSRedirect.h"
#include "DebugMacros.h"


#include <ESP8266HTTPClient.h>
#include <ArduinoJson.h>
#include "ESP8266WiFi.h"

char myssid[] = "SSID";         // your network SSID (name of your WiFi network)
char mypass[] = "PASS";          // your network password


//Credentials for Ipstack GeoLocation API...
const char* Host = "api.ipstack.com/";
String thisPage = "134.201.250.155? access_key =";
String key = "YOUR_API_KEY";
String ur=(String)Host+thisPage+key;
int status = WL_IDLE_STATUS;
String jsonString = "{\n";

double latitude    = 0.0;
double longitude   = 0.0;
int more_text = 1; // set to 1 for more debug output

#define OLED_RESET LED_BUILTIN //4
Adafruit_SSD1306 display(OLED_RESET);

#define NUMFLAKES 10
#define XPOS 0
#define YPOS 1
#define DELTAY 2


#define LOGO16_GLCD_HEIGHT 16
#define LOGO16_GLCD_WIDTH  16
static const unsigned char PROGMEM logo16_glcd_bmp[] =
{ B00000000, B11000000,
  B00000001, B11000000,
  B00000001, B11000000,
  B00000011, B11100000,
  B11110011, B11100000,
  B11111110, B11111000,
  B01111110, B11111111,
  B00110011, B10011111,
  B00011111, B11111100,
  B00001101, B01110000,
  B00011011, B10100000,
  B00111111, B11100000,
  B00111111, B11110000,
  B01111100, B11110000,
  B01110000, B01110000,
  B00000000, B00110000
};

#if (SSD1306_LCDHEIGHT != 64)
#error("Height incorrect, please fix Adafruit_SSD1306.h!");
#endif


void setup()   {
  Serial.begin(9600);

  // by default, we'll generate the high voltage from the 3.3v line internally! (neat!)
  display.begin(SSD1306_SWITCHCAPVCC, 0x3C);  // initialize with the I2C addr 0x3D (for the 128x64)
  
  display.clearDisplay();
  display.setTextSize(2);
  display.setTextColor(WHITE);
  display.setCursor(10,25);
  display.println("techiesms");
  display.setTextColor(WHITE); // 'inverted' text
  display.display();

  Serial.println("Start");
  // Set WiFi to station mode and disconnect from an AP if it was previously connected
  WiFi.mode(WIFI_STA);
  WiFi.disconnect();
  delay(100);
  Serial.println("Setup done");
  // We start by connecting to a WiFi network
  Serial.print("Connecting to ");
  Serial.println(myssid);
  WiFi.begin(myssid, mypass);

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println(".");


}


void loop() {

  WiFiClientSecure client;

  //Connect to the client and make the api call
  Serial.print("Requesting URL: ");
  Serial.println(ur);
  Serial.println(" ");
  if (client.connect(Host, 443)) {
    Serial.println("Connected");
    client.println("GET " + thisPage + key + );
    client.println("Host: " + (String)Host);
    client.println("Connection: close");
    client.println("Content-Type: application/json");
    client.println("User-Agent: Arduino/1.0");
    client.print("Content-Length: ");
    client.println(jsonString.length());
    client.println();
    client.print(jsonString);
    delay(500);
  }

  //Read and parse all the lines of the reply from server
  while (client.available()) {
    String line = client.readStringUntil('\r');
    if (more_text) {
      Serial.print(line);
    }
    JsonObject& root = jsonBuffer.parseObject(line);
    if (root.success()) {
      latitude    = root["latitude"];
      longitude   = root["longitude"];
    }
  }

  Serial.println("closing connection");
  Serial.println();
  client.stop();

  Serial.print("Latitude = ");
  Serial.println(latitude, 6);
  Serial.print("Longitude = ");
  Serial.println(longitude, 6);

  display.clearDisplay();
  display.setTextSize(2);
  display.setTextColor(WHITE);
  display.setCursor(15, 0);
  display.println("Routers");
  display.setTextColor(WHITE); // 'inverted' text
  display.setTextSize(2);
  display.setTextColor(WHITE);
  display.setCursor(40, 30);
  display.println(n);
  display.display();
  delay(2000);

  display.clearDisplay();
  display.setTextSize(2);
  display.setTextColor(WHITE);
  display.setCursor(15, 0);
  display.println("Latitude");
  display.setTextColor(WHITE); // 'inverted' text
  display.setTextSize(2);
  display.setTextColor(WHITE);
  display.setCursor(15, 30);
  display.println(latitude, 6);
  display.display();
  delay(2000);

  display.clearDisplay();

  display.setTextSize(2);
  display.setTextColor(WHITE);
  display.setCursor(15, 0);
  display.println("Longitude");
  display.setTextColor(WHITE); // 'inverted' text
  display.setTextSize(2);
  display.setTextColor(WHITE);
  display.setCursor(15, 30);
  display.println(longitude, 6);

  display.display();
  delay(2000);
 
 const char* host = "script.google.com";
 const char* GScriptId = "AKfycbxy9wAZKoPIpPq5AvqYTFxxxkkqK_avacf2NU_w7ycoEtlkuNt"; 
 const int httpsPort = 443; 

 String url = String("/macros/s/") + GScriptId + "/exec?value=Latitude";  
 String url2 = String("/macros/s/") + GScriptId + "/exec?vall=Longitude";

String payload_base =  "{\"command\": \"appendRow\", \
                    \"sheet_name\": \"TempSheet\", \
                       \"values\": ";
                       
HTTPSRedirect* client = nullptr;
client = new HTTPSRedirect(httpsPort);
client->setInsecure();
Start the respose body i.e. if the server replies then we can print it on serial monitor. 
client->setPrintResponseBody(true);
client->setContentTypeHeader("application/json");
  
Serial.print("Connecting to ");
Serial.println(host); 
 bool flag = false;
  for (int i = 0; i < 5; i++) {
    int retval = client->connect(host, httpsPort);
    if (retval == 1) {
      flag = true;
      break;
    }
    else
      Serial.println("Connection failed. Retrying...");
  }
  payload = payload_base + "\"" + sheetTemp + "," + sheetHumid + "\"}";
  
   if (client->POST(url2, host, payload)) {
    ;
  }
  else {
    ++error_count;
    DPRINT("Error-count while connecting: ");
    DPRINTLN(error_count);
  } 

}
```
