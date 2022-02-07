# 💡 Light Dimmer

## 📙 Description :
Application was designed to help control the brightness of LED's. Light brightness can be controlled using a smartphone, or adjusted automatically by the algorithm. System gets data from the light sensor, real-time clock and motion sensor. Commands are sent via Bluettoth communication. You must pair a Bluetooth device first time in Bluetooth settings. If the transmission is interrupted or connection is lost, it is required to reconnect. During microcontroller setup all settings set on the smartphone will be sent. This prevent discrepancies between phone and the microcontroller.

#### The following features have been implemented: 
1. Set the brightness of LED's by PWM
2. BLE communication between smartphone and microcontroller 
3. Algorithms that control the LED's depending on the mode selection. 


</br>



# LightDimmerMobile

<p>
First the Dimmer app must be installed on mobile. Please install the .apk file, which is located in the root folder of this solution. After installation, you have to connect to the device:
</p>

1. Connect to LightDimmer manually in Settings -> Bluetooth -> Add Device
2. Open the LightDimmer mobile app and click rounded blue search button situated on right-down side on screen.
3. Choose LightDimmer device from all BLE devices list
4. Wait until the blue BLE icon turn green. If the BLE icon turns red, there is a connection failure and please retry.
5. After successful configuration switch to the Dimmer tab to control the device.

<p float="left">
<img alt="Login" src="https://user-images.githubusercontent.com/38471368/151458771-899e7d1f-1d6a-49eb-a00e-80609bb1e1a7.png" width="49%" height="auto" />
<img alt="Credentials" src="https://user-images.githubusercontent.com/38471368/152879648-17a515c7-ad31-43e7-b69e-d589782e9c86.png" width="49%" height="auto" />
</p>


## 🛠️ Configure instruction :

- Run Android Studio
- In AVD Manager choose Pixel 4 XL 6.3" 1440x3040 560dpi
- Rebuild & run


## Bluetooth API:
> :warning: Bluetooth communication disables all pins of ADC_2!

![command](https://user-images.githubusercontent.com/38471368/152848607-3fcc07f0-adee-4cf3-9621-19bc74a2c552.png)
Each command sent from mobile consists of three components. </br>
Complete description of all commands is shown in the table below
1. Mode
2. Color
3. Value

</br>
<p>Send data from mobile to microcontroller by Bluettoth:</p>


| Command     | LED color|   Mode   |  State  |                 Description                 |
| ----------- | -------- | -------  | ------- | --------------------------------------------|
|  100-141    |    all   |  Motion  | off-on  | Motion based switch                         |
|  200-241    |    all   |  Adaptive| off-on  | Brightness set based on the light intensity |
|     30      |    all   |  TimeLine|   off   | Time-based switching                        |
|     31      |    all   |  TimeLine|   on    | Time-based switching                        |
|     400     |   white  |  Switch  |   off   | manually turn off                           |
|     401     |   white  |  Switch  |   on    | manually turn on                            |
|     410     |   yellow |  Switch  |   off   | manually turn off                           |
|     411     |   yellow |  Switch  |   on    | manually turn on                            |
|     420     |   red    |  Switch  |   off   | manually turn off                           |
|     421     |   red    |  Switch  |   on    | manually turn on                            |
|     430     |   green  |  Switch  |   off   | manually turn off                           |
|     431     |   green  |  Switch  |   on    | manually turn on                            |
|     440     |   blue   |  Switch  |   off   | manually turn off                           |
|     441     |   blue   |  Switch  |   on    | manually turn on                            |
| 50000-50100 |   white  |  Manual  | off-on  | manually adjust brightness                  |
| 51000-51100 |   yellow |  Manual  | off-on  | manually adjust brightness                  |
| 52000-52100 |   red    |  Manual  | off-on  | manually adjust brightness                  | 
| 53000-53100 |   green  |  Manual  | off-on  | manually adjust brightness                  |
| 54000-54100 |   blue   |  Manual  | off-on  | manually adjust brightness                  |


# LightDimmer


![architecture esp](https://user-images.githubusercontent.com/38471368/152176325-5d3605d4-9e8c-47a0-84ca-3590f441d3ab.png)


## Component pins:
 - ### CLOCK
   - SCL 22
   - SDA 21

## ⚙️ Function Diagram

<p align="center">
<img alt="Login" src="https://user-images.githubusercontent.com/38471368/151668234-11a7b346-089f-4768-a447-81deaf8c541d.png"  />
</p>

## ⏱️ Schedule Table

| Lighting Time  |  LED color |  
| -------------  | ---------- | 
|     16-22      |    white   |  
|     17-21      |    yellow  | 
|     17-23      |    red     | 
|     20-22      |    green   | 
|     17-20      |    blue    | 

## 📚 Required Libraries

- RTClib.h
- BluetoothSerial.h
- BH1750.h

## 🛈 Sources :

 - https://uxwing.com/
