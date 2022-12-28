1. In this course we define 5 layers TCP/IP network model.

2.    #       Layer name        Protocol        Protocol data unit      Addressing
      
      5       Application       HTTP, SMTP      Messages                  n/a
                                etc...

      4       Transport         TCP/UDP         Segment                   Port #'s
                        (User Datagram protocol)
      3       Network           IP              Datagram                IP addresses

      2       Data link         Ethernet, Wifi   Frames                 MAC addresses

      1       Physical          10 Base T,
                                802.11            Bits                    n/a

3.  a) Physical layer:

      Represent the physical devices that interconnects computers.
      This includes the --specifications for the networking cables-- and the --connectors that join devices-- along with the 
      --specifications that desribing how signals are sent over these connections--.

4.  b) data link layer (network interface or network access layer):
      
      at this layer we introduce our first protocols.
      This layer is responsible for --defining a common way to interpreting these signals--, so network devices can communicate.

      There are lots of protocols at this layer, but the most common one is --Ethernet--, beyond --specifing physical layer attributes--
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

8. In addition to TCP / IP 5 layer model, we have another well known model --Open System Interconnection (OSI) model--.


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
      usually home or office routers don't have very detailed routing tables. The purpose of these routers is to send traffic from
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
      address is set to --zero-- (first octect means from left, and least significant means the right one), it means the ethernet
      frame is intended only for the destination address.

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

      0                 8                    14                         20                 24
           preamable       Dest MAC address         Source MAC address         VLAN
               2
      Ether type           

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
      
      g. --frame check sequence (FCS)--:  4 bytes (32 btis) number that represents a --checksum (hash sum or hash value) value-- for 
            the entire frame.

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
      entry in the --ARP table--. When this happens, the node that wants to send data, send a --broadcast ARP message-- to the 
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
                  (--CIDR notation-- or --slash notation--)

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
            expected to be, --for example the first sequence number after syn, ack would be 1--.
      
      b. Acknowledgment number: is the seqence number of the next expected segment.

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

      c. PSH (push): This means, that the transmitting device wants the receiving device to push currently --buffered data-- to the
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

70. Port number is 16 bits number this range has been split up by the --IANA (Internet Assigned Numbers Authority)-- into independent 
      sections:

      a. Port 0 isn't in use for network traffic, but it's sometimes used in communications taking place between different programs
            on the same computer.

      b. Ports 1-1023: are referred to as --system ports--, or sometimes as “well-known ports.” These ports represent the official 
            ports for most well-known network services. In an earlier video, we talked about how HTTP normally communicates over port
            80, while FTP usually communicates over port 21. In most operating systems, administrator-level access is needed to start
            a program that listens on a system port.

      c. Ports 1024-49151 are known as --registered ports--. These ports are used for lots of other network services that might not be
            quite as common as the ones that are on system ports. A good example of a registered port is 3306, which is the port that
            many databases listen on. Registered ports are sometimes officially registered and acknowledged by the IANA, but not 
            always. On most operating systems, any user of any access level can start a program listening on a registered port.

      d. ports 49152-65535. These are known as --private or ephemeral-- ports. Ephemeral ports can't be registered with the IANA and
            are generally used for establishing outbound connections. You should remember that all TCP traffic uses a destination 
            port and a source port. When a client wants to communicate with a server, the client will be assigned an ephemeral port
            to be used for just that one connection, while the server listens on a static system or registered port.

[ATTENTION]
Not all operating systems follow the ephemeral port recommendations of the IANA. In this lesson, we'll continue to assume that
the ephemeral ports used for outbound connections consist of the ports 49152 through 65535. But it's important to know that this
exact range can vary depending on the platform you're working on. Sometimes portions of the registered ports range are used, but 
no modern operating system will ever use a system port for outbound communication.


///////////////////// Application layer /////////////////////

71. all the data in the packets of application layer will be in the payload section of the transport layer.

//////////////////// Network services //////////////////////

72. --DNS (Domain Name System)--: A global and highly distributed network service that --resolves-- strings of letters into IP 
      addresses.

[ATTENTION]
DNS lets you have a distributed data center, for example you have data center in Newyork that has a IP address 184.23.42.10 you can 
      resolve it to wheather.com, and another data center in Iran with IP address of 143.23.16.18 that resolve to the same domain 
      name

