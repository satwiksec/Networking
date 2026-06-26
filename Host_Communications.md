# Everything hosts do to speak on internet

## What is a host?
A host is any device that has an IP address and is connected to the network.

But context also matters. In cybersec terms, finding hosts means looking for end host like computers, servers, IoT and not
switches and routers.

## Terms:
### MAC Address
MAC address is the hardware address assigned to a network interface card (NIC).
It is used in the Layer 2 (Ethernet) header and is responsible for hop-to-hop delivery within a local network.

### IP Address
An IP address uniquely identifies a device on a network.
It is carried inside the Layer 3 (IP) header and is responsible for end-to-end delivery.

### ARP
ARP (Address Resolution Protocol) is used to find the MAC address associated with an IP address on the local network.

If the MAC address is unknown, the sender broadcasts an ARP Request:
```text
"My IP/MAC is 10.1.1.22 / a2:a2. Who has IP address 10.1.1.33?"
```
The device with IP address 10.1.1.33 replies with an ARP Reply using unicast, providing its MAC address.

### ARP cache
ARP cache (Address Resolution Protocol cache) is a temporary table stored on a device that maps IP addresses to MAC addresses on a local network.

## Actul Process
### When both Host connected directly

Host A: Sender, 
Host B: Receiver

- Host A has some application data to send and knows the destination IP address (perhaps obtained through DNS or entered manually).
  
- Host A checks its subnet mask to determine whether Host B is on the same local network.
  
- Once it has determined, it adds layer 3 header containing its source's IP address and destination IP for end to end delivery.
  
- If Host B is on the same subnet, Host A looks for Host B's MAC address in its ARP cache.

If the mapping is missing, Host A broadcasts an ARP Request asking:
"Who has 10.1.1.33?"

- After getting the ARP request, host B unicasts it's Mac address to Host A, and Host A encapsulates the IP packet inside an Ethernet frame by adding a Layer 2 header containing: Source MAC = Host A, Destination MAC = Host B

- The Ethernet frame is transmitted across the network.

Host B receives the frame, removes the Layer 2 header, processes the IP packet, removes the Layer 3 header, and finally delivers the original data to the appropriate application.
  
- The data is sent across the wire. Host B receives it, discards the Layer 2 and Layer 3 headers after they have served their purpose, and delivers the raw data to the intended application.
  
- The IP-to-MAC mapping is stored in the ARP cache for some time, allowing future communication without another ARP Request.
