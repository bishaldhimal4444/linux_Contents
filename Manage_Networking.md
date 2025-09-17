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
### Validate Networking Configuration:
1. validating the network configuration in RHEL ensures that the network settings are correct and functional.
2. follow these step-by-step instructions:
   - s1: verify network service status:
       ```
       sudo systemctl status network

       sudo systemctl start network
       sudo systemctl enable network
       ```
   - s2: validate network interfaces:
       ```
       nmcli dev status

       nmcli con show <interface_name>
       ```
   - s3: check ip address assignment:
       ```
       ip addr
       ip -br addr
       ```
   - s4: test connectivity:
       ```
       ping -c 4 127.0.0.1

       ip route
       ping -c 4 <gateway_ip>

       ping -c 4 8.8.8.8

       nslookup google.com
       dig google.com
       ```
   - s5: validate routing:
       ```
       ip route show
       ```
   - s6: validate configuration files:
       ```
       sudo cat /etc/NetworkManager/system_connections/
       ```
   - s7: monitor network logs:
       ```
       journalct -xe | grep network

       dmesg | grep eth
       ```

### Configure Networking from the Command line:
Service configuration files are stored in the **/etc/NetworkManager/system_connections directory.
- s1: identify network interface
- s2: configure network interface with "nmcli"
- s3: configure network interface using "ifconfig"
- s4: configure network by editing configuring files
- s5: verify the configuration
 
### Edit Network Configuration File
- s1: identify the network interface
    ```
    nmcli dev status
    ```
- s2: navigate to the configuration files
    ```
    cd /etc/sysconfig/network_scripts/
    ```
- s3: locate the configuration file (ifcfg-<interface_name>)
    
- s4: backup the configuration file
    ```
    cp ifcfg-<interface_name> ifcfg-<interface_name>.bak
    ```
- s5: edit the configuration file
    ```
    sudo vim ifcfg-<interface_name>
    ```
    (Modify the parameters as needed.)  
  TYPE=Ethernet  
  BOOTPROTO=dhcp  
  ONBOOT=yes  
  IPADDR=192.168.1.100 #static_IP  
  NETMASK=255.255.255.0 #subnet mask  
  GATEWAY=192.168.1.1 #default gateway  
  DNS1=8.8.8.8 #primary dns  
  DNS2=8.8.4.4 #secondary dns  
