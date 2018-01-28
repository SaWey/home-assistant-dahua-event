# Dahua event listener for home-assistant (http://home-assistant.io)

Code borrowed from https://github.com/johnnyletrois/dahua-watch and made into a home-assistant component

Copy the file your custom_components folder and add your configuration.
The component depends on pycurl, if that won't load, check your dependencies.

You can work with multiple camera's or NVR's
For a device, the only required config item is the host, all other values default to the ones below.

```
#Dahua event listener
dahua_event:
  name: Garage
  protocol: http
  host: 192.168.1.123
  port: 80
  user: admin
  password: admin
  events: VideoMotion,CrossLineDetection,AlarmLocal,VideoLoss,VideoBlind
``` 

You can also assign names to channels, if multiple channels are reported by a device.
Just add them at the end of your dahua_event device config:
``` 
channels:
    - number: 0
      name: keuken
    - number: 2
      name: garage
``` 


According to the API docs, these events are available:
(availability depends on your device and firmware)
- VideoMotion: motion detection event
- VideoLoss: video loss detection event
- VideoBlind: video blind detection event.
- AlarmLoca-l: alarm detection event.
- CrossLineDetection: tripwire event
- CrossRegionDetection: intrusion event
- LeftDetection: abandoned object detection
- TakenAwayDetection: missing object detection
- VideoAbnormalDetection: scene change event
- FaceDetection: face detect event
- AudioMutation: intensity change
- AudioAnomaly: input abnormal
- VideoUnFocus: defocus detect event
- WanderDetection: loitering detection event
- RioterDetection: People Gathering event
- ParkingDetection: parking detection event
- MoveDetection: fast moving event
- MDResult: motion detection data reporting event. The motion detect window contains 18 rows and 22 columns. The event info contains motion detect data with mask of every row.
- HeatImagingTemper: temperature alarm event

And here are some events that might work:
- TemperatureAlarm
- BatteryLowPower
- IPConflict
- HotPlug
- StorageLowSpace
- StorageFormat
- StorageNotExist
- ChassisIntruded