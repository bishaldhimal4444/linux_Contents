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
s5: Describe the Routing Table: ``` ip route ```  
s6: Trace Traffic Routes: ``` tracepath access.redhat.com ```  
s7: Troubleshoot port and service issues: ``` ss -ta ```  
where,   
  -t = show tcp sockets  
  -a = show all sockets  
  -n = show number instead of names for interfaces and ports
  -u = show udp sockets
  -l = show only listening sockets  
  -p = show the processes that uses the sockets  


## Configure Networking from the Command line: 
Network Manager Service:  
- monitors and manages a system's network settings.

Useful Network Manager Commands:  
- To show the network manager status of all network interfaces.
  ```
  nmcli dev status
  ```  
- to list all connections.
  ```
  nmcli con show
  ```
- to list the current settings for the connectiion name.
  ```
  nmcli con show name
  ```
- to add ad name a new connection profile.
  ```
  nmcil con add con_name
  ```
- to modify the connection name.
  ```
  nmcli con mod name
  ```
- to reload the configuration files, after manual file editing.
  ```
  nmcli con reload
  ```
- to activate the connection name.
  ```
  nmcli con up name
  ```
- to disconnect the interface, which also deactivates the current connection.
  ```
  nmcli dev dis dev
  ```
- to deletre the specified connection and its configuration file.
  ```
  nmcli con del name
  ```
