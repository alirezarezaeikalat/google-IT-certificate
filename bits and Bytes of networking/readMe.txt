1. In this course we define 5 layers TCP/IP network model.

2.    #       Layer name        Protocol        Protocol data unit      Addressing
      
      5       Application       HTTP, SMTP      Messages                  n/a
                                etc...

      4       Transport         TCP/UDP         Segment                   Port #'s
                        (User Datagram protocol)
      3       Network           IP              Datagram                IP addresses

      2       Data link         Ethernet, Wifi   Frames                 MAC addresses

      1       Physical          10 Base T,
                                802.11            Btis                    n/a

3.  a) Physical layer:

      Represent the physical devices that interconnects computers.
      This includes the --specifications for the networking cables-- and the --connectors that join devices-- along with the 
      --specifications that desribing how signals are sent over these connections--.

4.  b) data link layer (network interface or network access layer):
      
      at this layer we introduce our first protocols.
      This layer is responsible for --defining a common way to interpreting these signals--, so network devices can communicate.

      There are lots of protocols at this layer, but the most common one is --Ethernet--, beyod --specifing physical layer attributes--
      The Ethernet standards also define a protocol --responsible for getting data to nodes on the same network-- or link.

5.  c) Network layer (internet):
      
      Allow --different networks-- to communicate with each other through devices knows as --routers--.

      A collection of networks connected together through routers is an --internetwork--, the most famous one is --Internet--

      The most common protocol used at this layer is known as IP or internet protocol.

      --Network softwares-- usually divided into client and server categories, a single node may running multiple client or 
      server applications. you may run web browser and email applications(both client softwares) on the same node, and these client 
      softwares initiate the requests, to servers, but your email will be in your email program, and your web in your web browser, 
      this is because of the next layer, Transport layer.

6.  d) Transport layer: 
      
      Sorts out which client and server programs are supposed to get that data.

7.  e) Application layer:

      There are lot of protocols at this layer, and these protocols are applications specific.

8. In addition to TCP / IP 5 layer model, we have another well known model Open System Interconnection (OSI) model.


9. Cables connect different devices to each other and allowing data to be transmitted over them.

10. There are two common cables type now days:

      a. Copper cables: The most common form of copper twisted-pair cables used in networking are Cat5, Cat5e, and Cat6 cables.

            The difference between these how twisted-pairs are arranged inside these cables, can change how --fast data-- can be
            sent across them, and how --resistent-- these signals are to outside interference.

            Cat5e cables mostly replaced, Cat5 cables, because their internals reduce --crosstalk--. 
      
      b. Fiber optic cables: Contains optical fibers. use pulses of lights to represent ones and zeros.

11. Hubs and switches: The primary devices used to connect devices on a single network, usually called --LAN (local area network)--

      a. --Hub--: a --pysical layer-- device that allows for connection from many computers at once. All the devices connected to the 
            hub will end up talking to other devices at the same time. It's up to each system connected to the hub, determine if the 
            incoming data is meant for them, or ignore it.

            [ATTENTION]
            This creates a lot of noise in the network and cause creation of --collision domain--.

            -- collision domain--: A network segment where only one device can communicate at the time. because the cables are busy :)


      b. --switches--: switch is a --data link layer device--. This means that switch can --inspect the content of the ethernet
            protocol data-- and determine which system the data is intended for and then --only-- send the data to that device. 

12. Routers: is a --network layer device-- that knows how to send data between independent networks. routers --can inspect IP
      protocol data-- and determine where to send the data.

      [ATTENTION]
      routers store internal tables containing information about how to route traffic between lots of networks all around the world.
      usually home of office routers don't have very detailed routing tables. The purpose of these routers is to send traffic from
      inside of the network to the ISP router.

      --Core routers-- at ISPs have much more detailed routing tables, have to deal with much more traffic, and make decision about
            where to send traffic.
      
      --BGP (Border Gateway Protocol)--: Router share data between each other via this protocol, which lets them learn about the most
      optimal path to forward traffic.

----------------- Physical layer --------------

13. We sends ones and zeros through cables with --modulation--. modulation is a way of varying of the voltage of cable charge 
      moving across cables. for computer network, this called --line coding--.


