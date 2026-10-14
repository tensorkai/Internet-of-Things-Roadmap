# Networking and Wireless Communication

[Back to roadmap](../README.md)

## Prerequisites

Categories 04–06; basic calculations from 03.

## Topics to learn

- [ ] Separate physical/link, network, transport, and application layers. Explain MAC versus IP addresses and why a working radio link does not guarantee a working application.
- [ ] Learn IPv4 and IPv6 addressing, subnets, routing, DNS, DHCP, local discovery, NAT, firewalls, ports, and socket lifecycles.
- [ ] Compare TCP and UDP: reliability mechanisms, congestion, ordering, connection overhead, and application responsibilities.
- [ ] Use Ethernet and Wi-Fi; learn association, authentication, provisioning, signal strength, interference, reconnection, and time synchronization.
- [ ] Study BLE advertising, scanning, central/peripheral roles, GATT services and characteristics, connection intervals, pairing, and bonding.
- [ ] Compare Zigbee and Thread mesh roles, gateways/border routers, and commissioning. Thread supplies IP networking; Matter adds an application interoperability layer.
- [ ] Distinguish LoRa radio modulation from LoRaWAN networking. Study gateway coverage, network/application roles, airtime, receive windows, regional parameters, and downlink limits.
- [ ] Compare cellular IoT choices such as LTE-M and NB-IoT using coverage, operator support, provisioning, power, and recurring cost rather than assuming universal availability.
- [ ] Calculate link budgets and consider antenna placement, interference, walls, enclosures, packet size, and retransmissions. Confirm applicable regional radio rules for an actual deployment.
- [ ] Implement timeouts, capped exponential backoff with jitter, bounded offline queues, and recovery after address or network changes. Prevent reconnect storms.

## Hands-on work

1. Inspect DNS resolution, addressing, and a TCP connection using network tools and a packet capture.
2. Measure delivery rate and latency at several locations; record signal strength and environmental conditions.
3. Compare two connectivity choices in a requirements matrix, then implement one and test router and access-point restarts.

## Completion evidence

- [ ] Explain a failure at each network layer and show the evidence used to isolate it.
- [ ] Demonstrate automatic recovery without unbounded retries, queue growth, or loss of local control.
- [ ] Provide a justified connectivity choice with power, coverage, cost, and infrastructure assumptions.

