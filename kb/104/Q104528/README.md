---
layout: page
title: "Q104528: PC Adm: Microsoft Extraction Utilities Error Messages"
permalink: /kb/104/Q104528/
---

## Q104528: PC Adm: Microsoft Extraction Utilities Error Messages

{% raw %}

	Article: Q104528
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, version 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes error messages produced by the Microsoft LAN Manager and
	Novell Extract utilities that are packaged with version 3.2 of Microsoft Mail
	for PC Networks.
	
	LAN Manager Extract Utility
	---------------------------
	
	The Microsoft LAN Manager Extract utility (LMEXT.EXE) can produce the following
	error messages:
	
	  Error 2: Not enough memory to complete the process.
	
	  There is not enough RAM for the program to complete. This error rarely occurs
	  because the application does not require much memory. Free up additional
	  memory and rerun the application.
	
	  Error 3: Failed to access output file.
	
	  The program could not open the specified output file. Make sure the filename
	  is a valid MS-DOS filename, and there is sufficient disk space available
	  (about 1K should be enough). Also, make sure the specified file is not set to
	  read-only or hidden.
	
	  Error 50: The network request is not supported.
	
	  The named server does not support the user accounts subsystem service
	  requested. The likely cause of this error is that the server is not using
	  user-level security or that the user accounts subsystem service has not been
	  started.
	
	  Error 53: The network path was not found.
	
	  The program could not find or access the named server. Check the validity of
	  the server and make sure sufficient access rights are assigned. To confirm
	  the server, issue the LAN Manager NET VIEW command.
	
	  Error 2138: The workstation service is not started.
	
	  You are trying to run the program on a machine where the LAN Manager
	  Workstation service has not been started. To resolve this problem, start the
	  Workstation service by issuing the NET START WORKSTATION command.
	
	  Error 234: Additional data is available but could not be retrieved.
	
	  There was not enough memory to retrieve all the data the user accounts
	  subsystem could supply. This error commonly occurs when there are more than
	  600 users defined on the server.
	
	  Error nnnn: The process was unable to complete.
	
	  An unspecified error has occurred. Check to verify that the command-line
	  parameters are correct and retry the process.
	
	Novell Extract Utility
	----------------------
	
	The Novell Extract utility (NOVEXT.EXE) can produce the following error
	messages:
	
	  Error 3: Failed to access output file.
	
	  The program could not access the specified output file. Make sure the filename
	  is a valid MS-DOS filename, and that there is sufficient disk space available
	  (about 1K should be enough). Also, make sure the specified file's attributes
	  are not set to read-only or hidden.
	
	  Error 4: The process was unable to access the NetWare server.
	
	  This error occurs when you run the Extract program but you are not attached to
	  a NetWare server.
	
	  Error 5: The process encountered an error while accessing the NetWare
	  Bindery.
	
	  The process was unable to extract the user names from the NetWare Bindery.
	
	Additional query words: LM 2.10 2.20 3.20 3.11 admin
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN320
	Version           : WINDOWS:3.2
	
	=============================================================================
	

{% endraw %}
