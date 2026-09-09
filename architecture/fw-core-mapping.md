# FW-CORE — VMware Network Adapter to pfSense Interface Mapping

## Purpose

Before assigning WAN/LAN interfaces in pfSense, the VMware virtual network adapters were manually correlated with the pfSense `emX` interfaces using their MAC addresses.

This was done intentionally instead of using pfSense's automatic interface detection so that the relationship between the virtual hardware, VMware VMnets, and pfSense interfaces could be verified and documented.

## Verified MAC Address Mapping

| VMware Adapter    | MAC Address         | pfSense Interface |
| ----------------- | ------------------- | ----------------- |
| Network Adapter 1 | `00:0C:29:69:90:6C` | `em0`             |
| Network Adapter 2 | `00:0C:29:69:90:76` | `em1`             |
| Network Adapter 3 | `00:0C:29:69:90:80` | `em2`             |
| Network Adapter 4 | `00:0C:29:69:90:8A` | `em3`             |
| Network Adapter 5 | `00:0C:29:69:90:94` | `em4`             |
| Network Adapter 6 | `00:0C:29:69:90:9E` | `em5`             |

## Purdue-Model Network Mapping

Based on the VMware configuration, the verified interface mapping is:

| pfSense Interface | VMware Adapter | VMware Network | Purdue Zone      | Subnet          | Gateway      |
| ----------------- | -------------- | -------------- | ---------------- | --------------- | ------------ |
| `em0`             | Adapter 1      | VMnet2         | Corporate        | `10.10.10.0/24` | `10.10.10.1` |
| `em1`             | Adapter 2      | VMnet3         | OT DMZ           | `10.10.20.0/24` | `10.10.20.1` |
| `em2`             | Adapter 3      | VMnet4         | Central OT       | `10.10.30.0/24` | `10.10.30.1` |
| `em3`             | Adapter 4      | VMnet5         | Water Plant      | `10.10.51.0/24` | `10.10.51.1` |
| `em4`             | Adapter 5      | VMnet6         | Pipeline Station | `10.10.52.0/24` | `10.10.52.1` |
| `em5`             | Adapter 6      | VMnet7         | Substation       | `10.10.53.0/24` | `10.10.53.1` |

## Why MAC Address Verification Was Used

The `emX` names assigned by pfSense identify the network interfaces inside the FreeBSD operating system, but the names themselves do not identify which VMware VMnet an interface is connected to.

The MAC address provides the common identifier between VMware and pfSense.

The relationship is therefore:

**VMware Network Adapter → MAC Address → pfSense `emX` Interface → VMnet → Purdue Zone → IP Subnet**

This prevents accidental interface assignment and provides a repeatable troubleshooting method if an interface is ever moved or recreated.

## Final Interface Assignment

The verified mapping will be used for the pfSense interface assignment process:

* `em0` → Corporate / VMnet2
* `em1` → OT DMZ / VMnet3
* `em2` → Central OT / VMnet4
* `em3` → Water Plant / VMnet5
* `em4` → Pipeline Station / VMnet6
* `em5` → Substation / VMnet7

No VLAN interfaces are being created in pfSense. Network segmentation is being provided by separate VMware VMnets and dedicated virtual network adapters.
