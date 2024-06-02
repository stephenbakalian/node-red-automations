# Temaple Name

Every 30min get the temperature then categorize it into one of five options, then store it into a HA `input_select`. 

This makes it easier to manage other flows and automations based on ouside tempaerature ranges. 

## Flow

![Example image](./outsidetemp.png)


## Requirements

The full list of packages that are required:

        "node-red-contrib-home-assistant"

- A weather tracking entity in HA. I am using `Meteorologisk institutt (Met.no)`