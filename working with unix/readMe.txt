0. Brief introduction to unix:
  
  a. Unix was originally developed in 1969 by a group of AT&T employees Ken Thompson, Dennis Ritchie, Douglas McIlroy, and
      Joe Ossanna at Bell Labs.

  b. There are various Unix variants available in the market. Solaris Unix, AIX, HP Unix and BSD are a few examples. Linux is also
    a flavor of Unix which is freely available.

  c. Several people can use a Unix computer at the same time; hence Unix is called a multiuser system.

  d. A user can also run multiple programs at the same time; hence Unix is a multitasking environment.

1. The main concept that unites all the versions of Unix is the following four basics:

  a. Kernel: The kernel is the heart of the operating system. It interacts with the hardware and most of the tasks like memory 
      management, task scheduling and file management.

  b. Shell: The shell is the utility that processes your requests. When you type in a command at your terminal, the shell interprets
      the command and calls the program that you want. The shell uses standard syntax for all commands. C Shell, Bourne Shell and 
      Korn Shell are the most famous shells which are available with most of the Unix variants.

  c. Commands and Utilities: There are various commands and utilities which you can make use of in your day to day activities.
      cp, mv, cat and grep, etc. are few examples of commands and utilities. There are over 250 standard commands plus numerous 
      others provided through 3rd party software. All the commands come along with various options.

  d. Files and Directories: All the data of Unix is organized into files. All files are then organized into directories.
      These directories are further organized into a tree-like structure called the filesystem.

2. After you login to your unix machine, you can change your password with --passwd-- command.

3. you can use --whoami-- command to find your username.

4. you have three ways to finds out who is loggin besides you in the unix:

      a. --users-- command

      b. --who-- command

      c. --w-- command

5. you can logout from your unix machine with --logout-- command.

6. you can shutdown your unix machine with this commands (you need to be superuser for shutting down the machine with shell):

      a. --halt--: brings the system down immediatly.

      b. --init 0--: Powers off the system using predefined scripts to synchronize and clean up the system prior to shutting down.

      c. --init 6--: Reboots the system by shutting it down completely and then restarting it

      d. --poweroff--: Shuts down the system by powering off

      e. --reboot--: reboots the system.

      f. --shutdown--: Shutdown the system.

---------- File management in linux -----------

7. before we talk about file management in linux, we should talk about --filesystem--.

8. a) Space management b) metadata c) data encryption d) file access controll e) data integrity are the responsibilities of filesystem.

9. Everything begins with partitioning, Partitioning is done by a disk management tool provided by operating systems, 
    or a as text-based CLI tool provided by the system's --firmware--.

10. For example, a basic Linux installation has three partitions: one partition dedicated to the operating system,
    one partition for user files, and a swap partition.

11. Windows and Mac OS also have similar layout, although they don't use a dedicated swap partition. Instead, they manage swapping
     within the partition the operating system is installed on.
  
12. You have two method to choose for partitioning your device storage (Partitioning schemes):

      a. Master boot record (MBR) scheme

      b. GUID partition table (GPT) scheme

[ATTENTION]
Regardless of what partitioning scheme you choose, the --first few blocks on the storage device-- will always contain critical data
about your partitions. The system's --firmware-- uses these data structures to boot up the operating system.

13. --Firmware-- is a low-level software that programmed into readonly memory to operate the device or bootstrap another 
    program to operate the device.

14. In computers, the --firmware-- provides a standard environment for a complex software like an operating system to boot up and work
    with hardware components. However, on simpler systems like a printer, the firmware is the main operating system of the device.
    The printer menu is the interface of its firmware.

15. Computer firmwares are implemented based on two specifications:
        a. Basic Input/Output (BIOS)
        b. Unified Extensible Firmware Interface (UEFI)

16. The mission of the firmware (among other things) is to boot up the computer, run the operating system, and pass it the control of
    the whole system. A firmware also runs pre-OS environments (with network support), like recovery or diagnostic tools, or even a
    special shell to run text-based commands. The first few screens you see before your operating system's logo appears are the 
    output of your computer's firmware, verifying the health of hardware components and the memory.


-------------- Master Boot Record (MBR) partitioning scheme -------------

17. --MBR partitioning scheme-- is a part of the BIOS specifications, and used by BIOS-based firmwares.

18. On MBR-partitioned disks, the first sector on the storage device contains essential data to boot up the system.
        This sector is called --MBR--.

19. MBR contains the following information: 
        a. The boot loader, which is a simple program (in machine code) to initiate the --first stage-- of the booting process
        b. A partition table, which contains information about your partitions.

