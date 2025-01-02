# Message Definitions

| Message Name | Message Id | Data Length | Request Flag | Payload B1 | Payload B2 | Payload B3 | Payload B4 | Payload B5 | Payload B6 | Payload B7 | Payload B8 | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |
| Input Gear Shift | 0b00 | 2 | 0 | SRC_DEVICE_ID | DIRECTION |   |   |   |   |   |   | Sent to indicate a desire to shift gears. DIRECTION is a signed short (-2 DOWN to N, -1 DOWN, 1 UP, 2 UP to N) |
|   |   |   |   |   |   |   |   |   |   |   |   |   |
| Measured Throttle Position | 0b00 | 2 | 0 | SRC_DEVICE_ID | Throttle Position | - | - | - | - | - | - | Sent to indicate the measured throttle position |
| Input Transmission Gear | 0b00 | 2 | 0 | SRC_DEVICE_ID | Throttle Position | - | - | - | - | - | - | Sent to indicate the measured throttle position |
| Measured Engine RPM | 0b00 | 3 | 0 | SRC_DEVICE_ID | INT_p1 | INT_p2 | - | - | - | - | - | Sent to indicate the current engine RPM |
| Measured Wheel RPM | 0b00 | 3 | 0 | SRC_DEVICE_ID | INT_p1 | INT_p2 | - | - | - | - | - | Sent to indicate the current wheel RPM |
| Measured Wheel Speed | 0b00 | 5 | 0 | SRC_DEVICE_ID | FLOAT_p1 | FLOAT_p2 | FLOAT_p3 | FLOAT_p4 | - | - | - | Sent to indicate the current wheel speed |
| Measured GPS Speed | 0b00 | 5 | 0 | SRC_DEVICE_ID | FLOAT_p1 | FLOAT_p2 | FLOAT_p3 | FLOAT_p4 | - | - | - | Sent to indicate the current GPS speed
| Measured GPS Latitude | 0b00 | 5 | 0 | SRC_DEVICE_ID | FLOAT_p1 | FLOAT_p2 | FLOAT_p3 | FLOAT_p4 | - | - | - | Sent to indicate the current GPS latitude |
| Measured GPS Longitude | 0b00 | 5 | 0 | SRC_DEVICE_ID | FLOAT_p1 | FLOAT_p2 | FLOAT_p3 | FLOAT_p4 | - | - | - | Sent to indicate the current GPS longitude |
| Measured GPS Altitude | 0b00 | 5 | 0 | SRC_DEVICE_ID | FLOAT_p1 | FLOAT_p2 | FLOAT_p3 | FLOAT_p4 | - | - | - | Sent to indicate the current GPS altitude |
| Measured GPS Time | 0b00 | 2 | 0 | SRC_DEVICE_ID | RPM | - | - | - | - | - | - | Sent to indicate the current engine RPM |
| Measured GPS Date | 0b00 | 2 | 0 | SRC_DEVICE_ID | RPM | - | - | - | - | - | - | Sent to indicate the current engine RPM |
| Measured Tyre Data | 0b00 | 7 | 0 | SRC_DEVICE_ID | TYRE_INDEX | TYRE_DATA_TYPE | FLOAT_p1 | FLOAT_p2 | FLOAT_p3 | FLOAT_p4 | - | Sent to indicate current tyre data. TYRE_INDEX and TYRE_DATA_TYPE indicate which tyre and temp/pressure |
|   |   |   |   |   |   |   |   |   |   |   |   |   |
| Heartbeat | 1537, 0b11000000001, 0x601 | 1 | 0 | SRC_DEVICE_ID | - | - | - | - | - | - | - | Sent by every device every HEARTBEAT_MS milliseconds |
| Conscious Request | 1538, 0b11000000010, 0x602 | 2 | 1 | SRC_DEVICE_ID | DST_DEVICE_ID | - | - | - | - | - | - | Sent by SRC_DEVICE_ID to check if DST_DEVICE_ID is alive |
| Conscious Response | 1539, 0b11000000011, 0x603 | 1 | 1 | SRC_DEVICE_ID | - | - | - | - | - | - | - | Sent by SRC_DEVICE_ID to assert it is alive |
| Identity | 1540, 0b11000000100 | 2 | 1 | SRC_DEVICE_ID | DST_DEVICE_ID |   |   |   |   |   |   | Sent by SRC_DEVICE_ID to get the identifier of DST_DEVICE_ID |
| Announce | 1541, 0b11000000101 | 8 | 0 | SRC_DEVICE_ID | CHAR1 | CHAR2 | CHAR3 | CHAR4 | CHAR5 | CHAR6 | CHAR7 | Sent by SRC_DEVICE_ID to annouce its identifier CHAR1-7 |
|   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |



# Message Id Structure
| Bit     | 11-10    | 9-0        |
|---------|----------|------------|
| Purpose | Priority | Message Id |


## Message Priority



| Priority | Decimal | Binary | Name | Notes | Use Case(s) |
|---|---|---|---|---|---|
| HIGHEST | 0 | 0b00 | Input | Messages containing data from sensor or user inputs should use this priority | User Inputs, Sensor Data |
| HIGHER | 1 | 0b01 | Important | Messages containing time-sensitive or ephemeral data should use this priority | Time-sensitive Data, Ephemeral Data |
| LOWER | 2 | 0b10 | Normal | Messages that don't fit into their category above should use this priority | **Default** |
| LOWEST | 3 | 0b11 | Minor | Messages containing unimportant data should use this priority | Heartbeat / Health Notifications |
