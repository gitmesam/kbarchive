---
layout: page
title: "Q138678: HOWTO: Add &amp; Remove Network Connections in Visual FoxPro"
permalink: /kb/138/Q138678/
---

## Q138678: HOWTO: Add &amp; Remove Network Connections in Visual FoxPro

{% raw %}

	Article: Q138678
	Product(s): Microsoft FoxPro
	Version(s): 
	Operating System(s): 
	Keyword(s): kbnetwork kbvfp300 kbvfp500 kbvfp600
	Last Modified: 09-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Using the Windows API (Application Programming Interface) in conjunction with
	Foxtools.fll in FoxPro for Windows 2.x or DECLARE DLL in Visual FoxPro, you can
	add and remove network connections from within FoxPro.
	
	Although Visual FoxPro still supports the FOXTOOLS library for backward
	compatibility, the DECLARE command is the preferred method for calling DLL
	functions.
	
	MORE INFORMATION
	================
	
	The following sections cover the FoxPro 2.x and Visual FoxPro usage
	conventions.
	
	FoxPro 2.x
	----------
	
	In FoxPro 2.x using the FOXTOOLS library, you need to use the following steps to
	add and remove network connections.
	
	1. Use the following command to establish the library:
	
	     SET LIBRARY TO SYS(2004)+'FOXTOOLS.FLL' ADDITIVE
	
	2. Register the Windows API functions that you need to call. In this case,
	  WNetAddConnection() and WNetCancelConnection().
	
	     addconn=RegFn('WNetAddConnection','CCC','I')
	     delconn=RegFn('WNetCancelConnection','CI','I')
	
	3. To connect to a network device, issue the following command:
	
	     =CallFn(addconn,"\\SERVER\SHARE","password","<drive>:")
	
	4. To disconnect from a network connection, issue the following command:
	
	     =CallFn(delconn,"<drive>:",0)
	
	Visual FoxPro
	-------------
	
	Using the DECLARE DLL functionality, the previous steps can be reduced to the
	following commands:
	
	  **-- Set up API calls
	  Declare integer WNetAddConnection in WIN32API string,string,string
	  Declare integer WNetCancelConnection in WIN32API String,integer
	
	  **-- Add a network connection
	  =WNetAddConnection("\\SERVER\SHARE", "", "DriveLetter:")
	
	  **-- Remove a network connection
	  =WNetCancelConnection("DriveLetter:",0)
	
	The following information provides additional reference material on the two API
	calls used.
	
	WNetAddConnection()
	-------------------
	
	The WNetAddConnection() function redirects the specified local device (either a
	disk drive or a printer port) to the given shared device or remote server. It
	takes the following parameters:
	
	  lpszNetPathName   A pointer to a null-terminated string specifying
	                    the shared device or remote server, such as
	                    \\Server\Share.
	
	                    NOTE: Novell users should not use the double-colon
	                    syntax to reference a server and directory as they may
	                    be accustomed to doing. For example, do not try
	                    referencing a directory using this syntax:
	                    \\server\volume::\mydirectory. Instead, use this
	                    syntax: \\server\volume\mydirectory
	
	  lpszPassword      A pointer to a null-terminated string specifying
	                    the network password for the given device or
	                    server. If there is no password, you must still
	                    include a placeholder, as follows:
	
	                    =CallFn(addconn,"\\SERVER\SHARE","","<drive>:")
	
	  lpszLocalName     A pointer to a null-terminated string specifying
	                    the local drive or device to be redirected. All
	                    lpszLocalName strings (such as LPT1) are
	                    case-independent. Only the drive names A through
	                    Z and the device names LPT1 through LPT3 are
	                    used.
	
	WNetCancelConnection()
	----------------------
	
	The WNetCancelConnection() function cancels a network connection. It takes the
	following parameters:
	
	  lpszName          A pointer to the name of the redirected local
	                    device (such as LPT1: or D:).
	
	  fForce            A Boolean value that specifies whether any open
	                    files or open print jobs on the device should be
	                    closed before the connection is canceled.
	
	REFERENCES
	==========
	
	For more information about the WNetAddConnection() and WNetCancelConnection()
	API calls, please see the Microsoft Windows Software Development Kit (SDK)
	"Programmer's Reference, Volume 2: Functions," which contains information about
	the functions' return values and their meanings.
	
	NOTE: The API call return values will not be interpreted by FoxPro for Windows.
	
	For information about the Visual FoxPro DECLARE method, please see the "DECLARE -
	DLL" Help topic.
	
	Additional query words: DLL API
	
	======================================================================
	Keywords          : kbnetwork kbvfp300 kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP500 kbVFP600
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