20. Booting process in BIOS-based firmware:

    1) Once the system is powered on, the BIOS firmware starts and loads the content of MBR into the memory,
    and runs the boot loader inside it. Having the boot loader and the partition table in a predefined location like MBR, enables
    BIOS to boot up the system without having to deal with any file. 
    
    [ATTENTION]
    The boot loader code in the MBR takes between 434 bytes to 446 bytes of the MBR (out of 512b). 64 bytes is also allocated to
    the partition table for a maximum of four partitions. 446 bytes isn't big enough to accommodate too much code, though. That said,
    sophisticated boot loaders like --GRUB 2 on Linux-- split their functionality into pieces, or stages. The smallest piece, which is 
    known as the first-stage boot loader, sits within the MBR.

    2) The first-stage boot loader initiates the next stages of the booting process.

    [ATTENTION]
    Immediately after the MBR, and before the first partition, there's a small space, around 1MB, called the --MBR gap--. It can be used
    to place another piece of the boot loader, if needed. A boot loader, such as GRUB 2, uses the MBR gap to store another stage
    of its functionality. GRUB calls this the stage 1.5 boot loader, which contains a --file system driver--.

    3) The second stage boot loader, which is now file-system-aware, can load the operating system's boot loader file to boot up
        the operating system.

21. MBR has some limitations:

        a. MBR's data structure limits the number of partitions to only four primary partitions.

        b. Each partition can be maximum of 2TiB.

        c. The content of MBR sector has no back up, meaning if MBR gets corrupted due to an unexpected reason, 
            we'll have a useless storage device.

---------- GUID Partition table (GPT) scheme ---------

22. GPT is a part of UEFI specification.

23. In the GPT partitioning scheme, the first sector of the storage device is reserved for compatibility reasons with BIOS-based
     systems (Protective MBR). This is because some systems might still use a BIOS-based firmware but have a GPT-partitioned 
     storage device.

24. In GPT, all the booting services (boot loaders, boot managers, pre-os environments, and shells) live in a special partition
    called --EFI System Partition (ESP)--, which UEFI firmware can use. ESP even has it own file system, which is a specific version 
    of FAT. On Linux, ESP resides under the /sys/firmware/efi path.

25. Boot process in UEFI:

    a) UEFI-based firmware gets the booting configuration from NVRAM (which is non-volatile RAM). NVRAM contains the booting settings 
        as well as paths to the operating system boot loaders.

    b) UEFI-based firmware assumes that the storage device is partitioned with GPT, and looks up the ESP in the GPT partition table.

    c) Once the EFI partition is found, it looks for the configured boot loader, which is normally a file ending with .efi.

--------- Formating the partion ---------

26. After partitioning, we need to format our partitions.

27. Formatting involves the creation of --various data structures-- and --metadata-- used to manage files within a partition.
    These data structures are one aspect of a file system.

-------- Filesystems ----------

28. A --file system-- is a set of data structures, interfaces, abstractions and APIs that work together to manage any type of 
    file on any type of storage device, in a consistent manner.

29. Architecture of file systems (When people talk about file systems, they refer to one of these layers):

        a. Physical file system:
            The physical layer is the --concrete implementation-- of a file system. It is responsible for data storage and retrieval,
            as well as space management on the storage device.(or more precisely partitions). The physical file system interacts with
            the actual storage hardware, via --device drivers--.

        b. Virtual file system (VFS):
            The virtual file system provides a --consistent view-- of various file systems mounted on the same operating system.
            A VFS defines a contract (interface) that --all physical file systems-- must implement to be supported by the operating 
            system. However, this compliance isn't built into the file system core, meaning the source code of a file system doesn't
            include support for every operating system. Instead it uses a file system driver to adhere to the VFS rules.

            -- VFS is for connection of physical filesystem to operating systems --

        c. Logical file system:

            User programs don't directly interact with the VFS, though. Instead, they use a unified API, which sits between programs
            and the VFS. this API is logical filesystem.
            The logical file system is the user facing part of a file system, which provides an API to enable user programs to
            perform various file operations, such as OPEN, READ, and WRITE , without having to deal with any storage hardware.

30. What does it mean to mount a file system?

    On Unix-like systems, the --VFS assigns a device ID-- (for example dev/disk1s1) to each partition or removable storage device.
    Then, it creates a virtual directory tree and puts the content of each device under that directory tree as separate directories.
    The act of assigning a directory to a storage device (under the root directory tree) is --called mounting--, and the assigned 
    directory is called a --mount point--.

