<p align="center">*This project has been created as part of the 42 curriculum by cwenhaj.*</p>

# <h1 align="center">*NetPractice*</h1>

### Description

**NetPractice** is a practical introduction to computer networking fundamentals.
The goal of this project is **to understand how networks function by configuring small-scale network environments**.

Through a series of 10 exercises, it's about to:

- Configure IP addresses
- Understand subnet masks
- Set up default gateways
- Connect devices through routers and switches
- Troubleshoot non-functioning networks

Each level presents a broken network configuration that must be fixed in order to meet specific connectivity objectives.

### Instructions

To run the project, one should:

- Download the project files provided from the NetPractice intra page.
- Extract the archive into a folder of your choice.
- Open a terminal and navigate to the extracted folder.

Then do the following command:

**./run.sh**

This will start a local web server and open the training interface in your browser.

To use the interface, the school login is entered to load the personal configuration or one can use the "evaluation" tab to generate a random configuration

For each level:

- Network is fixed by adjusting the configuration
- To validate the solution, click [Check again] 
- To export your configuration file, click [Get my config] 

Once a level is completed, proceed to the next one.

Submission

- 10 levels must be completed
- The configuration for each level is exported using [Get my config]
- The 10 configuration files are placed at the root of the Git repository

### Resources

**Networking Concepts Covered**

- **TCP/IP addressing**
- **IP addresses (IPv4)**
- **Subnet mask**: used to divide an IP address into two parts. One part identifies the host (computer), the other part identifies the network to which it belongs
- **Default gateways**
- **Routers and switches**
OSI model (basic understanding)
- **Network troubleshooting**

**Learning Resources**

