---
layout: page
title: "Q183736: How to Administer IIS 3.0 from IIS 4.0 MMC"
permalink: /kb/183/Q183736/
---

## Q183736: How to Administer IIS 3.0 from IIS 4.0 MMC

{% raw %}

	Article: Q183736
	Product(s): Internet Information Server
	Version(s): WINNT:3.0,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 3.0, 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it
	if a problem occurs. For information about how to do this, view the
	"Restoring the Registry" Help topic in Regedit.exe or the "Restoring a
	Registry Key" Help topic in Regedt32.exe.
	
	SUMMARY
	=======
	
	With the Microsoft Management Console (MMC), you can also administer earlier
	versions of Internet Information Server (IIS). For example, if you have five Web
	servers running IIS 3.0 and you initially upgrade one of them to IIS 4.0, you
	can administer all of them from the MMC.
	
	MORE INFORMATION
	================
	
	To do this, follow these steps:
	
	1. Create a temporary folder.
	
	2. From the Windows NT 4.0 CD, copy the following files into the temporary
	  folder you have created:
	
	  Fscfg.dll, W3scfg.dll, and Gscfg.dll from \I386\inetsrv\ directory
	  Fscfg.hlp, W3scfg.hlp, and Gscfg.hlp from \I386\inetsrv\help\ directory
	
	3. Rename the files in the temporary folder. For example:
	
	    Old Name     New Name 
	    ========     ========
	    Fscfg.dll    Fscfg3.dll
	    W3scfg.dll   W3scfg3.dll
	    Gscfg.dll    Gscfg3.dll
	    Fscfg.hlp    Fscfg3.hlp
	    W3scfg.hlp   W3scfg3.hlp
	    Gscfg.hlp    Gscfg3.hlp
	
	NOTE: The Gopher DLL (Gscfg.dll) does not have to be renamed, but this has been
	done for consistency.
	4. Copy the renamed files into your C:\WINNT\system32\inetsrv directory.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems, including
	the failure of a Web site or FTP site, that may require you to reinstall your
	operating system. Microsoft cannot guarantee that problems resulting from the
	incorrect use of Registry Editor can be solved. Use Registry Editor at your own
	risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it.
	5. Add the following registry values (with data type REG_SZ) to
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\InetMgr\Parameters\AddOnServices:
	
	  WWW3 =
	  C:\WINNT\System32\inetsrv\w3scfg3.dll::SUPCFG:C:\WINNT\system32\inetsrv
	  \w3scfg.dll
	
	  FTP3 =
	  C:\WINNT\System32\inetsrv\fscfg3.dll::SUPCFG:C:\WINNT\system32\inetsrv
	  \fscfg.dll
	
	  GOPHER3 = C:\WINNT\System32\inetsrv\gscfg3.dll
	
	6. Connect to a server running IIS 3.0 from the MMC. To do this, follow these
	  steps:
	
	  a. Open the MMC.
	
	  b. Select Internet Information Server.
	
	  c. Click Action, and then click Connect.
	
	  d. Enter the name of the Web server to which you want to connect.
	
	At this point, the Web server can be viewed from the MMC.
	
	The Properties toolbar button in the MMC is not available for down-level sites.
	Instead, you must right-click on the name of the site and select Properties. You
	can also select Properties on the Action menu.
	
	You can also administer IIS 3.0 from the MMC of the Personal Web Server installed
	on Windows NT 4.0 Workstation. The DLLs must still be copied from the Windows NT
	4.0 Server compact disc and renamed. This work around is officially unsupported.
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis400 kbiis300
	Version           : WINNT:3.0,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