72. This process of using DNS to turn domain names to IP addresses known as --name resolution--.

73. There are five primary types of DNS servers:

      a. Caching name servers: Caching and recursive name servers are generally provided by an ISP or your local networking.
            most caching name servers are also recursive name servers. All domain names in global DNS system have a --TTL--
            or --time to live--. time to live is a value in --seconds-- that can be configured by the owner of the domain, that 
            tell name servers how long they can cache an entry.

      b. Recursive name servers: perform full DNS resolution requests recursively between other servers.

      c. Root name servers

      d. TLD name servers (TLD like .com)

      e. Authoritative name servers



74. Complete recursive resolution process: 

      a. The first step is always to contact the root name server, there are --13 root name servers--. 
            --they're responsible for directing queries toward the appropriate TLD name server--. In the past, these 13 root 
            name servers were distributed to very specific geographic regions. but today, they are distributed across globe via 
            --anycast--. any cast is A technique that's used to route traffic to different destinations depending on factors like 
            location, congestion, or link health. Today, there are --not 13 physical root servers-- across globe, actually there 
            are 13 authorities that provide route name lookups as a service..
      
      b. The root name server will respond to DNS lookup with the --TLD (Top Level Domain) name server-- that should query.
            for each TLD there is one TLD name server. It doesn't mean there is only one pysical name server. it's most likely a 
            global distribution of any cast accessible servers responsible for each TLD


      c. The TLD name servers will respond again with a redirect, this time informing the computer performing the name lookup with
            what --authoritative name server(NS record)-- to contact. Authoritative name servers are responsible for the last two 
            parts of any domain name which is the resolution at which a single organization may be responsible for DNS lookups.
      
      d. the DNS lookup could be redirected at the authoritative server which would finally provide the actual IP of the server 
            in question

[ATTENTION]
DNS is a great example of --application layer service-- that uses UDP instead of TCP. because the number of TCP packets in a recursive
      DNS lookup will be to much (44), and most of the time the response DNS name servers will be fit into one UDP packet.
DNS uses --port 53--.

75. --Resource record type--: DNS in practice operates with a set of defined --resource record types--. These allow for different 
      kinds of DNS resolutions to take place:
      
      a. --A record--: An A record is used to point a certain domain name at IPv4 IP address. 
            [ATTENTION]
            In its basic use, a single A record is configured for a single domain name. But a single domain name may have multiple 
            A records. This allows for technique known as --DNS round robins-- to balance traffic between multiple IP addresses.

            Example:
            Let's say we're in charge of a domain name www.microsoft.com. Microsoft is a large company and their website likely sees
            a lot of traffic. To help balance this traffic across multiple servers. We configure four A records for www.microsoft.com
            at the authoritative name server for the microsoft.com domain. We'll use the IPs 10.1.1.1, 10.1.1.2, 10.1.1.3, and 
            10.1.1.4. When the DNS Resolver performs a look-up of www.microsoft.com, all four IPs would be returned in the order first
            configured: 10.1 1.1, followed by 10.1.1.2, followed by 10.1.1.3, and finally, 10.1.1.4. The DNS resolving computer would
            know that it should try to use the first entry, 10.1.1.1, but it knows about all four just in case a connection to 
            10.1.1.1 fails. The next computer to perform a look up for www.microsoft.com would also receive all four IPs in the 
            response, but the ordering will have changed. The first entry would be 10.1.1.2, followed by 10.1.1.3, followed by 
            10.1.1,4, and finally, 10.1.1.1 would be last on that list. This pattern will continue for every DNS resolution attempt, 
            cycling through all of the A records configured and balancing the traffic across these IPs

      b. --AAAA record--: It is very similar to A record, instead it return the IPv6

      c. --CNAME (canonical name) record--: CNAME record is used to redirect traffic from one domain to another.
            configure CNAME record for microsoft.com that resolves to www.microsoft.com.

      [ATTENTION]
      CNAMEs are really useful because they ensure you only have to change the canonical IP address of a server in one place

      d. --MX (mail exchange) record--: This record is used to deliver email to the correct server.

      e. --SRV (service record)--: It is used to define the location of various services. MX is only for mail servers, SRV record, 
            can be defined to return the specifics of many different service types.
      
      f. --TXT (text) record--: This record orinally used for associating some descriptive text with a domain name for human 
            consumption. But over the years as the Internet and services that run on it have become more and more complex,
            the text record has been increasingly used to convey additional data intended for other computers to process.