14. Standard Cat6 cable has eight wire, consist of 4 pairs, how many pair that is used, depends on the --transmission technology--
      being used.

15. These cables allow for --Duplex communication-- (information can flow in both directions) (simplex communication)

16. The most common plugs in cables is --RJ45--, RJ45 plugs can be connected to RJ45 ports, most port has two LED light:
      
      a. link LED: cable properly connected to the two devices that are powered on.

      b. Activity LED: shows that data is sending through the cable between two devices.

17. --Patch panels-- are devices that has many ports.

------------ Data Link Layer -----------

18. In the past, switches hadn't been invented yet. This mean that frequently many or all devices on the network share the single 
      --collision domain-- (A segment of network where only one device can communicate at the time). This is because all data in the 
      collision domain is sent to all nodes connected to it. If two computers were to send data accross --the wire-- at the same time 
      it would result in the collision of the electrical currents representing our ones or zeros.

[ATTENTION]
we have two problem:
      a. collision of the data that is sent at the same time from different devices.
            (solved by CSMA/CD)

      b. sending data in the network to all devices.
            (solved by MAC addresses)

19. Ethernet as a protocol --solve this problem-- by using a technique known as --carrier sense multiple access with collision detection--
      --CSMA/CD--

      --CSMA/CD--: Used to determine when the communications channels are clear, and when a device is free to transmit data. 

20. The way CSMA/CD is works is simple. If there is no data transmitted on the segment, a node will feel free to send data, 
      If --two or more computers trying to send data at the same time--, the computers detect this collision and --stop sending data--.
      --Each device involved with collision then waits for --random interval of time--, before to try send data again.

21. In a collision domain all devices getting all the data, to solve this problem, --MAC address(Media Access control)-- comes to play.

22. --MAC address--: A --globally unique-- --identifier-- attached to an individual network interface. 

23. MAC address is a 48 bit (6 byte) number that is mostly showed by 6 groups of 2 hexidecimal numbers:

      b8:8d:12:36:64:94

24. The MAC address splits into two sections, the first three --octects-- of the mac address is --Organizational unique identifier--
      (OUI). The last three octects can be used by manufacturer to define unique addresses for each one of their devices.

25. Ethernet uses MAC addresses to ensure that data it sends has both an address for the machine that sent the transmission, as 
      well as the one that transmission was intended for.

26. A --unicast transmission-- is always meant for just one receiving address. At the ethernet level this is done by looking
      at a --special bit in the destination MAC address. If the --least significant bit in the first octet-- of a destination 
      address is set to --zero--, it means the ethernet frame is intended only for the destination address.

[ATTENTION]
This means it would be sent to all devices on the collision domain, but only actually received and process by the intended destination.

27. If the --least significant bit of the first octet of destination address-- is set to --one--, it means you are dealing with the 
      --multicast ethernet frame--. 

[ATTENTION]
this means --similarlly-- it would sent to all devices on the collision domain, and it will received or discarede depending on 
      criteria aside from their own MAC address. Network interfaces can be configured to accept lists of configured multicast
      addresses for these sort of communication.

28. An --ethernet broadcast-- is sent to every single device on a LAN. This is accomplished by using a special destination known as
       a broadcast address. The Ethernet broadcast address is all Fs (ff:ff:ff:ff:ff:ff).
       --Ethernet broadcasts are used so that devices can learn more about each other--. 
      
29. --Data packet--: An all-encompassing term that represents any single set of binary data being sent across a network link. 
      --data packet is not tie to any layer--
      data packets in data link layer known as --Ethernet frames--

30. --Ethernet frame--: A highly --structured-- collection of information presented in a --specific order--

[ATTENTION]
Almost all sections of an Ethernet frame are --mandatory-- and most of them have a --fixed size--.

