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

* Some brief history of the Wolfenstein series (review). 3D released in 1992.

* Some rudimentary game loop, event tracking, keyboard states, player class, and
  map data/state programming snippets in Javascript.

* Wolfenstein 3D is really just a top-down 2D game shown from a first person
  POV. No fancy math on calculating a z axis. All walls are orthagonal, fall
  on lines of the grid and are the full height of the room. Makes calculations
  super fast. Just some simple trig.

* This is a "raycasting" engine:
    - Only have to draw what the "rays" eminating from the player's eyes connect
      with.
    - The shorter the rays, the closer the object is drawn, giving some faux
      perspective.
    - Check where along the map's grid the player's rays connect with the grid
      lines.

* Once you have that down, you can put it into first person:
    - Draw a column at a time, looping through each column and draw one at a
      time, quickly. Height is a ratio of distance to give perspective.
    - Comes with a "fisheye" effect that can be fixed by taking the cosine of
      the player's ray angles when drawing columns. It isn't technically
      correct, but it looks much better to the player.

* Each time a ray hits a wall, we know where along the wall it hits. It's just
  a lucky side effect of the raycasting. Can assign a texture (image) to the
  wall at draw time and it will render correctly on the wall.

* What about the sprites and objects? **MORE CHEATING**:
    - Sprites are still the full height of the room, but their source images
      are drawn smaller to look proportional. The size they are drawn at is
      still a function of distance to give perspective through taking the
      derivative of the two points ("smallest angle").

* What to do about seeing through walls:
    - Draw each column of the sprite individually, so sprites get covered up
      by the wall if the wall is in between the player and the sprite.

* Speaker still has some improvements to make to his gradual demo:
    - Weapons
    - Floor Casting / Ceiling Casting (textures on floors/ceilings. W3D did not
      have this, but similar raycasting games have since).
    - Skyboxes (much easier than ceilings, big picture of clouds that rotates).
    - Enemies
    - Doors

* [Source Code](http://www.benfillmore.com/RayCast)

## Building a Better Thermostat (Matthew Treinish)

* What is a thermostat?
    - Simple closed-loop controler device, 1 input from a temperature sensor,
      1 output for controlling heating or A/C.

* Constraints for controlling the AC:
    - Can't take apart a window unit if you don't own it (i.e. included in rent).
    - No identifying information for the AC unit.
    - Wireless control is ideal.

* Solution for controlling the AC:
    - ZWave smart siwtch
    - Control via power (relay to turn on/off).
    - Measured current draw with clamp meter.

* What is Z-Wave:
    - Low power mesh network for sensors and devices.
    - Licensed by Sigma Designs.
    - Interoperability tested for all devices by Z-Wave Alliance.
    - Software API and protocol docs in the public domain.
    - Over 1700 certified devices.
    - OpenZWave is an open source library in C/Python to interface with a
      Z-Wave network.

* Sensing the temperature:
    - Wireless Z-Wave multi-sensor, leverages the Z-Wave network.
    - Can sense light, motion, temperature, UV, humidity, etc.

* Using Z-Wave:
    - Setup a Z-Wave network with Aeotec Z-Stick.
    - Register each device on the network.
    - Leverage OpenZWave to provide an API to interact with devices.

* Can use Home Assistant with these Z-Wave devices, provides a generic
  thermostat component.

* Issues:
    - Requires writing a spearate rule for every condition.
    - Some trigger rules were edge-triggered.
    - Switching became unreliable.
    - Adjusting the set point required a config update.

* Speaker wrote DallasMQTT:
    - Framework for polling sensors and pushing results on MQTT.
    - Handles an arbitrary number of sensors.
    - Written in Python.
    - Currently only supports Dallas 1 wire temperature sensor.

* Location tracking:
    - Start writing rules based on location.
    - Set temperature higher when not home.
    - Pre-cool apartment when heading home.

* Owntracks:
    - Open Source iOS and Android app for reporting location over MQTT.
    - Enables you to use either a private MQTT broker or public service.
    - Home Assistant component available.
