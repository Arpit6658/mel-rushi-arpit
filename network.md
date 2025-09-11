# Network Design - SYD Group 03

## 1. Project Assumptions

### 1.1 Location Details
- **Headquarters Location**: Sydney, New South Wales, Australia
- **Primary Branch Office**: Darwin, Northern Territory, Australia  
- **Additional Branch Locations**: Brisbane (QLD), Perth (WA), Adelaide (SA)

### 1.2 Staff Numbers
- **Headquarters (Sydney)**: 65 staff members
  - Administrative staff: 20
  - Project management consultants: 15
  - Senior leadership team: 8
  - ICT staff: 12
  - Marketing team: 5
  - Other support: 5
- **Branch Office (Darwin)**: 20 staff members
  - Electricians: 8
  - Electrical engineers: 4
  - Site supervisors: 3
  - Administrative support: 3
  - Management: 2

### 1.3 Infrastructure Assumptions
- **Building Configuration**: 
  - Headquarters: 3-floor building (Ground, Level 1, Level 2)
  - Branch office: Single-floor office and workshop facility
- **Business Type**: Truelec - electrical contracting business
- **Services**: Residential maintenance, industrial projects, building construction, gas projects, mining developments, telecommunications projects
- **Network Requirements**: Complete wired and wireless coverage with high availability
- **Security Systems**: CCTV monitoring, IoT sensors, RFID access control
- **Connectivity**: High-speed fiber connections with redundant links

## 2. Network Design Philosophy

### 2.1 Design Architecture
Our network implements a **hierarchical design** with three distinct layers:
- **Core Layer**: High-speed backbone providing redundant connectivity
- **Distribution Layer**: Policy enforcement and traffic aggregation
- **Access Layer**: End-user device connectivity with PoE support

The design emphasizes:
- **High Availability**: 99.5% uptime for business-critical operations
- **Scalability**: Easy expansion for new electrical projects and branches
- **Security**: Network segmentation protecting sensitive project data
- **Performance**: High-bandwidth support for CAD/engineering applications

## 3. IP Addressing Scheme

### 3.1 IP Address Requirements
- **First Octet**: 54 (last two digits of student ID 12310854)
- **Network Masks**: Mixed /16 and /24 subnets as specified
- **Address Range**: 54.0.0.0 - 54.255.255.255

### 3.2 IP Address Allocation

#### 3.2.1 Headquarters (Sydney) - 54.10.0.0/16
| Network Segment | IP Range | Subnet Mask | Purpose |
|----------------|----------|-------------|---------|
| **Core Infrastructure** | 54.10.1.0/24 | /24 | Core switches and routers |
| **Management Network** | 54.10.2.0/24 | /24 | Network management devices |
| **Server Network** | 54.10.10.0/24 | /24 | Internal servers (HR, CRM, accounting) |
| **Ground Floor LAN** | 54.10.20.0/24 | /24 | Ground floor workstations |
| **Level 1 LAN** | 54.10.21.0/24 | /24 | Level 1 office devices |
| **Level 2 LAN** | 54.10.22.0/24 | /24 | Level 2 management area |
| **WiFi Corporate** | 54.10.30.0/24 | /24 | Corporate wireless devices |
| **WiFi Guest** | 54.10.31.0/24 | /24 | Guest wireless access |
| **Security Systems** | 54.10.40.0/24 | /24 | CCTV, IoT sensors, RFID |
| **Engineering CAD** | 54.10.50.0/24 | /24 | High-performance CAD workstations |
| **VoIP Network** | 54.10.60.0/24 | /24 | IP phones and communication |
| **WAN Links** | 54.10.100.0/24 | /24 | Inter-site connectivity |