31.-- Ethernet frames sections--:

      a. --preamable--: A --preamble-- is 8 bytes (64 bits) long, and can itself be split in two parts.
      
      The first 7 bytes, The first seven bytes are a series of alternating ones and zeros. These act partially as a --buffer-- between
      frames and can also be used by the network interfaces to --synchronize internal clocks-- they use, to regulate the speed at which
      they send data.

      the last byte in the preamble is known as the --SFD or start frame delimiter--.

      b. Destination MAC address (6 bytes)

      c. Source MAC address (6 bytes)

      d. --VLAN-- (optional): It's worth calling out that instead of the EtherType field, you could also find what's known as a 
            --VLAN header--. It indicates that the frame itself is what's called a --VLAN frame--. If a VLAN header is present,
            the EtherType field follows it. VLAN header is 4 bytes.
            
            VLAN stands for virtual LAN. It's a technique that lets you have multiple logical LANs operating on the same physical
            equipment. Any frame with a VLAN tag will only be delivered out of a switch interface configured to relay that specific
            tag. This way you can have a single physical network that operates like it's multiple LANs. VLANs are usually used to
            segregate different forms of traffic. So you might see a company's IP phones operating on one VLAN, while all desktops 
            operate on another. 

      e. --EtherType field--: It's 16 bits(2 bytes) long and used to describe the protocol of the contents of the frame.

      f. --payload--: In networking term, payload is the actual data being transported. which is everything that is not header.
            can be anywhere from 46 to 1500 bytes long. --this contains data from all the higher levels--.
      
      g. --frame check sequence (FCS)--:  4 bytes (32 btis) number that represents a --checksum (hash sum or hash value) value-- for the entire
             frame.

            This --check sum value-- is calculated by performing what's known as --cyclical redundancy check-- against the frame.

            --Cyclical Redundancy Check (CRC)--: An important concept for data integrity, and is used in all over computing, 
                  not just networking.
            
            We have two --types of errors-- when sending data:

                  1. --bit errors--: only one bit in the data unit will change.

                  2. --burst errors--: group of bits has been changed in the transmission.

                        the --burst error length-- is the length between first ocurrance of the error and the last ocurrance of the 
                        error.
            
            -- Error detection--: error detection take place in the receiver side, but without the original message the error 
                  detection is impossible, so we need to send --additional bits, just for error detection--.
                  this bits is called --redundant bits--.
            
            The --process of the error detection-- is like this: 

                  a. The data send to --Generating function--

                  b. --Generating function-- generates --Redundant code(redundant bits, redundancy check)

                  c. The --redundant bits-- will append and send beside the actual data.

                  d. The receiver side, gets the data, and generates redundant bits for the received data, and compare it 
                        it with the received redundant bits, if matches, accept it, otherwise reject it.
            

            The ways of --Error detection--:

                  a. --vertical redundancy check (VRC)--: It is also known as --parity check--, it checks if the number of the ones in 
                        the data is odd or even. 
                  
                        data: 1100001  => There 3 ones, so it is odd, so => the VRC bit is set to 1

                        if there are even ones, the VRC bit would be 0. the --VRC bit is the most significant bit--

                        --VRC analysis--: VRC is --good for bit error--, and it is not good for --burst errors--.
                  
                  b. --Longitudinal redundancy check (LRC)--: It is also known as --two dimensional parity--, a block of bits is 
                        organized in rows and columns.

                        data blocks: 11100111 11011101 00111001 10101001

                              11100111
                              11011101
                              00111001
                              10101001
this is parity in column:     10101010

                        -- LRC analysis--: If two bits in one data unit is damaged, and two bits in exactly the same position in 
                                          another data unit is damaged, LRC can catch the burst error.
                  
                  c. --Checksum--: This process involves series of steps:

                        1. break the original message into k blocks with n bits in it.

                        2. sum all the k blocks

                        3. add the carry to the sum if any.

                        4. Do 1s complement to the sum = checksum

                        data unit: 10011001111000100010010010000100

                        1. breaking it into 4 blocks:

                              10011001          11100010          00100100          10000100

                        2,3. sum all 4 blocks and add the carry to sum:

                                    10000100
                                    00100100
                                    11100010
                                    10011001
                                    --------
                                  1000100011   
                                          10          this is the carry    
                                   ---------       
                                    00100101
                        
                        4. Do 1s complement: 
                                    00100101 => 11011010 (This is the checksum)
                        
                        5. The receiver sum all the blocks and checksum, if the result is all 1, it accept, if it is not it reject.

                        -- Checksum analysis--: if the sum of the column is not changed, the receiver won't detect the error.
                  
                  d. --Cyclic redundancy check (CRC)--: 
                        
                        1. Find the length of --divisor-- L (It is the number that is agreed between receiver and sender)

                        2. Append L-1 zero bits to the original message 

                        3. Perform binary division operation (by XOR operator)

                        4. Remainder of the division is --CRC-- and will append to the data.

                        --example--

                              (divisior))1101 - 100100(real message) - 000 (appended zero bits)

                              100100000 / 1101
                              1101
                              -----
                               1000            | 11
                               1101
                               -----
                                1010
                        
                        5. The receiver perform binary division, if the remainder is zero, the data is ok.

