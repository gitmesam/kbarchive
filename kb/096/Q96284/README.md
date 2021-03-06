---
layout: page
title: "Q96284: FoxUSER File Contents"
permalink: /kb/096/Q96284/
---

## Q96284: FoxUSER File Contents

{% raw %}

	Article: Q96284
	Product(s): Microsoft Fox Miscellaneous Products
	Version(s): MACINTOSH:2.01
	Operating System(s): 
	Keyword(s): 
	Last Modified: 23-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FoxBASE+ for Macintosh, version 2.01 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The FoxUSER file is a resource file that FoxBASE+/Mac uses to keep track of
	preferences. These preferences include window location (View window, Command
	window, Debug window), colors from the color picker, and preferences for text
	and program files. When viewed as an icon, the FoxUSER file looks like a fox
	head with nuts and bolts.
	
	MORE INFORMATION
	================
	
	The FoxUSER file must be moved into the System Folder after installation. This
	information is not included in the documentation for earlier versions of
	FoxBASE. In the March 1991 documentation and later printings, this requirement
	is noted on page 2-7 of the "User's Guide." If the FoxUSER file is not in the
	System Folder, one of the following problems could occur:
	
	- The "File does not exist" error appears when generating an .SCX file (screen
	  file) while the .SCX file is open.
	
	- The Preferences command on the Edit menu is not highlighted when a text file
	  or .PRG file is open.
	
	- You cannot change data types in MODIFY STRUCTURE. This could also be due to
	  an INIT/CDEV conflict.
	
	- The
	
	  Resource not found
	
	  error occurs when an ALERT command is used.
	
	- The Define and Default Layouts do not appear under Page Layout in the Report
	  Writer.
	
	- The View window and Command window do not appear when the application is
	  first started.
	
	- Your color preferences are not saved and the default preferences are used.
	
	Other resources that can be stored in the FoxUSER file include icons, pictures,
	and XCMDs. If the FoxUSER file has been modified in such a way that one of these
	resources is no longer there (either by reinstalling on top of the FoxUSER file
	or by using an editor such as ResEdit), the error "Resource not found" results.
	In report forms and screen files, a dimmed (grayed) box will appear if the
	resource cannot be found.
	
	A
	
	  Resource not found
	
	error message may occur if the FoxUSER file was not installed correctly; that is,
	if a copy of FoxUSER was dragged off Disk 1 after FoxInstall has run.
	
	Additional query words: 2.01 docerr unavailable out errmsg err msg
	
	======================================================================
	Keywords          :  
	Technology        : kbHWMAC kbOSMAC kbAudDeveloper kbFoxproSearch kbFoxBASE201Mac kbFoxBASESearch
	Version           : MACINTOSH:2.01
	
	=============================================================================
	

{% endraw %}