- [TCP/IP fundamentals and addressing](https://learn.microsoft.com/en-us/troubleshoot/windows-client/networking/tcpip-addressing-and-subnetting) 
- [Intro to IP Adresses and Subnets](https://www.youtube.com/watch?v=HQUw0CfQWAM&t=1097s)
- [Subnetting tutorials for Beginners](https://www.youtube.com/watch?v=FM169QUIQco)
- [Networking basics documentation](https://www.geeksforgeeks.org/computer-networks/basics-computer-networking/)
- [Practical Resource Subnet IPv4](https://subnetipv4.com/)
- [IP Address and Subnet Mask](https://www.youtube.com/watch?v=dCWDq2Ty00g)

<u>**AI**</u> tools were used to:

- Clarify networking concepts (TCP/IP, subnetting, routing)
- Assist in understanding exercise requirements

<u>**Notes**</u>
Each level is independent and increases in difficulty
Understanding subnetting is key to completing the project
Take time to analyze each network diagram before making changes

# TCP/IP

- **TCP (Transmission Control Protocol)** is a communication protocol to ensure data is sent and received accurately between devices

- **LAN (Local Area Network)**: Network of devices talking to each other in a located area

- **IP (Internet Protocol)**: An address of a device in a network. Allows for identification and location 
of a machine/device on LAN. Help devices talk to each other, each has a unique IP address (IPv4 ou IPv6)
There are always two IP addresses reserved in a network:
1- Network Address (First IP of the network). Example: 192.168.1.0
2- Bradcast Address (Last IP of the network). 192.168.1.255
so Usable IP range: 192.168.1.1 - 192.168.1. 254

# SUBNET (1 network)

It's a sub network of a larger network. It defines a range of IP addresses of a network and identifies whether a host belongs to a network.
The network address with CIDR notation of a subnet mask 
- e.g. 192.163.1.0 /24
A subnet mask indicates which part of an IP is fixed (network) and variable (host). 
- e.g. /24 or 255.255.255.0
The CIDR notation count the network bits

# SUBNETTING (More than 1 network)
We do subnetting when we want to create more networks taking a network and dividing it into sub-networks
- Step 1: Convert the subnet mask to binary (refer to the 2^position chart)
- Step 2: Find the CIDR notation (Total of network bits)
- Step 3: Find the increment (the last network bit)
- Step 4: Create the networks and find the ranges for each (include the network and bradcast addresses which are always reserved)

**7 Attributes of Subnetting**
  - Network ID :    First IP address in each sub-network
  - Broadcast IP:   Last IP address in each sub-network
  - First Host IP:  IP address after the Network ID
  - Last Host IP:   IP address before the Broadcast IP
  - Next Network:   IP address after the Broadcast IP
  - IP Addresses:   Number of IP addresses in each sub-network or group size
  - CIDR / Subnet : Converting between CIDR / Subnet Mask. Size of a particular subnet or the number of IP addresses in each subnet

  a- Start with 1, double until you reach 128  (right to left)
  b- Substract top row from 256
  c- From /32, list CIDR notation   (right to left)

  Cheat Sheet

  128   64    32   |  16   |  8     4      2     1        Group Size
  128   192   224  |  240  |  248   252    254   255      Subnet Mask
  /25   /26   /27  |  /28  |  /29   /30    /31   /32      CIDR

  - 1- Use given CIDR/mask to find column on cheat Sheet
    - a- CIDR?Subnet Mask map to each other
    - b- Locate group size
    - c- Start at ".0" in relevant octet
    - d- increase by Group Size until you PASS target IP
  - 2- Number BEFORE target IP is NETWORK ID
  - 3- Number AFTER target IP if the Next Network
  - 4- IP address BEFORE Next Network is Boadcast
  - 5- IP address AFTER Network ID is First Host
  - 6- IP address BEFORE Broacast IP is Last Host
  - 7- Group Size is total # of IP addresses
    - Don't forget to substract 2 if needed

Tips:
- 1- The Group Size can be multipled by 10 then doubled or tripled if necessary
- 2- Every Group Size at some point lands on 128 
- 3- Every group size lands on a Subnet value of the same column to the LEFT
- 4- Start higher  then substract

# SWITCH

A physical device inside a LAN that connects multiple devices and allows simultaneous communication. It can be connected to a router

# ROUTER

A physical, networking device. Operates between the LAN and WAN connecting the LAN to the WAN (Wider Area Network). Can have multiple IP addresses for different networks and forward data packets between the multiple networks

# GATEWAY

The same as the router, though functions differently
- Router: sends packets between different networks based on IP addresses
- Gateway: serves as a "gate" between two networks allowing them to communicate
- Has a single IP address (point-to-point link)

# Subnetting Cheat Sheet (IPv4)

## 1. Basic Concepts

* **IP Address**: Identifies a device (e.g. `192.168.1.10`)
* **Subnet Mask**: Defines network vs host part (e.g. `255.255.255.0`)
* **Network Address**: First address of subnet (not usable)
* **Broadcast Address**: Last address (not usable)
* **Usable IPs**: All addresses between network and broadcast

## 2. Common Subnet Masks

| CIDR | Subnet Mask     | Usable Hosts | Block Size |
| ---- | --------------- | ------------ | ---------- |
| /24  | 255.255.255.0   | 254          |   256      |
| /25  | 255.255.255.128 | 126          |   128      |
| /26  | 255.255.255.192 | 62           |   64       |
| /27  | 255.255.255.224 | 30           |   32       |
| /28  | 255.255.255.240 | 14           |   16       |
| /29  | 255.255.255.248 | 6            |   8        |
| /30  | 255.255.255.252 | 2            |   4        |

**Formula:**
`Usable hosts = 2^(host bits) - 2`

## 3. Block Size

**Formula:**
`Block size = 256 - last octet of subnet mask`

## 4. How to Find a Subnet

**Example:**
IP = `192.168.1.70`
Mask = `/26` (`255.255.255.192`)

1. Block size = `256 - 192 = 64`
2. Subnets:

   * 0–63
   * 64–127
   * 128–191
   * 192–255
3. `70` is in `64–127`

**Results:**

* Network: `192.168.1.64`
* Broadcast: `192.168.1.127`
* Usable range: `192.168.1.65 → 192.168.1.126`

## 5. Default Gateway

* Must be in the **same subnet**
* Usually:

  * First usable IP (`.1`)
  * Or last usable IP

**Example:**

* Network: `192.168.1.0/24`
* Gateway: `192.168.1.1`

## 6. Same Network Check

Devices communicate directly only if:

* Same **network**
* Same **subnet mask**

**Example:**

| Device | IP           | Mask          |
| ------ | ------------ | ------------- |
| A      | 192.168.1.10 | 255.255.255.0 |
| B      | 192.168.1.20 | 255.255.255.0 |

Same network → OK

## 7. Common Mistakes

* Gateway not in same subnet
* Using network or broadcast as host
* Wrong subnet mask
* Overlapping subnets
* Missing router between networks

## 8. Quick Mental Tricks

* `/24` → same first 3 octets
* `/25` → split into 2 (0–127 / 128–255)
* `/26` → split into 4 (64 blocks)
* `/27` → split into 8 (32 blocks)

## 9. Example (NetPractice Style)

**Problem:**

* PC1: `10.0.0.2/24`
* PC2: `10.0.1.3/24`

Different networks → cannot communicate

**Solution:**

* Put both in same subnet
* **or**
* Add a router with correct gateways

## Tips for NetPractice

* Always identify the subnet first
* Verify gateway validity
* Check masks carefully
* Avoid random changes
* Think step-by-step
