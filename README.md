# Secure System Configuration - Device hardening and firewall management

The network shown in the figure below is managed by 3 administrators, identified by their passcode c7531, c1247, and a1616. To improve the security of the network infrastructure, they decided to define the following zones: 
- ESTERNO zone, the public Internet network
- OSPITI zone, to provide connectivity to temporary guest visitors
- CLIENTI zone, a dedicated network to provide housing services to external customers
- INTERNO zone, the corporate network and its IT services

![Network Schema](https://github.com/ClaudioFio/Secure-System-Configuration_Device-hardening-and-firewall-management/blob/main/img/Network_schema.jpg)

Following the address table:

| Device     | Interface | IP address   |Subnet mask   |Default gateway   |
| :---:        |    :----:   |          :---: |          :---: |          :---: |
| FW-WAN      | GE 0/1       | 10.10.0.1   |255.255.255.0   |   |
| FW-WAN      | Serial 0/0/0       | 100.100.100.102   |255.255.255.252   | 100.100.100.101  |
| FW-WAN      | Serial 0/1/0       | 10.38.0.1  |255.255.255.252   |   |
| FW-WAN      | Serial 0/1/1       | 10.127.0.1   |255.255.255.252   |   |
| R-OSPITI      | GE 0/0       | 146.48.38.1   |255.255.255.0   |   |
| R-OSPITI       | Serial 0/0/0       | 10.38.0.2   |255.255.255.252   | 10.38.0.1  |
| R-SERVIZI      | GE 0/0       | 10.10.0.58  |255.255.255.0   |   |
| R-SERVIZI       | GE 0/1     | 146.48.58.1   |255.255.255.0   |   |
| R-UTENTI      | GE 0/0       | 10.10.0.96  |255.255.255.0   |   |
| R-UTENTI       | GE 0/1     | 146.48.96.1   |255.255.255.0   |   |
| R-CLIENTI      | GE 0/0       | 146.48.127.1  |255.255.255.0   |   |
| R-CLIENTI       | Serial 0/0/0     | 10.127.0.2   |255.255.255.0   | 10.127.0.1  |
| PC0      | FE 0       | 146.48.96.15  |255.255.255.0   | 146.48.96.1  |
| PC1      | FE 0   | 146.48.38.10   |255.255.255.0   | 146.48.38.1  |
| Server WWW      | FE 0       | 146.48.58.20  |255.255.255.0   | 146.48.58.1  |
| Server WWW2      | FE 0   | 146.48.58.28   |255.255.255.0   | 146.48.58.1  |
| Server FTP      | FE 0       | 146.48.58.21  |255.255.255.0   | 146.48.58.1  |
| Server RADIUS      | FE 0       | 146.48.58.230  |255.255.255.0   | 146.48.58.1  |
| Server C-WWW      | FE 0       | 146.48.127.80  |255.255.255.0   | 146.48.127.1  |

# Specification

Given the initial configuration "Network_initial.pkt" you want to configure the network such that.
1. Allow administrators remote SSH access to the R-OSPITI and R-CLIENTI routers from their workstations that are connected to the Users network, using personal credentials stored on the RADIUS server
2. From the INTERNO zone, it is possible to reach all services on the Internet network, while it is denied connection to computers connected to the OSPITI network. The INTERNO zone is protected in completely from access from the outside world, whether it is the network public network, the OSPITI network and the CLIENTI network.
3. Only WWW and WWW2 servers (both http and https) as well as the web services of the CLIENTI network 
4. From the OSPITI network, web browsing to any Internet site is allowed and web browsing web to WWW and WWW2 servers in addition to any web server available on the CLIENTI network.
5. The contents of the C-WWW server can be updated by uploading, to the same server, the files via FTP. Connection to the FTP service is allowed only from the UTENTI network.
6. From the INTERNO zone you want to monitor the availability of any host connected to the network CLIENTI via the Ping tool. From the Internet and the OSPITI network, for security reasons, it is not possible to check the operation of a host via Ping.

# Results

It is possible to view the network configured according to the previous specifications in the "Network_solution.pkt" file.
The steps to be taken to configure the network are shown in the file "Step-by-Step_Solution.txt"
