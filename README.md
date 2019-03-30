# MQTT_via_ESP01   
TCP/UDP Applicaton for ATmega & STM32F103 using ESP8266's AT firmware.   
You don't need An Ethernet card.   
You need only ESP8266 module.   

**MQTT_Publish_ESP01**   
Simple Pubish Application.   
Supprted arduino & stm32f103.   
It DON'T require any library.   

**MQTT_Subscribe_ESP01**   
Simple Subscribe Application.   
Supprted arduino & stm32f103.   
It DON'T require any library.   

![slide1](https://user-images.githubusercontent.com/6020549/35101108-a13451d8-fca1-11e7-8cfd-37d71f18f880.JPG)

**Socket_Client_ESP01**   
Simple TCP/IP Client Application.   
Supprted arduino & stm32f103.   
It DON'T require any library.   

**Socket_Server_ESP01**   
Simple TCP/IP Server Application.   
Supprted arduino & stm32f103.   
It DON'T require any library.   

**Socket_Client_WiFiEsp**   
Simple TCP/IP Client Application using WiFiEsp.   
Supprted arduino ONLY.   
It require Arduino WiFi library for ESP8266 modules.   
https://github.com/bportaluri/WiFiEsp   

**Socket_Server_WiFiEsp**   
Simple TCP/IP Server Application using WiFiEsp.   
Supprted arduino ONLY.   
It require Arduino WiFi library for ESP8266 modules.   
https://github.com/bportaluri/WiFiEsp   

![slide2](https://user-images.githubusercontent.com/6020549/35101341-9019e394-fca2-11e7-9edd-0aa9086fd5db.JPG)

**NTP_Client_ESP01**   
Simple NTP Client Application.   
Supprted arduino & stm32f103.   
It DON'T require any library.   

**SNTP_Client_ESP01**   
Simple SNTP Client Application.   
Supprted arduino & stm32f103.   
It DON'T require any library.   

![slide3](https://user-images.githubusercontent.com/6020549/35101499-241b1950-fca3-11e7-9876-0a22008ebc5a.JPG)

**SMTP_Client_gmail_ESP01**   
Simple SMTP Client Application.   
Supprted arduino & stm32f103.   
It DON'T require any library.   
You need gmail account.   

![slide4](https://user-images.githubusercontent.com/6020549/35125598-90e2a360-fced-11e7-89ed-045cd6c49984.JPG)


# Flash AT firmware to ESP-01.   

![esp01-flash](https://user-images.githubusercontent.com/6020549/33159146-b8456238-d053-11e7-8202-a86cca2f8a3d.jpg)

I'm using esp8266_flasher.exe and v2.0 AT Firmware(ESP).bin.   

---

# Setup ESP-01 using terminal software such as CoolTerm.   

![esp01-setup](https://user-images.githubusercontent.com/6020549/33159150-bdade984-d053-11e7-9b93-bbbf05573441.jpg)

    AT+GMR
    AT version:0.40.0.0(Aug  8 2015 14:45:58)
    SDK version:1.3.0
    Ai-Thinker Technology Co.,Ltd.
    Build:1.3.0.2 Sep 11 2015 11:48:04
    OK
    
    AT+CWMODE=1
    
    OK
    AT+CWLAP
    +CWLAP:(3,"Picking",-86,"34:12:98:08:4b:4a",1,-4)
    +CWLAP:(4,"ctc-g-fa4a2e",-92,"c0:25:a2:b1:8c:2e",2,3)
    +CWLAP:(4,"aterm-e625c0-g",-49,"c0:25:a2:ac:cb:ba",3,15)
    +CWLAP:(1,"aterm-e625c0-gw",-48,"c2:25:a2:ac:cb:ba",3,15)
    
    OK
    
    AT+CWJAP="Your AP's SSID","Your AP's password"
    WIFI CONNECTED
    WIFI GOT IP
    
    OK
    
    AT+CIPSTA?
    +CIPSTA:ip:"192.168.10.142"
    +CIPSTA:gateway:"192.168.10.1"
    +CIPSTA:netmask:"255.255.255.0"
    
    OK
    AT+CWQAP
    
    OK
    
    WIFI DISCONNECT


_*** UNO ONLY ***_   
_*** Change baudrate to 4800bps ***_   
_*** Because there is no the 2nd UART in UNO ***_   
_*** So UNO use Software Serial with low speed ***_

    AT+UART_DEF=4800,8,1,0,0
    
    OK
    at
    
    OK
    AT+RST

    OK
    
    Ai-Thinker Technology Co.,Ltd.
    
    invalid
    WIFI CONNECTED
    WIFI GOT IP

----

# Connect ESP-01 to UNO.

ESP-01(Tx) - UNO(D4)   
ESP-01(Rx) - UNO(D5)   

![ESP01-MQTT-UNO](https://user-images.githubusercontent.com/6020549/55268764-656f9f00-52d0-11e9-9120-360e397ffae0.jpg)

You can't use on-board 3.3V.    
An electric current is insufficient.   

----

# Connect ESP-01 to MEGA2560.

ESP-01(Tx) - MEGA(D19)   
ESP-01(Rx) - MEGA(D18)   

![ESP01-MQTT-MEGA](https://user-images.githubusercontent.com/6020549/55268794-9fd93c00-52d0-11e9-8cca-4f4bd202d745.jpg)

You can't use on-board 3.3V.    
An electric current is insufficient.   

----

# Connect ESP-01 to STM32F101(MAPLE Core).

ESP-01(Tx) - STM32F103(PA3)   
ESP-01(Rx) - STM32F103(PA2)   

![ESP01-MQTT-STM32F103_MAPLE-Core](https://user-images.githubusercontent.com/6020549/55268802-b1badf00-52d0-11e9-9c35-1e2a674c8dda.jpg)

MAPLE Core.    
https://github.com/rogerclarkmelbourne/Arduino_STM32   

----

# Connect ESP-01 to STM32F101(ST Core).

ESP-01(Tx) - STM32F103(PA10)   
ESP-01(Rx) - STM32F103(PA9)   

![ESP01-MQTT-STM32F103_ST-Core](https://user-images.githubusercontent.com/6020549/55268807-c303eb80-52d0-11e9-9056-7b15655bff30.jpg)

ST Core.    
https://github.com/stm32duino/Arduino_Core_STM32   

----

# How to Firmware Upate

1.Make sure TE(terminal equipment) is in sta or sta+ap mode   
    
    AT+CWMODE=3
    OK
    
2.Make sure TE got ip address   
    
    AT+CWJAP="ssid","12345678"
    OK
    
    AT+CIFSR
    192.168.1.134
    
3.Let's update   
    
    AT+CIUPDATE
    +CIPUPDATE:1    found server
    +CIPUPDATE:2    connect server
    +CIPUPDATE:3    got edition
    +CIPUPDATE:4    start start
    
    OK

----

Enjoy!!   

![esp01-mqtt-uno-tft](https://user-images.githubusercontent.com/6020549/33193265-cbbd2618-d10a-11e7-9dba-dd60643c27bb.JPG)


