---
layout: page
title: "Linkplay"
description: "Instructions on how to integrate a Linkplay based media player into Home Assistant."
date: 2018-12-04 22:00
sidebar: true
comments: false
sharing: true
footer: true
logo: linkplay.png
ha_category: Media Player
ha_release: 0.83
ha_iot_class: "Local Polling"
---


The `linkplay` platform allows you to control a [Linkplay](https://linkplay.com/) based music player from Home Assistant. Linkplay chipsets are used in devices from a wide range of manufacturers, a list of some of these devices can be found [here](https://linkplay.com/featured-products/).

To add your Linkplay based player to your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
media_player:
  - platform: linkplay
    host: IP_ADDRESS
    name: NAME
```

{% configuration %}
host:
  description: The host name or address of the Linkplay device, eg. 192.168.0.21.
  required: true
  type: string
name:
  description: Name of the Linkplay device. The name must exactly match the name of the device as specified in the mobile app used to control the device.
  required: true
  type: string
lastfm_api_key:
  description: Your own LastFM API key that can be used to fetch album cover art. An API key can be generated [here](https://www.last.fm/api/account/create).
  required: false
  type: string
{% endconfiguration %}

### {% linkable_title Service `linkplay_preset_button` %}

Simulate pressing one of the physical preset buttons on the device.

| Service data attribute | Optional | Description |
| ---------------------- | -------- | ----------- |
| `entity_id` | no | Name(s) of the Linkplay devices where the button should be pressed.
| `preset` | no | The preset button to simulate pressing.

### {% linkable_title Service `linkplay_connect_multiroom` %}

Connect a slave device to multiroom master device.

| Service data attribute | Optional | Description |
| ---------------------- | -------- | ----------- |
| `entity_id` | no | Name of the slave device that should be connected.
| `master_id` | no | Name of the master device to connect to.

### {% linkable_title Service `linkplay_remove_slaves` %}

Remove slave device(s) from multiroom master device.

| Service data attribute | Optional | Description |
| ---------------------- | -------- | ----------- |
| `entity_id` | no | Name of the master device from which the slaves should be removed.
| `slave_ids` | no | Name of the slave device(s) to remove.

