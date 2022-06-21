### I2C Framework Expansion Card Parts

|  # | Part                                      | RefDes  | Preferred Part Number      |
|---:|-------------------------------------------|---------|----------------------------|
|  1 | C 100nF X7R 16V (0805)                    | C1      | 478-5311-1-ND              |
|  1 | C 470nF X7R 16V (0805)                    | C2      | 1276-1199-1-ND             |
|  3 | C 1uF X7R 16V (0805)                      | C3-C5   | 1276-6471-1-ND             |
|  1 | DS LED (0805)                             | DS1     | 475-1415-1-ND              |
|  2 | F 200 mA fast (0805)                      | F1-F2   | 507-1811-1-ND              |
|  1 | J JST XH Vertical (4w)                    | J1      | 455-2249-ND                |
|  1 | P USB C, plug, straddle 0.8mm             | P1      | WM12855-ND                 |
|  3 | R 3.3K 0.125W (0805)                      | R1-R3   | RMCF0805FT3K30CT-ND        |
|  1 | R 5.1K 0.125W (0805)                      | R4      | RMCF0805FT5K10CT-ND        |
|  1 | U MCP2221 (SOIC-14)                       | U1      | MCP2221-I/SL-ND            |
|  1 | VR AP2138N-3.3TRG1 (SOT23-3)              | VR1     | AP2138N-3.3TRG1DICT-ND     |
|  1 | C 10nF X7R 16V (0805) `NOT POPULTED`      | C6      | 399-17617-1-ND             |
|  1 | U LTC4311 (SOT363) `NOT POPULATED`        | U2      | LTC4311CSC6#TRPBFCT-ND     |


#### Board Size

|       |      Dimensions | Area    | Thickness |
|-------|-----------------|---------|-----------|
| PCB   |  24.0 x 27.9 mm | 1.1 in² |    0.8 mm |


#### Power

| Property | Value  |
|----------|-------:|
| Voltage  |    5 V |
| Current  | 100 mA |


#### Jumpers

##### 3V3

This jumper has to be bridged for operation in 3.3V. If this jumper is bridged,
5V jumper MUST NOT be bridged too.

##### 5V

This jumper has to be bridged for operation in 5V. If this jumper is bridged,
3.3V jumper MUST NOT be bridged too.

For operation at 5V, the following components can be omitted:
* C3-C4
* VR1


#### Pull-up Resistors

It's really hard to get an universal pull-up resistor values when it's not
known ahead of time what capacitance will I2C bus end up with. Considering
this device is intended for testing I2C, I trust 3.3KΩ is still enough to
allow for decent bus capacitance while also high enough not to mess with
devices. However, this is just a starting point and changing pull-up resistors
(either with higher or lower values) is sometime necessary.

You can also populate `C6` and `U2` with LTC4311 I2C "accelerator" that will
greatly improve rise time. I find that usually messing with I2C is enough.


#### USB communication

USB is not ideal protocol for I2C communication due to how transfers are
handled and thus your I2C bandwidth will be severly limited.
