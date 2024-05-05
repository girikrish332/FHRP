FHRP Configuration README
Overview

This README provides guidance on configuring First Hop Redundancy Protocol (FHRP) using the Hot Standby Router Protocol (HSRP) on Cisco routers R1 and R2.
Requirements

    Cisco routers (R1 and R2) with appropriate interfaces and connectivity established.
    Basic understanding of Cisco IOS commands.

Configuration Steps
R1 Configuration

    Access router R1 through the command line interface.

en
conf t

Configure interface FastEthernet0/0 with an IP address and enable it.

csharp

int f0/0
ip add 10.207.1.10 255.255.255.0
no sh

Set a default route.

ip route 0.0.0.0 0.0.0.0 10.207.1.1

Configure interface FastEthernet1/0 with an IP address and enable it.

csharp

int f1/0
ip add 10.0.1.1 255.255.255.0
no sh

Configure HSRP on interface FastEthernet1/0.

    standby 1 preempt
    standby 1 ip 10.0.1.254

R2 Configuration

    Access router R2 through the command line interface.

en
conf t

Configure interface FastEthernet0/0 with an IP address and enable it.

csharp

int f0/0
ip add 10.207.1.20 255.255.255.0
no sh

Set a default route.

ip route 0.0.0.0 0.0.0.0 10.207.1.1

Configure interface FastEthernet1/0 with an IP address and enable it.

csharp

int f1/0
ip add 10.0.1.2 255.255.255.0
no sh

Configure HSRP on interface FastEthernet1/0.

    standby 1 preempt
    standby 1 ip 10.0.1.254

Notes

    Ensure that the HSRP priority is appropriately set on each router to determine the active/standby role.
    Verify connectivity and failover behavior after configuring HSRP.
