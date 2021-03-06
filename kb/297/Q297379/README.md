---
layout: page
title: "Q297379: Programs Can Revert to the Default Settings on Terminal Server"
permalink: /kb/297/Q297379/
---

## Q297379: Programs Can Revert to the Default Settings on Terminal Server

{% raw %}

	Article: Q297379
	Product(s): Microsoft Windows NT
	Version(s): 2000,4.0
	Operating System(s): 
	Keyword(s): kbenv w2000termsrv
	Last Modified: 05-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows 2000 Server 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After a new Terminal Server or Terminal Services server is set up and installed,
	users who log on to the new server may lose their personalized program settings
	(such as Microsoft Office or Microsoft Outlook settings). This behavior is
	caused by the registry compatibility mechanism that is included in Terminal
	Server and Terminal Services in Application Server mode, which reverts the
	settings to the default settings when it detects that the settings on the server
	are newer than those in a user's profile.
	
	CAUSE
	=====
	
	When you install a program on a Terminal Server or a Terminal Services server,
	you typically install the program in Install mode. You use Install mode so that
	changes to the HKEY_CURRENT_USER\Software key are echoed to the
	HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Terminal
	Server\Install\Software key. This area is known as the shadow area. All registry
	keys (not each value) are time stamped; the time for the last write operation in
	Install mode is also stored in the LatestRegistryKey REG_DWORD value in the
	HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Terminal
	Server\Install\IniFile Times key. The value is the number of seconds since
	January 1, 1970.
	
	Similarly, when an .ini file is updated in Install mode, the update time is
	stored in the same key. The write operations to this key set the hidden
	timestamp on the key itself.
	
	When a user logs on in Execute mode, Userinit.exe compares the hidden timestamp
	on this key to the timestamp stored in
	HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\Terminal
	Server\LastUserIniSyncTime. If the hidden timestamp is more recent, new software
	must have been installed on the server (that is, either an .ini file has been
	updated or registry keys have been updated). Userinit then enumerates all the
	keys in the Terminal Server compatibility shadow and compares its hidden
	timestamp to the corresponding key in HKEY_CURRENT_USER\Software. If the shadow
	key is newer, the corresponding key in HKEY_CURRENT_USER\Software is deleted.
	This leverages the registry mapping in Execute mode that reads and applies a
	registry value from the shadow if it is missing in HKEY_CURRENT_USER\Shadow.
	
	This behavior can revert program settings to the default values (the values
	stored in the shadow registry) if, for example, a new server has been built.
	When a user logs on to the new server, it has a very recent timestamp in
	HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Terminal
	Server\Install\IniFile Times. This starts the registry synchronization process,
	deleting user preferences for many programs.
	
	WORKAROUND
	==========
	
	There are several methods to work around this behavior, including:
	
	1. Use Sysprep and "ghost" new servers. This ensures that new servers inherit
	  the registry timestamps from the original build.
	
	2. Write to HKEY_CURRENT_USER\Software in Install mode with the system clock set
	  in the past.
	
	3. Remove shadow keys that could potentially overwrite user preferences.
	
	MORE INFORMATION
	================
	
	Settings that are applied by Group Policy or a system policy typically survive
	the synchronization process because they are time stamped with the current
	system time. However, if Group Policy is not changed, and NoGPOListChanges has
	not been set for the registry extension (the settings are applied only if the
	policy has changed), the issue could still occur.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv w2000termsrv 
	Technology        : kbWinNTsearch kbWinNT400search kbwin2000Serv kbWinNTSsearch kbWinNTS400search kbwin2000ServSearch kbwin2000Search kbNTTermServ400 kbNTTermServSearch
	Version           : :2000,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
