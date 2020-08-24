---
layout: default
title: Data Schema
nav_order: 4
parent: v1
permalink: /v1/data_schema
---

| BDS Schema          | Description                                  |
|---------------------|----------------------------------------------|
| bazze_device_id     | Bazze Device ID (hash of advertising id)     |
| bazze_event_id      | Bazze Event ID (hash of whole row)           |
| bazze_source_id     | Bazze Source ID (code word)                  |
| bazze_mgrs          | MGRS coordinate (1km)                        |
| bazze_geohash       | Geohash coordinate (1km)                     |
| advertising_id      | Advertiser ID (mandatory)                    |
| timestamp           | Event time stamp (mandatory)                 |
| latitude            | Latitude – when available                    |
| longitude           | Longitude – when available                   |
| altitude            | Altitude                                     |
| ip_address          | ipv4 (mandatory)                             |
| wifi_ssid           | Wifi SSID (scanned/connected) (mandatory)    |
| wifi_bssid          | Wifi BSSID (scanned/connected) (mandatory)   |
| country             | Country (mandatory)                          |
| horizontal_accuracy | Horizontal Accuracy - when available         |
| user_agent          | User Agent                                   |
| publisher_id        | Publisher ID                                 |
| iot_signals         |                                              |
