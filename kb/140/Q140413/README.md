---
layout: page
title: "Q140413: Bypassing Display Settings Test During an Unattended Setup"
permalink: /kb/140/Q140413/
---

## Q140413: Bypassing Display Settings Test During an Unattended Setup

{% raw %}

	Article: Q140413
	Product(s): Microsoft Windows NT
	Version(s): 3.5 3.51
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	After the unattended installation of Windows NT is completed and the computer is
	rebooted, the display settings dialog box appears requiring you to test the
	display settings. The display setting test can be bypassed by modifying the
	default SYSTEM hive in the \I386 directory after you copy it from the Windows NT
	3.5 and 3.51 compact disc.
	
	MORE INFORMATION
	================
	
	An unattended installation is run by specifying the /U switch with Winnt.exe or
	Winnt32.exe. For more information, please see the following article(s) in the
	Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q136153
	  TITLE : Using an Answer File for an Unattended Installation
	
	To bypass the display setting test, remove the DETECT value from the default
	SYSTEM hive in \I386 directory after you copy it from the Windows NT 3.5 and
	3.51 compact disc (The registry editor, Regedt32.exe, is required to modify the
	SYSTEM hive.):
	
	WARNING: Modification of the default SYSTEM hive can cause serious, system- wide
	problems before and after Setup and may require you to reinstall Windows NT to
	correct them. Microsoft cannot guarantee that any problems res ulting from the
	modification of SYSTEM registry can be solved. Make the registry modifications
	at your own risk.
	
	1. From the Windows NT 3.5 or 3.51 compact disc, copy the \I386 directory from
	  the CD-ROM to the local directory. For example, if your CD-ROM drive is drive
	  D and the local directory is on C:\NTSETUP, type the following:
	
	  " xcopy d:\i386 c:\ntsetup" (without the quotation marks)
	
	2. Expand System._ in the local directory by typing:
	
	  expand -r system._
	
	3. Rename the System._ file to System.bak.
	
	To load SYSTEM hive into the registry
	-------------------------------------
	
	1. Run the registry editor (Regedt32.exe).
	
	2. From the Registry menu, choose the Load Hive option.
	
	  The Load Hive dialog box appears.
	
	3. In the Drives scrolling list, select the drive which contains the SYSTEM
	  hive.
	
	4. In the Directories option box, choose the directory that contains the SYSTEM
	  hive. The files in this directory now appear in the option box beneath the
	  File Name option box.
	
	5. Choose OK. A second "Load Hive" dialog box appears.
	
	6. In this dialog box, enter SYS_TEMP and Choose OK.
	
	  The SYS_TEMP hive now appears as subkey of the HKEY_USERS and
	  HKEY_LOCAL_MACHINE predefined keys.
	
	7. Click on HKEY_LOCAL_MACHINE window and choose DETECT value in
	  \SYS_TEMP\System\ControlSet01\GraphicDrivers.
	
	8. Remove the DetectDisplay value by pressing the DELETE key.
	
	To unload the SYS_TEMP hive from the Registry
	---------------------------------------------
	
	1. Choose SYS_TEMP hive.
	
	2. From the Registry menu, choose the Unload Hive option.
	
	The SYS_TEMP hive that you have unloaded no longer exists in the registry and it
	is saved as SYSTEM hive in the local directory.
	
	Additional query words: video test inf automate
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : 3.5 3.51
	
	=============================================================================
	

{% endraw %}
