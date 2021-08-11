# HomeAssistant-ZHA-4-Gang-Zigbee-Switch-TS004F

After spending at least an hour or more running through the various threads regarding this 4-Gang switch, specifically the TS004F. I thought I would just put a concise rundown on how to get this working and the outcomes / limitations.

**Firstly, the limitations:**

This will not be configured as a 12 button switch. The only actions that are available once correctly configured are:

- Turn On button pressed
- Turn off button pressed
- Dim up button pressed
- Dim down button pressed
- Dim up continuously pressed
- Dim down continuously pressed
- Dim down released after long press

**Configuration**

Before proceeding, delete any instances of this device in your ZHA integration and ensure that your gateway is on the latest firmware version.

1.  Create a folder on your HA instance **config** folder called **custom_zha_quirks** for instance

    `\\homeassistant\config\custom_zha_quirks`

2. Create a file in this new folder called **ts004f.py** and copy the latest content of the file:

    [TS004F custom quirk](https://github.com/zigpy/zha-device-handlers/pull/969/files)

3. In your **config\configuration.yaml** add the following lines:

    `zha:`
        `custom_quirks_path: /config/custom_zha_quirks/`

4. Restart your HA instance

5. In the ZHA integration, add a new device, this will start the searching process

6. On the device, hold the BOTTOM LEFT button for 10+ seconds, until all four lights begin flashing

7. Wait for several seconds until ZHA discovers the device

**Outcome**

One point of confusion seems to be that no entities show up. This is expected. This device will add EVENTS not entities.

So you may not see any change from previous in the ZHA discovered device.

However, when you are creating automations etc, you will see the new events available:

![ZHA TS004F-2](https://user-images.githubusercontent.com/4596455/128861272-58308365-a5c7-410a-96be-7c82b0a96190.png)

As far as I know, at this point, this is the end result that we can expect.

