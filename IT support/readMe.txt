1. What is IT (information technology):

    The use of digital technology, like computers or internet to store and process data into useful information

2. What is a computer?
    computer is a device that store and process data by performing calculation

3. What is a algorithm?
    It is just a series of steps that solve specific problem

4. What is cryptography?
    is a art of writing and solving codes

5. What id diod and how it works?
                    (P-dope  ----  N-dope) (one side has holes ---- another side has electrons)
    it is silicon with two side, one side in N-dope and another side is P-dope, in the boundry the electron from N-dope migrate to the
    electron to the P-side, so it makes the field at the boundary (negative ---- positive) and the resulting field, will oppose any
    further migration of the electrons

6. Computer language is binary system, and for historical reason we use byte (8 bits) for computer communication

7. character encoding:

    a. The oldest character encoding is ASCII:
        It represent engilish alphabet, digits and punctuation marks

            The great feature of ASCII is that we have to only use 127 out 256 combination that we can have with one byte
        
    
    b. But we need more character, more languages and other things, and we can't fit all of them in 256 possible combination,
        the most prevelant encoding is UTF-8:

            UTF-8 allows us to store characters in more than bytes

8. Binary system:

        a. we use switches for showing 1 or zero in computers.

        b. what if we have two switch for one element?

            the one switch should change another another switch state as well as the lamp.
        
            We have ---logic gates--- for this task.

        c. --logic gates--  are digital version of boolean logic. They normally works at two level voltage, a positive level and zero
            level.

                We have AND logic gates, OR logic gates, NOT logic gates, XOR logic gates, and NAND (not both) logic gates.

9. Abstraction: To take a relatively complex system, and simplify it for use by providing common interface.

10. Computers use multiple layers of abstraction and stack them for the user

11. Computers can be cut into four --main layers--:

        a. hardware

        b. operating system

        c. softwares

        d. users

-------------- This is the hardware part --------------

-------------- CPU ------------------------

12. We give instructions in --binary-- line by line to CPU, and CPU proccess these instructions, and send them back to us.
    but how these instructions travel around the computer?

        we have something called External Data Bus (EDB):

            a. EDB is row of wires that interconnnect the part of the computer. When we send a voltage to one of the wires, 
            we say the state of the wire is on, or represented by a 1. If there's no voltage, then we say that the state is off,
            represented by a 0.

            b. EDBs come in different sizes: 8, 16, 32, and 64 bits.

13. How cpu interact with different parts, specially RAM?

        imagine a 8 bits EDB, our CPU receive data from EDB, and gets to work:

            The CPU talks to --Memory Controll Chip-- through --Address Bus-- and ask for data, MCC takes that data from RAM and sends
            it through EDB to CPU. There are faster way to get data, CPU has --Cache--. Cache use to store recently or 
            frequently data. (L1, L2, L3)

            Inside the CPU there are components that we call --registers--. They stores data that CPU are working with.

            

14. But how does our CPU know when the set of instruction ends, and a new one begins?

        CPU connects to special wire, called clock wire, when we send and receive data, it sends a voltage to that clock wire
        to let the CPU know it can start doing calculations. Think of our clock wires as the ticking of a clock. For every tick,
        the CPU does one cycle of operations

15. Additional resources for Cache in the CPU:

        -Most modern desktop and server CPUs have at least three independent caches:

            a. Data cache: usually this cache organized as a hierarchy of more cache levels (L1, L2, L3, and rarely L4).

            b. Instruction cache: to speed up executable instruction fetch 

            c. Translation Lookaside Buffer (TLB): used to speed up virtual-to-physical address translation for both executable 
                                                    instructions and data, the TLB cache is part of the memory management unit (MMU)
                                                    and not directly related to the CPU caches

        - Data transfered between memeory and cache in fixed sized, we call this --cache lines-- or --cache blocks--, when a 
            cache line copy from memory to CPU, a --cache entry-- will be created. The cache entry will include the copied data as
            well as the requested memory location (called a tag).
        
        - when a processor need to read or write from or to memory, The cache checks for the existence of the requested memory location
            If the proccessor finds the memory location, we have --cache hit--, and if it doesn't find we have --cache miss--.
            In case of cache miss, the proccessor allocate new cache entry and copy the data from the memory.
        
        -- cache hit rate and miss rate affects --cache performance--, --access time to cache-- also affects cache performance.

        -- CPU stalls: when cpu waiting for cache line, CPU will ran out of things to do. we call this state --CPU stall--

            There are two general solution to address CPU stall:

                a. Out of order execution: he CPU attempts to execute independent instructions after the instruction that is 
                    waiting for the cache miss data

                b. simultaneous multithreading (SMT), which allows an alternate thread to use the CPU core while the first thread
                     waits for required CPU resources to become available.

16. Every CPU has instruction set, hard coded in it. these instructions set add functionality like adding, subtracting, and 
    Copying data.