76. Each domain name has 3 parts, for example www.google.com:

      a. The last part is known as TLD (Top Level Domain). Administration and definition of TLDs is handled by a non profitable 
            organization known as ICANN (The Internet Corporation for Assigned Name and Numbers)

      b. domain: Used to demarcate where controls move from a TLD name server to an authoritative name server.

      c. sometimes referred to as a host name if it's been assigned to only one host.

[ATTENTION]
DNS can technically support up to --127 levels of domain-- in total for a single --fully qualified domain name (FQDN)--.

[ATTENTION]
Each individual section can only be 63 characters long and a complete FQDN is limited to a total of 255 characters

77. --DNS Zones--: An authoritative DNS server is actually responsible for a specific --DNS zone--. Actually Root name server and 
      TLD servers are authoritative servers, because each one of them are responsible for a DNS zone. 

      DNS zones are configured in --zone files--: Simple configuration files that are declared all the resource record type
            for a particular zone.
      
      So a zone file has to contain an --SOA, or a Start of Authority resource record declaration--. This SOA record declares the zone 
      and the name of the name server that is authoritative for it. Along with the SOA record, you'll usually find --NS records-- 
      which indicate other name servers that may also be responsible for this zone

//////////////////// DHCP ////////////////
78. You can see all the settings that your DHCP servers assigned to your computer: 

79. You can change the setting of DHCP server, for example you can use --Address reservation-- for your computer, It means 
      that everytime a computer with a specific MAC address connect to the network gets the same IP address.

            Adress Reservation table

            IP address              Device name             MAC address

[IMPORTANT]
80. DHCP is a service that is run on a server, such as windows server or linux server, It is also a service that is run on 
      --routers--

81. DHCP server uses two protocol for ip assignment: 

      a. dynamci allocation

      b. Automatic allocation: it is like dynamic allocation, but it try to give the same ip to the same device if it is 
            possible

      c. Fixed allocation

[ATTENTION]
DHCP is an --application layer-- protocol, which means it relies on the transport, network, data link and physical layers to 
	operate.
       But you might have noticed that the entire point of DHCP is to help configure the network layer itself. so how does DHCP 
       does its job without configuring the network layer?

       --DHCP discovery--: is the process by which a client configured to use DHCP attemps to get network configuration 
       information. the DHCP discovery has 4 steps:

            a. --server discovery--: DHCP clients sends what's known as --DHCP discover message--

                  DHCP listens on --UDP port 67--, and DHCP discover message are always sent --from UDP port 68--

                  So the DHCPDISCOVER message is encapsulated in a UDP datagram with a destination port of 67 and a source port of 68.
                  This is then encapsulated inside of an IP datagram with a destination IP of 255.255.255.255, and a source IP of 
                  0.0.0.0, and this will be encapsulate in frame with source MAC address of the client and destination MAC address 
                  of FF:FF:FF:FF:FF:FF for broadcasting
            
            b. --DHCPOFFER-- message will be send from DHCP server to the client. The response would be sent as a DHCPOFFER message with
                  a destination port of 68, a source port of 67, a destination broadcast IP of 255.255.255.255, and its actual 
                  IP (for example 192.168.1.1) as the source. Then it will be encapsulate in the frame with the source MAC address of 
                  the DHCP server and the destination MAC address of the client. this DHCPOFFER message has the the ip that clients 
                  want, but it is possible that client reject this ip but it is a rare situation.
            
            c. --DHCPREQUEST-- message: sends from the client to the DHCP server. Since the IP hasn't been assigned yet, this is
                   again sent from an IP of 0.0.0.0, and to the broadcast IP of 255.255.255.255.
            
            d. --DHCPACK--: This message is again sent to a broadcast IP of 255.255.255.255, and with a source IP corresponding to 
                  the actual IP of the DHCP server. Again, the DHCP client would recognize that this message was intended for itself
                  by inclusion of its MAC address in one of the message fields.

