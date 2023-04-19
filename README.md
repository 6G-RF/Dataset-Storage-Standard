# RF Channel Dataset Storage Interface

Component overview:
- Testbeds
- Environments
- Measurement Scenarios
- Datasets

## Software defined radios

```yaml
define &B210:
  name: "B210"
  min_freq: 70E6
  max_freq: 5E9
  min_BW: 250E3
  max_BW: 40E6
```

## Testbed Description file

```yaml
name: "Techtile"
descrption: "Small description"
url: "https://github.com/techtile-by-dramco"
num_rx_antennas: 280 # how many antennas can be used in RX mode
num_tx_antennas: 280 # how many antennas can be used in TX mode
num_antennas: 280 # how many physical/virtual antennas can be used
antennal_loc: # physical location of each antenna element (relative to the first antenna element) [x,y,z]
  - [0,0,0]
  - [0,0,1]
antenna_loc_unit: "m" # unit used for antenna locations
level: "L3" # Level of testbed
software_define_radio:
  <<: *B210
```