17. When you select your CPU, you need to make sure it is compatible with your motherboard. There are two types of sockets:

        a. Land grid array (LGA): on motherboard pinned out
        b. Pin grid array (PGA): pins are on CPU

-------------------  RAM -----------------

18. There are lots of types of RAM, and the one that is commonly found in computers is DRAM, dynamic random access memory.

19. After DRAM created, SDRAM created (Synchronous DRAM) this type of DRAM synchronized to our system clock speed allowing quicker
    data processing.

20. After SDRAM, double data rate SDRAM was created (DDR SDRM)


---------------- Motherboards --------------

21. The most important carachteristic of motherboard is chipset, most motherboards have two chip:    

        a. northbridge chip that interconnects stuff like RAM and video cards, in some mother board, the northbridge chip is integrated
            in the CPU, so there is no northbridge chip

        b. southbridge chip which maintains our IO controllers.

        c. Expansion slots: expansion slots allow us to increase the functionality of our computer. The standard for expansion slots
            today is PCIe (Peripheral component Interconnect express)
            
            a PCIe bus looks like a slot on the motherboard
            a PCIe base expansion card looks like smaller circuit board

        d. form factor: The form factor is the specification of a motherboard – the dimensions, power supply type, 
            location of mounting holes, number of ports on the back panel, etc. ...

            The most common form factor is ATX (advanced Technology eXtended), ATX has different sizes 

            ITX (Information Technology eXtended) it is much smaller that ATX

-------------- Storages -------------------

22. There are two types of hard drives used today:

        a. Hard disk drives (HDD):  use --spinning platter-- and mechanical arm to read or write information. The speed that platter 
            rotates allows you to read or write data faster. RPM(Revolution per minute)

            This kind of hard drives are more prone to damages, because there are more moving parts.
        
        b. Solid state drives (SSD): SSDs have no moving parts, and data is stored on microchips, 

23. There are few hard drives --interfaces-- that hard drives use to connect to our systems. --ATA-- are the most common, The most 
    common ATA ones are --serial ATA-- or --SATA-- which uses one cable for data trasfer. SATA drives are hot swapable, It means you 
    can add them when the system is running.

24. Using SATA cables are not good for SSD, so the new one is MVM express or MVMe, Instead of using cable, the drive is added as a 
    expansion slot.

----------- Power supplies ---------------

25. Power supply in our computer, convert AC to low voltage DC

---------- Mobile devices ---------------

26. The small mobile devices, usually uses SoC (System on a Chip): Packs the CPU, RAM, and sometimes even the storage in a single chip.


--------- Peripherals ---------------

27. --Peripherals-- are anything that you connect to your computer to extend its functionality

28. USB stands for Universal serial bus

29. The most recent usb connector is --type-C conncetor -, It is used for video, audio, power and data transfer.

29. --DVI connectors-- is just used for video, there is no audio

30. --HDMI connectors-- is used for video and audio

31. --Display port-- is also used for audio and video.

32. How does CPU interpret the inputs from Peripheral devices, for example when you press a keyboad button, your are sending a
    byte to cpu, but cpu doesn't have instruction to handle this byte. but any Peripheral has a program to tell cpu how to run them,
    this programs called --services or drivers--

33. Our CPU does not know about external devices, so it has to connect to something called --BIOS (Basic Input Output services)--
    The BIOS is a software that help initialize the hardware in our computer and get our operating system up and running.
    BIOS does not stored on hard drive, it stored on CMOS 

34. There is alternative for BIOS, --UEFI (Unified Extensible Firmware Interface)--


----------- Operating systems ------------

35. SSH is a protocol implemented by other programs to securely access one computer from another one, to use ssh you need to have 
    --ssh client-- install on one of the computers, and --ssh server-- on another one.

36. to login to another machine with ssh, we need to have a) a account on that computer, and aslo b) host name or ip address of that
    computer.

37. to connect to ssh server on unix machines:   

        ssh <account name>@<ip address or host name>

38. you can connect to ssh server, with password or public-private key. you can lock something with public key, but you can only
    unlock it with private key.

39. you can also connect to another machine, using --VPN (virtual private network)--, VPN allows you to connect to a private networks
    like you work network, with internet.

40. you can use ssh protocol on windows machine using --Putty-- open source software.

---------- Operating system explanation ------------

41. Operating system is the whole package that manage our computer resources and let us to interact with it.

42. each operating system has two part:

            User space:                                 Kernel space:           (interact with computer hardware)
                                                        Processor manager
            Applications                                Memory manager
                                                        File manager
                                                        I/O manager

43. Linux operating system is opensource, so it has manay different ones that developed by different organizations, we call these 
        different linux versions, Linux distributions. (Ubuntu, Debian, red hat)


---------- Files and File systems ---------------