31. --File metadata-- is a data structure, contains data about the file:

        a. File size
        b. Timestamps, like creation date, last accessed date, and modification date
        c. The file's owner
        d. The file's mode (who can do what with the file)
        e. What blocks on the partition are allocated to the file
        --and a lot more

32. Metadata isn’t stored with the file content, though. Instead, it’s stored in a different place on the disk 
    but associated with the file. In --Unix-like systems--, the metadata is in the form of special data structures, called inode.
    --Inodes-- are identified by a unique number called the inode number. Inodes are associated with files in a data structure called 
    inode tables.

33. In an ext4 inode, the address of the allocated blocks is stored as a set of data structures called --extents-- (within the inode).
    Each extent contains the address of the first data block allocated to the file, and the number of the next continuous blocks
    that the file has occupied.

    you can see the inodes:
        df -i

34. you can see the inode unique number that associated with each file using:

        ls -il

[ATTENTION]
The number of inodes on a partition is decided when the partition is formatted. So as long as there's free space and there are unused
inodes, files can be stored on the storage device. It's unlikely that a personal Linux OS would run out of inodes. However, 
enterprise services that deal with a large number of files (like mail servers) have to manage their inode quota smartly.

35. On NTFS, the metadata is stored differently, though. NTFS keeps file information in a special data structure called the 
    --Master File Table (MFT)--. Every file has at least one entry in MFT, which contains everything about the respective file,
    including its location on the storage device - similar to inodes.

36. Storage devices are divided into fixed-sized blocks called --sectors--. A sector is the minimum storage unit on a storage device,
     and is between 512 bytes and 4096 bytes (Advanced Format).

37. file systems use a high-level concept as the storage unit, called --blocks--. Blocks are an abstraction over physical sectors and 
    consist of multiple sectors. Depending on the size of a file, the file system allocates one or more blocks to each file.

38. The file system is aware of every used and unused block on the partitions, so it’ll be able to allocate space to new files or
     fetch the existing ones when requested. 
     
39. The most basic storage unit in ext4-formatted partitions is the block. However, the contiguous blocks are grouped into 
    --block groups-- for easier management.

40. Each --block group-- has its own data structures and data blocks. Here are the data structures a block group can contain:

        a. --Super Block--: a metadata repository, which contains --meta data about the entire file system--, such as total number of
            blocks in the file system, total blocks in block groups, inodes, and more. Not all block groups contain the super block,
            though. A certain number of block groups store a copy of the super as a backup.
        
        b. --Group Descriptors--: Group descriptors also contain bookkeeping information for each block group

        c. --Inode Bitmap--: Each block group has its own inode quota for storing files. A block bitmap is a data structure used
            to identify used and unused inodes within the block group. 1 denotes used and 0 denotes unused inode objects.

        d. --Block Bitmap--: a data structure used to identify used and unused data blocks within the block group. 
            1 denotes used and 0 denotes unused data blocks

        e. --Inode Table--: a data structure which defines the relation of files and their inodes. The number of inodes stored in 
            this area is related to the block size used by the file system.

        f. --Data Blocks--: This is the zone within the block group where file contents are stored.

41. Ext4 file systems even take one step further (comparing to ext3), and organise block groups into a bigger group called flex block
    groups. Each flex box group contains a number block groups. The data structures of each block group, including the block bitmap,
    inode bitmap, and inode table, are concatenated and stored in the first block group within the respective flex block group. Having
    all the data structures concatenated in one block group (the first one) frees up more contiguous data blocks on other block groups
    within each flex block group.
            
---------- Getting started in Linux ----------

42. You can see the calendar in lunx with >>cal

43. You can change password for your current user in linux: 
        >> passwd

44. You can see your current user:

        >> whoami

45. You can see --logged in users--:

        >> users

        or 

        >> who

-------- File management in linux ----------

42. In unix there are 3 types of files:

        a. Ordinary files: An ordinary file is a file on the system that contains data, text, or program instructions. 
            In this tutorial, you look at working with ordinary files.
        
        b. Directories:  Directories store both special and ordinary files. For users familiar with Windows or Mac OS, 
            Unix directories are equivalent to folders.

        c. Special Files: Some special files provide access to hardware such as hard drives, CD-ROM drives, modems, and Ethernet
            adapters. Other special files are similar to aliases or shortcuts and enable you to access a single file using
            different names.