///////////////// Network layer ///////////////////

32. Ip numbers are 4 bytes (32 bits) and usually shows in --dotet decimal notation--:

            12.34.56.78       

33. on many modern networks you can connect a new device and an IP address will be assigned to it automatically through a 
      technology known as DHCP --dynamic host configuration protocol--. IP address that is assigned this way, known as dynamic 
      IP address

      a. dynamic IP address: the ip address that is assined by DHCP

      b. Static IP address: In most cases --static IP addresses-- are reserved for servers and network devices.

34. Data packet in network layer under IP protocol reffers to --IP datagram--.

35. IP datagram a highly structured series of fields that are stricly defined.

36. The IP datagram divide into two sectiosn: 
      
      a. --IP datagram header:

            0           4               8                 16       19                                  31 (bit)
            |   Version | Header length |  Service type   |                   Total length                |
            |        Identification                       | Flags   |           Fragment Offset           |
            |         TTL               |    Protocol     |                   Header Checksum             |
            |                                   Source IP address                                         |
            |                                   Destination IP address                                    |
            |     Options                                                              | Padding          |

            1. --Version--: show what version of internet protocol we are using. The most common version is IPv4

            2. --Header length--: shows the length of header in bytes, it is always --20 bytes-- when we have IPv4,
                  20 bytes is the minimum length of the IP header.
            
            3. --Service type--: These bits can be used to specify the details about quality of service (QoS) technologies.

            4. --Total length--: total length of IP datagram.

            5. --Identification--: Since the max length of IP datagram is 2^16 bits, if the data that we want to send is more 
                  than this number, we have to break the data into multiple packets, so --identification-- shows which 
                  packets are belong to the same message.
            
            6. --Flag--: Used to indicate if a datagram is allowed to be fragmented, or to indicate that the datagram 
                  has already been fragmented.

            7. --Frament offset--: If a datagram has to cross from a network allowing a larger datagram size to one with a smaller
                  datagram size, the datagram would have to be fragmented into smaller ones. The fragmentation offset field contains
                  values used by the receiving end to take all the parts of a fragmented packet and put them back together in the
                  correct order.
            
            8. --TTL (Time to Live)--: This field is an 8-bit field that indicates how many router hops a datagram can traverse before
                   it's thrown away. Every time a datagram reaches a new router, that router decrements the TTL field by one 

            9. --Protocol--: This is another 8-bit field that contains data about what transport layer protocol is being used.
                   The most common transport layer protocols are TCP and UDP,
            
            10. --Checksum--: TTL and checksum will change at each router.

            11. Options: This is an optional field and is used to set special characteristics for datagrams primarily used for
                  testing purposes.
            
            12. --Padding--: Since the IP options field is both optional and variable in length, the padding field is just a series of
                   zeros used to ensure the header is the correct total size

      b. --IP datagram payload--:  contains information from high level

[ATTENTION]
each layer packet payload contains all the infromation (including payload and header) from the higher level layer.

37. --IP Address classes--: IP addresses divide into two section --network id-- and --host id--, --The address class system--
       is a way of defining how the --global IP address space is split up--. There are three type of address classes.

       a. class A: first octet used for network id (has 24 bits for host ids, it has 2^24 individual addresses)

       b. Class B: two octet used for network id, and other two for host id

       c. Class C: three octet used for network id, and the last one used for host id.


      Class            Starting IP address           Last IP address
      A                     0.0.0.0                  127.255.255.255
      B                     128.0.0.0                191.255.255.255
      C                     192.0.0.0                223.255.255.255
      D                     224.0.0.0                239.255.255.255          (used for network multicasting)
      E                     240.0,0,0                255.255.255.255          (used for testing)