#### 3.2.2 Branch Office (Darwin) - 54.20.0.0/16
| Network Segment | IP Range | Subnet Mask | Purpose |
|----------------|----------|-------------|---------|
| **Branch Core** | 54.20.1.0/24 | /24 | Branch router and core switch |
| **Branch LAN** | 54.20.10.0/24 | /24 | Office workstations |
| **Branch WiFi** | 54.20.20.0/24 | /24 | Wireless devices |
| **Workshop Network** | 54.20.30.0/24 | /24 | Workshop equipment and testing |
| **Branch Servers** | 54.20.40.0/24 | /24 | Local file and application servers |
| **WAN to HQ** | 54.20.100.0/24 | /24 | MPLS link to headquarters |

#### 3.2.3 Additional Branch Offices
- **Brisbane Branch**: 54.21.0.0/16
- **Perth Branch**: 54.22.0.0/16  
- **Adelaide Branch**: 54.23.0.0/16

## 4. Network Architecture Design

### 4.1 Headquarters Network Infrastructure

#### 4.1.1 Core Layer
- **Primary Core Switch**: Cisco Catalyst 9500-48Y4C
  - 48 x 25G SFP28 ports, 4 x 100G QSFP28 ports
  - Redundant power supplies for high availability
  - Advanced Layer 3 routing capabilities
  - Price: $42,000 AUD

- **Secondary Core Switch**: Cisco Catalyst 9500-32QC (Redundancy)
  - 32 x 100G QSFP28 ports for backbone connectivity
  - Stacked configuration with primary core switch
  - Automatic failover capabilities
  - Price: $38,000 AUD

#### 4.1.2 Distribution Layer
- **Distribution Switches (Per Floor)**: Cisco Catalyst 9300-48P
  - 48 x 1G copper ports, 4 x 10G SFP+ uplinks
  - PoE+ support for IP phones and access points
  - Advanced security and QoS features
  - Quantity: 3 (one per floor)
  - Price: $8,500 AUD each

#### 4.1.3 Access Layer
- **Access Switches**: Cisco Catalyst 9200-24P
  - 24 x 1G copper ports, 4 x 10G SFP+ uplinks
  - PoE+ support for end devices
  - Energy-efficient design
  - Quantity: 6 switches
  - Price: $3,200 AUD each

#### 4.1.4 WAN Infrastructure
- **Primary WAN Router**: Cisco ISR 4431
  - Multiple WAN interfaces for ISP connections
  - VPN capabilities for branch connectivity
  - Advanced security features
  - Price: $14,092 AUD (Including GST)

- **Backup WAN Router**: Cisco ISR 4321 (Redundancy)
  - Secondary internet connection management
  - Automatic failover capabilities
  - Load balancing support
  - Price: $8,500 AUD

### 4.2 Branch Office Network Design

#### 4.2.1 Branch Infrastructure
- **Branch Router**: Cisco ISR 4321
  - WAN connectivity to headquarters via MPLS
  - Local internet breakout capability
  - Integrated security features
  - Price: $8,500 AUD

- **Branch Switch**: Cisco Catalyst 9200-48P
  - 48 x 1G copper ports for comprehensive connectivity
  - 4 x 10G SFP+ uplinks to router
  - PoE+ support for wireless APs and IP phones
  - Price: $3,200 AUD

## 5. WiFi Network Design

### 5.1 Enterprise WiFi Architecture
- **Wireless Controller**: Cisco 9800-CL (Cloud-based)
- **Access Points**: Cisco Catalyst 9120AXI (WiFi 6)
- **Coverage Strategy**: Full building coverage with 20% overlap

### 5.2 WiFi Configuration and Settings

#### 5.2.1 Headquarters WiFi Configuration
| Setting | Value | Technical Justification |
|---------|-------|------------------------|
| **Corporate SSID** | Truelec-Corporate | Clear business identification |
| **Guest SSID** | Truelec-Guest | Separate network for visitors |
| **Security Protocol** | WPA3-Enterprise (Corporate), WPA3-Personal (Guest) | Latest security standards |
| **Authentication** | 802.1X with RADIUS (Corporate), PSK (Guest) | Enterprise-grade authentication |
| **Encryption** | AES-256 | Strong data protection |
| **Channel Width** | 80MHz (5GHz), 20MHz (2.4GHz) | Optimal performance balance |
| **Band Selection** | 5GHz preferred, 2.4GHz fallback | Better performance characteristics |
| **Power Settings** | Auto (15-20dBm maximum) | Optimal coverage without interference |
| **Load Balancing** | Enabled (max 50 clients per AP) | Even load distribution |
| **Fast Roaming** | 802.11r enabled | Seamless mobility support |

