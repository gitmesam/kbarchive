---
layout: page
title: "Q136199: NetWare Programs Fail to Run and Display Error Messages"
permalink: /kb/136/Q136199/
---

## Q136199: NetWare Programs Fail to Run and Display Error Messages

{% raw %}

	Article: Q136199
	Product(s): Microsoft Windows NT
	Version(s): 3.1 3.5 3.51 4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	On your computer running Windows NT, when you try to run a NetWare program using
	Client Services for NetWare (CSNW) or Gateway Services for NetWare (GSNW), your
	NetWare program fails and displays an error message.
	
	The following are examples of common NetWare programs that fail to run and the
	resulting error messages that appear:
	
	  SLIST.EXE:
	
	  Error reading server names (-30719)
	
	  VOLINFO.EXE, SYSCON.EXE, PCONSOLE.EXE, SESSION.EXE:
	
	  You are not logged into file server. You must be logged in to use this
	  utility.
	
	  FCONSOLE.EXE:
	
	  File server is running advanced NetWare version 0.00.0. This utility requires
	  advanced NetWare version 2.10.0 or greater
	
	  CHKVOL.EXE:
	
	  The specific volume not found
	
	  MAP or CAPTURE:
	
	  Warning: Unexpected error 4, error code 8801
	
	  -or-
	
	  Error: unexpected error 0x89ff during <API call name>
	
	CAUSE
	=====
	
	Your network redirector is not loaded.
	
	RESOLUTION
	==========
	
	To solve this problem, load the network redirector before you run the Netware
	program.
	
	The redirector is automatically installed when you install GSNW or CSNW, but is
	not automatically loaded into memory. To load the network redirector
	automatically through your AUTOEXEC.NT file, which is in the
	%SystemRoot%\SYSTEM32 directory, follow the example of this AUTOEXEC.NT file:
	
	@echo off
	break on
	REM AUTOEXEC.BAT is not used to initialize the MS-DOS environment.
	REM AUTOEXEC.NT is used to initialize the MS-DOS environment unless a REM
	different startup file is specified in an application's PIF.
	
	REM Install CD ROM extensions
	lh %SystemRoot%\system32\mscdexnt.exe
	
	REM Install network redirector (load before dosx.exe)
	lh %SystemRoot%\system32\redir
	
	REM Install DPMI support
	lh %SystemRoot%\system32\dosx
	
	REM Install network redirector
	lh %SystemRoot%\system32\nw16
	lh %SystemRoot%\system32\vwipxspx
	
	
	Additional query words: prodnt syscon pconsole filer
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : 3.1 3.5 3.51 4.0
	
	=============================================================================
	

{% endraw %}
