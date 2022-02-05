[![GitHub stars](https://img.shields.io/github/stars/seechay/HomeAssistantConfig.svg?style=plasticr)](https://github.com/seechay/HomeAssistantConfig/stargazers)
[![GitHub last commit](https://img.shields.io/github/last-commit/seechay/HomeAssistantConfig.svg?style=plasticr)](https://github.com/seechay/HomeAssistantConfig/commits/main)
[![HA Version](https://img.shields.io/badge/Running%20Home%20Assistant-2021.12.10%20-darkblue)](https://github.com/home-assistant/home-assistant/releases/latest)


# Overview
This is my personal [Home Assistant](https://home-assistant.io) configuration. I first started my journey into home automation with home assistant version 0.70. After having been inspired by others many times over, I've finally cleaned up my configuration in hopes to inspire others. Most of my automation is done in node-red as it was more powerful when I first started. Moving forward, I am putting more automations directly into home assistant for ease of sharing with others, now that the built in automation system has matured.

# <a name="menu">Menu</a>
 | [Statistics](#statistics) | [Devices](#devices) |

## <a name="statistics">Statistics</a>
<!---
Captured with

|Domain|Count|
|-|-|
{%- for d in states | groupby('domain') %}
|{{ d[0] }}|{{ states[d[0]] | count  }}|
{%- endfor %}
--->
|Domain|Count|
|-|-|
|alarm_control_panel|2|
|automation|22|
|binary_sensor|148|
|calendar|11|
|camera|24|
|climate|3|
|cover|1|
|device_tracker|139|
|group|16|
|input_boolean|29|
|input_number|5|
|input_select|8|
|input_text|4|
|light|32|
|lock|4|
|media_player|31|
|number|2|
|persistent_notification|1|
|person|2|
|plant|1|
|proximity|1|
|remote|1|
|scene|2|
|script|27|
|select|2|
|sensor|859|
|sun|1|
|switch|112|
|timer|1|
|utility_meter|2|
|vacuum|2|
|weather|4|
|zone|4|

## <a name="devices">Device Menu</a>
 | [Backup Batteries](#batteries) | [Hubs](#hubs) | [Lighting](#lighting) | [Climate](#climate) | [Outlets & Switches](#outlets) | [Security](#security) | [Voice Assistant](#voice) | [Sensors](#sensors) | [Cameras](#cameras) | [Garage](#garage) | [Vacuum](#vacuum) | [Network](#network) | [Other Hardware](#other) |

## <a name="batteries">Backup Batteries</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
| [CyberPower 1500VA](https://amzn.to/3FPlKHd)| 2 | USB | [Network UPS Tools (NUT)](https://www.home-assistant.io/integrations/nut/) | Used to monitor power consumption and provide backup power in case of an outage. One is dedicated to my server running home assistant and various containers, the other is used in the entertainment stand in the livingroom. It provides the ability to lock out motion controlled lights based on power consumption. |
| [APC 600VA](https://amzn.to/3xrW40g)| 2 | USB | [Network UPS Tools (NUT)](https://www.home-assistant.io/integrations/nut/) | Used to monitor power consumption and provide backup power in case of an outage. One monitors the gaming desktop and peripherals in the office, the other is in my network closet. |

TBD (NodeRed config coming soon)

## <a name="hubs">Hubs</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
| [HUSBZB-1 USB Hub](https://amzn.to/30hOxF1)| 1 | USB | [ZHA](https://www.home-assistant.io/integrations/zha/) | Used to control all Zigbee devices. Highly recommend using a USB extension cable when plugging directly into your computer running HA. It also supports Z-Wave, which is why I got it, but I currently only have Zigbee devices. |
| [RTL-SDR](https://amzn.to/3cW3nnA)| 1 | USB | [MQTT](https://www.home-assistant.io/integrations/mqtt/) | Used to read in various RF signals through software defined radio. Integrated with [rtlamr2mqtt](https://github.com/allangood/rtlamr2mqtt) running in docker. Currently being used to get my gas meter into the energy dashboard. |

HUSBZB configured via integrations GUI. For relevant RTL-SDR configuration see [configuration.yaml](https://github.com/seechay/HomeAssistantConfig/blob/main/config/configuration.yaml), [template.yaml](https://github.com/seechay/HomeAssistantConfig/blob/main/config/template.yaml), and [sensor.yaml](https://github.com/seechay/HomeAssistantConfig/blob/main/config/sensor.yaml)

## <a name="lighting">Lighting</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
| [LIFX Color A19](https://amzn.to/3cXE8RY) | 13 | Wi-Fi| [LIFX](https://www.home-assistant.io/integrations/lifx/) | Color changing Wi-Fi light bulbs. Used in existing ceiling fans (no separate light switch wiring available) for mood lighting and circadian lighting. |
| [LIFX Color BR30](https://amzn.to/3rhS95c) | 2 | Wi-Fi| [LIFX](https://www.home-assistant.io/integrations/lifx/) | Color changing Wi-Fi flood light bulbs. Used in night stands for ceiling projected lights (better on my eyes for reading in bed). |
| [TP Link Dimmer Switch](https://amzn.to/3D0mnvy) | 5 | Wi-Fi| [TP-Link](https://www.home-assistant.io/integrations/tplink/) | Smart dimmer switches used on recessed ceiling lighting fixtures and outdoor lighting. |
| [TP Link 3-Way Switch](https://amzn.to/2ZtnI0k) | 2 | Wi-Fi| [TP-Link](https://www.home-assistant.io/integrations/tplink/) | 3-way switches for lights controlled from multiple switches. |

See [configuration.yaml](https://github.com/seechay/HomeAssistantConfig/blob/main/config/configuration.yaml), [scenes.yaml](https://github.com/seechay/HomeAssistantConfig/blob/main/config/scenes.yaml) and [groups.yaml](https://github.com/seechay/HomeAssistantConfig/blob/main/config/groups.yaml) for configuration details. The automations themselves are nearly all in Node-Red. TBD (NodeRed config coming soon)


## <a name="climate">Climate</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
| [Nest Learning 3rd Gen](https://amzn.to/313F1pd) | 2 | Wi-Fi | [Nest](https://www.home-assistant.io/components/nest/)  | Thermostat for each floor. |
| [Aqara Temperature Sensor](https://amzn.to/2ZtzYhl) | 12 | Zigbee | [ZHA](https://www.home-assistant.io/integrations/zha/) | Provides room temperature and humidity. |
| [Plantower PMS5003](https://amzn.to/32G2n5a) | 1 | [ESP8266](https://amzn.to/3raGKEi) | [ESPHome](https://www.home-assistant.io/integrations/esphome/) | PM2.5 air/dust sensor connected to the ESP. |

The nest is connected via the Nest Smart Device Management API. I've been pretty happy with a fixed schedule (despite the learning ability) on the thermostat, so there aren't many automations related to climate. The temperature sensors are currently for awareness and the nest gets switched into away mode when we leave the house using presence detection (HA is way more reliable than the nest app). The air sensor is used to notify me if the air quality drops.

ESP config can be found [here](https://github.com/Seechay/HomeAssistantConfig/blob/main/config/esphome/PlayroomNode.yaml). Notifications can be found TBD (NodeRed config coming soon) and presence can be found TBD (NodeRed config coming soon)

## <a name="outlets">Outlets & Switches</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
| [KMC 3+1 Outlet Smart Plug ](https://amzn.to/3HZOKxS) | 2 | MQTT/Tasmota | [Tasmota](https://www.home-assistant.io/integrations/tasmota/) | Flashed with tasmota. Currently monitors power of washing machine and used to control power to my 3D printers. |
| [VeSync Smart Plug ](https://amzn.to/3d1GkaN) | 4 | Wi-Fi | [VeSync](https://www.home-assistant.io/integrations/vesync/) | Power consumption and control of holiday lights, my MagicMirror and my ambilight setup. |

Lights and MagicMirror are controlled based on presence detection, see TBD (NodeRed config coming soon). 

My washing machine is partially automated around the KMC plug. This outlet can handle the load without me having to worry. Utilizing the appliance [blueprint](https://community.home-assistant.io/t/notify-or-do-something-when-an-appliance-like-a-dishwasher-or-washing-machine-finishes) I generate a series of notifications depending on the state of the washer. Alexa pestering begins when the clothes stay in the washer for too long. See [automations.yaml](https://github.com/seechay/HomeAssistantConfig/blob/main/config/automations.yaml) and TBD (NodeRed config coming soon).

## <a name="security">Security</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
| [Alarm Decoder](https://www.alarmdecoder.com/catalog/index.php/cPath/1) | 1 | W-Fi | [AlarmDecoder](https://www.home-assistant.io/integrations/alarmdecoder/) | Using the AD2pHAT connected to a Raspberry Pi Zero W, I am able to integrate the entirety of my existing Honeywell Vista-20P alarm system into HA. |

Automatic arming/disarming based on bed states and presence detection. I also tap into the existing motion detectors for some additional presence based lighting control. See TBD (NodeRed config coming soon)

## <a name="voice">Voice Assistant</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
| [Amazon Echo](https://amzn.to/3DVXQJw) | 2 | Wi-Fi | [Alexa Media Player (Custom Component)](https://github.com/custom-components/alexa_media_player) | Voice assistant, home audio system, and notifications. |
| [Amazon Echo Flex](https://amzn.to/3EcbMPy) | 2 | Wi-Fi | [Alexa Media Player (Custom Component)](https://github.com/custom-components/alexa_media_player) | Voice assistant, home audio system, and notifications. |
| [Amazon Echo Dot](https://amzn.to/3CUJkjP) | 4 | Wi-Fi | [Alexa Media Player (Custom Component)](https://github.com/custom-components/alexa_media_player) | Voice assistant, home audio system, and notifications. |
| [Amazon Echo Show](https://amzn.to/32jRIxl) | 2 | Wi-Fi | [Alexa Media Player (Custom Component)](https://github.com/custom-components/alexa_media_player) | Voice assistant, home audio system, notifications, and baby monitor. |


I use these for means of disabling automations, requesting things outside of automations (light brightness/color), viewing interior cameras (easy baby monitor),  relaying notifications based on room occupancy, and as a primary media system. See TBD (NodeRed config coming soon)


## <a name="sensors">Sensors</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
| [Google Nest Protect Battery](https://amzn.to/3IWjoZx) | 3 | Wi-Fi | [Homekit Controller](https://www.home-assistant.io/components/homekit_controller/) | Smoke and Carbon Monoxide Detector. As I'm using the new Nest SDM API and bought these after they migrated from the original API, I can't bring these in with the Nest integration. Instead I have [Homebridge](https://github.com/homebridge/homebridge) running in docker with the [homebridge-nest](https://github.com/chrisjshull/homebridge-nest) plugin. |
| [HC-SR04 (Ultrasonic Sensor)](https://amzn.to/3pt2WIq) | 2 | [ESP8266](https://amzn.to/3raGKEi) | [ESPHome](https://www.home-assistant.io/integrations/esphome/) | Distance sensor placed under bed slats for bed occupancy. Used to trigger lighting, security and bedtime automations. |
| [PIR Motion Sensor](https://amzn.to/3yWQP9A) | 1 | [ESP8266](https://amzn.to/3raGKEi) | [ESPHome](https://www.home-assistant.io/integrations/esphome/) | Motion sensor part of my ESP based multi sensor. |
| [DHT22 (Temperature / Humidity Sensor)](https://amzn.to/3Ft9VGJ) | 1 | [ESP8266](https://amzn.to/3raGKEi) | [ESPHome](https://www.home-assistant.io/integrations/esphome/) | Temperature sensor part of my ESP based multi sensor. |
| [Aqara Motion Sensor](https://amzn.to/3FtP4mZ) | 8 | Zigbee | [ZHA](https://www.home-assistant.io/integrations/zha/) | Provides room occupancy and brightness level. |
| [Aqara Door Sensor](https://amzn.to/32ixtA9) | 2 | Zigbee | [ZHA](https://www.home-assistant.io/integrations/zha/) | Used for triggering lighting automations. |
| [Aqara Magic Cube](https://amzn.to/3emIIKb) | 1 | Zigbee | [ZHA](https://www.home-assistant.io/integrations/zha/) | Mostly used for fun. Controls various things in the living room based on gestures. Prompts Alexa to complain with a random phrase if dropped. |

For bed occupancy see [binary_sensor.yaml](https://github.com/Seechay/HomeAssistantConfig/blob/main/config/binary_sensor.yaml) configuration and the corresponding ESP nodes [master_sg_1](https://github.com/Seechay/HomeAssistantConfig/blob/main/config/esphome/master_sg_1.yaml) and [master_sg_3](https://github.com/Seechay/HomeAssistantConfig/blob/main/config/esphome/master_sg_1.yaml). I used to use strain guages, but they weren't reliable enough (and sg_3 just happened to be my third attempt and I never renamed it when I repurposed the ESP). My nodes are placed on different wooden slats on each bed and I've noticed that after my vacuum runs, the carpet underneath the ultrasonic sensors causes the distance it reads to go out of sync. So I found a work around by capturing the highest value after the vacuum runs see TBD (NodeRed config coming soon) and using that as my max value and comparing that with the current reading and a pre-defined delta for a threshold. It's worked way better than my initial empirical calculations of a threshold against the raw value. Eventually I will move the other sensor to use the same approach.

Motion sensor based lighting automations can be found TBD (NodeRed config coming soon)

The magic cube configuration can be found TBD (NodeRed config coming soon)

## <a name="cameras">Cameras</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
| [Ring Video Doorbell 2](https://amzn.to/32xsPOg) | 1 | Wi-Fi | [Ring](https://www.home-assistant.io/components/ring/) | View of the frontdoor, but most importantly presence based announcements when someone rings the doorbell. |
| [Wyze Cam V2](https://amzn.to/3pt5fey) | 3 | Wi-Fi | [Frigate (Custom Component)](https://github.com/blakeblackshear/frigate-hass-integration) | Used for UI streams.
| [Reolink E1 Zoom](https://amzn.to/3HojVlL) | 1 | Wi-Fi | [Frigate (Custom Component)](https://github.com/blakeblackshear/frigate-hass-integration) | Used for UI streams. Also used to provide snapshots for notifications if my garage door is opened.
| [Ubiquiti Unifi Protect G3 Instant](https://amzn.to/3EqSMwb) | 1 | Wi-Fi | [Unifi Protect (Custom Component)](https://github.com/briis/unifiprotect) | Cheap wide angle lens camera. Used as a baby monitor. |
| [Ubiquiti UniFi Cloud Key Gen2 Plus](https://amzn.to/3eqvlIY) | 1 | Ethernet | [Unifi Protect (Custom Component)](https://github.com/briis/unifiprotect) | Unifi Protect NVR. |

I don't have any automations based on the cameras directly. The camera streams are passed to my instance of Frigate. From there object detection is ran and if a person is detected while we are not home, I will get a notification with a screen shot of what was found. The ring stream doesn't work fast enough to be useful (even in the native app), so I just use the binary sensor to trigger an alexa notification on whatever room is occupied and send a notification to our phones if we are home. Normally the dogs go haywire if they hear the chime go off, this prevents that while still alerting us someone is here.

## <a name="garage">Garage</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
| [MyQ Smart Garage Hub](https://amzn.to/3HojVlL) | 1 | Wi-Fi | [MyQ](https://www.home-assistant.io/integrations/myq/)| Used to drive actionable notifications if the garage door is still opened or opened while we are away. |
| Tesla Model 3 | 1 | Wi-Fi | [Tesla (Custom Component)](https://github.com/alandtse/tesla) | My main vehicle. No dedicated automations to this yet, just importing the data because I can. 

The MyQ is mostly reliable, but it sometimes takes a bit to update its state. Home Assistant will occasionally think the garage is open, which is why I send a picture of my garage to verify if it is indeed opened. See TBD (NodeRed config coming soon)


## <a name="vacuum">Vacuum</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
| [Neato D5](https://amzn.to/3oq336A) | 1 | Wi-Fi | [Neato](https://www.home-assistant.io/integrations/neato/)| Automated to run whenever we leave the house and the vacuum hasn't cleaned in the last 2 hours. |
| [Roborock S5](https://amzn.to/3oq336A) | 1 | Wi-Fi | [MQTT](https://www.home-assistant.io/components/mqtt/)| Integrated via MQTT from Valetudo. Automated to run whenever we leave the house and the vacuum hasn't cleaned in the last 2 hours. Automatically meets me at the garbage can for bin emptying. |

Neato and Dwayne the Roborock Johnson (can you smell what the roborock is cleaning?) are controlled via [scripts.yaml](https://github.com/Seechay/HomeAssistantConfig/blob/main/config/scripts.yaml) with the automations found TBD (NodeRed config coming soon). My model of Neato doesn't have nearly as many functions as Dwayne does, so it's just a clean when we're gone kind of thing. It lives on the 2nd floor which is all carpet and does a great job sucking up the dog hair. Dwayne lives on the first floor and can spot clean each room and has the ability to mop the non-carpeted areas downstairs. He also makes it easy to clean thanks to [rockbin](https://github.com/johnDorian/rockbin), which allows me to query for how long it has been since the bin was last removed. When I come home, Dwayne meets me at the garbage can and when the bin is re-inserted, he automatically returns to his dock.

## <a name="network">Network</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) | 

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
|  [Ubiquiti UniFi Cloud Key Gen2 Plus](https://amzn.to/3eqvlIY) | 1 | Ethernet | [Ubiquiti Unifi](https://www.home-assistant.io/integrations/unifi/) | This contains my unifi controller and provides statistics via [Unifi Gateway](https://github.com/custom-components/sensor.unifigateway) in addition to device_trackers for presence detection. |
| [Ubiquiti Networks Unifi Security Gateway (USG)](https://amzn.to/3rr0UJM) | 1 | Ethernet | [Ubiquiti Unifi](https://www.home-assistant.io/integrations/unifi/)| The router I use for my unifi network and provides statistics via [Unifi Gateway](https://github.com/custom-components/sensor.unifigateway) in addition to device_trackers for presence detection. |
| [Ubiquiti UniFi nanoHD](https://amzn.to/3J5z8sl) | 2 | Ethernet | [SNMP](https://www.home-assistant.io/integrations/snmp/) | These are my wireless access points and used to get various sensor information via SNMP. |

My network provides redundant presence detection for our mobile devices, but also provides presence detection for guests. When a guest is detected, guest mode gets enabled which configures how certain automations work. Normally when I lay in bed, all of the lights go off, but I'm sure my guests would not like that as much as I do, so that gets disabled.

For SNMP configuration and guest detection configuration see [sensor.yaml](https://github.com/Seechay/HomeAssistantConfig/blob/main/config/sensor.yaml). When guest mode is active ```input_boolean.guest_mode``` is set to true, which various automations check for.


## <a name="other">Other Hardware</a>

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |

| Device  | Quantity | Connection | Home Assistant | Notes |
| ------------- | :---: | ------------- | ------------- | ------------- |
| [Dell R720](https://amzn.to/3upAKJt) | 1 | Ethernet | N/A | This is my main server. Multiple VMs and docker containers are running in here, such as HA OS, Plex, media managers, game servers, pen test environment and development environment. |
| [Printrbot Simple Metal](https://amzn.to/3usv55q) | 1 | Wi-Fi | [OctoPrint](https://www.home-assistant.io/integrations/octoprint/) | My first 3D printer. Very small print bed, but it's my old reliable. |
| [Reach3D Printer](https://amzn.to/3usv55q) | 1 | Wi-Fi | [OctoPrint](https://www.home-assistant.io/integrations/octoprint/) | Kickstarter DIY 3D printer. Has a larger and heated print bed, but prints that are too tall get a little messy. |
| [Canon MF634Cdw](https://amzn.to/3Le5jI7) | 1 | Wi-Fi | [Internet Printing Protocol (IPP)](https://www.home-assistant.io/integrations/ipp/)| Color laser printer in the office. I can see my toner levels in home assistant. |

3D printer configuration for the Printrbot can be found in [scripts.yaml](https://github.com/Seechay/HomeAssistantConfig/blob/main/config/scripts.yaml). Currently the Reach3D has no automations dedicated to it as I only have 1 instance of OctoPrint and the Printrbot is almost always connected to it.

| [Go to Main Menu](#menu) | [Go to Device Menu](#devices) |



