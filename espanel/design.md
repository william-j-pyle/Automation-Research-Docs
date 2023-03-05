# NSPanel Design

| Entity ID                                      | Name                                    |
|------------------------------------------------|-----------------------------------------|
| binary_sensor.epoxy_mode                       | Epoxy Mode                              |
| binary_sensor.left_button                      | Left Button                             |
| binary_sensor.right_button                     | Right Button                            |
| button.nspanel_craftroom_nextion_tft_upload_2  | nspanel-craftroom Nextion TFT Upload    |
| button.nspanel_craftroom_restart_2             | nspanel-craftroom Restart               |
| button.nspanel_craftroom_test_buzzer           | nspanel-craftroom Test Buzzer           |
| number.brightness                              | Brightness                              |
| number.brightness_dimdown                      | Brightness dimdown                      |
| sensor.current_display_page                    | Current display page                    |
| sensor.nspanel_craftroom_esphome_version       | nspanel-craftroom ESPHome Version       |
| sensor.nspanel_craftroom_temperature_2         | nspanel-craftroom Temperature           |
| sensor.nspanel_craftroom_uptime_human_readable | nspanel-craftroom Uptime Human Readable |
| sensor.nspanel_craftroom_uptime_sensor         | Device Uptime                           |
| sensor.nspanel_craftroom_wifi_signal_strength  | WiFi Signal Sensor                      |
| switch.alarm_active                            | Alarm Active                            |
| switch.disable_dim_down                        | Disable dim-down                        |
| switch.disable_screensaver                     | Disable Screensaver                     |
| switch.nextion_initialization                  | Nextion Initialization                  |
| switch.nspanel_craftroom_relay_1_2             | nspanel-craftroom Relay 1               |
| switch.nspanel_craftroom_relay_2_2             | nspanel-craftroom Relay 2               |
| switch.nspanel_craftroom_screen_2              | nspanel-craftroom Screen                |


## Nextion Configuration

### Globals

| Variable   | ESPHomeID            | Default | Usage                                                                                                        |
|------------|----------------------|---------|--------------------------------------------------------------------------------------------------------------|
| scr_bright | screen_bright        | 80      | Brightness value of the screen when visible (30-100)  doesn’t allow for screen to be set to off              |
| scr_dim    | screen_dim           | 30      | Brightness value of the screen when not in use and not sleeping (20-70) doesn’t allow for full bright or off |
| sec_dim    | screen_dim_seconds   | 15      | Seconds of nonuse before device dims screen to scr_dim                                                       |
| sec_sleep  | screen_sleep_seconds | 60      | Seconds of nonuse before device changes page=screensaver                                                     |
| sec_home   | screen_home_seconds  | 30      | Seconds of nonuse when page!=home before device changes page=home                                            |
| sec        |  N/A                 | N/A     | Seconds elapsed since last use, incremented by eventLoop timer

### Component to be copied to every page

**`Timer`** eventLoop - fires every 100ms

- increments GBL.sec every 10 loops
- if GBL.sec<sec_dim
  - if dim!=scr_bright
    - set dim=scr_bright
- if GBL.sec>=sec_sleep
  - set page=screensaver
- if GBL.sec>=sec_dim
  - set dim=scr_dim
- if page!=home && GBL.sec>=sec_home
  - set page=home

**`TouchCap`** activity - fires on touch

- if page==screensaver
  - page=home
- set GBL.sec=0

### Home Page

Information

### Device Pages

#### Security

Use eventLoop Timer to control functionality

**Required Input**
- Security.Pin - text len min 4 max 6
- Security.state - Armed Home/Armed Away/Disarmed/Arming

**Display**
- If Security.state = Disarmed
  - Hide Keypad
  - Hide Armed Icon
  - Show Arm Home
  - Show Arm Away
- If Security.state = Armed*
  - Show Armed Icon
  - Show Keypad
  - Hide Arm Home
  - Hide Arm Away

**Keypad Functionality**
- Displays digits 0-9, back, clear, Enter
- Displays pin box in password mode
- Pressing 0-9, appends value to pin box
- Pressing back, removes last char from pin box
- Pressing clear, removes all chars from pin box
- Pressing enter,
  - compares pin box to Security.Pin, match will publish Security.state=Disarmed
  - removes all chars from pin box

#### Media

#### Lighting

#### Fireplace

#### Thermostat

#### Weather

#### Fan

### Utility Pages

#### Notify

#### Screensaver

#### Connecting
