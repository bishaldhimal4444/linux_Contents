### TCP/IP Network Model vs. OSI Model:
TCP/IP
- 4 layers (Application, Transport, Internet and Link)
OSI Model:
- 7 layers (Application, Presentation, Session, Transport, Network, DataLink and Physical)

### IPv4 vs. IPv6:
IPv4 - 32 bits
IPv6 - 128 bits

## Validate Networking 
s1: Gather Network Interface Information: ``` ip link show ```
s2: Display IP Address: ``` ip addr show ens3 ```
s3: Display Performance Statistics: ``` ip -s link show ens3 ```
s4: Verify Connectivity between Hosts: ``` pig -c3 ip_addr ```
s5: 
