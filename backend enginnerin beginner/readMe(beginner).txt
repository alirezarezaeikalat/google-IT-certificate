1. Skills for backend engineer: 

      a. Communication protocols (TCP, UDB, HTTP, Web sockets, GRPC)

      b. Web servers (type of web server like single thread like node or multithread like apache,
          there are some web servers that act as proxy and web server like nginx
      
      c. database engineering

      d. proxies: proxies, reverse proxies, caching layer, load balancer 

      e. caching layers

      f. messaging system

      g. web APIs frameworks like express, django

      h. message formats (like xmls, jsons, protocol buffer)

      i. security (encryption like TLS)


2. OSI model (open systems interconnection model)
    OSI standardize the communication in computer systems

    MAC (media access control) address is a unique 48 bit that identifies your network card.

    different with public and private ip address: 

        around 90s your computer has modem, and this modem has a public ip address, this address 
        is accessible through internet, for example if you have a node js app in your pc, everybody 
        can access that, for example public ip (47.144.221.167) your app could be on port 8080
        47.144.221.167:8080

        but nowdays everyhome has a router, a router serve multiple purpose:

          1. it is the one that connect to internet, it has a modem (it has public ip address)

          2. the rest of your network, for example your mobile and your pc gets another ip addresses
              (internal ip addresses) and your router gets internal ip address as well. like 192.168.1.1

              for example if you have a node js app in one of the machine in your network with this 
              ip address (192.168.1.1:8080) other machines in the same network can access your app
              with correct address, but other machine outside your network can not access your app
              because this ip address is internal ip address, and if machines outside your network
              use the router public ip address, they still get error, because this public ip address
              is for the router, not for the machines, to solve this you can use:

              port forwarding: it means you can write in to your router, that if you get requests
              to certain port you can forward it to the specific internal ip address, for example: 

                47.144.221.167:8080 (this router public ip address) -> 192.168.1.9:8080

    
    10.0.0.3 is a web server having a web app and 10.0.0.5 wants to consume it, 
    Try to explain this: 
    [ATTENTION]
    each layer is the package of protocols

            Layer 7 Application: you make a get request GET / 10.0.0.3:80
                                    Http header, cookies, content type (these are string information that will change to bits)
            There are lots of protocols that used in this layer for example:

                FTP: used for file transfer
                Http(s): used for web surfing
                SMTP: used for emails
                Telnet: used for virtual terminals

            Layer 6 Presentation:   change data recieved from application layer to machine understandable binary fromat (Translation)

                                for example change ASCI ------> EBCDIC
                
                and also use Data compression in this layer(Data compression)
            
                you can encrypt data in this layer if it is neccessary (Encryption)

 

            Layer 5 Session: Establish session tag (add session id to the data that we are going to send)
                
                Setting up sessions:
                    Check user credentials
                    Assign numbers to session to identify them
                    Negotiate services needed for the session
                    Negotiate who begins sending data

                    (This is Syn in wireshark)

                Maintaining sessions (Keep alive in wireshark)

                Tear down sessions (This is FIN in wireshark)

            Layer 4 Transport: breaks the huge data into multiple segments, and each segment taged with lots of data including 
                                source and destination port, these segments are in sequence.
            
            Layer 3 Network: changes those segments to packets, each packets can have multiple segements from the last step, and
                            in this layer, source and destination ip address will be added to each packet. 
            [ATTENTION]
            There is no error check in this layer.

            Layer 2 Data Link: this layer, some how is physical, and will break the packets into frames, and attach source
                                and destination MAC address to each frame.

                                sometimes we don't know the MAC address of the machine that we want to connect, in this 
                                situation the ARP(address resolution protocol) comes, which takes the ip address and 
                                reverse it to MAC address.
                                data link layer splits into two sections:
                                    a. Logical link control (LLC) : gets all the frames and make them in order, and check the 
                                        health of frames
                                    b. Media Access Control (MAC) : check the media(for example cable) to avoid collision

            Layer 1 physical layer: we can send these information (1 and zeros) through electric signal, light signals
                                    and remember electricity and light doesn't have direction, so we send these signals
                                    through space, and each system will catch these signals, and when it gets the first 
                                    frame, it will understand from the mac address, is it the right destination or not
                                    (this layer consist of cabling and devices, this devices has NIC(network interface card) or 
                                    external ones like usb or PCI based)


3. Stateful vs stateless applications: 

        

4. TCP and UDP connections: 

        TCP stands for transmission control protocol is used to send a message from one server to another server, for example
        browsers use TCP (Http is based on TCP), or databases uses TCP most of the times.

        pros of using TCP: 

            a. acknowledgment: TCP in order to have acknowledgment, it add additional information to the message that it want
                to send, so when the data recieved, the server will know about the success of the sent proccess.
            
            b. Gauranteed delivery: because it has acknowledgment, if the send process fails, it will resend the message, untill
                the send process is successful
            
            c. connection based: the client and server first need to establish a unique connection between each other, they first
                create stateful connection (maintained on both ends).
            
            d. congestion control: normally in network there are lots of signal that has been sent, so sometimes because of 
                the traffic the message can't be received successfully, TCP has congestion control, it means that, it only
                sends data when the network can handle it
            
            e. Ordered packets: internet does not gaurantee that packets is going to received in ordered, so TCP adds 
                additional information to the message, to preserve the order of the message.
        
        cons in TCP: 
            a. larger packets: we have data for acknowledgment, we have data for Gauranteed delivery and ...

            b. more bandwidth

            c. slower than udp

            d. stateful
            