43. Unix commands for file management:

        a. >> ls   lists the files and directories in the current directory

        b. >> ls -l :

            drwx------@  4 mac  staff   128 Jan 21 15:41 Applications

        - First column: Represents the file type and the permission given on the file. Below is the description of all type of files.

        - Second Column − Represents the number of memory blocks taken by the file or directory.

        - Third Column: Represents the owner of the file. This is the Unix user who created this file.

        - Fourth Column: Represents the group of the owner. Every Unix user will have an associated group.

        - Fifth Column: Represents the file size in --bytes--.

        - Sixth Column: Represents the date and the time when this file was created or modified for the last time.

        - Seventh Column: Represents the file or the directory name.

44. different file type in Unix:
    
    - : Regular file, such as an ASCII text file, binary executable, or hard link.
    b : Block special file. Block input/output device file such as a physical hard drive.
    c : Character special file. Raw input/output device file such as a physical hard drive.
    d : Directory file that contains a listing of other files and directories.
    l : Symbolic link file. Links on any regular file.
    p : Named pipe. A mechanism for interprocess communications.
    s : Socket used for interprocess communication.

45. Metacharecter: Metacharecters have special meaning in linux. For example, * means 0 or more character, ? means one character.
    
        >> ls *.txt

46. Hidden files in linux starts with . (dot), Unix programs (like shell) use this files for configuration. to see hidden files use:

        >> ls -a 
47. important hidden files:

        .profile: The Broune shell (sh) initializing script

        .kshrc: The Korn shell (ksh) initialization script

        .cshrc: The C shell (csh) initialization script

        .rhosts: The remote shell configuration file

48. you can use vi editor to create and edit --ordinary files-- in unix based OS:

        >> vi <filename>       (creates the file)

        press i key         (go to edit mode)

        press escape        (go out of edit mode)

        press shif+zz       (go out of vi editor)

    you have to come out of edit mode, then move inside the file:
        
        l key to move right 
        h key to move left
        j key to move down
        k to move up

49. you can see the content of the file:

        cat <filename>

        cat -b <filename>       (see the content with line number)

50. you can see the word count of the file with wc command:

        wc <filename>

        2 19 103 filename               (line count / word count / characters count / filename)

51. Copying files: 

        cp source_file destination_file

52. renaming files:

        mv old_file new_file

53. to remove a file:

        rm filename

        rm -i filename      (ask for are you sure to delete this file)

---------------- Directory management in Linux --------------

54. You can go to home directory anytime you want: 

        >> cd ~

55. go other users home directory:

        >> cd ~username

56. To determine where you are within filesystem hierarchy:

        >> pwd

57. To see files and directories in the directory:

        >> ls directoryname

58. To create a directory:

        >> mkdir directoryname

59. You can use absolute path in making directories:

        >> mkdir /Users/mac/directoryname
    
    If There are not parent directory you will get an error:

        >> mkdir /ghasem/ahmad/ali      (this will give an error)
    
    To make parent directories as well use -p flag:

        >> mkdir -p /ghasem/ahmad/ali

60. to remove directory:

        >> rmdir directoryname

61. To change directory: 

        >> cd directoryname

62. change directory name:

        >> mv old new 

62. dot(.) represent current directory and double dot (..) represent parent directory

--------------  Permission -------------------

63. Every file and directory in Unix has the following attributes:

    a. Owner permissions − The owner's permissions determine what actions the owner of the file can perform on the file.

    b. Group permissions − The group's permissions determine what actions a user, who is a member of the group that a file 
        belongs to, can perform on the file.

    c. Other (world) permissions − The permissions for others indicate what action all other users can perform on the file.

    $ls -l /home/amrood
    -rwxr-xr--  1 amrood   users 1024  Nov 2 00:10  myfile
    drwxr-xr--- 1 amrood   users 1024  Nov 2 00:10  mydir
    
    (first 3 column for owner, second 3 column for group, third 3 column for other permission)

64. You can change permission with --chmod-- in two ways, --symbolic mode-- and the --absolute mode--:

        a. --symbolic mode--:

            u -> owner permission
            g -> group permission
            o -> other permission
            + -> add 
            - -> remove
            = -> set 

            chmod o+wx,u-x,g = rx testfile 

                -> adds write and execute to other permission
                -> removes execute from owner permission 
                -> set group permission to r-x
        
        b. --absolute mode--:

            Octal Permission Representation:

            0 -> no permission 
            1 -> execute permission --x
            2 -> write permission -w-
            3 -> execute(1) + write(2) permission -wx
            4 -> read permission r--
            5 -> read(4) + execute(1) r-x
            6 -> read(4) + write(2) rw-
            7 -> read(4) + write(2) + execute(1) rwx

            chmod 755 testfile  (7 -> owner, 5 -> group, 5 -> other)

65. When you create a user account on unix, it assigns a owner ID and group Id to each user.