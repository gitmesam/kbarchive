---
layout: page
title: "Q120884: Setup Using SETUP.SHH File with Windows for Workgroups 3.11"
permalink: /kb/120/Q120884/
---

## Q120884: Setup Using SETUP.SHH File with Windows for Workgroups 3.11

{% raw %}

	Article: Q120884
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): WINDOWS:3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 03-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups version 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to run an automated setup using the SETUP /H:<FILENAME>
	command (where <FILENAME> is the name of the SETUP.SHH file used in the
	automated setup) and you specify a network card with the setting
	netcardid=<number>, setup does not work correctly.
	
	NOTES:
	
	- SETUP.SHH is a template that you can modify with a text editor.
	
	- The netcardid=<number> setting is documented in the Windows for
	  Workgroups Resource Kit version 3.1 ( 3-23 through 3-30).
	
	
	WORKAROUND
	==========
	
	To work around this problem:
	
	1. Run the full setup on one machine, and get Windows for Workgroups installed
	  and working properly with the network.
	
	2. Copy the PROTOCOL.INI file to the end of the SETUP.SHH file you are using for
	  the automated setup. Use the following syntax:
	
	  copy setup.shh + c:\windows\protocol.ini <new setup.shh file>
	
	3. Open the SETUP.SHH file and change
	
	  makeprotocol=no
	
	  to:
	
	  makeprotocol=yes
	
	  This line tells the setup program to make a PROTOCOL.INI file with the
	  settings in the SETUP.SHH file and strip whatever is in the [protocol.ini]
	  section.
	
	MORE INFORMATION
	================
	
	The above workaround should succeed if all the machines have identical network
	cards and configurations. If they have different network cards, you must do this
	for each separate network card.
	
	Additional query words: 3.11
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch kbWFW311
	Version           : WINDOWS:3.11
	
	=============================================================================
	

{% endraw %}
