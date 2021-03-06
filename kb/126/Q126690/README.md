---
layout: page
title: "Q126690: INFO: Windows NT 4.0 Setup Troubleshooting Guide"
permalink: /kb/126/Q126690/
---

## Q126690: INFO: Windows NT 4.0 Setup Troubleshooting Guide

{% raw %}

	Article: Q126690
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbsetup kbOPK kbSBKkbfaq
	Last Modified: 14-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	
	     ====================================================
	     Microsoft Windows NT 4.0 Setup Troubleshooting Guide
	     ====================================================
	
	-----------------------------------------------------------------------
	| INFORMATION PROVIDED IN THIS DOCUMENT IS PROVIDED "AS IS" WITHOUT     |
	| WARRANTY  OF ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT |
	| LIMITED TO THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS   |
	| FOR A PARTICULAR PURPOSE. The user assumes the entire risk as to the  |
	| accuracy and the use of this information. This information may be     |
	| copied and distributed subject to the following conditions:           |
	| 1) All text must be copied without modification and all pages must be |
	| included;  2) All components of this information must be distributed  |
	| together; and  3) This information may not be distributed for profit. |
	|                                                                       |
	| Copyright (C) 1995 Microsoft Corporation.  All Rights Reserved.       |
	| Microsoft, MS-DOS, and Windows are registered trademarks and Windows  |
	| NT is a trademark of Microsoft Corporation.                           |
	| COMPAQ is a registered trademark of Compaq Computer Corporation.      |
	| Intel and Pentium are registered trademarks of Intel Corporation.     |
	| MIPS is a registered trademark of MIPS Computer Systems, Inc.         |
	| OS/2, and PS/2 are registered trademarks of International Business    |
	| Machines Corporation.                                                 |
	| Panasonic is a registered trademark of Matsushita Electric Co., Ltd.  |
	| SONY is a registered trademark of Sony Corporation.                   |
	-----------------------------------------------------------------------
	
	Table of Contents
	=================
	
	- Introduction
	
	- Pre-setup and Text-mode Setup Issues
	
	- Setup Failure During Reboot from Character-based to GUI-based Mode
	
	- GUI-Based Setup to First Boot Issues
	
	Introduction
	============
	
	This troubleshooting guide describes how to overcome problems setting up
	Windows NT on Intel architecture (x86) computers. These techniques may
	work for computers that are on the Windows NT Hardware Compatibility List
	(HCL) and for computers that are not on the HCL--that is, not certified by
	Microsoft to be Windows NT compatible.
	
	The HCL is a compilation of computers and computer hardware that have been
	extensively tested with Windows NT for stability and compatibility. It is
	the guide used by Microsoft Product Support Services to determine whether
	or not a computer is supported for use with the Windows NT operating
	system.
	
	If you are setting up a computer that is mission-critical, please see the
	HCL included in the Support folder of the Windows NT compact disc for a
	list of computers that are currently certified by Microsoft to be Windows
	NT compliant. If your computer is not included on the list, contact
	Microsoft for an updated Windows NT HCL.
	
	MICROSOFT DOES NOT MAKE ANY GUARANTEES THAT WINDOWS NT WILL INSTALL OR
	MAINTAIN DATA INTEGRITY AFTER FOLLOWING THE INSTRUCTIONS AND SUGGESTIONS
	CONTAINED HEREIN.
	
	Pre-setup and Text-mode Setup Issues
	====================================
	
	Architecture of Character-based Setup
	-------------------------------------
	
	Detection of Hardware and Hardware Settings:
	
	During the first part of Setup (referred to as character-based Setup),
	Windows NT examines your system architecture for foundation level
	information and drivers. This information includes:
	
	- CPU type (x86, MIPS, ALPHA, or PPC)
	- Motherboard type (PCI, VESA, MCA, EISA, or ISA)
	- Hard disk controllers
	- File systems
	- Free space on hard disks
	- Memory
	
	Windows NT looks for any devices that must be initialized at startup in
	order for your computer to run. Windows NT also constructs a "mini"
	version of Windows NT, which is used to reboot the computer into the
	Graphical User Interface mode (GUI-mode) portion of Setup. Therefore, it
	is critical that the information Windows NT gathers at this point is
	accurate.
	
	Windows NT may incorrectly detect controllers and settings if your
	computer uses nonstandard or proprietary bus components or enhancements
	that do not follow industry standards; these nonstandard enhancements
	include SMP 1.1, PCI 2.1, special bus drivers, or caching chips for burst-
	mode transfer. If the information gathered is incorrect, Setup may not
	work at a later stage. Incorrect detection is often a symptom of a
	hardware or configuration problem that may also cause Setup to stop.
	
	Before You Begin Installation of Windows NT
	-------------------------------------------
	
	HARDWARE:
	
	Windows NT is a 32-bit operating system and is very hardware intensive. In
	MS-DOS and most 16-bit operating systems, hardware is not accessed until
	it is required. Under Windows NT, hardware drivers are written to and
	polled much more heavily for input/output (I/O) instructions. Hardware
	problems that have gone unnoticed or have seemed to be minor under other
	operating systems are likely to be amplified when running under Windows
	NT.
	
	Minimum Hardware Requirements:
	
	  Windows NT Workstation:
	
	   - 12 MB of RAM
	   - VGA level video support
	   - Keyboard
	   - IDE, EIDE, SCSI, or ESDI hard disk
	   - 486/25 processor or better
	   - CD-ROM drive, floppy disk drive, or active network connection
	
	  Windows NT Server:
	
	   - 16 MB of RAM
	   - VGA level video support
	   - Keyboard
	   - IDE, EIDE, SCSI, or ESDI hard disk
	   - 486/25 processor or better
	   - CD-ROM drive, 1.44 MB or 1.2 MB floppy disk drive, or active network
	     connection
	
	  NOTE: On Windows NT Server, 16 MB of RAM affords minimal functionality;
	  Microsoft highly recommends 32 MB of RAM or more. Microsoft also
	  recommends the following preferred hardware:
	
	   - 486DX2/50 processor or better
	   - 28.8 v.34 external modem, for remote debugging and troubleshooting
	   - Windows NT compatible CD-ROM drive
	
	Minimum Space Requirements for Windows NT Workstation and Server:
	
	  Standard Installation                       124 MB of free disk space
	  WINNT /b                                    124 MB of free disk space
	  Copying I386 folder to hard disk            223 MB of free disk space
	
	NOTE: For ease of supportability, Microsoft recommends at least a 1 GB
	file allocation table (FAT) system partition for computers that do not
	require security. This space is used for Windows NT installation,
	pagefile, and MS-DOS 6.22 or Windows 95 installation. The advantage of
	this configuration is the ability to copy over drivers or boot files in
	the event of a virus, file corruption, or upgrade problem.
	Disk Format:
	
	To access a disk from Windows NT, the drive must be uncompressed or
	compressed only with the NTFS file compression included in Windows NT 3.51
	or 4.0. Windows NT is not compatible with Microsoft DoubleSpace, Stacker,
	or any other compression software or hardware. The root folder of the
	Windows NT boot drive cannot be compressed, or an upgrade or installation
	does not succeed.
	
	Windows NT supports only the following EIDE addressing schemes:
	
	- Logical Block Addressing (LBA)
	- ONTrack Disk Manager
	- EZDrive
	- Extended Cylinder Head Sector (ECHS)
	
	NOTE: The high-performance file system (HPFS) is no longer addressable or
	convertible under Windows NT 4.0. If you have an HPFS volume, conversion
	must occur prior to upgrading your computer to Windows NT 4.0. If there is
	no previous version of Windows NT on your computer, and the data on an
	HPFS partition needs to be accessed from Windows NT, you must back up the
	data on the partition and reformat the partition to FAT or NTFS.
	
	If you use one of the above methods, some implementations require special
	partitioning utilities and disk preparation utilities. Do not format these
	drives under Windows NT.
	
	Hardware Configuration Information:
	
	On some computers, Shadow RAM and L2 Write Back Cache cause detection and
	hardware problems, including not responding and STOP error messages. These
	features must be disabled at the BIOS level if you experience any
	problems. Check your computer manual for information about disabling these
	features.
	
	Verify that there are no Power On Self Test (POST) errors prior to
	starting Setup, and make certain that each adapter and peripheral device
	is set to an independent IRQ, memory address, and DMA channel.
	
	In order to successfully install Windows NT, we recommended that you obtain
	the following information:
	
	  Adapter Card      Required information
	  ===============   =====================================================
	  Video             Adapter or chip set type
	  Network Card      IRQ, I/O address, DMA (if used), connector type (BNC,
	                    twisted pair, and so on)
	  SCSI Controller   Adapter model or chipset, IRQ and bus type
	  Mouse             Mouse type, port (COM1, COM2, bus or PS/2)
	  I/O Port          IRQ, I/0 address, DMA (if used) for each I/O port
	  Sound Card        IRQ, I/O address, DMA
	  External Modem    Port connections (COM1, COM2, and so on).
	  Internal Modem    Port connections or IRQ and I/0 address (for non-
	                    standard configurations)
	
	Included on the Windows NT CD-ROM is the NTHQ tool that obtains all of
	the above information in text format. To use the NTHQ tool, follow these
	steps:
	
	1. Go to the \Support\Hqtool folder on the Windows NT CD-ROM.
	
	2. Insert a floppy disk in drive A.
	
	3. Run the MAKEDISK tool.
	
	4. With the disk in the drive, restart the computer.
	
	Also on the Windows NT CD-ROM is the SCSITOOL tool for obtaining SCSI
	information. To use the SCSITOOL tool, follow these steps:
	
	1. Go to the \Support\Scsitool folder on the Windows NT CD-ROM.
	
	2. Insert a floppy disk in drive A.
	
	3. Run the MAKEDISK utility.
	
	4. With the disk in the drive, restart the computer.
	
	This tool currently only supports SCSI adapters from Adaptec and BusLogic.
	
	NOTE: Windows NT currently does not support the following controller and
	BIOS enhancements:
	
	  32 bit I/O BIOS switch
	  Enhanced Drive Access
	  Multiple Block addressing or Rapid IDE
	  Write Back Cache on disk controllers
	  Power Management features
	
	CHOOSING THE CORRECT SETUP METHOD
	---------------------------------
	
	Standard Setup:
	
	Installing directly from the Windows NT CD-ROM or Windows NT boot floppy
	disks is almost always the best method of setting up Windows NT. It offers
	the best support for alternate Hardware Abstraction Layers (HALs), timing,
	and third-party drivers. If you have a supported CD-ROM drive, you should
	choose this setup method.
	
	NOTE: If you lose or misplace the Setup disks required for a standard
	setup, run either WINNT /OX or WINNT32 /OX to create new boot disks for a
	standard setup.
	
	WINNT or WINNT32 Setup:
	
	This method was designed for network installations or for computers with
	unsupported CD-ROM drives. It builds the boot disks and performs a file
	copy of the setup folder to the hard disk before the Setup procedure
	begins. It is the second best choice.
	
	Installing over a Network
	-------------------------
	
	For networks in which the Windows NT installation files are kept on a
	central server, network installations can be accomplished using the WINNT
	command or by copying the entire I386 folder from Windows NT CD-ROM to
	the hard disk and then running WINNT from the local disk. This can reduce
	network traffic and dependency.
	
	NOTE: The method of copying the I386 folder can also be used when there
	are hard disk or driver issues that otherwise block the use of the CD-ROM.
	
	Unsupported Setup Methods
	-------------------------
	
	WINNT /B or WINNT32 /B is used for floppyless setup. It copies the boot
	files to the root folder of drive C and then uses the hard disk as if it
	were the boot disk. If you have timing issues on your computer, such as
	problems accessing the hard disk or similar error messages, this method
	can be used, but WINNT is much more reliable. Please note that this method
	does not work if you are running BIOS-level virus protection.
	
	WINNT /W allows you to set up Windows NT from within Windows, bypassing
	the drive locking and enhanced driver issues involved with setup from
	Microsoft Windows. Again, this bypasses many of the Windows NT Setup
	safety features and is not recommended.
	
	WINNT /U is the command for unattended setup. This can only be used on
	computers in which all the components are standard and no user input is
	required. If there are any problems, Setup stops until the problem is
	resolved.
	
	WINNT /T: or WINNT32 /T: is used for specifying a drive on which temporary
	setup files are placed. If not specified, Setup attempts to locate a drive
	for you, attempting the target drive first, and then the boot drive. If
	neither of these drives is available, Windows NT Setup may not succeed. In
	this case, you should use the /T switch to specify a drive other than the
	target drive or the boot drive.
	
	Viruses
	-------
	
	Windows NT cannot be installed on a computer infected by a virus. This
	troubleshooting guide documents several errors caused by viruses. If your
	computer is infected, please obtain a commercial anti-virus scanner and
	remove the virus prior to attempting Windows NT Setup. Attempting to
	remove a virus using other means can render a computer unbootable.
	
	Troubleshooting: Pre-Setup and Text-Mode Setup Issues
	-----------------------------------------------------
	
	Problem 1:
	
	When I insert the boot disk, I get the following error:
	
	  Operating System not found
	
	Setup does not begin.
	
	Resolution 1:
	
	Check your computer's BIOS to make certain drive A is available as a boot
	drive. If it is and the error still occurs, this is an indication of a
	damaged boot floppy disk or a drive that is out of calibration.
	
	To create new Windows NT Setup boot floppy disks, format three disks on
	the computer on which you are planning to install Windows NT. Then, from
	the CD-ROM I386 folder, type "WINNT /OX" (without the quotation marks).
	This builds a fresh set of Setup floppy disks.
	
	For more information on creating Windows NT Setup boot floppy disks, see
	the following article in the Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q131735
	  TITLE     : How to Create Windows NT Boot Floppy Disks
	
	Problem 2:
	
	After I boot the Setup disk, my computer stops responding, the floppy disk
	drive light stays lit, and Setup does not proceed.
	
	Resolution 2:
	
	This is an indication of a damaged boot disk or a disk controller problem.
	Run WINNT /OX to create new boot floppy disks. If you are using a SCSI
	controller for your floppy disks, make certain that all internal and
	external devices are properly terminated.
	
	Problem 3:
	
	When Setup inspects the hard disk, the following error message appears:
	
	  Setup did not find any hard drives on your computer.
	
	Resolution 3:
	
	Make sure all hard disks are turned on and properly connected to your
	computer. If you are certain the hard disks are properly connected, do the
	following general hard disk troubleshooting to verify your hard disks.
	
	Check for viruses:
	
	Scan the drive for viruses; if the Master Boot Record is infected, Windows
	NT may not see the hard disk properly. Please use a commercial virus
	scanning program to check your hard disk for a virus. Even if the drive is
	formatted using NTFS, the Master Boot Record can become infected.
	
	Verify SCSI Hard Disks:
	
	If the hard disk is a SCSI drive, check the following items:
	
	- Use the SCSITOOL tool on the Windows NT CD-ROM to verify the correct
	  configuration information for your hard disk.
	
	- Is there a valid boot sector on the drive?
	
	- Are all SCSI devices properly terminated?
	
	- If you are using a passive terminator, upgrade to an active terminator.
	
	- Is the BIOS on the boot (initiating) SCSI adapter enabled?
	
	- Are the BIOSes on all non-initiating SCSI adapters disabled? When the
	  BIOS on a non-initiating SCSI adapter is enabled, it can experience an
	  error at startup and/or interfere with hardware interrupt 13 calls to
	  the initiating hard disk controller, resulting in an inability to boot
	  or in random hangs during installation.
	
	- Was the hard disk partitioned and formatted using this SCSI adapter? If
	  not, repartitioning the drive or possibly low-level formatting the
	  drive may be required.
	
	- Verify that your SCSI configuration adheres to the following industry
	  standards for SCSI hard disks:
	
	  Standard    Bit    Cable Pin    Max. x-fer    Max SCSI   Description
	              Width  Name  Count  Rate MB/sec   Devices
	  --------------------------------------------------------------------
	  SCSI-1      8      A     50       5           8          Asynchronous
	  SCSI-2      8      A     50       10          8          Fast
	  SCSI-2      16     A+B   50+68    20          8          Fast+wide **
	  SCSI-2      32     A+B   50+68    40          8          Fast+wide **
	  SCSI-3      8      A     50       10          8          Fast
	  SCSI-3      16     P     68       20          16         Fast+wide *
	  SCSI-3      32     P+Q   68+68    40          32         Fast+wide **
	
	     *  = with 1 cable
	     ** = with 2 cables
	
	  Standard: The name of the SCSI standard as defined by ANSI.
	
	  Bit width: The number of bits that are transferred by the SCSI bus
	  during the data transfer phase.
	  Cable Names: A is most common, P is becoming more popular, A+B is
	  currently not popular due to cost and space issues.
	
	  Pin Count: The number of pins in the cable.
	
	  Max Transfer Rate (MB/sec): Number of bits transferred over the SCSI
	  bus in one second.
	
	  Max SCSI Devices: The maximum number of devices that can be
	  connected to the SCSI bus with one host adapter installed.
	
	  Descriptions
	  ------------
	
	  Asynchronous: A handshaking protocol that requires a handshake for
	                every byte transferred. (Synchronous transfers a
	                series of bytes before handshaking occurs, increasing
	                the data transfer rate.)
	
	  Fast:         Fast SCSI is an option that doubles the synchronous
	                data transfer speed. The speed is achieved by removing
	                excess margins from certain times and delays. To use
	                the fast SCSI option, high quality cables are
	                required. This option is compatible with normal
	                synchronous SCSI and has:
	
	                 - Up to 10 MB/second over an 8 bit bus.
	
	                 - Synchronous data transfer negotiation required.
	
	                 - Single-ended implementation recommendations: m
	                   maximum cable length of 3 meters and active
	                   terminators.
	
	  Wide:         Wide SCSI is an option that adds a second SCSI cable
	                of 68 conductors. This cable provides a data path for
	                16- or 32-bit data. This path has separate handshake
	                signals and is for data transfer only. The transfer
	                rate is two or four times the present transfer rate of
	                SCSI-1. With the second cable, SCSI-2 remains
	                compatible with the 8-bit SCSI.
	
	- With the release of Windows NT version 4.0, drivers for certain SCSI
	  adapters have been moved from the base operating system to the Windows
	  NT Driver Library (in the Drvlib folder) included on the Windows NT
	  version 4.0 CD-ROM. Check the following list to determine if any of
	  your adapters are affected by this change. If your computer has an
	  adapter that appears on this list, you must create a driver disk before
	  installing Windows NT version 4.0. Use this disk to install the
	  appropriate driver(s) during Setup, or keep the disk handy and install
	  the driver using Control Panel once Setup is finished.
	
	  The following drivers have been moved:
	
	     Always.sys
	     Dtc329x.sys
	     T128.sys
	     T13b.sys
	     Tmv1.sys
	     Ultra124.sys
	     Wd33c93.sys
	
	  The following adapters are affected by this change:
	
	     SCSI ADAPTERS:
	
	     Always IN-2000
	     Data Technology Corp. 3290
	     Maynard 16-bit SCSI Adapter
	     MediaVision Pro Audio Spectrum-16
	     Trantor T-128
	     Trantor T-130B
	
	     DISK CONTROLLERS:
	
	     UltraStor 124f EISA Disk Array Controller
	
	  Please see the Windows NT Hardware Compatibility List (HCL) for
	  additional information about these storage adapters. For more
	  information on the Windows NT HCL, see the following article in the
	  Microsoft Knowledge Base:
	
	     ARTICLE-ID: Q131303
	     TITLE     : Latest Windows 2000 and Windows NT Hardware Compatibility List (HCL)
	
	  To create a driver disk for drivers that have been moved to the Driver
	  Library, follow these steps:
	
	  1. Create a blank, formatted 3.5-inch disk.
	
	  2. Copy all files from the following folder to the blank disk:
	
	        Drvlib\Storage\Retired\X86
	
	  3. Label this disk "Drivers Disk."
	
	  To install drivers from the drivers disk during Windows NT version 4.0
	  Setup, follow these steps:
	
	  1. Start Windows NT Setup. During Setup, a message appears stating
	     "Setup has recognized the following mass storage devices in your
	      computer."
	
	  2. When you are prompted, press S to skip detection, then press S again
	     to display a list of supported SCSI host adapters.
	
	  3. Click Other at the bottom of the list.
	
	  4. Insert the Drivers Disk when you are prompted to do so, and click
	     your host adapter from this list.
	
	  Windows NT now recognizes any devices attached to this adapter. Repeat
	  this step for each host adapter not already recognized by Windows NT
	  Setup.
	
	Verify EIDE Hard Disks:
	
	If the hard disk is an EIDE drive, check the following items:
	
	- Verify that the system drive is the first drive on the first IDE
	  controller on the motherboard.
	
	- In the computer's BIOS, verify that file I/O and/or disk access are set
	  to standard. Most computers ship with access set to either 32-bit or
	  enhanced access.
	
	Verify IDE or ESDI Hard Disks:
	
	If the drive is an IDE or ESDI drive, check the following items:
	
	- If possible, verify the controller is functional in a different
	  computer.
	
	- If the drive is larger than 1024 cylinders, make certain you are using
	  a supported disk configuration utility.
	
	- Verify that the drive is jumpered correctly for master, slave, or
	  single drive.
	
	Problem 4:
	
	Setup does not boot and the following error message appears:
	
	  Setup is unable to locate the hard drive partition prepared by
	  the MS-DOS portion of Setup.
	
	  When you run the MS-DOS Windows NT Setup program, you must specify a
	  temporary drive that is supported by Windows NT. See your System
	  Guide for more information.
	
	Resolution 4:
	
	You may be using Windows NT Setup boot floppy disks that were created
	while running the WINNT variation of Setup and you are trying to install
	from a CD-ROM. Create Setup boot floppy disks using WINNT /OX or use the
	original Setup boot disks to install.
	
	Problem 5:
	
	Windows NT displays an error message that there is no valid partition.
	
	Resolution 5:
	
	Make certain you have a valid primary MS-DOS partition on the drive. If
	necessary, you can create a primary MS-DOS partition using Windows NT
	Setup or MS-DOS FDISK.
	
	If the drive was originally formatted for the installation of Windows 95,
	the partition may be marked for the FAT 32 file system. Windows NT 4.0
	does not currently recognize the FAT 32 format and, therefore, does not
	install. If this is the case, you must back up all data and create new
	partitions either from Windows NT 4.0 or from MS-DOS 6.22 in order to
	continue the installation.
	
	For further troubleshooting steps, refer to "Resolution 3" for hard disk
	drive troubleshooting information.
	
	Problem 6:
	
	I cannot choose the option to upgrade my current Windows NT 3.x
	installation.
	
	Resolution 6:
	
	After character-mode Setup is complete, the Setup.log file is deleted from
	the original System32 folder. If Setup stopped in the GUI portion
	of setup and you try to restart Setup from the Setup boot disks or by
	using the WINNT or WINNT32 command, NT does not find the Setup.log file it
	requires for validation of the original NT installation.
	
	If an upgrade stopped during the GUI portion of setup because of a lack of
	disk space or a misconfiguration of hardware, the correct method for
	recovery is to exit Setup and restart the computer; the GUI portion of
	setup automatically restarts. If the GUI portion cannot restart, you need
	to create a parallel installation of Windows NT and restore the Setup.log
	file to the original Windows NT System32 folder from your tape backup. If
	there is no tape backup or you cannot install a parallel copy of Windows
	NT, you must reformat the hard disk if the drive is formatted using NTFS.
	If the drive is formatted as a FAT drive, use an MS-DOS boot disk and
	delete or move files until there is enough room for a reinstallation of
	Windows NT.
	
	Problem 7:
	
	When I try to format the partition, Windows NT stops responding (hangs) at
	X% complete.
	
	Resolution 7:
	
	Make certain your hard disks do not have caching enabled. Set drive
	controllers that have caching capabilities to Write Through, not Write
	Back. If necessary, format the drive to approximately 5-10 MB less than
	the actual size of the partition first chosen.
	
	For further troubleshooting steps, refer to "Resolution 3" for hard disk
	drive troubleshooting information.
	
	Problem 8:
	
	Setup stops responding (hangs) while copying files to the hard disk.
	
	Resolution 8:
	
	This indicates one of two problems:
	
	- The incorrect Hardware Abstraction Layer (HAL) is being loaded.
	
	  Restart Setup. When the "Windows NT is examining your hardware
	  configuration" message appears, press F5. This takes you to a menu with
	  various HALs listed. If you are running Windows NT on a Pentium
	  computer with a single processor, choose the single processor HAL. If
	  you are running Windows NT on a Compaq or Sequent computer using an OEM
	  HAL, choose Other and insert the disk provided by that manufacturer.
	
	- Setup is using reserved memory.
	
	  Disable "Video Shadow RAM" and "32-bit Enhanced File Throughput" in
	  the computer's BIOS.
	
	Character-based to GUI-based Mode Setup Issues
	==============================================
	
	Architecture
	------------
	
	During the reboot from character-based to GUI-based Setup, Windows NT is
	loaded for the first time. Windows NT tries to find a valid hard disk and
	partition, poll the adapters, and test the bus. This is the most likely
	point of failure, when the drivers are loaded into memory and multi-
	threading is initialized.
	
	STOP Messages (Blue Screens)
	----------------------------
	
	Text mode STOP Messages or "blue screens" are used to identify and debug
	hardware and software problems that occur while loading or running Windows
	NT. When a mission critical operating system fails, it is preferable to
	generate an obvious error message, such as the blue screen, rather than to
	simply fail in an "invisible" manner and possibly damage data. The blue
	screen consists of a STOP message, the text translation, the addresses of
	the violating call, and the drivers loaded at the time of the STOP screen.
	The STOP screen gives you and a Microsoft Technical Support Professional the
	necessary information to locate and identify problem areas.
	
	STOP messages indicate where the error has occurred at both the address
	and driver levels; for example:
	
	  *** STOP: 0x0000001E (0xC0000047,0xFA8418B4,0x8025ea21,0xfd6829e8)
	  KMODE_EXCEPTION_NOT_HANDLED c0000047 from fa8418b4 (8025ea21,fd6829e8)
	  *** Address fa8418b4 has base at fa840000 - i8042prt.SYS
	  *** Address 8025ea21 has base at 8025c000 - SCSIPORT.SYS
	
	The STOP message identifies the type of exception, and the exception
	indicates where the problem occurred; that is, whether it was user mode
	(involving user-mode operating system software) or kernel mode (involving
	operating system, third-party drivers, or hardware). The third and fourth
	line describe which components were immediately involved and at what
	addresses.
	
	For example, if the error listed above occurred during Setup, the problem
	might be in the driver that involves the SCSI portion of the operating
	system. If you receive this error during Setup, you should make certain
	the SCSI controller you are using is compatible with Windows NT and that
	the IRQs, SCSI Ids, and termination are correct on the computer. If you
	are sure all of the above are correctly configured, you can try swapping
	out the SCSI controller card for another and try installing again.
	
	For more information on STOP messages, see the Windows NT Resource Kit.
	
	Troubleshooting: Character-based to GUI-based Mode Setup Failures
	-----------------------------------------------------------------
	
	Problem 1:
	
	After removing the third Setup disk from my computer and restarting, a
	blue screen stating "STOP: 0x0000007b Inaccessible Boot Device" appears
	and Setup stops.
	
	Resolution 1:
	
	This indicates a problem accessing the boot disk using the Windows NT
	driver. See "Resolution 3" of Part 1: Troubleshooting: Pre-Setup and Text-
	mode Setup Issues.
	
	Problem 2:
	
	After removing the third Setup disk from the computer and restarting, a
	blue screen with the following error message appears and setup stops:
	
	      Setup has encountered a fatal error that prevents it from
	      continuing.  Contact your software representative for help.  Status
	      code (0x4, 0, 0, 0)
	
	Resolution 2:
	
	This usually indicates the presence of a virus in the Master Boot Record.
	Scan the drive for viruses; if the Master Boot Record is infected, Windows
	NT may not see the hard disk properly. Please use a commercial virus
	scanning program to check your hard disk for a virus. Even if the drive is
	formatted using NTFS, the Master Boot Record can become infected.
	
	Problem 3:
	
	My computer hangs when rebooting into character-based setup.
	
	Resolution 3:
	
	The Windows NT 4.0 CD-ROM is bootable using the El Torrito "no emulation"
	specification. If your computer has the ability to boot from your CD-ROM
	drive, but does not support the "no emulation" mode, remove the Windows NT
	4.0 CD-ROM and restart the computer. Once Windows NT Setup has restarted,
	insert the Windows NT 4.0 CD-ROM.
	
	Problem 4:
	
	Instead of rebooting from text mode into GUI mode, the following error
	message appears:
	
	  NTOSKRNL.EXE is missing or corrupt.
	
	Resolution 4:
	
	If you are installing to a drive other than drive C and the primary drive
	is a FAT drive, edit the Boot.ini file and change the partition
	information. To do so, follow these steps:
	
	1. Remove the Read Only and System File attributes from the Boot.ini file.
	  Type the following command at an MS-DOS command prompt:
	
	     attrib -s -r c:\boot.ini
	
	2. Edit the Boot.ini file and change the partition number for Windows NT.
	  Change the Windows NT line to the following line:
	
	  For IDE drives and SCSI drives attached to a SCSI adapter with its own
	  BIOS:
	
	     multi(0)disk(x)rdisk(0)partition(y)\winnt="Windows NT on ?:"
	
	  For SCSI drives attached to a SCSI adapter without its own BIOS:
	
	     scsi(0)disk(x)rdisk(0)partition(y)\winnt="Windows NT on ?:"
	
	  where x is the drive number, y is the partition number, and ? is the
	  drive letter on which Windows NT resides.
	
	If you are using the Windows NT 4.0 upgrade version CD-ROM, note that the
	upgrade version CD-ROM can be used to upgrade from Windows NT 3.5 or 3.51
	to Windows NT 4.0. You can also use the upgrade version to install Windows
	NT 4.0 into a new folder. The upgrade version cannot be used to upgrade
	or install over Windows NT version 3.1.
	
	However, if the Windows NT 3.1 installation CD-ROM is available, you can
	create a parallel installation of Windows NT 4.0 using the upgrade
	version. If you are using the NTFS file format under Windows NT 3.1,
	please note that these files are no longer accessible from Windows NT 3.1
	after Windows NT 4.0 has been installed because of an alteration in the
	file formatting and translation.
	
	NOTE: To install Windows NT 4.0 over an existing Windows NT 4.0
	installation, only the full retail version can be used.
	
	Problem 5:
	
	During the reboot from text-mode setup to GUI-mode Setup, the following
	error message appears:
	
	  HAL.DLL is missing or corrupt.
	
	Resolution 5:
	
	This error message occurs when a computer that is not listed on the
	Windows NT Hardware Compatibility List (HCL) is using an ASUSTECH (ASUS)
	dual-processor motherboard with only one processor present.
	
	NOTE: The HCL certifies complete systems, not individual motherboards. For
	more information on the HCL, see the following article in the Microsoft
	Knowledge Base:
	
	  ARTICLE-ID: Q131303
	  TITLE     : Latest Windows NT Hardware Compatibility List (HCL)
	
	You can work around this problem by setting the J14 jumper (on the
	motherboard) for a dual-processor computer, even though the computer has
	only one processor.
	
	Problem 6:
	
	When I install Windows NT on a multiprocessor computer, the following
	error message appears:
	
	  HAL: Bad APIC version.
	
	  HAL: This HAL.DLL requires an MPS version 1.1 system. Replace HAL.DLL
	  with the correct HAL for this system. The system is halting.
	
	Resolution 6:
	
	This error message occurs when a computer attempts to boot with a
	symmetric multiprocessing (SMP) HAL on a computer with Multi-Processor
	Specification (MPS) architecture that currently has only a single
	processor.
	
	To work around this problem, use any of the following methods:
	
	- Install Windows NT using the Custom Setup option and verify that the
	  computer type is not identified as an MPS computer. If Setup detects
	  the computer as an MPS computer, change the computer type to AT
	  Compatible.
	
	- Edit the Txtsetup.sif file on the Setup boot disk. In the [HAL] section
	  change the following line:
	
	     mps11_mp    = halmps.dll  ,2,hal.dll
	
	  to:
	
	     mps11_mp    = hal.dll  ,2,hal.dll
	
	  This forces the standard ISA/EISA HAL to be loaded.
	
	- If you are currently running Windows NT 4.0, choose a different kernel
	  and HAL when you boot Windows NT. If a second processor is added later,
	  you may need to manually copy and rename the correct HAL file.
	
	Problem 7:
	
	I need to install other files during the reboot between text-based and GUI-
	based Setup, but cannot catch the Boot menu when Windows NT reboots to GUI-
	mode Setup.
	
	Resolution 7:
	
	Boot from a system disk. If you need to access the previous operating
	system multiple times, boot from the previous operating system and, with a
	text editor, modify the Boot.ini file to pause indefinitely by changing
	the timeout value to "-1". To do so, follow these steps:
	
	1. Remove the Read Only and System File attributes from the Boot.ini file.
	  To do so, type the following command at an MS-DOS command prompt:
	
	     attrib -s -r c:\boot.ini
	
	2. Edit the Boot.ini file and change the timeout line to the following:
	
	     [boot loader]
	     timeout=-1
	
	Problem 8:
	
	An error message appears when restarting into GUI-mode Setup. If the error
	is hardware related, there may be an error message from the BIOS or from
	Windows NT in the form of a blue Stop screen, such as any of the
	following:
	
	  ***STOP 0x00000080
	  NMI_HARDWARE_FAILURE
	
	  ***STOP 0x0000007f
	  UNEXPECTED_KERNEL_MODE_TRAP
	
	  ***STOP 0x0000007a
	  KERNEL_DATA_INPAGE_ERROR
	
	  ***STOP 0x00000077
	  KERNEL_STACK_INPAGE_ERROR
	
	  ***STOP 0x00000051
	  REGISTRY_ERROR
	
	  ***STOP 0x0000002f
	  INSTRUCTION_BUS_ERROR
	
	  ***STOP 0x0000002e
	  DATA_BUS_ERROR
	
	  ***STOP 0x0000002d
	  SCSI_DISK_DRIVER_INTERNAL
	
	Resolution 8:
	
	Check your computer for viruses, or for hard disk damage. For a virus
	scan, please use any available commercial virus scanning software that
	examines the Master Boot Record (MBR) of the drive. Viruses can infect
	both FAT and NTFS file systems.
	
	These errors may also be a result of hard disk drive damage. If you are
	using the FAT file system and do not yet have Windows NT 4.0 installed,
	use Scandisk or another MS-DOS-based hard disk tool to verify the
	integrity of your hard drive. Note that the Scandisk tool can damage long
	file names used by Windows NT 4.0 when run from an MS-DOS prompt.
	
	If you are using the NTFS file system, or you already have Windows NT 4.0
	installed, try to boot to a previous version of Windows NT to run CHKDSK
	/F /R. If you cannot boot to a previous version of Windows NT, try to
	install to a parallel folder to run CHKDSK /F /R.
	
	Another common cause of the above STOP error messages is failing RAM. Use
	a diagnostic tool to test the RAM in your computer.
	
	Check that all adapter cards in your computer are properly seated. You can
	use an ink eraser or Stabilant-22 to clean the adapter card contacts.
	
	Finally, you can take the computer to a repair facility for diagnostic
	testing. A crack, scratched trace, or bad component on the motherboard can
	also cause these problems.
	
	Problem 9:
	
	When restarting from character-based to GUI-based Setup, before or at the
	version screen, either of the following stop codes appear:
	
	  0x0000000A
	  IRQL_NOT_LESS_OR_EQUAL
	
	  0x0000001E
	  KMODE_EXCEPTION_NOT_HANDLED
	
	Resolution 9:
	
	This may indicate the presence of a third-party driver at the system level
	that is incompatible with Windows NT 4.0, or a damaged driver that did not
	get copied correctly during the text-mode portion of Setup.
	
	Try installing Windows NT into an empty folder. If it installs correctly,
	try to access the first folder and replace the damaged file or remove the
	files associated with any suspect third-party drivers.
	
	If you are unable to install Windows NT into an empty folder, check all
	essential hardware, including adapters, drive controllers, and so on. If
	you have nonessential adapters in your computer, remove them and try the
	installation again.
	
	Also verify that the essential hardware in use is Windows NT certified and
	has up-to-date firmware, if applicable.
	
	Problem 10:
	
	After I reboot, the screen stays black or the video is skewed.
	
	Resolution 10:
	
	This problem usually occurs if either the video is not resetting correctly
	during the restart, or the video is sharing an IRQ.
	
	Turn your computer off and then on again. If the video works, you probably
	need to turn off the computer each time you restart Windows NT. This
	problem is video and system BIOS related.
	
	If, after you turn it off, the computer comes back in an unusable state,
	check for IRQ and memory conflicts with other cards in your computer. If
	you are using a PCI-based computer, make certain the video is not using
	IRQs 2, 9, or 12.
	
	To recover from an incorrect video driver or parameter, choose the
	VGA-only mode from the Boot menu and then reconfigure the video display
	driver from the Video tool in Control Panel.
	
	GUI-Based Setup to First Boot Issues
	====================================
	
	Architecture
	------------
	
	During the GUI portion of Setup, Windows NT installs the drivers, creates
	accounts, configures the network settings, and builds the system tree. If
	there are hardware problems or conflicting hardware settings, Windows NT
	probably may not succeed in installing or upgrading.
	
	Problems after the final reboot of Windows NT Setup are normally due to
	incorrect information either in the Boot.ini file or in the hardware
	configuration.
	
	In Windows NT 4.0, the GUI portion of Setup can be restarted. If the
	installation stops because of an incorrect hardware setting or incorrect
	account information, turn the computer off and back on. The GUI portion of
	setup restarts.
	
	Troubleshooting: GUI-based Setup to First Boot Issues
	-----------------------------------------------------
	
	Problem 1:
	
	I receive the following error message during GUI-mode Setup:
	
	  External library procedure NtPathToDosPath reported the following
	  error. 'Unable to open the specified symbolic link object.'
	
	Resolution 1:
	
	This error message indicates that the path to the installation media is no
	longer accessible. This error message occurs when you have added new
	hardware to the computer (for example, a SCSI controller, a SCSI CD-ROM
	drive, or an ATAPI compatible CD-ROM drive) before running Setup, but
	without adding the device drivers in the original Windows NT installation
	first.
	
	When Windows NT Setup reboots the computer to continue GUI-mode Setup,
	Windows NT only finds devices installed under the previous version of
	Windows NT (because you are running in the context of the original Windows
	NT installation.)
	
	To correct this problem, reboot to the original installation if possible,
	and add the appropriate driver.
	
	If no hardware has been added, make certain the hardware is accessible
	under the original version. If the hardware was not supported under the
	previous version, remove the hardware, complete the installation, and add
	the device once Setup has finished.
	
	Problem 2:
	
	When I attempt to install a driver located in the Drvlib folder on the
	Windows NT CD-ROM during GUI-mode Setup, the following error message
	appears:
	
	  NONCRITICAL ERROR
	
	  The external library procedure, CopySingleFile, reported the following
	  error: Unable to do the specified file copy operation.
	
	If I choose to continue (ignoring the error), Setup is not able to
	completely or correctly install the software.
	
	Resolution 2:
	
	This problem occurs when you install Windows NT from an unsupported CD-ROM
	or network drive.
	
	Setup copies the contents of the I386 folder from the Windows NT CD-ROM to
	the local hard disk. When you reach GUI-mode Setup, communication to the
	unsupported media or the network drive is terminated.
	
	To work around this problem, copy the required drivers from the Drvlib
	folder on the Windows NT CD-ROM to the local hard disk or to a floppy
	disk.
	
	Problem 3:
	
	When I start GUI-mode Setup with multiple CD-ROM drives, the following
	message appears:
	
	  Please insert Windows NT Workstation/Server CD-ROM.
	
	Resolution 3:
	
	To set up Windows NT 4.0 on a computer with multiple CD-ROM drives
	installed, use either of the following methods:
	
	- Choose the CD-ROM drive that has first priority. You cannot view which
	  CD-ROM drive has priority on your computer, but you can follow this
	  list of priority:
	
	   - SCSI devices
	   - IDE (ATAPI) devices
	   - Non-SCSI devices in the following order: Sony, Panasonic, Mitsumi
	
	- Place the Windows NT 4.0 CD-ROM in each CD-ROM drive until the CD-ROM
	  drive that has priority on your computer accepts it for copying files.
	
	Problem 4:
	
	I do not want to install a network adapter during the network portion of
	Setup, but I want to install the protocols to preserve bindings and
	settings.
	
	Resolution 4:
	
	This situation might be due to requiring a newer driver for your network
	card, or the use of a third-party driver for Remote Access Service (RAS)
	or server capabilities.
	
	If the computer is only a server or workstation, not a primary or
	secondary domain controller, when you are prompted for a network adapter,
	choose the MS Loopback adapter and proceed with the installation normally.
	Once the computer is operational, you can go back and remove the
	MSLoopback adapter and install the correct adapter or third-party driver.
	
	Problem 5:
	
	Is it important to create an Emergency Repair Disk (ERD) when prompted?
	
	Resolution 5:
	
	Yes. In most cases, an Emergency Repair Disk and a tape backup are your
	primary tools for disaster recovery. If you choose not to create an
	Emergency Repair Disk, you are greatly diminishing the chances of
	recovering your Windows NT installation in the event of hardware or
	software failure.
	
	Problem 6:
	
	During GUI-mode Setup, the computer hangs at random intervals, either
	during file copies or between screens.
	
	Resolution 6:
	
	This usually indicates problems with interrupt (IRQ) conflicts, video, or
	the SCSI bus. To resolve these problems, check the following items:
	
	- Reconfirm the hardware configuration if the problem appears to be
	  hardware interrupt related (for example, you install the network card
	  and the computer stops responding).
	
	- If there are problems with the video after rebooting during an upgrade,
	  try these steps:
	
	  1. Turn the computer off and on, and then try again to boot into GUI-
	     mode Setup.
	
	  2. Modify the Boot.ini file to boot to VGA-only mode during GUI-mode
	     Setup. To do so, follow these steps:
	
	     a. Remove the Read Only and System File attributes from the Boot.ini
	        file. Type the following command at an MS-DOS command prompt:
	
	           attrib -s -r c:\boot.ini
	
	     b. Open the Boot.ini file with a text editor and change the default
	        line to include the "/basevideo" flag.
	
	The information contained in this document represents the current view of
	Microsoft Corporation on the issues discussed as of the date of
	publication. Because Microsoft must respond to changing market conditions,
	it should not be interpreted to be a commitment on the part of Microsoft,
	and Microsoft cannot guarantee the accuracy of any information presented
	after the date of publication.
	
	This document is for informational purposes only.
	MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.
	
	SUMMARY
	=======
	
	
	
	Additional query words: 4.00 prodnt tshoot ntfaqset
	
	======================================================================
	Keywords          : kbsetup kbOPK kbSBK kbfaq
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
