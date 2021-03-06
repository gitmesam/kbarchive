---
layout: page
title: "Q102489: Mac Gty: How to Extract and Install Access Gateways"
permalink: /kb/102/Q102489/
---

## Q102489: Mac Gty: How to Extract and Install Access Gateways

{% raw %}

	Article: Q102489
	Product(s): Microsoft Mail For Appletalk Networks
	Version(s): WINDOWS:3.0,3.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for AppleTalk Networks, versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can extract access gateways from version 3.0 or later Microsoft Mail for
	AppleTalk Networks servers that contain a master gateway. The access gateways
	can then be installed on additional servers to allow local users to send
	messages through the master gateway.
	
	To do this, the Network Manager must use the Gateway Installer program (located
	in the Gateways folder included on the Extras Disk, Disk 4).
	
	Notes
	-----
	
	Although it is possible to install the access gateway while you are signed into
	the server from a remote workstation, Microsoft recommends that you run the
	Gateway Installer program on the Macintosh containing the Mail server receiving
	the access gateway.
	
	After you install the access gateway, the master gateway will authorize the
	access gateway server to send mail through the gateway. Any defined gateway
	recipients on the master gateway will automatically be propagated to the access
	server.
	
	Steps to Install the Access Gateway
	-----------------------------------
	
	In the following description, assume that the Mail server containing the master
	gateway is named "Master" and the server receiving the access gateway is named
	"Access."
	
	1. Sign in as the Network Manager of Master.
	
	2. Start the Gateway Installer program.
	
	3. Select the name of the gateway to be extracted from the "Gateways Installed
	  on This Server" window.
	
	4. From the Gateway menu, choose Extract Access Gateway. Use the Save dialog box
	  to save the file to your hard disk drive or to a floppy disk.
	
	5. Transfer the access component file to the mail Server, which will receive the
	  access gateway.
	
	6. Sign in as the Network Manager of Access.
	
	7. Start the Gateway Installer program.
	
	8. From the Access menu, choose Install Access Gateway. When you are prompted
	  for an input file, use the file exported in step 3.
	
	9. Quit the Gateway Installer program.
	
	Additional query words: 3.00 3.10
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailATN300 kbMailATN310
	Version           : WINDOWS:3.0,3.1
	
	=============================================================================
	

{% endraw %}
