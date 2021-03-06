---
layout: page
title: "Q80393: How to Rebuild the Default Windows REG.DAT File"
permalink: /kb/080/Q80393/
---

## Q80393: How to Rebuild the Default Windows REG.DAT File

{% raw %}

	Article: Q80393
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): win31
	Last Modified: 15-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	- Microsoft Windows for Workgroups versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	During installation of Microsoft Windows, the REG.DAT file is not copied from
	the original distribution disks. Instead, REG.DAT is built using the Windows
	Registration Information Editor (REGEDIT.EXE) and the SETUP.REG file (located in
	the Windows SYSTEM subdirectory) during Setup.
	
	If the REG.DAT file is corrupted, one of the following error messages may be
	displayed:
	
	  File Manager cannot open or print the specified file. Start the application
	  used to create this file, and open or print it from there.
	
	  There is no application associated with this file. Choose Associate from the
	  File menu to create an association.
	
	  There is a problem with REG.DAT. Delete REG.DAT and restart Windows.
	
	  Setup had a problem with REG.DAT, SHELL.DLL or disk space.
	
	  Windows registration database program is not valid
	
	  OLE server initialization failed
	
	  Windows registration database is not valid
	
	  Unable to start the Quick Recorder as an OLE server.
	
	If, for whatever reason, the REG.DAT file is corrupted or deleted, you can
	rebuild the file using the information below.
	
	MORE INFORMATION
	================
	
	The REG.DAT file contains information about file associations and OLE objects.
	The Windows 3.1 Setup program calls the Registration Information Editor to add
	default associations (for Paintbrush, Notepad, and so on) and objects (Packager,
	Paintbrush, and Sound Recorder).
	
	Rebuilding the REG.DAT File for Applications Included with Windows
	------------------------------------------------------------------
	
	You can manually create a new REG.DAT file or restore the defaults by following
	the steps below.
	
	Notes
	-----
	
	- Be sure to rename your existing REG.DAT file before you try to rebuild it.
	
	- These steps assume your Windows directory is on drive C and is named WINDOWS.
	
	1. Run Program Manager or File Manager.
	
	2. From the File menu, choose Run.
	
	3. In the dialog box, type the following:
	
	  regedit /u c:\windows\system\setup.reg
	
	NOTE: A message appears to confirm that the information has been registered. The
	database now contains the original registration information that was installed
	with Windows. To rebuild the REG.DAT file for other applications, see the
	"Rebuilding the REG.DAT File for Other Applications" section below.
	
	4. Choose OK.
	
	  NOTE: You may need to exit and restart Windows in order to see the REG.DAT
	  file displayed in File Manager and execute the following step.
	
	5. In File Manager, select the REG.DAT file found in the Windows program
	  directory, then choose Associate from the File menu and associate Files with
	  Extension: DAT and REG with REGEDIT.EXE.
	
	  NOTE: When you removed the old REG.DAT file, you also removed your file
	  associations list; therefore, you must choose REGEDIT.EXE using the Browse
	  button.
	
	6. Exit and restart Windows.
	
	Rebuilding the REG.DAT File for Other Applications
	--------------------------------------------------
	
	For applications other than the Windows-based programs included with Windows 3.1,
	the technique varies for rebuilding REG.DAT. Some applications, such as
	Microsoft Word 2.0 for Windows, rebuild their entries every time the application
	is started. Other applications may register themselves only during their setup
	processes.
	
	NOTE: If you are using Word 2.0 for Windows, make sure to include the path to the
	Word for Windows program directory and the WW20.REG file located there (for
	example, C:\WINWORD\WW20.REG) so that the registration database is updated.
	
	If the application includes an .REG file, you can add that information to the
	registration database. To do so, use any of the following methods:
	
	- Choose Merge Registration File from the File menu in the Registration
	  Information Editor. Then select the .REG file for the application to be added
	  to the database and choose OK.
	
	  -or-
	
	- Use the same steps described above, substituting the name of the .REG file.
	  Otherwise, consult the application's documentation or contact your vendor for
	  more information about rebuilding the REG.DAT file.
	
	  -or-
	
	- Run Windows File Manager and double-click the application's .REG file.
	
	If you need to rebuild the registration database for all your applications, use
	the following steps:
	
	1. From the File menu in File Manager, choose Search.
	
	2. Search for *.REG from C:\. Ensure that the Search All Subdirectories check
	  box is selected before you choose OK.
	
	3. Run SETUP.REG by double-clicking the file icon or by highlighting it and then
	  pressing ENTER.
	
	4. Run every other .REG file brought up by the File Manager search (just as you
	  did in step 3). Remember to search each available hard disk for .REG files so
	  that every program will be registered in the new REG.DAT file.
	
	For instructions about registering Microsoft Office version 4.x applications,
	query on the following words in the Microsoft Knowledge Base:
	
	  ole and regedit and office
	
	
	Additional information about Registration Information Editor is available in
	Windows 3.1 Help.
	
	REFERENCES
	==========
	
	"Microsoft Windows Resource Kit for Operating System Version 3.1," Chapter 11,
	page 360
	
	Additional query words: gpf
	
	======================================================================
	Keywords          : win31 
	Technology        : kbAudDeveloper kbWin3xSearch kbWFWSearch kbZNotKeyword3 kbWin310 kbWin311 kbWFW310 kbWFW311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
