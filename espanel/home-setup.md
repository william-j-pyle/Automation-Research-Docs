# Home Setup

## Foyer

- NSPanel-Foyer
  - Relay-Left.id=Foyer-Light
  - Relay-Right.id=FrontPorch-Light
  - Button-Left
    - Press
      - Relay-Left.state=!Relay-Left.state
      - Hass.Foyer-Light-Stairs.state=!Relay-Left.state
    - Press-Long
      - Relay-Left.toggle
  - Button-Right
    - Press
    - Press-Long

- NSPanel-Upstairs-Hallway
  - Relay-Left.id=Upstairs-Hallway-Light
  - Relay-Right.id=Foyer-Light-Stairs
  - Button-Left
    - Press
  - Button-Right
    - Press
    - Press-Long
