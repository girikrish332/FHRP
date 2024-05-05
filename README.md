# FHRP Configuration for Routers R1 and R2

## Overview
This repository contains the configuration for implementing First Hop Redundancy Protocol (FHRP) on routers R1 and R2. FHRP provides high availability and fault tolerance for network devices by allowing multiple routers to share a virtual IP address.

## Configuration Details

### R1 Configuration
```plaintext
interface FastEthernet0/0
  ip address 10.207.1.10 255.255.255.0
  no shutdown

interface FastEthernet1/0
  ip address 10.0.1.1 255.255.255.0
  no shutdown

ip route 0.0.0.0 0.0.0.0 10.207.1.1

standby 1 preempt
standby 1 ip 10.0.1.254
standby 1 priority 100
interface FastEthernet0/0
  ip address 10.207.1.20 255.255.255.0
  no shutdown

interface FastEthernet1/0
  ip address 10.0.1.2 255.255.255.0
  no shutdown

ip route 0.0.0.0 0.0.0.0 10.207.1.1

standby 1 preempt
standby 1 ip 10.0.1.254
standby 1 priority 200
Usage

To implement this configuration, copy the respective configurations to the CLI interface of routers R1 and R2, and ensure proper connectivity and redundancy in the network infrastructure.
Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Usage

To implement this configuration, copy the respective configurations to the CLI interface of routers R1 and R2, and ensure proper connectivity and redundancy in the network infrastructure.
Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
