# RF Channel Dataset Storage Interface

Component overview:
- Testbeds
- Environments
- Measurement Scenarios
- Datasets

## Testbed Description file

```yaml
num_rx_antennas: 280 # how many antennas can be used in RX mode
num_tx_antennas: 280 # how many antennas can be used in TX mode
num_antennas: 280 # how many physical/virtual antennas can be used
antennal_loc: # physical location of each antenna element (relative to the first antenna element)
  - [0,0,0]
  - [0,0,1]
antenna_loc_unit: "m" # unit used for antenna locations
level: "L3" # Level of testbed
min_freq: 70E6
max_freq: 5E9
min_BW: 250E3
max_BW: 40E6

```
