# Thursday (Day 2)

## Why We Can't Have an Internet of Nice Things (Sean Dague)

* Many points of failure in a typical device -> home internet -> vendor cloud
  -> mobile app IoT home setup (think Nest):
    - Mobile device support.
    - Interesting automation needs to be done on mobile phone.
    - What if vendor cloud service goes away?
    - What if you can't get to the service?
    - What if your home internet has an outage?
    - Bad firmware updates.
    - Crowded spectrum at home.

* So, not a super great model if you want something that actually stays up.

* If a company wants to stop supporting a device, they can just brick the
  devices and shutdown the cloud service.

* Big DDoS attack on Dyn in 2016 went through a bunch of IoT security
  cameras that were left wide open.

* Every option has trade offs in security, ease of use, cost, long-term
  viability, etc. There's no one-stop shop for building out a home
  automation ecosystem, and they typically play okay at best with other
  brands.

* Things you might want to have be IoT:
    - Lighting
    - Door Locks
    - AV / Audio
    - Weather Sensors
    - Blinds
    - Motion Sensors

* Home Assistant Project:
    - Written in python
    - Home automation hub
    - Run it on a computer (say a Raspberry Pi 3) at home, and it will talk
      to a bunch of specialized vendor hubs, can sometimes talk directly
      to devices. Can also do OAuth handshakes for devices that must connect
      to some external vendor cloud.
    - Fully open sourced, anyone can add support for any currently
      unsupported device.
    - Extremely clean UI.

## Putting the Third Dimension in Wolfenstein (Benjamin Fillmore)

## Building a Better Thermostat (Matthew Treinish)
