# hass-roborock
Communicates with roborock using Tuya, so can be used alongside roborock app.

To get token from roborock app, run on rooted device (bluestacks / genymotion should work and be the easiest way of doing it):

```
adb exec-out run-as com.roborock.smart find /data/data/com.roborock.smart/files/rr_cache/ | egrep rr_tuya_[0-9] | xargs -n1 adb exec-out run-as com.roborock.smart cat > roborock_details.gz 
gzip -d roborock_details.gz 
```

Then token is listed in the JSON structure under "localKey". The device ID is listed under "devId"

In Home Assistant goto HACS -> Integrations. In the upper right corner menu select "Custom Repositories".
Add the URL of this project  https://github.com/89jd/hass-roborock and choose "Integration" as category.
Now restart Home Assistant
Next goto the Home Assistant -> Configuration -> Integrations and add the Roborock integration and enter a name, the localKey and devID you found and the IP off the Roborock.

The Roborock should now became available as an entity, not a device.


