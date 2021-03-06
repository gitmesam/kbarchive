---
layout: page
title: "Q138876: New Features in Compaq NT SSD Version 1.16"
permalink: /kb/138/Q138876/
---

## Q138876: New Features in Compaq NT SSD Version 1.16

{% raw %}

	Article: Q138876
	Product(s): Microsoft Windows NT
	Version(s): 3.5,3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The information in this article details changes and updates contained in the
	Compaq Support Software Diskette (SSD), for Windows NT 3.5x, version 1.16. The
	information for this article was taken directly from the NTREADME.HLP file found
	on the SSD.
	
	MORE INFORMATION
	================
	
	The 1.16 release of the Compaq Support Software Diskette for Windows NT 3.5x (NT
	SSD) contains the following new features and maintenance modifications:
	
	New Features in Compaq NT SSD Version 1.16 Pass B
	-------------------------------------------------
	
	Compaq On-Line Recovery Server Option:
	
	New support that provides automated switch over for pairs of Compaq servers
	connected via a serial link. The system is composed of the Compaq ProLiant
	Storage, Recovery Server switch and the On-Line Recovery agent. If one system
	fails, the surviving server detects the failure and causes the switch of the
	drives from the failed server to itself. This feature is listed in the SSD as
	option line-item Compaq On-Line Recovery Server.
	
	New Features in Compaq NT SSD Version 1.16 Pass A
	-------------------------------------------------
	
	Compaq NT SSD Setup:
	
	Added the option line-item Convert to Uniprocessor Support when downgrading from
	a multi to single processor unit.
	
	Added the option line-item Upgrade to Multiprocessor Support when upgrading from
	a single to multiprocessor-processor unit.
	
	Added the option line-item Compaq On-Line Recovery Agent for support.
	
	Compaq HAL Support:
	
	Added new support for the Advanced Program Interrupt Controller (APIC) for dual
	processor support (HALMPS.DLL)
	
	Fixed a problem where the /PRINT option in BOOT.INI can now work with the
	crashdump utility.
	
	Fixed a problem where a time delay was occurring per array controller during
	shutdown with a Compaq Array Controller installed in the system
	
	Added a /MOVEINT BOOT.INI option. (See the Compaq HAL features for more detailed
	information).
	
	Compaq 32-Bit SCSI-2 Controllers SCSI Miniport Driver:
	
	Fixed a problem where the driver was not detecting disabled Compaq 32-Bit
	Fast-Wide SCSI-2 /E controllers.
	
	Updated NCR SCSI processor script code
	
	Additional code and resource optimizations
	
	Compaq ProLiant  Storage System Driver:
	
	Fixed a problem where the device indicator information in the device slot pages
	were not being updated when indicator states changed.
	
	Compaq SCSI Compression/Options Adapter SCSI Miniport Driver:
	
	Removed driver support. Driver supporting this adapter is located on Compaq NT
	SSD Version 1.15 and earlier.
	
	Compaq Systems Management Driver:
	
	Fixed a problem where under heavy stress the system will experience a lock up.
	This problem will only occur on Compaq ProLiant 4000 and ProLiant 4500 installed
	with 4 processors.
	
	Compaq Integrated NetFlex-L Driver:
	
	Modified interrupt routine to be able to see an Apple Talk Network on a Windows
	NT system.
	
	Fixed a problem where the correct maximum lookahead value was not getting
	reported correctly.
	
	Fixed a problem where the All Multicast list was getting overwritten by a request
	to change to receive a specific multicast list.
	
	Compaq NetFlex-2 Driver:
	
	Fixed a problem where the adapter might not initialize because of timeout events
	with assigning interrupts.
	
	Availability:
	
	In addition to being available on the Compaq SmartStart CD, the Compaq NT SSD is
	also available via the following mechanisms. SoftPaq SP1382.EXE is for version
	1.16 of the Compaq NT SSD. Available for download on the Compaq BBS (713)
	378-1418. Available for download on CompuServe. Go CPQFORUM. Available from
	anonymous ftp on the Internet. FTP to ftp.compaq.com. Available on the Compaq
	QuickFind CD, under SoftPaqs (subject to QuickFind CD releases). Available on
	World Wide Web on the Internet at www.compaq.com.
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : :3.5,3.51
	
	=============================================================================
	

{% endraw %}
