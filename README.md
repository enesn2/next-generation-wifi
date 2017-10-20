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


## Mesh networks 
An open problem is running tests of these network topologies on Orbit. For example, generating topologies of these networks on Orbit can be made easier (without hardcoding).
### [Batman](https://www.open-mesh.org/projects/open-mesh/wiki/BATMANConcept)
### The Optimized Link State Routing Protocol
The Optimized Link State Routing Protocol ([OLSR](https://www.ietf.org/rfc/rfc3626.txt)) is developed for mobile ad hoc networks. The main feature of this protocol is the existence "multi-point relays" (MPR). This set is selected such that it covers (in terms of radio range) all symmetric strict 2-hop nodes.In OLSR, every node in the network chooses a set of neighboring nodes to be MPRs, which are in charge of distributing control messages. Nodes which have been selected as multipoint relays by some neighbor node(s) announce this information periodically in their control messages.  Thereby a node announces to the network, that it has reachability to the nodes which have selected it as an MPR.  In route calculation, the MPRs are used to form the route from a given node to any destination in the network.  Furthermore, the protocol uses the MPRs to facilitate efficient flooding of control messages in the network. Each node maintains information about the set of neighbors that have selected it as MPR.

## Next generation WLAN
### MAC
In "IEEE 802.11ax: Challenges and Requirements for Future High Efficiency WiFi" authors describe the improvements that will be made in the next generation of the 801.11 standard. To increase spatial reuse changes will be made to how the channel is being sensed and how transmit power is set per user. Some problems that the next generation WiFi will face are its coexistence with LTE and its limitations in supporting IoT applications such as range and power consumption.

## Ultra-Wideband Radio Technology:
Potential and Challenges Ahead
With appropriate technical standards, UWB
devices can operate using spectrum occupied by
existing radio services without causing interference,
thereby permitting scarce spectrum
resources to be used more efficiently.

## Minimising the effect of WiFi interference in 802.15.4 wireless sensor networks
802.15.4 wireless is ZigBee. The paper proposes to use RSSI to estimate interference from competing networks and the choose the best channel to setup the network. The ZigBe communication is improved by picking the channels not affected by ongoing
WiFi transmissions. 

## 5G Multi-RAT LTE-WiFi Ultra-Dense Small Cells

The authors analyze the possibility of integrated multi radio access technology. While many of today’s pico cells are still installed by the mobile network operators in a (semi-) planned manner, the deployment of femto cells remains mostly unplanned.Therefore, ultradense networks are becoming a reality. "Therefore, any UE that wishes to use a non-3GPP
(alien) RAT together with cellular access must route its traffic
to the operator’s PDN GW, from where the packets will be
forwarded to the destination following the logic of mobile IP.
Since mobile IP traffic is blocked by most network address
translation (NAT) devices, which are abundant in today’s IPv4
infrastructure, the mobile IP session needs to be tunneled to
the PDN GW through a VPN tunnel." 



TODO: Capture effect in WiFi, see if there is a variable guard interval solution


## Increasing Indoor Wireless Capacity Using Directional Antennas

The author of this paper proposes a new way to increase bandwidth of indoor wifi networks using directional antenna. Traditionally directional antenna's are used outdoors where the "Line of sight" is clear between reciever and transmitter. This paper explores an algorithm named DIRC to utilize directional antenna's in indoor environment to increase bandwidth.

Problems with indoor directional antennas:
-Determining direction of antenna
-Determining which antennas can transmit concurrently.

For first problem: determining direction of antenna DIRC parts itself from max SNR approach. Max SNR is basically finding which orientation provides maximum Signal to noise ratio. Max SNR can be effective in outdoor environments however indoors if two recievers are close to each and recieve signals from two different antenna's based on their SNR a large interferance will occur. To tackle this problem DIRC exploits reflected paths to minimize interferance. 

To determine which antennas can transmit concurrently DIRC utilizes a conflict graph where it uses a brute force algorithm to compare different paths for different nodes and how interferance occur between them.

The DIRC algorithm uses this conflict graph and schedule requests accordingly.

More about DIRC here: http://delivery.acm.org/10.1145/1600000/1592589/p171-liu.pdf?ip=91.230.41.205&id=1592589&acc=PUBLIC&key=36E5A5D4E382B3FA%2E36E5A5D4E382B3FA%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35&CFID=991547228&CFTOKEN=20628814&__acm__=1507042339_67b3d63f3b7e6b7acf38124fa1c88204

## Adjacent Channel Interference in 802.11a Is Harmful: Testbed Validation of a Simple Quantification Model

Even though 802.11a OFDM there still exists interference between adjacent channels. This paper may be useful because it describes how to setup an experiment in WiFi involving sensitive readings. 
