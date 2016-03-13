+++
categories = ["linux", "command"]
date = "2016-03-13T12:14:21-03:00"
learning = ""
title = "What is the maximun ram supported?"

+++

**Discover how much ram machine supports:**

{{<highlight bash>}}
sudo dmidecode -t 16
{{</highlight>}}

Output:

```
# dmidecode 2.12
SMBIOS 2.6 present.

Handle 0x002E, DMI type 16, 15 bytes
Physical Memory Array
  Location: System Board Or Motherboard
  Use: System Memory
  Error Correction Type: None
  Maximum Capacity: 8 GB
  Error Information Handle: Not Provided
  Number Of Devices: 2
```

**Discover your currently memory installed:**

{{<highlight bash>}}
sudo dmidecode -t 17
{{</highlight>}}

Output:

```
# dmidecode 2.12
SMBIOS 2.6 present.

Handle 0x002F, DMI type 17, 28 bytes
Memory Device
  Array Handle: 0x002E
  Error Information Handle: Not Provided
  Total Width: 64 bits
  Data Width: 64 bits
  Size: 4096 MB
  Form Factor: DIMM
  Set: None
  Locator: ChannelA-DIMM0
  Bank Locator: BANK 0
  Type: DDR3
  Type Detail: Synchronous
  Speed: 1333 MHz
  Manufacturer: 0194
  Serial Number: 04570365
  Asset Tag: 9876543210
  Part Number: SH564128FH8N0QHSCG
  Rank: 2

Handle 0x0031, DMI type 17, 28 bytes
Memory Device
  Array Handle: 0x002E
  Error Information Handle: Not Provided
  Total Width: 64 bits
  Data Width: 64 bits
  Size: 4096 MB
  Form Factor: DIMM
  Set: None
  Locator: ChannelB-DIMM0
  Bank Locator: BANK 2
  Type: DDR3
  Type Detail: Synchronous
  Speed: 1333 MHz
  Manufacturer: Kingston
  Serial Number: E738A62B
  Asset Tag: 9876543210
  Part Number: 9905471-021.A00LF
  Rank: 2
```