38. --all the data of IP datagram-- will be in the --payload of the Ethernet frame--, IP datagram has a Ip address in it, we 
      have to translate this ip address to the MAC address. We do this by --Address Resolution Protocol (ARP)--

39. --ARP--: A protocol used to discover the hardware address of a node with a certain IP address.

[ATTENTION]
40. Almost all network connected devices will retain a local --ARP table--. An ARP table is just a list of IP addresses an the Mac
       addresses associated with them.
       In unix based OS, you can see your arp table with --arp -a-- 


41. Let's say we want to send some data to the IP address 10.20.30.40. It might be the case that this destination doesn't have an 
      entry in the --ARP table--. When this happens, the node that wants to send data send a --broadcast ARP message-- to the 
      Mac broadcast address, which is all F's. These kinds of broadcasts ARP messages are delivered to all computers on the local
      network. When the network interface that's been assigned an IP of 10.20.40 receives this ARP broadcast, it sends back what's 
      known as an ARP response. This response message will contain the MAC address for the network interface in question.
      Now, the transmitting computer knows what MAC address to put in the destination hardware address field, and the Ethernet 
      frame is ready for delivery. It'll also likely store this IP address in its local ARP table, so that it won't have to send 
      an ARP broadcast the next time it needs to communicate with this IP, handy. ARP table entries generally expire after a short 
      amount of time to ensure changes in the network are accounted for.

42. There are a handful of practical reasons people use IP Lookup, even with its limitations:

      a. Law enforcement and fraud investigators use online tools to see what ISP is hosting a spammer.

      b. Blacklist databases use it to find spammers or other violators and block their access to email servers.

      c. Retailers often use IP Lookup to make sure someone charging thousands of dollars is at the mailing address linked to 
       the card...and not actually overseas with a stolen credit account.

      d. You can use it to verify that someone who tells you in an email that they're across town isn't really in 
            an abandoned warehouse in another country.

43. --subnetting-- is the process of taking a large network and splitting it up into many individual smaller subnetworks or subnets.

                              (home router sends)                                                      (core router sends)
44. to 9.100.100.100 IP adress ==> Core routers (knows this IP belongs to the 9.0.0.0 Class A Network) ==>
      
                                                                                       (gateway routers sends)
      ==> --gateway routers-- responsible for the network by looking at the network ID. ==> sending that data to the proper 
            system by looking at the host ID

[ATTENTION]
45. A --gateway router-- specifically serves as the entry and exit path to a certain network

46. --The problem-- is that for example class A networks has 2^24 host id, and it is a lot to connect to a gateway router.
      to solve this issue we use --subnetting--. With subnetting we divide our network to many smaller individuals.
      these subnets has their -- own gateway routers -- serving as the ingress and egress point for each subnet. 

47. -- Sub net ID--: In a world with subnetting, some bits that would normally comprise the host ID are actually used for the subnet ID.
       With all three of these IDs representable by a single IP address, we now have a single 32-bit number that can be accurately 
       delivered across many different networks. At the internet level, core routers only care about the network ID and use this to
       send the datagram along to the appropriate gateway router to that network. That gateway router then has some additional 
       information that it can use to send that datagram along to the destination machine or the next router in the path to get there.
       Finally, the host ID is used by that last router to deliver the datagram to the intended recipient machine.
       Subnet IDs are calculated via what's known as a --subnet mask-- (a 32 bit number).

                  9               100             100            100
                  00001001     01100100         01100100       01100100
subnet mask:      11111111     11111111         11111111       00000000             (255.255.255.0)

                  we also shows subnet mask with this notation: 9.100.100.100/24     (24 is the number of ones)
                  (CIDR notation or slash notation)

