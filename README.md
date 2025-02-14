# Leakomatic home automation scripts
Some python scripts to make it easier to integrate leakomatic devices to home automation systems.

No guarantees whatsoever that they work in the future since Leakomatic don't provide any official API.

Updated to also handle Sleep mode.

## Docs
get-status.py
```
python3 get-status.py -h
usage: get-status.py [-h] -u USERNAME -p PASSWORD -d DEVICE [-s | --home-status | --no-home-status] [-a | --alarm-status | --no-alarm-status] [-j | --json | --no-json] [--disable-json-beatify | --no-disable-json-beatify]

options:
  -h, --help            show this help message and exit
  -u USERNAME, --username USERNAME
                        Username to cloud.leakomatic.com
  -p PASSWORD, --password PASSWORD
                        Password to cloud.leakomatic.com
  -d DEVICE, --device DEVICE
                        Device id to target. Can be seen in the path of the request that looks like "/devices/[your-ID]/change_mode.json" when changing mode.
  -s, --home-status, --no-home-status
                        Print if in away or home mode
  -a, --alarm-status, --no-alarm-status
                        Print the alarm status. "Alarm" if there currently is an alarm, "No alarm" otherwise
  -j, --json, --no-json
                        Print the raw json
  --disable-json-beatify, --no-disable-json-beatify
                        Don't beatify the json, just print it on one row
```

change-home-mode.py
```
python3 change-home-mode.py -h
usage: change-home-mode.py [-h] -m MODE -u USERNAME -p PASSWORD -d DEVICE

options:
  -h, --help            show this help message and exit
  -m MODE, --mode MODE  Put on or of home mode. 0 is home, 1 is away
  -u USERNAME, --username USERNAME
                        Username to cloud.leakomatic.com
  -p PASSWORD, --password PASSWORD
                        Password to cloud.leakomatic.com
  -d DEVICE, --device DEVICE
                        Device id to target. Can be seen in the path of the request that looks like "/devices/[your-ID]/change_mode.json" when changing mode.
```


## Example
Get if the device is in home or away mode
```
$ get-status.py --username user@example.com --password not-a-real-password --device 9999 -s
Home
```

The sleep mode was added to make it possible to control our Leakomatic M3i from my automatic
irrigation system in the garden. When irrigation starts the Leakomatic is put in Sleep mode
and when irrigation ends it is put in Home mode.