[Description]
At this stage, the computer that's acting as the DHCP client should have all the information it needs to operate in a full fledged
      manner on the network it's connected to. All of this configuration is known as --DHCP lease-- as it includes an 
      --expiration time--. A DHCP lease might last for days or only for a short amount of time

////////////////// NAT (Network Address Translation) //////////////

[ATTENTION]
82. NAT is used primarily for security and IPv4 limitations.

83. At its most basic level, NAT is a technology that allows a gateway, usually a router or firewall, to rewrite the source IP of an
       outgoing IP datagram while retaining the original IP in order to rewrite it into the response.

       The process of hiding the source IP by gateway router known as --IP masquerading--, by usin IP masquerading all the network
       computers IPs will be hidden from outside world, we call this --one to many NAT--


84. It is possible to configure your router to perform NAT for any outbound packet.


85. --NAT and transport layer--:

      The problem is how router defines the right machine for inbound traffic after NAT?

            a. The simplest way to do this is by --Port preservation--: A technique where the source port choosen by the client from 
                  the ephemeral ports (49152 to 65535), used by router to find the right machine.

                  even with the large range of ephemeral ports, it is possible that two computer choose the same source port around 
                  the same time. In this situation, the router normally selects random unused port instead.
            
            b. port forwarding: A technique where specific destination ports can be configured to always be delivered to specifics 
                  nodes.

86. --IPv4 exhaustion--: The IANA has been in charge of distributing IP addresses since 1988.

87. The IANA has primarily been responsible with assigning address blocks to the five --regional internet registries or RIRs--

88. The five RIRs are:
      
      a. --AFRINIC--, which serves the continent of Africa,
        
      b. --ARIN-- which serves the United States, Canada and parts of the Caribbean.
         
      c. --APNIC--, which is responsible for most of Asia, Australia and New Zealand and Pacific Island nations.
       
      d. --LACNIC-- which covers Central and South America and any parts of the Caribbean not covered by ARIN. 
      
      e. --RIPE--, which serves Europe, Russia and the Middle East and portions of Central Asia. 
     

89. The two solutions for IPv4 exhaustion is --NAT-- and non-routable address spaces.

/////////////////// VPNs (Virtual Private Networks) //////////////////

90. Businesses have lots of reasons to want to keep their network secure, and they do this by using some of the technologies 
      we've already discussed --firewalls--, --Nat--, --use of non routable address space--, things like that. Organizations often 
      have  proprietary information that needs to remain secure. Network services that are only intended for employees to access and 
      other things. One of the easiest ways to keep network secure is to use various securing technologies, so only devices 
      physically connected to their local area network can access these resources. But employees aren't always in the office. 
      They might be working from home or on a business trip, and they might still need access to these resources in order to get 
      their work done.
      
91 That's where VPNs come in. --Virtual private networks-- or VPNs are a technology that allows for the extension of a private or 
      local network to host that might not work on that same local network

92. VPNs are --tunneling protocols--.

93. Example of using vpn to connect to a business local network:

      a. First lets examine the typical connection in the local network: when you want to send data to another computer in the local 
            modern network (IP network), you form a typical packet:

                  Ethernet
                  IP
                  TCP
                  data
      
      b. for virtual private network, first we assign the IP address to the remote machine as if it is in the local network.
             The remote machine sends the data to gateway server instead of the destination machine and wrap the data into:

                  IP
                  UDP
                  IP
                  TCP
                  data
            the gateway server remove the IP and UDP part, and assign the proper Ethernet header, and deliver the data to the right
            machine.
      
      we use cryptography for data security when we want to send data in this way, --hashing-- for being sure that data is not altered 
            and --encrypting-- for keep the data safe. 

[ATTENTION]
To use VPN you have to configure your network to send data through gateway router for a certain IP

94. Proxy servers acts between client and servers for several benefits:

            a. anonymity

            b. Security

            c. Content filtering

            d. Increased performance by caching

