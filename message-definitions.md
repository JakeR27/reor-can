# Message Definitions

| Message Name | Message Id | Data Length | Request Flag | Payload B1 | Payload B2 | Payload B3 | Payload B4 | Payload B5 | Payload B6 | Payload B7 | Payload B8 | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |


# Message Id Prefixes
| Priority | Decimal | Binary | Name | Notes | Use Case(s) |
|---|---|---|---|---|---|
| HIGHEST | 0 | 0b00 | Input | Messages containing data from sensor or user inputs should use this priority | User Inputs, Sensor Data |
| HIGHER | 1 | 0b01 | Important | Messages containing time-sensitive or ephemeral data should use this priority | Time-sensitive Data, Ephemeral Data |
| LOWER | 2 | 0b10 | Normal | Messages that don't fit into their category above should use this priority | **Default** |
| LOWEST | 3 | 0b11 | Minor | Messages containing unimportant data should use this priority | Heartbeat / Health Notifications |
