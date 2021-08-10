# HomeAssistant-ZHA 4 Gang Zigbee Switch TS004F
Documentation for enabling the 4 Gang Zigbee Switch TS004F in HomeAssistant using ZHA Integration

After spending at least an hour or more running through the various threads regarding this 4-Gang switch, specifically the TS004F. I thought I would just put a concise rundown on how to get this working and the outcomes / limitations.

**Firstly, the limitations:**

This will not be configured as a 12 button switch. The only actions that are available once correctly configured are:

- First Button Pressed
- Second Button Pressed
- Third Button Pressed
- Fourth Button Pressed
- Third Button Continuosly Pressed
- Fourth Button Continuosly Pressed
- Fourth Button Released After Long Pressed (I dont see this mentioned elsewhere but it shows as an event on mine.

**Configuration**

Before proceeding, delete any instances of this device in your ZHA integration and ensure that your gateway is on the latest firmware version.

1.  Create a folder on your HA instance **config** folder called **custom_zha_quirks** for instance

    `\\homeassistant\config\custom_zha_quirks`

2. Create a file in this new folder called **ts004f.py** and copy the latest content of the file:

    [TS004F custom quirk](https://gist.github.com/koying/7ffb29e2db56649b8cb7fd5702a2ff46#file-ts004f-py)

3. In your **config\configuration.yaml** add the following lines:

    `zha:`
        `custom_quirks_path: /config/custom_zha_quirks/`

4. Restart your HA instance

5. In the ZHA integration, add a new device, this will start the searching process

6. On the device, hold the BOTTOM LEFT button for 10+ seconds, until all four lights begin flashing

7. Wait for several seconds until ZHA descovers the device

**Outcome**

One point of confusion seems to be that no entities show up. This is expected. This device will add EVENTS not entities.

So you may not see any change from previous in the ZHA discovered device.

However, when you are creating automations etc, you will see the new events available:

![ZHA TS004F](https://user-images.githubusercontent.com/4596455/128822919-41dfefc0-977e-43f7-85a5-664bd35909d1.png)

As far as I know, at this point, this is the end result that we can expect.

