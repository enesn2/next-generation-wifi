# Literature research notes  #

## Frameworks to implement wireless communication
### SDR Devices
+ [Universal Software Radio Peripheral](https://www.ettus.com/) - The USRP software defined radio products are designed for RF applications from DC to 6 GHz, including multiple antenna (MIMO) systems. Example application areas include white spaces, mobile phones, public safety, spectrum monitoring, radio networking, cognitive radio, satellite navigation, and amateur radio (from the website). In stock configuration the FPGA performs several DSP operations, which ultimately provide translation from real signals in the analog domain to lower-rate, complex, baseband signals in the digital domain. The FPGA can be modified to perform additional operations. The device drivers work on all platforms and support several frameworks and programming languages. Some models have embedded processors running Linux. Daughterboard modules serve as the RF front end. RFNoC is a software that allows FPGA implementation using GNU Radio. 

+ [bladeRF](https://www.nuand.com/) presumably has similar functionalities at a more affordable price.

### Open-source wireless drivers
+ [ath5k](https://wiki.debian.org/ath5k) is a Linux kernel driver supporting Atheros 802.11a/bg PCI/PCI-E chips.
+ [ath9k](https://wiki.debian.org/ath9k) looks like the newer version of the above.

## Security problems in wireless
### WiFi security
"Advanced Wi-Fi Attacks Using Commodity Hardware" several ways off-the-shelf WiFi dongles can be used to execute low-layer security attacks. This implies that these can be hacked and used in the same ways as USRP, for example. 

The first kind of attack they describe is to modify the client's share of the bandwidth. This can be done by modifying client's contention window, SIFS, transmit power and bitrate. They also describe how TKIP can be decrypted by malicious users. One defense mechanism against this behavior is DOMINO. They also implement several continuous and selective jamming techniques. Man-in-the-middle attack can be done by cloning an AP on a different channel and jamming the original AP until all users switch from it. 

### Authentication and confidentiality
In "Securing Wireless Systems via Lower Layer Enforcements" propose a PHY solution to achieve authentication. Authors in "Physical Layer Authentication over MIMO Fading Wiretap Channels" offer a different perspective. 

### Minstrel

[Minstrel](https://wireless.wiki.kernel.org/en/developers/documentation/mac80211/ratecontrol/minstrel) is a rate control algorithm that uses a heuristic approach to determine the optimal bitrate for highest throughput. Most other algorithms work based on some presumptions.  

## Next generation WLAN
### MAC
In "IEEE 802.11ax: Challenges and Requirements for Future High Efficiency WiFi" authors describe the improvements that will be made in the next generation of the 801.11 standard. To increase spatial reuse changes will be made to how the channel is being sensed and how transmit power is set per user. Some problems that the next generation WiFi will face are its coexistence with LTE and its limitations in supporting IoT applications such as range and power consumption.


## Mesh networks 
An open problem is running tests of these network topologies on Orbit. For example, generating topologies of these networks on Orbit can be made easier (without hardcoding).
### [Batman](https://www.open-mesh.org/projects/open-mesh/wiki/BATMANConcept)
### The Optimized Link State Routing Protocol
The Optimized Link State Routing Protocol ([OLSR](https://www.ietf.org/rfc/rfc3626.txt)) is developed for mobile ad hoc networks. The main feature of this protocol is the existence "multi-point relays" (MPR). This set is selected such that it covers (in terms of radio range) all symmetric strict 2-hop nodes.In OLSR, every node in the network chooses a set of neighboring nodes to be MPRs, which are in charge of distributing control messages. Nodes which have been selected as multipoint relays by some neighbor node(s) announce this information periodically in their control messages.  Thereby a node announces to the network, that it has reachability to the nodes which have selected it as an MPR.  In route calculation, the MPRs are used to form the route from a given node to any destination in the network.  Furthermore, the protocol uses the MPRs to facilitate efficient flooding of control messages in the network. Each node maintains information about the set of neighbors that have selected it as MPR.



TODO: Capture effect in WiFi, see if there is a variable guard interval solution

Test