[ATTENTION]
Proxy is just a concept. There are lots of common use case of proxies: 

            a. Web proxy:
                  In the past we can use Web proxies for --caching-- but nowdays they are mainly used for content filtering.

            b. Reverse proxy: A service that might appear to be a single server to external clients, but actually represent many
                  services behind it.

                        It is used for example by twitter for --load balancing-- between their physical servers: 

                                    client            reverse proxy           application server 1
                                                                              application server 2
                                                                              application server 3
                                                                                    ....
                                                                              
////////////// History of Internet ///////////////////

95. At first two students from Duke university used the --public telephone network--, --The public Switched Telephone Network or
       PSTN-- that also sometimes referred to as the --Plain Old Telephone Service or POTS-- for connecting computers together.
      The system they built is known as --USENET--.

96. A dial-up connection uses POTS for data transfer, and gets its name because the connection is established by actually dialing a
      phone number.

97. Transferring data across a dial-up connection is done through devices called --modems. Modem stands for modulator demodulator--, 
      and they take data that computers can understand and turn them into audible wavelengths that can be transmitted over POTS

98. Early modems had very low --baud rates--. A baud rate is a measurement of how many bits could be passed across a phone line in a
      second.

99. --Broadband-- has many definitions but in case of internet connectivity, it's used to reffer to any connectivity technology that
       is not dial-up. They are much faster than dial-up connections and they are always on.
       There are four common broadband solutions available today:
      
      a. --T-carrier technologies-- were first invented by AT&T in order to provision a system that allowed lots of phone calls to
             travel across a single cable
            
            Every individual phone call was made over individual pairs of copper wire before Transmission System 1, the first 
            T-carrier specification, called T1 for short, With the T1 specification, AT&T invented a way to carry up to 
            --24 simultaneous phone calls across a single piece of twisted pair copper--. Years later, this same technology was 
            repurposed for data transfers.
            Each of 24 telephone channel was cable of transmitting --64 kilobits--, making a single T1 line capable of transmitting
            data at --1.544 megabits-- per second

            More improvements to the T1 line were made by developing a way of multiple T1s to act as a single link. So a --T3 line--
            is 28 T1s, all multiplexed, achieving a total throughput speed of 44.736 megabits per second

      b. --digital subscriber lines or DSL--: DSL operates on public telephone network but at a frequency range that didn't 
            interfere with normal phone calls.

            like dial-ups modems, DSL technologies also use their own modems. But, more accurately, they're known as --DSLAMs or 
            Digital Subscriber Line Access Multiplexers--. Unlike dial-up modems, the they're usually --long-running--. 
            This means that the connection is generally established when the DSLAM is powered on and isn't torn down until the 
            DSLAM is powered off.
            
            There are lots of DSL technologies available, but they are in a minor way, for a long time the two most common ones were
            
            1. --ADSL (Asymetric Digital Subscriber Line)--: The download and upload speed are different. Usually for home users 

            2. --SDSL (Symetric Digital Subscriber Line)--: The download and upload speed are the same. Usually for the datacenters.
                  most SDSLs have upper bound limit of --1.544 megabits--. Same as T1 technology.
            
            3. --HDSL (High Bit Rate Digital Subscriber Line)--: These are DSL technologies that provide speed more than 1.544 megabits
                  per second.
       
      c. --cable broadband--: The history of both the --telephone and computer networking-- tells a story that started with all 
            communications being wired. But the recent trend is moving towards more and more of this traffic becoming wireless.

            The history of television follows the opposite path. Originally, all television broadcasts were wireless transmissions
            sent out by giant television towers and received by smaller antennas in people's homes.
            Starting in the late 1940s in the United States, the first cable television technologies were developed. At the time,
            they mainly wanted to provide television access to remote towns and rural homes that were out of range of capabilities
            of television towers at the time.

            Much like how DSL was developed, cable companies quickly realized that the coaxial cables generally used by cable 
            television delivery into a person's home were capable of transmitting much more data than what was required for TV 
            viewing. By using frequencies that don't interfere with television broadcast, cable-based Internet access technologies
            were able to deliver high speed Internet access across these same cables.

            [ATTENTION]
            One of the difference between cable broad band technologies and other technologies is something that known as 
            --Shared bandwidth technology--. In DSL and even dial-ups the connection from your home or business goes directly to
             what's known as a --Central Office or CO-- and you have a point to point connection.

            [VERY IMPORTANT]
            Cable Internet connections are usually managed by what's known as a --cable modem--. This is a device that sits at the 
            edge of a consumer's network and connects it to the --cable modem termination system, or CMTS--. The CMTS is what 
            connects lots of different cable connections to an ISP's core network.
      
      d. --fiber connections--


