# Sandbox lesson 2: The Central Switch LAN

_Level: Beginner — BuildTheNet 3D Sandbox_

**Status: Verified.** Completed on 2026-11-23; every requirement was machine-checked against the network built in BuildTheNet and passed.

Snapshot taken 2026-11-23. Built in a simulation — no physical or production equipment was involved.

## Scenario

Direct connections do not scale. A Layer 2 switch gives every endpoint its own port in a star, and learns which MAC lives where so frames go only where they need to.

## Objective

Deploy 1 Switch and 3 PCs. Connect each PC to a switch port with a Straight-Through cable. Address the PCs in 192.168.10.0/24 (e.g. .10, .11, .12) and confirm every PC can ping every other PC.

## Checks

| # | Check | Status | Checked by |
|---|---|---|---|
| 1 | Deploy 1 Switch and 3 PCs. Connect each PC to a switch port with a Straight-Through cable. Address the PCs in 192.168.10.0/24 (e.g. .10, .11, .12) and confirm every PC can ping every other PC. | Passed | Sandbox check |

## Result

The lesson's check passed on this snapshot:

> Every PC reaches every other PC through the switch.

## What I did

Built from an empty canvas: 4 devices and 3 cables.

- Juniper-EX-1 (SWITCH): [running-config](configs/Juniper-EX-1.txt)
- PC-1 (PC): 192.168.10.10 255.255.255.0, gateway 192.168.1.1
- PC-2 (PC): 192.168.10.11 255.255.255.0, gateway 192.168.1.1
- PC-3 (PC): 192.168.10.12 255.255.255.0, gateway 192.168.1.1

- Cabled Juniper-EX-1 ge-0/0/0 to PC-1 Eth0
- Cabled Juniper-EX-1 ge-0/0/1 to PC-2 Eth0
- Cabled Juniper-EX-1 ge-0/0/2 to PC-3 Eth0

## Topology

![Topology diagram](topology.svg)

## Addressing

| Device | Interface | Address | Mask | Mode | Gateway |
|---|---|---|---|---|---|
| PC-1 | Eth0 | 192.168.10.10/24 | 255.255.255.0 | VLAN 1 | 192.168.1.1 |
| PC-2 | Eth0 | 192.168.10.11/24 | 255.255.255.0 | VLAN 1 | 192.168.1.1 |
| PC-3 | Eth0 | 192.168.10.12/24 | 255.255.255.0 | VLAN 1 | 192.168.1.1 |

## Device configurations

Running-configs as `show running-config` prints them in the BuildTheNet sandbox. Passwords, secrets, keys and SNMP communities are replaced with `<removed>`.

- [Juniper-EX-1](configs/Juniper-EX-1.txt)

---

Built on [BuildTheNet](https://www.buildthenet.io/sandbox)
