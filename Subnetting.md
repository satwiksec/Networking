# Subnetting

### What is IP Address
An IP address is an identifier on a network. IPv4 is a 32-bit system, separated by periods. Each section is called an *octet*.
The number range for each octet is 0-255.

```text
192.168.1.0 (decimal format)
11000000.10101000.00000001.00000000 (binary format)
```

An IP address has two parts:
- Network Address: ID assigned to the network
- Host address: ID assigned to the host in the network.

  
  The network address bits are denoted by 1s and the host bits by 0s.
  Based on how many bits are occupied by the network and host address, there are five classes- A, B, C, D, E.
  
  eg:
  ```text
  11111111.11111111.11111111.00000000       (Class A)
  |________________________| |______|
        Network bits         Host Bits
  ```
  
## What is a Subnet?


## Subnet Mask

A subnet mask reveals how many bits in the IP address are used for the network by masking the network portion of the IP address.