//////////////////////// WAN (Wide Area Network) Technologies /////////////////////

100. Problem statement:

      for example you have a small office, You decide to use --non-routable address space-- for the internal IPs because IP addresses
      are scarce and expensive. You set up a router and configure it to perform --NAT--. You configure a --local DNS server-- and a
      --DHCP server-- to make network configuration easier. And of course, for all of this to really work, you sign a contract with
      an ISP to deliver a link to the Internet to this office, so your users can access the web.
      Maybe some sales people will need to connect to resources on the LAN you set up while they're on the road. So you configure
      a --VPN server-- and make sure the VPN server is accessible via --port forwarding--

      so What if you have a second office in another location that want access to your local resources?????

101. This is where we use --WAN (Wide Area Network)--. A wide area network acts like a single network, but spans across multiple
      physical locations

[ATTENTION]
WAN technologies usually require that you contract a link across the Internet with your ISP. This ISP handles sending your data 
from one site to the other. So it could be like all of your computers are in the same physical location

102. Imagin a network of computers on one side of the country and another network of computers on the other. Each of those networks
      ends at a demarcation point, which is where the ISP's network takes over. The area between each demarcation point and the 
      ISP's actual core network is called a --local loop--. This local loop would be something like a T-carrier line or a high 
      speed optical connection to the provider's local regional office. From there, it would connect out to the ISP's core network
      and the Internet at large.

103. WANs work by using a number of different protocols at the data link layer to transport your data from one site to another.
     --In fact, these same protocols are what are sometimes at work at the core of the Internet itself, instead of are more 
     familiar ethernet--.

104. There are two solutions instead of usin WAN, because usin WAN is expensive: 

      a. --Cloud services--: cloud lets companies outsource all or part of their different pieces of infrastructure to other 
            companies to manage. For example you can have cloud storage, or have a cloud hosting provider host your email server 
            for you.

      b. --Point to Pont VPN--: A point-to-point VPN, also called a --site-to-site VPN--, establishes a VPN tunnel between two sites.
            This operates a lot like the way that a traditional VPN setup lets individual users act as if they are on the network 
            they're connecting to. It's just that the VPN tunneling logic is handled by network devices at either side, so that users
            don't all have to establish their own connections.

///////////// Wireless networks ///////////////

105. The most common way for wireless communication defined by --IEEE 802.11 standards--

106. These set of specifications that we also call --802.11 family-- make up set of technologies we call WiFi

107. Different 802.11 standards generally use the same basic protocol but might operate at differenct --frequency band-- 

108. Wifi technologies uses --radiowaves-- to transfer data, they operates on a few different --frequency bands--

109. Wifi networks operates on a few different frequncy bands. Most commonly 2.4 GHz and 5 GHz

110. There are lots of 802.11 specifications. The most commone ones are:
      
      a. 802.11b        b. 802.11a        c. 802.11g        d. 802.11n              e. 802.11ac

[ATTENTION]
In terms of our networking model, you should think of 802.11 protocols as defining how we operate at both the physical and the
       data link layers.

111. 802.11 Frame fields:

