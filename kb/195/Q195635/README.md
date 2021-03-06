---
layout: page
title: "Q195635: Install /S100 Series Compaq Switched SCSI Cluster"
permalink: /kb/195/Q195635/
---

## Q195635: Install /S100 Series Compaq Switched SCSI Cluster

{% raw %}

	Article: Q195635
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-AUG-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Cluster Server 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Compaq cluster model S/100 uses existing technology and proprietary software
	to implement Microsoft Cluster Server using Smart Array controllers and the
	Compaq Recovery Server Option (RSO) switch. Standard installation procedures for
	Microsoft Cluster Server do not apply to these configurations.
	
	The cables to the arrays and slots for the controllers must be configured
	properly according to the accompanying Compaq documents. Please contact Compaq
	support and reference the S/100 Shared SCSI/RAID Storage - Compaq ProLiant
	Storage System with Compaq Recovery Server Option. This article describes brief
	installation steps and some suggested tuning enhancement based on experience
	with the product, and some suggested changes by Compaq support. While this
	article contains suggestions to avoid previously experienced issues, if you
	implement the suggestions from this article while following the manufacturer
	supplied installation steps and continue to experience problems, you may need to
	contact Compaq support for further assistance.
	
	MORE INFORMATION
	================
	
	Before installing the S/100 cluster, please check the following items to ensure
	correctness:
	
	- Make sure the Recovery Server Option (RSO) firmware is suitable for
	  clustering.
	
	- Check the computer's BIOS and ensure proper revision level for the server.
	
	- Make sure installed adapters are balanced between PCI buses according to the
	  Compaq whitepaper on bus balancing. (This is not mandatory but may help
	  performance under load.)
	
	- Check IRQ assignments. If you have the opportunity to assign separate
	  interrupts to each installed adapter, do so. If the COM ports are not in use
	  and the additional interrupts would help accomplish this configuration, then
	  do so. Otherwise, if you must share interrupts, only share them with similar
	  devices. Based on experience with this configuration, we suggest having disk
	  controllers share interrupts and each network port have a separate interrupt.
	
	- Obtain current drivers for your network adapters. If using any Netflex-3 or
	  "Compaq Netelligent TX 10/100" adapters that use the TLAN chipset, obtain the
	  driver update noted in SP11377. You can also use a Compaq SSD version that
	  contains this driver update or later revision. This update is not just for
	  adapter teaming but helps avoid some possible issues with these adapters in
	  some configurations.
	
	- Obtain the latest installation software for the S/100 from Compaq. The
	  initial release was 1.0. There have been a few updates since then. You should
	  use 1.01a or later update if available.
	
	- Read the release notes for the Compaq software version you are using. In the
	  notes ther is a suggestion about putting each TCP/IP address resource in a
	  separate resource monitor. While in some configurations this may increase
	  performance, in others it may create excessive overhead by having many
	  resource monitor processes. Previous issues have shown that placing the
	  Compaq S/100 disk resources in their own resource monitor achieves similar
	  goals and can prevent failover problems in some configurations. Make this
	  change after installation of the complete cluster; or after installation of
	  the first node.
	
	- Ensure array cables are attached according to the Compaq manual, and to array
	  controllers located in the same slot number on each server. Beware of
	  possible issues with dual ported controllers, as cabinets attached to dual
	  ported controllers will both failover together, not independently.
	
	- Ensure matching firmware on controllers attached to the same array cabinet.
	  Check firmware revisions on the controllers in the event that they are out of
	  date.
	
	The installation procedure for the S/100 consists of the following basic steps
	that must be performed using the installation software provided by Compaq which
	also prompts for the Windows NT Server 4.0 Enterprise Edition CD. For best
	results, consult the Compaq S/100 Cluster manual as well. The basic steps to
	install the S/100 cluster are:
	
	1. Install Windows NT Server 4.0, Enterprise Edition.
	
	2. Install Windows NT Server 4.0 Service Pack 6a.
	
	3. Install the latest Software Support Diskette (SSD) from Compaq for the S/100
	  hardware.
	
	4. Choose drive letters for any attached arrays for cluster use. Make sure the
	  same drive letters are available on the second node for these same devices.
	  Do not allocate these drive letters to mapped network drives, CD-ROM drives,
	  or other devices.
	
	5. Install Compaq S/100 proprietary software.
	
	6. Insert the correct disk when the S/100 installation prompts you for Windows
	  NT 4.0, Enterprise Edition disk 2.
	
	7. Choose disk resources to be managed by the cluster through the S/100 drivers.
	
	8. When you restart the computer, the S/100 installation scans the resources.
	
	9. Follow steps 1 through 5 on the second node to join the existing cluster.
	
	NOTE: If you do not have the Compaq S/100 proprietary software, the shared arrays
	may not be visible as choices and the cluster installation may not work
	properly. Also, if you notice that the disk resources created are of type
	"Physical Disk" then this may be an indication that the Compaq software has not
	been used. Also, if using Windows NT 4.0 Service Pack 4 (or a later version), be
	sure to reapply the service pack after installing the cluster software.
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: Cleo switched scsi recovery option mscs
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400xsearch kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400xsearch kbAudDeveloper kbClustServSearch
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
