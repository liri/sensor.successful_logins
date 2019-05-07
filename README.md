# sensor.successful_logins
Home Assistant sensor which allows you to get information about successful logins.

To get started put `/custom_components/successful_logins/sensor.py` in your config directory: 
`<config directory>/custom_components/successful_logins/sensor.py`  

For example: 
`/home/homeassistant/.homeassistant/custom_components/successful_logins/sensor.py`  

**Example configuration.yaml:**

```yaml
# if you're missing a logger setup, paste the below in your configuration.yaml file
logger:
  default: critical

# this is the setup of the custom sensor
sensor:
  - platform: successful_logins
```

**Configuration variables:**

| key | required | default | description
| --- | --- | --- | ---
| **platform** | yes | | The sensor platform name.
| **enable_notification** | no | `true` | Turn on/off `persistant_notifications` when a new IP is detected, can be `true`/`false`.
| **exclude** | no | | A list of IP adresses you want to exclude.
| **provider** | no | 'ipapi' | The provider you want to use for GEO Lookup, 'ipapi', 'extreme', 'ipvigilante'.
| **log_location** | no | | Full path to the logfile.
| **time_frame** | 12 | | The sensor scan time frame in log file, value is in hours.

**Default view:**
![Default view](/img/sensor.jpg)

**Card view:**
![Card view](/img/sensor_card.jpg)

If a new IP is detected, it will be added to a `.logged_in_ips.yaml` file in your configdir, with this information:

```yaml
8.8.8.8:
  ip_address: 8.8.8.8
  city: Mountain View
  country: US
  hostname: google-public-dns-a.google.com
  last_authenticated: '2018-07-26 09:27:01'
  previous_authenticated_time: '2018-07-26 09:27:01'
  region: california
```

If not disabled, you will also be presented with a `persistent_notification` about the event:\
![notification](/img/persistant_notification.png)

## Debug logging

In your `configuration.yaml`

```yaml
logger:
  default: warn
  logs:
    custom_components.sensor.successful_logins: debug
```

***
