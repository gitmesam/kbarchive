---
layout: page
title: "Q143398: Problems Running Remote Registry and MSNDS"
permalink: /kb/143/Q143398/
---

## Q143398: Problems Running Remote Registry and MSNDS

{% raw %}

	Article: Q143398
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): 3rdpartynet win95 kb3rdPartyNetClient
	Last Modified: 28-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to use the Remote Registry service to remotely administer a
	computer running the Microsoft Service for NetWare Directory Services (MSNDS),
	you may receive one of the following error messages:
	
	- Unable to connect to <computer name>. Make sure that this computer is
	  on the network, has remote administration enabled, and that both computers
	  are running remote registry service.
	
	- Unable to connect to <computer name>. Make sure you have permission to
	  administer the computer.
	
	CAUSE
	=====
	
	These errors can occur if any of the following conditions are true:
	
	- You attempt to use the Remote Registry service while you are logged on to a
	  NetWare Directory Services (NDS) tree, and you are using a server for
	  user-level security that is part of the same NDS tree.
	
	- You are logging on to an NDS tree and your password on the NDS tree is
	  different than the password for your account on the server that is providing
	  user-level security.
	
	- Bindery emulation is not set to the correct container on the NetWare 4.x
	  server you are using for user-level security.
	
	RESOLUTION
	==========
	
	To connect to a remote workstation using the Remote Registry service with MSNDS,
	the following requirements must be met:
	
	- Both workstations must be set up for the Remote Registry service.
	
	- Both workstations must have Remote Administration set up correctly. For
	  additional information, please see the following article in the Microsoft
	  Knowledge Base:
	
	  Q141460 How to Install Remote Administration Services
	
	- User-level security must be installed and set to a bindery-based NetWare
	  server that is not part of the NDS tree. The server can be either a NetWare
	  3.x server or a NetWare 4.x server with bindery emulation set for the
	  container where user accounts reside. This server cannot be a member of the
	  NDS tree you log on to.
	
	- Your password for the NDS tree must be the same as the password on the server
	  you are using for user-level security.
	
	  NOTE: If your password for the user-level security server has been cached, it
	  is possible to use a different password for logging on to the NDS tree.
	
	MORE INFORMATION
	================
	
	The Remote Registry service requires the use of user-level security and is
	currently a bindery-based tool that does not understand NDS. Therefore, the
	server used for user-level security must not be part of the NDS tree you are
	logging on to.
	
	
	======================================================================
	Keywords          : 3rdpartynet win95 kb3rdPartyNetClient 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	
	=============================================================================
	

{% endraw %}