[ATTENTION]
48. Each subnetwork has a constant part, this constant part defined with subnet mask and we call part of this constant part subnet id
      for example: we have subnet that 9.100 is constant for it or 9.50 is constant for another subnet, how do we find that these 
      parts are constant for these two subnet, we use subnet mask

      256.256.0.0 (this is subnet maks)

      for example we can have another subnet after the 9.100, 9.100.50, we know these parts are constant for this subnet, we define 
      the constant part with subnet mask:

      256.256.256.0           (9 is class A address type so the first octet is network id, and the second and third octet is 
                              subnet id)

49. There was --problems-- with Class addresses and subnetting approach. 

      a. Network id sizes: 
            
            1. The class A network has only 256 network ids that is not enough

            2. the class C has 16777214 network ids, that is too much entries in routing tables

      b. Host id sizes:
            
            1. In Class A the number of host ids is to much for businesses (16777214)

            2. In Class B the number of host ids is to much for most businesses (65534)

            3. In Class C the number of host ids is not enough for most businesses (256)


50. To solve these problems the --CIDR (Classless Inter-Domain Routing)-- comes to play.

      CIDR expands on the concept of subnetting by using subnet masks to --demarcate networks--. To demarcate something means to set
      something off. When discussing computer networking, you'll often hear the term --demarcation point-- to describe where one 
      network or system ends and another one begins.

IN CIDR the concept of Network ID and subnet ID becomes one. 

      9.100.100.100/24 or 9.100.100.100
                          255.255.255.0

IN CIDR the network ID determinded by subnet mask:
      In this example the network ID is 9.100.100

51. Before CIDR if a company with a network C needs more host IDs, It has to get another network C ID: 
      and will get another 254 host ids (total of 508), but with CIDR it can use /23 subnet mask, and will have 510 host ids.

/////////////// Routing /////////////

[ATTENTION]
A router is a device that has at least two network interfaces.

52. Basic routing has 4 steps: 

      a. A router receives data packet on one of its interfaces

      b. Examine destination IP of this packet

      c. Looks up IP destination network in routing table

      d. The router forwards that out through the interface that's closest to the remote network. As determined by additional 
            info within the routing table.

53. Details of routing procedure between two network with same Router:

      Network A                Router                    Network B 
      192.168.1.0/24                                   10.0.0.0/24


gateway interface of network A               gateway interface of network B
      192.168.1.1                                     10.0.0.254
  00:00:0A:BB:28:FC                          00:00:0A:BB:28:FD        


      a. A Computer on network A with 192.168.1.100 sends packet to 10.0.0.10 
      
      b. This computer knows 10.0.0.10 is not on its local subnet so 

      c. sends the data to MAC address of gateway router (It means the IP destination address in Ethernet frame payload is different
       from the MAC address in the Ethernet frame header)
      
      d. The router's interface on Network A receives the packet because it sees that destination MAC address belongs to it.
            The router then trips away the data-link layer encapsulation, leaving the network layer content, the IP datagram. 
            
      e. It looks in its --routing table--, and see the destination IP address of 10.0.0.10 Belongs to network B(10.0.0.0/24). It
            also sees that this network is one hob away, since it is directly connected It has the destination MAC address in its ARP 
            table. 
      
      f. router needs to form a new packet to forward it to network B. 

                  Application           Message

                  Transport             Message / TCP or UDP header

                  Network               Message / TCP or UDP header / IP header 

                  Data link    footer / Message / TCP or UDP header / IP header / Ethernet header
            
            1. most of the data is duplicated from the first data packet, but it has to change the TTL (decreament by one) and 
                  checksum of the IP header
            
            2. In Ethernet header it changes the Source MAC address (put its own MAC address) and it puts the MAC address of the 
                  10.0.0.10 in the destination MAC address

53. IF the network A wants to send packet to network C that is not directly connected, The procedure is the same, but Router A 
      (Router between network B and C) looks into its routing table and find the quickest way to send the packet to Router B that 
      is directly connected to network C.

54. Routing tables can vary a ton depending on the make and class of the router, but they all share a few things in common:

      
      Destination network         Subnet mask       Interface         Next hub          Metric

55. routers keeps their tables updated through --routing protocols--:

