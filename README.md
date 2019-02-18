# make_project_lighthouse58

# Summary
Lighthouse58 is an Internet of Things learning case based upon the LEGO ® Lighthouse Point 31051 which build has been enhanced.
Integrated are several objects with devices, e.g. Top Light, OLED display Weather Underground data, Motion Detector, Outdoor Light, Indoor Lights, Light Dimmers, Ambient Light, LED Status Indicators. The Control Unit hardware is a Raspberry Pi with TinkerForge Bricks & Bricklets.

The Lighthouse58 is controlled via
* Node-RED Browser Dashboard.
* Windows Client (developed with B4J).
* Browser Dashboard (multi client control) running as a Server (developed with B4J) on the Control Unit.

![lighthouse58-p](https://user-images.githubusercontent.com/47274144/52942457-5578ad00-336b-11e9-81a8-ed2c28b7a3a9.png)
![lighthouse58-cu](https://user-images.githubusercontent.com/47274144/52942452-54e01680-336b-11e9-8a37-7a781b9bd089.png)
![lighthouse58-c](https://user-images.githubusercontent.com/47274144/52942451-54e01680-336b-11e9-81fc-e89255de6044.png)

# Objectives
* To develop an IoT learning case
* To control objects containing devices
- An object is for example a house or a group of houses.
- A device for example a light, switch, servo motor, sensor (e.q. temperature, illuminance, contact, motion) or virtual (e.q. weather request).
- Each device has a set of actions to control, e.g.light = on | off | state | blink(n).
* To experiment with hardware, sensors, software
* To build objects with devices
* To design a messaging concept
* To apply learningâ€™s from previous IoT experiments
* To explore, learn & share
* To have fun

_Note:_ Details to be found in the Lighthouse58 Concept (lighthouse58.pdf).

## Functionality
### Lighthouse

* Top Light Flashing based on the properties of the selected Lighthouse.
* Information Display showing a clock & weather information (temperature, airpressure, beaufort, wind direction) measured at the nearest lighthouse lat/lon position.
* Lighthouses configuration (Windows client), e.g. name, position, flash interval, flash on off RGB colors, refrence url.
* Lighthouse show reference information in default browser (Windows client).

### Pier
* Motion Detector with Dashboard indicator start & stop time.
* Outdoor light switch, dimmer and red, green or blue color setting.

### Lightkeeper Cottage
* Room light switch, dimmer and red, green or blue color setting.

### Boathouse
* Room light switch, dimmer and red, green or blue color setting.

### Control Unit
* Ambient Light measuring illuminance (in Lux). Depending darkness level, the Pier Outdoor Light is switched on (depending configuration setting).
* Shutdown the Control Unit.
* Shutdown the Control Unit via Dashboard or Micro Switch.
* Status indicators (Trend, Alarm) for CPU Â°C, Dis Space Used, Memory Used
* The Control Unit uses a Raspberry Pi 2B to control TinkerForge Bricks & Bricklets.

### Weather
* Weather Underground data every hour for the Lighthouse position and display in a browser Dashboard.

### MQTT Console
* MQTT Console for the Windows Client listing the TinkerForge MQTT messages.

## Hardware
* Raspberry Pi with TinkerForge Master Bricks and Bricklets connected.
* Communication between devices: TinkerForge Brick MQTT Proxy.

## Software
* Browser Dashboard: developed with Node-RED - an open source visual programming tool by IBM.
* The Node-RED addon Dashboard is used to control the Lighthouse58 via Browser.

![lighthouse58-d](https://user-images.githubusercontent.com/47274144/52942455-5578ad00-336b-11e9-9173-99d1547558fe.png)
![lighthouse58-w](https://user-images.githubusercontent.com/47274144/52942459-5578ad00-336b-11e9-877e-b5e522618a05.png)

#### Windows Client Dashboard: developed with B4J.
(requires installation of B4J and additional libraries - see B4J source).
* Uses the TinkerForge Brick MQTT Proxy and does not require Node-RED.

![lighthouse58-b4j-dashboard](https://user-images.githubusercontent.com/47274144/52943794-3596b880-336e-11e9-976c-60306811682b.png)

![lighthouse58-b4j-dashboard-lighthouses](https://user-images.githubusercontent.com/47274144/52943795-3596b880-336e-11e9-9cb3-03e6defefcc6.png)

#### Browser Dashboard: developed with B4J.
(Server B4J code (requires installation of B4J and additional libraries - see B4J source).
* Runs as a Server on the Control Unit, uses the TinkerForge Brick MQTT Proxy and does not require Node-RED, but requires Java.
* Responsive design using the w3.css framework.
* Multiple clients can control the dashboard. The state of the controls is updated in the browser for each connected client.
* Request Weather Information from Weather Underground and display in Dialog.
* Trigger Control Unit system check (displayed as status message in a label on each connected client) and shutdown.
* Dialogs for showing the selected Lighthouse information and About box.
* Server application runs on the Control Unit (Raspberry Pi). Access via Browser with URL http://ip-adress-raspberry-pi:51042.
* Messaging based on MQTT using TinkerForge messages. No linkage with Node-RED, means the B4J solution runs without Node-RED.
* Settings defined as a map stored in external settings file - the same file is used by the Windows Client.
* Library TFMQTT is used to control the TinkerForge Bricklets. Libraries used: jcore,jserver,jrltfmqtt,jmqtt,json,jhttp,jstringutils,jkssh2.

![lighthouse58-b4j-dashboard-server](https://user-images.githubusercontent.com/47274144/52943860-5c54ef00-336e-11e9-9695-82d382c0e22b.png)