44. There are three components to handling files on OS:

        a. data 

        b. metadata

        c. filesystem


45. Different operating systems, use different file systems:

        windows -> NTFS     (microsoft developing another filesystem called ReFS)

        macOs -> APFS

        linux -> ext4 

--------- Process management --------

46. A important task of kernel is Process management, a --process-- is a program that's --executing-- like our internet browser or 
    text editor.
47. A --program-- is an application that we can run, each program can have many processe, for example you can have many tabs in 
    google chrome

[Very important]
48. To run a process we need to allocate resources (RAM and CPU) to the process, but How does CPU runs multiple process at the same
    time?

    Actually It doesn't, it execute processes one by one, through --time slice--

--------- Memory management --------

49. To increase our ram, we use --Virtual memory--, virtual memory is the combination of the hard drive and RAM that acts like
        a memory that our process can use.

50. The kernel handle the process of taking --pages-- of data and swapping between RAM and virtual memory.

------- I/O management --------

51. Our kernel doesn't just handle the communication of data between OS and devices, it also handles the comminucation of data 
    between devices.

------ Userspace --------

52. There are two ways that users can interact with OS:
        
        a. --shell--: is a program that interprets text commands and sends them to OS to execute.

            The most common shell is --Bash-- (Bourne Again shell) in linux 

        b. --graphical user interface-- 

--------- Logs -----------

53. --Logs-- are files that record system events in our computer.

-------- The process of booting -------

Power on -> BIOS runs Power on self test (POST) -> a boot drive will be selected -> BIOS will find boot loader -> 

    bootloader runs OS -> after OS, kernel will be run -> Essential system processes and user space items will be launched


-------- Basic networking ----------

54. The --internet-- is the physical connection of computers and wires around the world.

55. The --web-- is the information on the internet. The --world wide web-- is not the only way to access --internet--, Email, Chat, 
    and File-Sharing programs are another ways to use --Internet--.


56. We don't connect to internet --directly--, computers that we call --server-- connects directly to internet, servers store the
     websites, that we use.

57. The machine that we use, like our mobile phones, computers called clients. 

[VERY IMOPORTANT]
clients don't connect directly to the internet. Instead they connect to a network run by --Internet Service Provider--. ISPs have 
    already built networks and run all the necessary physical cabling that connects millions of computers together in one network.
    They also connect to other networks and other ISPs. These other networks connect to the networks of Google, Reddit, and 
    universities. Basically, all the other networks in the world, together, they form one giant network of computers called the
    Internet. 

58. Computers on a network have an identifier, called IP address.

59. --Network protocols-- are set of rules for how we transfer data into network.

60. There are two very important protocols in the internet --TCP/IP-- protocols.

        a. --IP protocol--: is responsible for delivering our packets to the right computers.

        b. --TCP--: is a protocol that handles --reliable-- delivery of information from one network to another.

61. There is a very important --web protocol-- called Domain Name System or DNS.

62. There are different version of IP addresses, the current protocol is IPv4 (Internet Protocol Version 4), It is 32 bit protocol,
    
        byte.byte.byte.byte         (73.52.242.3)

63. There is limitation for the number of the possible IP address because of the 4 byte nature of IPv4, so the IPv6 used now days.
        (Internet protocol version 6) IPv6 is 128 bit (16 byte).

64. -- NAT (Network Address Translation): Lets organizations use one public IP address, and many private IP addresses whithin 
        network.

--------------- Trouble shooting ---------

65. Troble shooting is the process of diagnosting and solve the problem.

66. The first thing in trouble --shooting is ask questinos--.

67. The next thing is to --isolating the problem-- to find --the root cause--

68. Another method is --follow the cookie crumb--. It means to go back to the first the problem is started.

69. Always --Start with quickest Step first method--

70. There are three factor for working in IT world:

        a. Passion: the IT world is always changing, so you have to learn all the time. 

        b. Problem solving: You need to have a strategy, and the tools and resources to find the solution.

        c. Communication

71. Great customer service needs:

        a. Exhibiting empathy

        b. Being conscious of your tone

        c. Acknowledging the person

        d. Developing trust


72. Check --bugzila or redmine-- to document your job with issues.

73. Write documentation for all your issues, your documentation must be exact, must have steps, and every one can understand it
    and you have to write --what works and what not works--.

74. In a interview it is good to memorize your elevator pitch:

        a. who your are
        
        b. what kind of career your are looking for

75. During the technical interview, it is okey to say that you are not sure about the answer, but you should say, how will 
    you find the answers, define your strategy to find the answer, and if you have something in your mind, it is ok to share it 
    with the interviewer.

76. When you mentioned concepts or technologies, you should be ready to explain them and articulate why you may choose one thing
    over another

77. It is ok and expected to ask follow up questions from the interviewer, for example if the problem is, the user can't connect
        to the internal systems, you can ask about the operating system that user is using or other things...