56. Routing protocols fall into two main categories:

      a. Interior gateway protocols: Used by routers to share information within a single --autonomous system--.
            --autonomous system--: A collection of networks that all fall under the control of a single network operator. 
            for example: A large corporation that need to route data between their many offices and each of them has a separate LAN,
                  or many routers that employed by a ISP 

            1) Link state routing protocols: The information on every router sends to any router in a autonomous system, and they 
                  use more complicated algorithms to determine the best path.
            example of this:  OSPF, or Open Shortest Path First (IETF RFC2328).

            2) distance-vector protocols: each router sends the list(vector) of its networks and distances to all neighbor routers.
            example of this is --RIP(routing information protocol)-- 
            --EIGRP, or Enhanced Interior Gateway Routing Protocol--

      b. Exterior gateway protocols: used by routers representing the --edge of an autonomous systems-- to share data.

            High level: 

                  --Core internet routers-- need to know about autonomous systems in order to properly forward traffics.

            
            --Internet Assigned Numbers Authority (IANA)-- is a non-profit organization that helps manage things like IP address
            allocation. Along managing IP addresses allocation, the IANA is responsible for --ASN or autonomous system number--
            allocation.

            ASN s are 32 bits number

57. --RFC (request for comments)--: RFC outlined a number of networks that would be defined as --non-routable address space--.
      non-routable IPs reserved for nodes on a network but no gateway routers can forward traffic to these addresses.

      10.0.0.0/8

      172.16.0.0/12

      192.168.0.0/16

[ATTENTION]
It should be called out that interior gateway protocols will route these address spaces. So, they are appropriate for use within
 an autonomous system but exterior gateway protocols will not.


 /////////////////// Transport Layer ////////////////////

 58. --Multiplexing-- in the transport layer means that nodes on the network have the ability to direct traffic toward many
      different receiving services. --Demultiplexing-- is the same concept, just at the receiving end, it's taking traffic that's
       all aimed at the same node and delivering it to the proper receiving service.

59. Transport layer handles multiplexing and demultiplexing through ports (16 bit number).

      10.0.0.1:80             This kind of notation knows as --socket address or socket number--

60. Dissection of a TCP segment:    


      Bit 0                                     Bit 15   Bit 16                                        Bit 31
            Source port                                                 Destination port

                                                Sequence number

                                                Acknowledgment number
      header          empty(6)   control flags(6)                       Window
      length(4)

                  Checksum                                                    Urgent

                  Options(0 or 16 if any)                               padding

                                                Data payload(varies)
      
      a. sequence number: this is a 32 bits number that's used to keep track of where in a sequence of TCP segments this one is 
            expected to be.
      
      b. Acknowledgment number: is the number of the next expected segment.

      c. Control flags: we will discuss these later.
      
      d. TCP window: Specifies the range of sequence numbers that might be sent before an acknowledgment is required.

      e. Urgent pointer field: The Urgent pointer field is used in conjunction with one of the TCP control flags to point out
            particular segments that might be more important than others. This is a feature of TCP that hasn't really ever seen
            adoption and you'll probably never find it in modern networking

      f. Options field: Like the urgent pointer field, this is rarely used in the real world, but it's sometimes used for more 
            complicated flow control protocols.

61. TCP control flags (we define them in the order that they are appearing):

      a. URG (urgent): A value of one here indicates that the segment is considered urgent, and the urgent pointer field has more
            data about this.
      
      b. ACK (acknowledgment): A value of one in this field shows that the acknowledgment field should be examined.

      c. PSH (push): This means, that the transmitting device wants the receiving device to push currently- buffered data to the
            application on the receiving end as soon as possible. A buffer is a computing technique, where a certain amount of data
            is held somewhere, before being sent somewhere else. This has lots of practical applications. In terms of TCP, it's used
            to send large chunks of data more efficiently. By keeping some amount of data in a buffer, TCP can deliver more meaningful
            chunks of data to the program waiting for it. But in some cases, you might be sending a very small amount of information,
            that you need the listening program to respond to immediately. This is what the push flag does.
      
      d. RST (reset): This means, that one of the sides in a TCP connection hasn't been able to properly recover from a series of
            missing or malformed segments. It's a way for one of the partners in a TCP connection to basically say, "Wait, I can't put
            together what you mean, let's start over from scratch.
      
      e. SYN (synchronize): It's used when first establishing a TCP connection and make sure the receiving end knows to examine the
            sequence number field.
      
      f. FIN (finish): When this flag is one, it means the transmitting computer doesn't have any more data to send and the connection
            can be closed.