number of octects:
                   2             2          6          6           6          2          6       0-7951      4
            frame control   Duration ID   Address1   Address2   Adress3    Sequence   Address4    Data      FCS
                                                                           Controle              Payload

      a. --frame control field--: This is 16 bits long field that contains number of subfields that are used to describe how the 
            frame itself should be proccessed. This includes what version 802.11 is used.
      
      b. --Duration field--: It specifies how long the total frame is. So, the receiver knows how long it should expect to have to
            listen to the transmission
      
      c. four address fields: let's first discuss why they are --four fields instead of two--

            The most common wireless architecture uses --wireless access point--, A device that bridges the wireless and wired 
            portion of the network.

            a large wireless network might have lots of access points. Devices on a wireless network will --associate-- with a 
            certain access point. This is usually the one they're physically closest to. But, it can also be determined by all
            sorts of other things like general signal strength, and wireless interference

            There are four address fields, because there needs to be room to indicate which wireless access point should be 
            processing the frame. So, we'd have our --normal source address field--, which would represent the MAC address of the 
            sending device. But, we'd also have the --intended destination on the network--, along with a --receiving address-- and a
            --transmitter address--. The receiver address would be the MAC address of the access point that should receive the frame,
            and the transmitter address would be the MAC address of whatever has just transmitted the frame.

            [ATTENTION]
            In lots of situations the destination and receiving address are the same.
            Source and transmitter addresses are the same.
            But sometimes depends on wireless network architecture the frames send from one access point to another
      
      d. Sequence control field: The sequence control field is 16 bits long and mainly contains a sequence number used to 
            keep track of ordering the frames.

112. The many different 802.11 specifications -- most commonly b, a, g, n, and ac -- all operate with the same basic data link 
      protocol. But, how they operate at the physical layer varies. Each of these specifications can have --different ranges--, can
      use --different modulation techniques--, can have --different transmission bit rates--, operate on 
      --different frequency bands--, etc.

      Memorizing all of these differences probably isn’t worth the time unless you’re going to be working with many different 
      types of wireless networks all the time. The most important thing to remember is that networks that operate on the 5Ghz 
      band are almost always faster, but have less of a range. Most of the 2.4Ghz networks are slightly slower and more 
      susceptible to interference, but usually cover a larger area

113. There are main few ways that a wireless network can be configured:

      a. --ad-hoc networks--: nodes speaks directly to each other

      b. --Wireless LANS (WLAN)--: one or more access point act as a bridge between a wireless and wired network

             wireless devices  ->   access point  -> Gateway router   -> Internet or wired network

      c. --Mesh networks--: It is kind of hybrid network of two

114. --Wireless channels--: Channels are individual, smaller sections of the overall frequency band used by a wireless network
            channels help to address colission domains

      [ATTENTION]
      2.4 GHz and 5 GHz are just shorthand for where these frequency bands actually begin.

      for example for 2.4 GHz


      2.400   2.410   2.420  2.430  2.440  2.450  2.460  2.470  2.480  2.490  2.500  


      Between these two frequencies (2.4 and 2.5 Ghz) are a number of channels. Since different countries and regions have
      different --regulatory committees-- for what radio frequencies might be used for what, exactly how many channels are available
      for use depends on where in the world you are.

      For example, dealing with an 802.11b network, --channel one-- operates at 2412 megahertz, but since the channel width is 22
      megahertz, the signal really lives on the frequencies between 2401 megahertz and 2423 megahertz.

      Some channels overlap but some are far enough apart so they won't interfere with each other at all.

      Let's look again at 802.11b network running on a 2.4 Gigahertz band. With a channel width of 22 megahertz, channel one with
      its midpoint at 2412 megahertz, is always completely isolated from channel six with its midpoint at 2437 megahertz and
      channel 11. 
      
      Today, most wireless networking equipment is built to auto sense what channels are most congested. Some access points will
      only perform this analysis when they start up, others will dynamically change their channel as needed. Between those two 
      scenarios and manually specified channels, you can still run into situations where you experience heavy channel congestion


115. Wireless securtiy:

      - Problem statement: 
      When you're sending data over a wired link, your communication has a certain amount of inherent privacy. The only devices
      that really know what data is being transmitted are the two nodes on either end of the link. Someone or some device that
      happens to be in close proximity can't just read the data. With wireless networking, this isn't really the case, since there
      aren't cables, just radio transmissions being broadcast through the air, anyone within range could hypothetically intercept
      any transmissions

      To solve this --Wired Equivalant Privacy (WEP)--: An encryption technology that provides a very low level of privacy.
      --WEP uses 40 bits key for encryption--, and it can be cracked in couple of minutes.
      
      WEP mostly replaced by --WPA encryption algorithm--, WPA uses 128 bits key. Today, mostly we use --WPA2 for encryption.
      WPA2 uses 256 bits key--

///////////// Cellular networks ///////////

116. Cellular networks are most like Wifi network. One of the biggest differences is that these frequencies can travel over longer
      distances more easily, usually over many kilometers or miles.

