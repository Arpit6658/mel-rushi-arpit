
Network Design
Assumptions

Figure 1: WAN connection for all sites
The diagram is a hub-and-spoke type of network with HQ as a central hub and the branches being linked via the VPN/MPLS to the ISP cloud (Mazhar et al. 2023). This architecture provides single point administration, scaling and secure connectivity. A single instance of HQ WAN connection is thus susceptible such that it must be redundant and ideally traffic-path routing is required to remain solid.

Figure 2: Security Architecture
The architecture is a layered security which includes firewalls, VPNs, IDS/IPS, segmentation and endpoint protection. Integrated SIEM and SOC have centralized monitoring and response (Pawlicki et al. 2022). This defense-in-depth approach promotes resilience by guaranteeing protection of traffic, applications and devices. It is however very efficient and should be updated regularly, staffed with experts and the complexity of configuration minimized.
Design Philosophy
The network design adheres to the hierarchical architecture, which includes Core, Distribution, and Access layers to provide good structuring of connectivity and easy management. The Core layer is used to provide high-speed backbone services, the Distribution layer carries out policies and routing, and the Access layer provides end-user access(Pawlicki et al. 2022). Such a layered approach is more scaling and less complicated to trouble shoot. Redundant links, backup devices and failover mechanisms ensure high availability and reduce the downtime in order to achieve business continuity. Scalability helps in the expansion in the future as the company expands. VLANs and firewalls provide security segmentation to isolate sensitive systems to minimize the attack surfaces and prevent the access of corporate data by unauthorized parties.
IP Addressing Scheme
Location & Segment
IP Range
Subnet Mask
Purpose
Melbourne HQ – Core
54.10.0.0/16
255.255.0.0
Core backbone and inter-VLAN routing
Melbourne HQ – Servers
54.20.10.0/24
255.255.255.0
Application, database, file servers
Melbourne HQ – Staff LAN
54.20.20.0/24
255.255.255.0
Office desktops, laptops, printers
Melbourne HQ – WiFi Corp
54.20.30.0/24
255.255.255.0


Secure corporate wireless network
Melbourne HQ – WiFi Guest
31.10.40.0/24
255.255.255.0


Guest wireless with internet-only
Darwin Branch – Staff LAN
31.20.50.0/24
255.255.255.0


Branch office desktops and devices
Darwin Branch – Servers
31.20.60.0/24
255.255.255.0


Local file/print and backup servers
WAN Links (HQ–Branch)
54.30.0.0/30
255.255.255.252
Point-to-point WAN connections
Management VLAN (All)
54.40.70.0/24
255.255.255.0


Switches, routers, APs management
CCTV & IoT Devices
31.50.80.0/24
255.255.255.0


Surveillance cameras and IoT sensors

Table 1: IP Addressing Scheme
WiFi Design
The wireless network should be built in such a way that it offers secure, reliable and high performance to the staff and guests. There are two SSIDs deployed: a Corporate WiFi based on WPA3 Enterprise with RADIUS authentication of staff equipment, and a Guest WiFi with no access to internal resources and to the internet(Mazhar et al. 2023). The access points are well distributed to provide uninterrupted coverage, load balancing and roaming within office locations. VLAN will isolate the traffic of guests and corporate and reduce security threats. Band steering makes devices steer to 5GHz with greater throughput and still be compatible with 2.4GHz. The controller-based management allows for monitoring, updating, and detecting intrusions, which guarantee stability in security and performance.

Figure 3:  Wifi Design
Hardware Recommendations
Category
Recommended Device
Quantity
Purpose
Approx. Cost
Core Switch
Cisco Catalyst 9500-24Q
1
High-performance backbone switching
$18,000
Distribution Switches
Cisco Catalyst 9300-24T
2
Policy enforcement and VLAN routing
$9,000 each
Access Switches
Cisco Catalyst 9200-24P
6
End-user connectivity with PoE support
$4,500 each
Routers (HQ & Branch)
Cisco ISR 4331
2
WAN connectivity and routing
$3,800 each
Firewalls
Fortinet FortiGate 100F
2
Next-gen firewall for HQ and branch
$6,000 each
HQ Servers
Dell PowerEdge R740 (2×Xeon, 64GB RAM)
2
Application, database, virtualization
$12,500 each
Branch Server
Dell PowerEdge R540 (1×Xeon, 32GB RAM)
1
File/print services and local backup
$7,500

Table 2: Hardware Recommendations
Estimated Total (Approx.): $90,000 AUD
