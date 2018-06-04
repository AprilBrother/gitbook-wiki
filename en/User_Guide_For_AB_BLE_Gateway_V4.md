

[← AB BLE Gateway V4 Main Page](AB_BLE_Gateway_V4.md)



## Data Format

Gateway V4 post data in [MessagePack](https://msgpack.org/) format.
MessagePack is an efficient binary serialization format. It lets you
exchange data among multiple languages like JSON. But it's faster and
smaller.

MessagePack is an efficient binary serialization format. It lets you
exchange data among multiple languages like JSON. But it's faster and
smaller. We can get more library for programming languages to parse
MessagePack.

## Keys

The data decoded is a dictionary with these keys:

  - v - firmware version
  - mid - message ID
  - time - boot time
  - ip - the IP for gateway
  - mac - the mac address for gateway
  - devices - an array for BLE advertising datas that gateway collected

The devices array contain RAW advertising data for BLE device. An
example hex data frame, see the section "Data Format For Key Devices"

`00 12 3b 6a 1a 64 cf aa 02 01 06 1a ff 4c 00 02 15 b5 b1 82 c7 ea
b1 49 88 aa 99 b5 c1 51 70 08 d9 00 01 cf 64
c5`

|            |                                       |                                                                                           |
| ---------- | ------------------------------------- | ----------------------------------------------------------------------------------------- |
| Bytes      | Description                           | Example                                                                                   |
| byte 1     | advertising type, see the table below | 00                                                                                        |
| byte 2 - 7 | mac address for BLE device            | `12 3b 6a 1a 64 cf`                                                                       |
| byte 8     | RSSI, minus 256 for real value        | aa, 0xaa - 256 = -86                                                                      |
| byte 9 -   | Advertisement data                    | 02 01 06 1a ff 4c 00 02 15 b5 b1 82 c7 ea b1 49 88 aa 99 b5 c1 51 70 08 d9 00 01 cf 64 c5 |
|  |

Advertising Type Code

|      |                                          |
| ---- | ---------------------------------------- |
| Code | Description                              |
| 0    | Connectable undirected advertisement     |
| 1    | Connectable directed advertisement       |
| 2    | Scannable undirected advertisement       |
| 3    | Non-Connectable undirected advertisement |
| 4    | Scan Response                            |
|  |

### Data Format For Key Devices

以这段数据为例hex=`02C8FD1949A530CE0201061AFF4C000215EB6D469624BE4663B15230D46B0E9CC9000D002AC0`

    02 = adv type
    C8FD1949A530 = mac address
    CE = rssi
    0201061AFF4C000215EB6D469624BE4663B15230D46B0E9CC9000D002AC0 = raw advertising data