62. TCP three-way handshake using control flags: 

      Computer A                              Computer B
                              SYN
                  ------------------------->
                              SYN/ACK
                  <-------------------------
                              ACK
                  -------------------------->

63. The four-way handshake: 

      Computer A                              Computer B
                              FIN
                  <--------------------------
                              ACK
                  --------------------------->
                              FIN
                  --------------------------->
                              ACK
                  <--------------------------

64. --Sockets--: A socket is one endpoint of a two-way communication link between two programs running on the network. A socket is bound
       to a port number so that the TCP layer can identify the application that data is destined to be sent to.

65. --TCP socket states--:

      a. --LISTEN--: A TCP socket is ready and listening for incomming connections, you see this on --server side only--.

      b. --SYN_SENT--: This means a synchronization request has been sent, but the connection hasn't been established yet.
            you'd see this on --client side only--
      
      c. --SYN_RECEIVED--: A socket previously on a LISTEN state, has received the synchronization request and send back the 
            SYN/ACK. But it hasn't received the final ACK. you can see this only in the --serverside--.
      
      d. --Established--: The TCP connection is in working order and both sides are free to send data to each other.

      e. --FIN_Wait--: A FIN has been sent, but the corresponding ACK from the other end hasn't been received yet.

      f. --CLOSE_WAIT--: The connection has been closed on the TCP layer, but the application that opened the socket, hasn't released
            its hold to the socket.
      
      g. --CLOSED--: The connection is completely closed.

[ATTENTION]
Socket states varies from operating system to operating system.

66. Connection oriented protocols: Establishes the connection, and uses this to ensure that all data has been properly transmitted.

67. Our protocols at lower levels of our network model, like IP and Ethernet, do use checksums to ensure that all the data they
      received was correct. But did you notice that we never discussed any attempts at resending data that doesn't pass this check?
      That's because that's entirely up to the transport layer protocol.

68. --In connection oriented protocols--, like TCP there are lots of overhead to ensure data properly transmitted.

69. In connection less protocols: you just add the destinatio port and send the data. for example in video streaming, loss of 
      several segments it is not that important, so we use UDP for sending data.

70. Port number is 16 bits number this range has been split up by the IANA (Internet Assigned Numbers Authority) into independent 
      sections:

      a. Port 0 isn’t in use for network traffic, but it’s sometimes used in communications taking place between different programs
            on the same computer.

      b. Ports 1-1023: are referred to as --system ports--, or sometimes as “well-known ports.” These ports represent the official 
            ports for most well-known network services. In an earlier video, we talked about how HTTP normally communicates over port
            80, while FTP usually communicates over port 21. In most operating systems, administrator-level access is needed to start
            a program that listens on a system port.

      c. Ports 1024-49151 are known as --registered ports--. These ports are used for lots of other network services that might not be
            quite as common as the ones that are on system ports. A good example of a registered port is 3306, which is the port that
            many databases listen on. Registered ports are sometimes officially registered and acknowledged by the IANA, but not 
            always. On most operating systems, any user of any access level can start a program listening on a registered port.

      d. ports 49152-65535. These are known as private or ephemeral ports. Ephemeral ports can’t be registered with the IANA and
            are generally used for establishing outbound connections. You should remember that all TCP traffic uses a destination 
            port and a source port. When a client wants to communicate with a server, the client will be assigned an ephemeral port
            to be used for just that one connection, while the server listens on a static system or registered port.

[ATTENTION]
Not all operating systems follow the ephemeral port recommendations of the IANA. In this lesson, we’ll continue to assume that
the ephemeral ports used for outbound connections consist of the ports 49152 through 65535. But it’s important to know that this
exact range can vary depending on the platform you’re working on. Sometimes portions of the registered ports range are used, but 
no modern operating system will ever use a system port for outbound communication.


///////////////////// Application layer /////////////////////

71. all the data in the packets of  application layer will be in the payload section of the transport layer.
