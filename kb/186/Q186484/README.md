---
layout: page
title: "Q186484: Netware Functionality in Terminal Server"
permalink: /kb/186/Q186484/
---

## Q186484: Netware Functionality in Terminal Server

{% raw %}

	Article: Q186484
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Terminal Server adds three new functions to Windows NT Server 4.0's NetWare
	utilities:
	
	- The NetWare option in User Manager under User Config allows password
	  synchronization
	- The NDSPSVR utility allows administrator to set the preferred NDS server
	- The NetWare User Access for Terminal Server utility migrates Novell NetWare
	  accounts to Terminal Server.
	
	MORE INFORMATION
	================
	
	These settings allow you to configure users so that their password will be
	verified against the specified NetWare Server before it is checked on the logon
	domain. If the password on the logon domain is different from the user's NetWare
	password, the user's logon domain password will be updated to match the NetWare
	password.
	
	The NetWare Authentication Server is specific to the selected user(s).
	
	Specify the name of the NetWare Server used to authenticate the user in Server
	Name. Leaving this entry blank disables this feature for the selected user(s).
	
	The domain administrator information is specific to this domain.
	
	In User Name, type the domain administrator account to use when updating user
	domain passwords to match NetWare passwords. This must be an existing account
	with Administrator privileges on this domain.
	
	In Password and Confirm Password, type the domain administrator account's
	password.
	
	NDSPSVR
	-------
	
	Use the Ndspsvr.exe utility to enable and disable a preferred server for NetWare
	Directory Service log on attempts. The use of which is as follows:
	
	NDSPSVR - enable or disable a Preferred Server for NDS log on attempts
	
	[/Q] query current setting
	
	[/ENABLE:fileservername] enable Preferred Server [fileservername]
	
	[/DISABLE] disable Preferred Server
	
	[/?] display help message
	
	For example, to set the preferred server to a NetWare server named NW41SERVER,
	you would type:
	
	  "NDSPSVR /ENABLE:NWSERVER41" (without the quotation marks)
	
	To disable preferred servers for NDS log on attempts, you would type:
	
	  "NDSPSVR /DISABLE" (without the quotation marks)
	
	To determine the name of the preferred server (and whether the NDS preferred
	server is enabled), you would type:
	
	  "NDSPSVR /Q" (without the quotation marks)
	
	Note that this setting is system global; that is, it applies to all users.
	
	NetWare User Access for Terminal Server Utility
	-----------------------------------------------
	
	With this utility, you can migrate users and groups that are part of a NetWare
	4.1 Server's bindery context to the Terminal Server. Migrated user passwords
	will initially be blank.
	
	For this utility to migrate users correctly there must be no password
	restrictions set in User Manager. For instance, not allowing blank passwords or
	setting a minimum password length will cause the user creation to fail. The
	symptom that will reveal this problem is if groups are migrated, but user
	accounts are not.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400 kbNTTermServSearch
	Version           : WinNT:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
