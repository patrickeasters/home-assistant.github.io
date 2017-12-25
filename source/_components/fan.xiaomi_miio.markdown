---
layout: page
title: "Xiaomi Air Purifier 2"
description: "Instructions how to integrate your Xiaomi Air Purifier 2 within Home Assistant."
date: 2017-10-13 12:35
sidebar: true
comments: false
sharing: true
footer: true
logo: xiaomi.png
ha_category: Switch
ha_version: 0.57
ha_iot_class: "Local Polling"
---

The `xiaomi_miio` fan platform allows you to control the Xiaomi Air Purifier 2, Air Purifier 2S andd Air Purifier Pro.

Currently, the supported features are

* On, Off
* Operation modes (auto, silent, favorite, idle)
* Buzzer (on, off)
* LED (on, off), LED brightness (bright, dim, off)
* Favorite Level
* States
  - power
  - aqi
  - humidity
  - temperature
  - mode
  - led
  - led_brightness
  - buzzer
  - child_lock
  - brightness
  - favorite_level
  - filter1_life
  - f1_hour_used
  - use_time
  - motor1_speed

## {% linkable_title Setup %}

Please follow the instructions on [Retrieving the Access Token](/components/vacuum.xiaomi_miio/#retrieving-the-access-token) to get the API token to use in the `configuration.yaml` file.

To add a Xiaomi Air Purifier to your installation, add the following to your `configuration.yaml` file:

```yaml
fan:
  - platform: xiaomi_miio
    name: Xiaomi Air Purifier 2
    host: 192.168.130.66
    token: YOUR_TOKEN
```

Configuration variables:
- **host** (*Required*): The IP of your plug.
- **token** (*Required*): The API token of your plug.
- **name** (*Optional*): The name of your plug.

## {% linkable_title Platform Services %}

### Service fan/xiaomi_miio_set_buzzer_on

Turn the buzzer on.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on specific air purifier. Else targets all.  |

### Service fan/xiaomi_miio_set_buzzer_off

Turn the buzzer off.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on specific air purifier. Else targets all.  |

### Service fan/xiaomi_miio_set_led_on

Turn the led on.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on specific air purifier. Else targets all.  |

### Service fan/xiaomi_miio_set_led_off

Turn the led off.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on specific air purifier. Else targets all.  |

### Service fan/xiaomi_miio_set_led_brightness

Set the led brightness. Supported values are 0 (Bright), 1 (Dim), 2 (Off).

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on specific air purifier. Else targets all.  |
| `brightness`              |       no | Brightness, between 0 and 2.                          |

### Service fan/xiaomi_miio_set_favorite_level

Set the favorite level of the operation mode "favorite".

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on specific air purifier. Else targets all.  |
| `level`                   |       no |  Level, between 0 and 16.                             |
