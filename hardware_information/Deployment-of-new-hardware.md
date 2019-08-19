# Deployment of new hardware

This document describes the physical installation of the AC922 system. See
https://www.redbooks.ibm.com/redpapers/pdfs/redp5472.pdf for full details
on the AC922 physical specifcations.

## Racking

The AC922 system is a 2U rack-mount server. The air-cooled model (8335-GTG)
is compatible with a standard OEM 19" rack.

The water-cooled model (8335-GTW) requires the 42U IBM Enterprise Slim Rack
(7965-S42).

## Power requirements

The AC922 has 2 redundant 2200W power supplies, and requires cables with Rong
Feng 203P-HP plug. They should each be plugged into a seprate PDU capable of
delivering 10 Amps to the socket.

The two power supplies provide redundant power, but permormance may be
degraded if one power supply is offline, especially in 6 GPU configurations.


## Networking

The AC922 has a 1 Gigabit ethernet port onboard, this interface is available
to the BMC for remote management. The BMC will be available on this interface
any time the machine is connected to power, even if the system is powered off,
or if no operating system is boot or present.

A dedicated management subnet is recommended to isolate the BMC from the
general use network.

## OpenBMC/IPMI

The AC922 is managed by a Baseboard Management Controller, or BMC.

This controller is essentially a self-contained computer running linux, from
which the system's hardware can be managed.

See

https://www.ibm.com/support/knowledgecenter/en/POWER9/p9eih/p9eih_openbmc_kickoff.htm

for detailed information about usign the BMC.

