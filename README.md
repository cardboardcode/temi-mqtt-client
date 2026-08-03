# **What Is This?**
An Android app that runs an MQTT client for temi, which can be used for prototyping purposes.

## **Prerequisites**
Set up an MQTT broker.

> [!WARNING]
> Note that this app is hardcoded to use port 1883 -- it does not use SSL.

## **Configure** :wrench:
Add a ``secrets.properties`` file to the root folder with the following content:

```
MQTT_HOSTNAME="<INSERT BROKER IP ADDRESS HERE>"
MQTT_USERNAME="<INSERT mqtt-user>"
MQTT_PASSWORD="<INSERT mqtt-password>"
ROBOT_NAME="<INSERT robot-name>" 
ROBOT_SERIAL="<INSERT TEMI SERIAL NO>"
```
`ROBOT_NAME` is non-critical but good for logging.

## **Build** :hammer:

1. **Open** Android Studio (`Android Studio Quail 2 | 2026.1.2 Patch 1`)
2. **Build** the project.
3. **Connect** to Temi via `adb` remotely.
4. **Run** the app on Temi.

## **Run** :rocket:

1. **Install** the app.

> [!NOTE]
> Follow the instructions from the official guide. [Click here](https://github.com/robotemi/sdk/wiki/Installing-and-Uninstalling-temi-Applications).

2. **Start** the app.
3. **Edit** the hostname in the provided text-field, if needed.
4. **Tap** on the `Connect` button.


## **Topics**
### **Publish**
Search for `mMqttClient.publish` in MainActivity.java for all published messages. 

In summary:
```bash
temi/{id}/status/info
temi/{id}/status/utils/battery
temi/{id}/event/user/interaction
temi/{id}/event/user/detection
temi/{id}/event/waypoint/goto
```
where `{id}` is the robot's serial number.


### **Subscribe**
Search for `mMqttClient.subscribe` and `parseMessage` in MainActivity.java for all subscribed messages. 

In summary:
```bash
temi/{id}/command/waypoint
temi/{id}/command/move
temi/{id}/command/tts
temi/{id}/command/media
```
where `{id}` is the robot's serial number.
