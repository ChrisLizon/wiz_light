# wiz_light
A Home assistant integration for (Phillips, SLV and more) WiZ Light bulbs

Tested with the following smart lights:

* [Original Phillips Wiz WiFi LEDs](https://www.lighting.philips.co.in/consumer/smart-wifi-led)
* [SLV Play RGB bulb](https://www.amazon.de/dp/B07PNCDJLW)

## Kudos and contributions
Thank you [@angadsingh](https://github.com/angadsingh) for make such incredible improvements!!

Bug fixes:
 - Fixes https://github.com/sbidy/wiz_light/issues/6: make the whole component truly async using non-blocking UDP
 - Light control now works even when lights are set to a rhythm.

Features:
 - Supports switching the light to rhythm mode! (rhythm is defined as a scene for HA)
 - Implements a pattern of sending multiple command UDP datagrams until response is received
 - Consolidates getPilot and setPilot calls using a PilotBuilder and PilotParser. Removes unnecessary UDP calls for each and every attribute (color, temperature, brightness, scene, etc.) and makes a combined getPilot/setPilot call
 - enhanced debug logging for UDP

This component does need a dependency on `pywizlight` like @sbidy's component which will be install automatically by Home Assistant.

## Next improvement:
- Implement hacs.xyz structure

## Working features 
 - Brigtness
 - Color (RGB)
 - White Color Temprature
 - On/Off, Toggle
 - Effects
 - Setting a rhythm as a scene

 Next up:
  - testing with other hardware -- **Contribution required !!**
  - Config Flow Support
  - Pull to the HA master

## Install for testing 
If you want to try the integration please clone this repo to `<confdir>/custom_components/`.

Run `git clone https://github.com/sbidy/wiz_light` within the `<confdir>/custom_components/`.

You also have to install the `pywizlight` and `asyncio_dgram` packages (`pip install -r requirements.txt`). Questions? Check out the github project [pywizlight](https://github.com/sbidy/pywizlight)

## Testing
See `test.py` for how the underlying API works

## HA config
To enable the platform integration add 
```
light:
  - platform: wiz_light
    name: <Name of the device>
    host: <IP of the bulb>
  - platform: wiz_light
    name: <Name of the device#2>
    host: <IP of the bulb#2>
```