///////////////// Diagnosting connectivity issues /////////
117. --ICMP or Internet control message protocol-- is used to communicate network issues.

[ATTENTION]
118. ICMP is mainly used by a --router or remote host-- to communicate why a transmission has failed back to the origin of the
      transmission.

119. ICMP packet structure:

      (8 bits)     8 bits       16 bits           32 bits
      type         code        checksum       Rest of header 

                  Payload section


      --Type--: specifies what type of message is being delivered. Some examples are -- destination unreachable-- or 
            -- time exceeded--
      
      -- Code --: Indicates a more specific reason for the message than just the type, for example of the destination unreachable
            type there are individual codes for things like --destination network unreachable--, and 
            --destination port unreachable--
      

      --Rest of header--: This field is optionally used by some of the specific types and codes to send more data.


      --Payload--: The payload for an ICMP packet exists entirely so that the recipient of the message knows which of their 
            transmissions cause the error being reported. It contains the entire IP header, and the first 8 bytes of the data
            payload section of the offending packet

[ATTENTION]
120. ICPM wasn't developed for human. The point is so that these sorts of error messages can be delivered between networked
 computers automatically. But there's also a --specific tool-- and --two message types-- that are very useful to human operators.

      tool: ping -> ping let you send a special type of ICMP message, called --Echo request--. An ICMP echo requests essentially
            just ask destination. Hey are you there? If the destination is up and running and able to communicate on the
            network, it will send back an ICMP --echo reply-- message type.

      two message types:  --Echo request-- and --echo reply--

121. In all operating systems ping command line has number of flags that you can change its behaviors like the number of echo 
      requests to send, how large they should be and ...


122. Problem statement: 

      With ping, you now have a way to determine if you can reach a certain computer from another one. You can also understand
      the general quality of the connection. But communications across networks, especially across the Internet usually, cross
      lots of intermediary nodes. Sometimes, you need a way to determine where in the long chain of router hops the problems
      actually are.

      - Solution:
            --Traceroute-- is an awesome utility that lets you discover the paths between two nodes, and gives you information
             about each hop along the way.

124. --Traceroute-- uses --TTL header-- field to do its job. We know that TTL field is decremented by one, by every router that
      forwards the packet. When the TTL field reaches zero, the packet is discarded and an ICMP Time Exceeded message is sent
      back to the originating host. Traceroute uses the TTL field by first setting it to one for the first packet, then two 
      for the second, three for the third and so on. By doing this clever little action, traceroute makes sure that the 
      very first packet sent will be discarded by the first router hop. This results in an ICMP Time Exceeded message, 
      the second packet will make it to the second router, the third will make it to the third, and so on. This continues 
      until the packet finally makes it all the way to its destination. For each hop, traceroute will send three 
      identical packets.

125. On each line, you'll see the --number of the hop and the round trip time for all three packets--. You will also see the 
      IP of the device at each hop, and a host name if traceroute can resolve one. On Linux and MacOS, traceroute sends --UDP
      packets to very high port numbers--. On Windows, the command has a shortened name --tracert--, and defaults to using ICMP 
      echo request

126. Two more tools that are similar to traceroute are --mtr-- on Linux and MacOS and --pathping-- on Windows

127. You can use some tools for checking connectivity at --Transport layer-- or testing ports:

      a. --Netcat-- on Linux and Mac OS:

            >> nc google.com 80

            If the connection fails, the command will exit. If it succeeds, you'll see a blinking cursor, waiting for more input.
            This is a way for you to actually send application layered data to the listening service from your own keyboard

            If you're really only curious about the status of a report, you can issue the command, with a -z flag, which stands
            for Zero Input/Output Mode

            >> nc -z google.com 80

            -v is also used for verbose mode:

            >> nc -v google.com 80


      b. --Test-NetConnection-- on Windows:

            >> Test-NetConnection google.com    (This will also shows the info about data link layer)

            >> Test-NetConnection  -ComputerName google.com -port 80

////////////// DNS ///////////////

128. You can use --nslookup-- CLI to findout about the DNS server:

      nslookup google.com 

129. or you can use nslookup in interactive mode:

      >> nslookup

      