#### 5.2.2 Access Point Deployment
- **Headquarters**: 15 access points total
  - Ground Floor: 6 APs (reception, meeting rooms, workshop areas)
  - Level 1: 5 APs (offices, project rooms)
  - Level 2: 4 APs (executive areas, server room)
- **Branch Office (Darwin)**: 4 access points
  - Office area: 2 APs
  - Workshop: 2 APs (industrial-grade units)

### 5.3 Guest Network Security
- **Network Isolation**: Complete isolation from corporate resources
- **Bandwidth Limiting**: 10Mbps per user, 100Mbps total
- **Session Management**: 8-hour session limit with re-authentication
- **Content Filtering**: Business-appropriate web filtering
- **Captive Portal**: Terms of service acceptance required

## 6. Hardware Recommendations and Pricing

### 6.1 Core Networking Equipment

#### 6.1.1 Headquarters Equipment
| Device | Model | Specifications | Quantity | Unit Price (AUD) | Total Price (AUD) | Supplier Link |
|--------|--------|----------------|-----------|------------------|-------------------|---------------|
| **Core Switch** | Cisco Catalyst 9500-48Y4C | 48x25G + 4x100G, redundant PSU | 1 | $42,000 | $42,000 | [Secure IT Store](https://www.secureitstore.com.au/C9500-48Y4C.asp) |
| **Backup Core Switch** | Cisco Catalyst 9500-32QC | 32x100G, stacking capability | 1 | $38,000 | $38,000 | [Secure IT Store](https://www.secureitstore.com.au/C9500-32QC.asp) |
| **Distribution Switch** | Cisco Catalyst 9300-48P | 48x1G + 4x10G, PoE+, Layer 3 | 3 | $8,500 | $25,500 | [Device Deal](https://www.devicedeal.com.au/switches/cisco-switches/catalyst-9300/) |
| **Access Switch** | Cisco Catalyst 9200-24P | 24x1G + 4x10G, PoE+ | 6 | $3,200 | $19,200 | [Device Deal](https://www.devicedeal.com.au/switches/cisco-switches/) |
| **WAN Router (Primary)** | Cisco ISR 4431 | Multi-service router, VPN, security | 1 | $14,092 | $14,092 | [Melbourne Global](https://www.melbourneglobal.com.au/cisco-isr4431-k9-cisco-isr-4431-4ge-3nim-8g-flash-4g-dram-ipb/) |
| **WAN Router (Backup)** | Cisco ISR 4321 | Backup router, failover | 1 | $8,500 | $8,500 | [Secure IT Store](https://www.secureitstore.com.au/ISR-4321.asp) |
| **Firewall** | Cisco ASA 5516-X | Next-gen firewall, IPS, VPN | 1 | $6,500 | $6,500 | [Device Deal](https://www.devicedeal.com.au/firewalls/cisco-firewalls/) |
| **Wireless Controller** | Cisco 9800-CL | Cloud controller, 500 AP license | 1 | $4,200 | $4,200 | [Secure IT Store](https://www.secureitstore.com.au/C9800-CL-K9.asp) |
| **WiFi Access Points** | Cisco Catalyst 9120AXI | WiFi 6, 2.5G ethernet, PoE+ | 15 | $850 | $12,750 | [Device Deal](https://www.devicedeal.com.au/wireless/cisco-wireless/) |

**Headquarters Networking Total**: $170,742 AUD

#### 6.1.2 Branch Office Equipment
| Device | Model | Specifications | Quantity | Unit Price (AUD) | Total Price (AUD) | Supplier Link |
|--------|--------|----------------|-----------|------------------|-------------------|---------------|
| **Branch Router** | Cisco ISR 4321 | WAN connectivity, VPN, routing | 1 | $8,500 | $8,500 | [Secure IT Store](https://www.secureitstore.com.au/ISR-4321.asp) |
| **Branch Switch** | Cisco Catalyst 9200-48P | 48x1G + 4x10G, PoE+ | 1 | $3,200 | $3,200 | [Device Deal](https://www.devicedeal.com.au/switches/cisco-switches/) |
| **Branch Firewall** | Cisco ASA 5508-X | Small office firewall, VPN | 1 | $3,800 | $3,800 | [Device Deal](https://www.devicedeal.com.au/firewalls/cisco-firewalls/) |
| **WiFi Access Points** | Cisco Catalyst 9120AXI | WiFi 6, centrally managed | 4 | $850 | $3,400 | [Device Deal](https://www.devicedeal.com.au/wireless/cisco-wireless/) |

**Branch Office Networking Total**: $18,900 AUD

### 6.2 Server Infrastructure

#### 6.2.1 Headquarters Servers
| Server Type | Model | Specifications | Quantity | Unit Price (AUD) | Total Price (AUD) | Supplier Link |
|-------------|--------|----------------|-----------|------------------|-------------------|---------------|
| **Application Servers** | Dell PowerEdge R650 | 2x Xeon Silver 4314, 64GB RAM, 2TB SSD | 3 | $8,500 | $25,500 | [Dell Australia](https://www.dell.com/en-au/shop/servers-storage-and-networking/poweredge-r650-rack-server/spd/poweredge-r650) |
| **Domain Controllers** | Dell PowerEdge R350 | Xeon E-2378G, 32GB RAM, 1TB SSD | 2 | $5,200 | $10,400 | [Dell Australia](https://www.dell.com/en-au/shop/servers-storage-and-networking/poweredge-r350-rack-server/spd/poweredge-r350) |
| **File Server** | Dell PowerEdge R750 | 2x Xeon Silver 4314, 128GB RAM, 20TB HDD | 1 | $12,000 | $12,000 | [Dell Australia](https://www.dell.com/en-au/shop/servers-storage-and-networking/poweredge-r750-rack-server/spd/poweredge-r750) |
| **Backup Server** | Dell PowerEdge R350 | Xeon E-2378G, 64GB RAM, 10TB HDD | 1 | $7,500 | $7,500 | [Dell Australia](https://www.dell.com/en-au/shop/servers-storage-and-networking/poweredge-r350-rack-server/spd/poweredge-r350) |

**Server Infrastructure Total**: $55,400 AUD

#### 6.2.2 Branch Office Server
| Server Type | Model | Specifications | Quantity | Unit Price (AUD) | Total Price (AUD) | Supplier Link |
|-------------|--------|----------------|-----------|------------------|-------------------|---------------|
| **Local Server** | Dell PowerEdge R350 | Xeon E-2378G, 32GB RAM, 2TB SSD | 1 | $5,200 | $5,200 | [Dell Australia](https://www.dell.com/en-au/shop/servers-storage-and-networking/poweredge-r350-rack-server/spd/poweredge-r350) |

### 6.3 Infrastructure Equipment

#### 6.3.1 Power and Environmental
| Equipment | Model | Specifications | Quantity | Unit Price (AUD) | Total Price (AUD) | Supplier Link |
|-----------|--------|----------------|-----------|------------------|-------------------|---------------|
| **UPS Systems** | APC Smart-UPS SRT 5000VA | 5kVA, online double conversion | 2 | $4,500 | $9,000 | [APC Australia](https://www.apc.com/shop/au/en/products/APC-Smart-UPS-SRT-5000VA-230V/P-SRT5KXLI) |
| **Server Racks** | APC NetShelter SX 42U | 42U with cable management | 2 | $1,800 | $3,600 | [APC Australia](https://www.apc.com/shop/au/en/products/NetShelter-SX-42U-600mm-Wide-x-1070mm-Deep-