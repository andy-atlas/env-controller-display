# env-controller-display

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
  temp_entity: sensor.veg_tent_air_sensor_temperature
  humidity_entity: sensor.veg_tent_air_sensor_humidity
  vpd_entity: sensor.veg_tent_vpd
  vpd_target_entity: sensor.veg_tent_active_target_vpd
  fan_entity: fan.veg_tent_exhaust_fan_fan
  vpd_mode_entity: input_select.veg_tent_vpd_mode
