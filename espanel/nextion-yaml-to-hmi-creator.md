hex 08 00 00 - blocks

next block is either 10 00 00 or F FF FF





# Yaml to Panel (Y2P)

Y2P requirements:

- All configuration is done in a simple YAML file
- YAML file can be processed by Y2P to generate:
  - ESPHome.yaml device configuration file
  - NSPanel.hmi file that can be edited in Nextion Editor if desired.
  - NSPanel.tft file that can be directly deployed to device
- Images specified in YAML can be PNG, JPG, BMP and will be automatically converted to Nextion RGB565 format.
- Image conversion will be capable of resizing, croping, and using neighboring pixels to better process gradients when doing color reduction
- Fonts specified in YAML will be dynamically converted and added.
- A font will have ability to accept a list of SVG files to create a resulting font
- Fonts are limited to the ASCII codepage, no other codepages are currently planned.
- YAML will be capable of doing popups with user defined pages with similar functionality to keyboards
- Generated HMI will have the following builtin functionality:
  - Brightness Control
  - Auto Dimming
  - Auto Sleeping (Blank screen not disable screen)
  - Swipe Top->Down, Bottom->Up
  - Swipe Left->Right, Right->Left
  - Boot/Connecting Screen that awaits HASS Connection
  - Wake on touch/click
- All generated code will be sourced from user editable templates
- full support for template code 