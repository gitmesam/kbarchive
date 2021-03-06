---
layout: page
title: "Q142238: BUG: Setup /AUTO Fails to Install 32-bit ODBC on Windows NT"
permalink: /kb/142/Q142238/
---

## Q142238: BUG: Setup /AUTO Fails to Install 32-bit ODBC on Windows NT

{% raw %}

	Article: Q142238
	Product(s): Open Database Connectivity (ODBC)
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbSDKODBC kbBug kbISS
	Last Modified: 05-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Open Database Connectivity, version 2.0 
	-------------------------------------------------------------------------------
	
	BUG#: 3191 (ODBCSDK2)
	
	SYMPTOMS
	========
	
	The setup program provided in the ODBC SDK 2.10a fails to install the 32-bit
	ODBC components on Windows NT when the /AUTO switch is used.
	
	WORKAROUND
	==========
	
	- You can modify the setup program by calling SQLConfigDataSource after
	  SQLInstallODBC. For more details on SQLConfigDataSource, please refer to
	  Chapter 24, Installer DLL Function Reference, of the "ODBC 2.0 Programmer's
	  Reference and SDK Guide."
	
	- You can use SQLWritePrivateProfileString, a macro call that calls
	  WritePrivateProfileString in the Windows API, to write a value name and data
	  to the ODBC.INI subkey of the registry. For more details on
	  SQLWritePrivateProfileString, please refer to Chapter 24, Installer DLL
	  Function Reference, of the "ODBC 2.0 Programmer's Reference and SDK Guide."
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the ODBC 2.10a SDK. We are
	researching this problem and will post new information here in the Microsoft
	Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	The Driver Setup Toolkit is included with the ODBC SDK to give developers an
	easy way to include a customized setup program with their deliverable database
	drivers. The toolkit is located in the \ODBCSDK\DRVSETUP.KIT directory and is
	specifically designed to enable developers to customize an ODBC-compatible
	driver setup program.
	
	The driver setup program supports automatic setup. This is useful for multi- user
	environments, where users can set up drivers from a network drive; automatic
	setup provides all users with the same ODBC drivers and data sources. To setup
	automatically, users run the setup program with the /AUTO switch.
	
	For more details, please refer to Chapter 6, Using the Driver Setup Toolkit, of
	the "ODBC 2.0 Programmers Reference and SDK Guide."
	
	The following is an excerpt from the ODBC SDK 2.10 release notes:
	
	Chapter 6: Using the Driver Setup Toolkit (Problems and Information)
	--------------------------------------------------------------------
	
	"Setup /AUTO works on Windows NT as well. However, on Windows NT, you cannot
	configure a standalone system first and get a copy of the ODBC.INI and
	ODBCINST.INI files, as the information for 32-bit setup is in the registry. (See
	step 4 in "To configure a system for automatic setup, the network
	administrator.") You must manually create these files for network installation
	on Windows NT workstations. The file format for ODBC.INI is described in the
	ODBC 2.0 Programmer's Reference. The file format for the ODBCINST.INI file is
	the same for both 16-bit and 32-bit drivers."
	
	However, when you manually create ODBC.INI and ODBCINST.INI files and run
	Setup.exe, you will encounter the following error:
	
	  Setup is unable to install ODBC.
	  C:\~SMPLSTP.T\ODBCINST.INI is either empty or missing.
	
	Actually, Setup.exe creates a temporary directory: C:\~SMPLSTP.T and ODBCINST.INI
	does exist in that directory.
	
	Note that Setup /AUTO has been tested on Windows 95 and does not work on this
	operating system either.
	
	Additional query words: Visual C++ Basic
	
	======================================================================
	Keywords          : kbSDKODBC kbBug kbISS 
	Technology        : kbAudDeveloper kbODBCSearch kbODBC200
	Version           : :2.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
