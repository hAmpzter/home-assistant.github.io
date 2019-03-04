---
layout: page
title: UpCloud
description: Instructions on how to integrate UpCloud within Home Assistant.
date: 2018-01-28 20:00
sidebar: true
comments: false
sharing: true
footer: true
ha_category:
  - System Monitor
  - Binary Sensor
  - Switch
ha_release: 0.65
logo: upcloud.png
ha_iot_class: Cloud Polling
redirect_from:
  - /components/binary_sensor.upcloud/
  - /components/switch.upcloud/
---

The `upcloud` component allows you to access the information about your [UpCloud](https://www.upcloud.com/) servers from Home Assistant.

There is currently support for the following device types within Home Assistant:

- [Binary Sensor](#binary-sensor)
- [Switch](#switch)

## {% linkable_title Setup %}

Set up your API user credentials in your [UpCloud control panel](https://my.upcloud.com/).

## {% linkable_title Configuration %}

To integrate your UpCloud servers with Home Assistant, add the following section to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
upcloud:
  username: YOUR_API_USERNAME
  password: YOUR_API_PASSWORD
```

{% configuration %}
username:
  description: Your UpCloud API username.
  required: true
  type: string
password:
  description: Your UpCloud API user password.
  required: true
  type: string
scan_interval:
  description: Update interval in seconds.
  required: false
  type: integer
  default: 60
{% endconfiguration %}

## {% linkable_title Binary Sensor %}

The `upcloud` binary sensor platform allows you to monitor your UpCloud servers.

To use your UpCloud servers, you first have to set up your [UpCloud hub](#configuration) and then add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
binary_sensor:
  - platform: upcloud
    servers:
      - 002167b7-4cb1-44b7-869f-e0900ddeeae1
      - 00886296-6137-4074-afe3-068e16d89d00
```

{% configuration %}
servers:
  description: List of servers you want to monitor.
  required: true
  type: list
{% endconfiguration %}

## {% linkable_title Switch %}

The `upcloud` switch platform allows you to control (start/stop) your UpCloud servers.

To use your UpCloud servers, you first have to set up your [UpCloud hub](#configuration) and then add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
switch:
  - platform: upcloud
    servers:
      - 002167b7-4cb1-44b7-869f-e0900ddeeae1
      - 00886296-6137-4074-afe3-068e16d89d00
```

{% configuration %}
servers:
  description: List of servers you want to control.
  required: true
  type: list
{% endconfiguration %}
