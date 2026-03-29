# 🌱 env-controller-display

https://www.instagram.com/p/DWZN_imDmET/?utm_source=ig_web_copy_link&igsh=MzRlODBiNWFlZA==

A clean, ESPHome-powered display for monitoring your grow environment in real time.

View **temperature, humidity, VPD, target VPD, and fan speed** — all without opening Home Assistant.

---

## 🚀 Features

- 📊 Real-time environmental metrics (Temp / RH / VPD)
- 🎯 Target VPD tracking with status feedback
- 🌬️ Fan speed display (percentage)
- 🎛️ VPD mode control (Early / Mid / Late / Custom)
- ⚡ Powered by ESPHome + LVGL
- 🔌 Fully integrated with Home Assistant

---

## 📦 Installation

Create a new ESPHome device and use the configuration below.

---

## 🛠 Example Configuration

```yaml
esphome:
  name: env-controller-display
  friendly_name: Environment Controller Display

esp32:
  board: esp32-p4-evboard

logger:

api:

ota:
  - platform: esphome

esp32_hosted:
  active_high: true
  variant: ESP32C6
  reset_pin: GPIO54
  cmd_pin: GPIO19
  clk_pin: GPIO18
  d0_pin: GPIO14
  d1_pin: GPIO15
  d2_pin: GPIO16
  d3_pin: GPIO17

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password
  power_save_mode: none

packages:
  env_controller_display:
    url: https://github.com/andy-atlas/env-controller-display.git
    file: env-controller-display.yaml

# 🔥 Only edit this section
substitutions:
  temp_entity: sensor.air_sensor_temperature
  humidity_entity: sensor.air_sensor_humidity
  vpd_entity: sensor.tent_vpd
  vpd_target_entity: sensor.active_target_vpd
  fan_entity: fan.exhaust_fan_fan
  vpd_mode_entity: input_select.vpd_mode
