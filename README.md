# Dataset Storage Standard (DSS)

## Summary 
This repository contains the description of a data storage standard in order to store and retrieve data in a standardized manner. 
It is intantionated primairily in the context of data storage of RF channel sounding, RF simulations, acoustic experiments, in order to conviently store, exchange and access data.

The standard exists of human-readable files (YAML) describing the testbed and experiments, and a common data storage format.

### What is it

### What is it not

## Interface Description

Component overview:
- Environments (description)
- Testbed (description)
- Experiment (description)
- Data Source (description)
- Datasets
- API
  * Storage Location (URL/local)

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

## Experiment Description file
```yaml
name: "same name as file"
description: "Describing the file"
testbed: *ref_testbed
scenarios:
 - data_source: #optional list of data_source indexes
   data_source_type: "SDR"
   sampling_rate: 250e3
   domain: "freq"
   freq: 433e6
   pos_type: "GPS" # or relative
 - data_source_type: "ADC"
   sampling_rate: 10e3
```

per scenario described in the experiment description file, a new data set is stored with the samen name as the experiment file including a postfix 01,02,03,...

## Dataset

A simple data set structure is used to store the data of a specific experiment scenario. A tensor is used with the following dimensions:
```
data source | data | channel (optional) | timestamp (optional) | user (optional) | position (optional)
```

The datatypes should be infered from the dataset. The timestamp could be infered from the start_time in the experiment description file, but this is not required.
Based on the start time and the sampling rate, these timestamp can be generated. The channel dimension indicates which channel of the data source is used. For example, some software-defined-radios have multiple rx chains on the same SDR board, each RX chain is seen as a seperate channel. The position of the user can be included in the dataset or in the scenario file depending.
If the user is fixed during the scenario, it should be included in the scenario descpription, otherwise it can be included in the dataset. 

The dataset is stored in a HDF5 to keep interoperability with a range of programming languages.

All metatadata required to interpret the dataset needs to be included in the dataset file.
Example, in xarray the `attrs` could contain the serialized yaml files as an ordered dictonary.

## API

Example usages:

### Plot the PDP for each user position
```python
experiment = load("meas.yml")
scenarios = experiment.get_scenarios()

for sc in scenarios:
    grouped_ds = sc.get_ds().groupby("position")
    for ds in grouped_ds:
        utils.plot_pdp(ds)
```

## Uses of the DSS
-



