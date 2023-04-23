# Dataset Storage Interface

## Summary 
This repository contains the description of a data storage interface in order to store and retrieve data in a standardized manner. 
It is intantionated primairily in the context of data storage of RF channel sounding, RF simulations, acoustic experiments, in order to conviently store, exchange and access the experiment data.

### What is it

### What is it not

## Interface Description

Component overview:
- Testbeds
- Environments
- Measurement Scenarios
- Data Acquisition System
- Datasets
- Storage Location (URL/local)

## Data Sources

### Types

- SDR: software-defined radio
- ADC/DAC: raw ADC/DAC measurement device
- VNA

```yaml
define &B210:
  name: "B210"
  type: "SDR"
  min_freq: 70E6
  max_freq: 5E9
  min_BW: 250E3
  max_BW: 40E6
  num_channels: 2 
```

## Testbed Description file

While not required, we suggest adding your testbed description files in [the following repository](https://github.com/6G-Testbeds/Testbed-Description-Files).
Below are some examples and the YAML schema to make your own testbed description file.


