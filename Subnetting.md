# Subnetting

## What is an IP Address?

An IP address (Internet Protocol Address) is a unique logical address assigned to a device on a network for identification and communication.

### IPv4

IPv4 is a 32-bit addressing system in which an IP address is divided into four 8-bit sections called **octets**, separated by periods.

Each octet ranges from **0 to 255**.

```text
192.168.1.0 (Decimal)
11000000.10101000.00000001.00000000 (Binary)
```

An IP address consists of two parts:

- **Network ID** – Identifies the network.
- **Host ID** – Identifies a device within the network.



## What is Subnetting?

Subnetting is the process of dividing a large IP network into smaller subnetworks (subnets) to improve network performance, security, and efficient IP address utilization.



## Subnet Mask

A subnet mask is a 32-bit number that identifies which part of an IP address represents the **network** and which part represents the **host**.

- **1s** represent the **network portion**.
- **0s** represent the **host portion**.

In **Classful Addressing**, IPv4 addresses are divided into five classes (A, B, C, D, and E) based on the number of bits used for the network and host portions.

### Example (Class C)

```text
11111111.11111111.11111111.00000000
|________________________| |______|
     Network Bits          Host Bits

Network Bits  : 24
Host Bits     : 8

Total Addresses : 256
Reserved        : 2
Usable Hosts    : 254
```

### Default Subnet Masks

```text
Class A : 255.0.0.0
Class B : 255.255.0.0
Class C : 255.255.255.0
```

### Why 255?

255 is the decimal representation of the binary value `11111111`.

```text
11111111
= 128 + 64 + 32 + 16 + 8 + 4 + 2 + 1
= 255
```



## CIDR Notation

CIDR (Classless Inter-Domain Routing) represents the number of bits used for the **network portion** of an IP address.

It is written as **/n**, where **n** is the number of network bits.

### Example 1

```text
11111111.11111111.11111111.00000000
|_________________________|
         24 Bits

CIDR = /24
```

### Example 2

```text
11111111.11111110.00000000.00000000
|______________|
     15 Bits

CIDR = /15
```



## Network ID

The **Network ID** is the first IP address of a network. It uniquely identifies the network itself and **cannot be assigned to any host**.

It is obtained by performing a **Bitwise AND** operation between the IP Address and the Subnet Mask.



## Finding the Network ID (Bitwise AND)

### Example

```text
IP Address : 205.150.65.0
Subnet Mask: 255.255.255.192 (/26)
```

Convert both to binary:

```text
IP Address : 11001101.10010110.01000001.00000000
Subnet Mask: 11111111.11111111.11111111.11000000
             ---------------------------------  (Bitwise AND)
Network ID : 11001101.10010110.01000001.00000000
```

Convert the result back to decimal:

```text
Network ID = 205.150.65.0/26
```


## Number of Subnets & Hosts

### Number of Subnets

```text
Subnets = 2^n
```

where,

**n = Number of host bits borrowed to create subnet bits.**

### Number of Hosts

```text
Hosts = 2^m - 2
```

where,

**m = Number of host bits remaining after subnetting.**

Two addresses are subtracted because they are reserved for:

- **Network ID** (First Address)
- **Broadcast ID** (Last Address)

### Example

Suppose the network is:

```text
192.168.1.0/24
```

The addresses are:

```text
192.168.1.0      ← Network ID
192.168.1.1      ← Host
192.168.1.2      ← Host
...
192.168.1.254    ← Host
192.168.1.255    ← Broadcast ID
```



## Broadcast ID

The **Broadcast ID** (Broadcast Address) is the **last IP address** of a network. It is used to send data to **every device within the same network** and **cannot be assigned to any host**.

The Broadcast ID is obtained by setting **all host bits to 1**.

### Example

```text
Network : 192.168.1.0/24

Host Bits

11111111

Broadcast Address

192.168.1.255
```



## Summary


 **IP Address** | Unique logical address assigned to a device. 
 **Subnet Mask** | Identifies the network and host portions of an IP address. 
 **CIDR** | Represents the number of network bits. 
 **Network ID** | First IP address of a subnet; identifies the network. 
 **Broadcast ID** | Last IP address of a subnet; sends data to all devices in the subnet. 
 **Usable Hosts** | Total addresses − 2 (Network ID and Broadcast ID). 
