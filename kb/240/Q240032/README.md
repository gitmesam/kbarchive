---
layout: page
title: "Q240032: CG5: Err Msg: Msvcp60.dll Is Linked to the Missing Export Msvcrt"
permalink: /kb/240/Q240032/
---

## Q240032: CG5: Err Msg: Msvcp60.dll Is Linked to the Missing Export Msvcrt

{% raw %}

	Article: Q240032
	Product(s): Microsoft PowerPoint for Windows
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbsetup kbdta
	Last Modified: 24-FEB-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Clip Gallery 5.0 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to start Clip Gallery 5.0, you may receive one of the following
	error messages:
	
	  Msvcp60.dll is linked to the missing export Msvcrt.dll.
	
	  -or-
	
	  Msvcp60.dll is linked to the missing export Msvcrt.dll:lc_collate_cd.
	
	CAUSE
	=====
	
	This behavior can occur if an incorrect version of the Msvcrt.dll file is
	installed on your computer.
	
	RESOLUTION
	==========
	
	To resolve this issue, use one of the following troubleshooting methods.
	
	Repair Office 2000
	------------------
	
	NOTE: Because there are several versions of Windows, the following steps may be
	different on your computer. If they are, please consult your product
	documentation to complete these steps.
	
	Steps to Repair Office 2000
	
	1. Close all programs that are open.
	
	2. Click Start, point to Settings, and then click Control Panel.
	
	3. In Control Panel, double-click the Add/Remove Programs icon.
	
	4. In the Add/Remove Programs Properties dialog box, click your Microsoft Office
	  2000 installation, and then click Add/Remove.
	
	5. In the Microsoft Office 2000 Maintenance Mode dialog box, click Repair
	  Office.
	
	6. In the Reinstall/Repair Microsoft Office 2000 dialog box, click to select
	  "Repair errors in my Office installation", and then click Finish.
	
	7. When the Office Repair is finished, you may be prompted to restart Windows.
	  If you are, click Yes and let Windows restart.
	
	Reinstall the Msvcrt.dll File
	-----------------------------
	
	To reinstall the Msvcrt.dll file, use the appropriate method for your operating
	system.
	
	NOTE: Because there are several versions of Windows, the following steps may be
	different on your computer. If they are, please consult your product
	documentation to complete these steps.
	
	Microsoft Windows NT 4.0, Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition (Me):
	
	To reinstall the Msvcrt.dll file under Windows NT 4.0, Windows 95, Windows 98, or
	Windows Me, follow these steps:
	
	1. Quit all running programs.
	
	2. Rename the Msvcrt.dll file. To do this:
	
	  a. In Windows 95/98 or Windows NT 4, click Start, point to Find, and then
	     click "Files or Folders".
	
	  b. In the Named box on Windows 95/98 or Windows NT 4, type "msvcrt.dll"
	     (without the quotation marks).
	
	  c. In the "Look in" box, click My Computer, and then click Find Now.
	
	  d. In the list of found files, right-click the Msvcrt.dll file, and then
	     click Rename.
	
	  e. Type "msvcrt.old" (without the quotation marks), and then press ENTER.
	
	     NOTE: If you are running any programs that are using the Msvcrt.dll file,
	     you receive the following error message:
	
	  Cannot rename Msvcrt.dll: Access is denied.
	
	  Make sure the disk is not full or write-protected and that the file is not
	  currently in use.
	
	     If you receive this error message, follow these additional steps (f-k),
	     otherwise skip to step 3:
	
	  f. On the Start menu, click Shut Down.
	
	  g. In the Shut Down Windows dialog box, click "Restart in MS-DOS mode" and
	     then click Yes. You should see a blank screen with a command prompt
	     similar to the following:
	
	     c:\windows>
	
	  h. Type the following
	
	  cd system
	
	     and then press ENTER.
	
	  i. Type the following
	
	  ren msvcrt.dll msvcrt.old
	
	     and then press ENTER.
	
	  j. Type the following
	
	  exit
	
	     and then press ENTER. Windows restarts.
	
	  k. If you receive any kind of "error starting program" or "can't find
	     required .dll" error message, click OK to bypass them.
	
	3. Click Start, point to Settings, and then click Control Panel.
	
	4. Double-click the Add/Remove Programs icon.
	
	5. Click the Office 2000 product that you installed on the computer, and then
	  click Add/Remove.
	
	6. In the Microsoft Office 2000 Maintenance Mode dialog box, click Repair
	  Office.
	
	7. Click Reinstall Office, and then click Finish.
	
	Microsoft Windows 2000:
	
	To reinstall the Msvcrt.dll file under Windows 2000, follow these steps:
	
	1. Click Start, point to Programs, point to Accessories, and then click Windows
	  Explorer.
	
	2. Open the following folder in Windows Explorer:
	
	  C:\Winnt\System32\dllcache
	
	  Right-click the Msvcrt.dll file, and then click Rename on the shortcut menu.
	
	3. Type "msvcrt.old" (without the quotation marks), and then press ENTER.
	
	4. Obtain a copy of the Msvcrt.dll file from the Microsoft Office 2000 Service
	  Release 1 (SR-1) CD, or from the administrative installation on your network.
	
	5. Copy the Office 2000 SR-1 version of the Msvcrt.dll file to the
	  C:\WINNT\System32\dllcache folder.
	
	6. Click Start, point to Programs, point to Accessories, and then click Command
	  Prompt.
	
	7. Type the following
	
	  cd system32
	
	  and then press ENTER.
	
	8. Type the following
	
	  ren msvcrt.dll msvcrt.old
	
	  and then press ENTER.
	
	9. Close the Command Prompt window.
	
	  Microsoft Windows 2000 File Protection replaces the missing version of the
	  Msvcrt.dll file with the "backup" from the C:\WINNT\System32\dllcache folder.
	  In this case, that file is the Office 2000 SR-1 version.
	
	10. Restart the computer for the changes to take effect.
	
	Additional query words: 5.00 clipgallery setup Msvcrt dll msvcp60
	
	======================================================================
	Keywords          : kbenv kberrmsg kbsetup kbdta 
	Technology        : kbWordSearch kbFrontPageSearch kbExcelSearch kbPowerPtSearch kbWorksSearch kbPublisherSearch kbClipGallerySearch kbClipGallery500 kbHomePubSearch kbPhotoDrawSearch
	Version           : :5.0
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
