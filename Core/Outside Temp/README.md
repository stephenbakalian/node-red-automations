# Outside Temp

Every 30min get the temperature then categorize it into one of five options, then store it into a HA `input_select`. 

This makes it easier to manage other flows and automations based on ouside tempaerature ranges. 

## Flow

![Example image](./outsidetemp.png)


## Requirements

### Node-Red packages

        "node-red-contrib-home-assistant"

### Home Assistant

- A weather tracking entity in HA. I am using [Environment Canada](https://www.home-assistant.io/integrations/environment_canada/)

It is also useful to use a feels like temperature if possible. An example of this is 

````yaml
- platform: template
  sensors:
    feels_like_temp:
      friendly_name: "Feels Like"
      device_class: temperature
      unit_of_measurement: "°C"
      value_template: >
        {% if not is_state('sensor.name_humidex', 'unknown') %}
          {{ states('sensor.name_humidex') }}
        {% elif not is_state('sensor.name_wind_chill', 'unknown') %}
          {{ states('sensor.name_wind_chill') }}
        {% else %}
          {{ states('sensor.name_temperature') | round(0) }}
        {% endif %}
````
  