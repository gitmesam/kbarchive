---
layout: page
title: "Q117767: ADT2: &quot;Error Occurred in WriteSTF&quot; Error Msg in Setup Wizard"
permalink: /kb/117/Q117767/
---

## Q117767: ADT2: &quot;Error Occurred in WriteSTF&quot; Error Msg in Setup Wizard

{% raw %}

	Article: Q117767
	Product(s): Microsoft Access Distribution Kit
	Version(s): WINDOWS:2.0
	Operating System(s): 
	Keyword(s): kberrmsg kbsetup
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Access Developer's Toolkit, version 2.0 
	-------------------------------------------------------------------------------
	
	Moderate: Requires basic macro, coding, and interoperability skills.
	
	SYMPTOMS
	========
	
	When you run the Microsoft Access Developer's Toolkit version 2.0 Setup Wizard,
	you may receive the following error message when the Setup Wizard creates the
	disk images:
	
	  Error occurred in WriteSTF
	
	CAUSE
	=====
	
	This error message can occur if any of the files you included with your
	application has a name that contains an apostrophe (') or an ampersand (&).
	This error message may also occur if the swu2016.dll file is missing from the
	Microsoft Access folder.
	
	NOTE: The swu2016.dll file is copied to the Access directory when you install the
	ADT on any computer.
	
	
	RESOLUTION
	==========
	
	Rename the file that has an apostrophe in its name to a new name that does not
	contain an apostrophe or make sure the swu2016.dll file is in the Microsoft
	Access folder, and then run the Setup Wizard again.
	
	STATUS
	======
	
	This behavior no longer occurs in the Microsoft Access Developer's Toolkit for
	Windows 95 version 7.0.
	
	MORE INFORMATION
	================
	
	After you see the "Error occurred in WriteSTF" error message, the following
	error message will appear:
	
	  File '<disk-image path>\Disk1\setup.stf' is opened for exclusive access
	  by another application.
	
	Although the Setup Wizard will seem to finish successfully, the Setup disks that
	are created will not work correctly. When you try to install your application
	from these Setup disks, you will receive the following error message, and then
	Setup will terminate:
	
	  Object ID 23: Group Object: Bad Data Value.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Use any text editor (such as Windows Notepad) to create a text file with the
	  name TEST'1.TXT. (Note the apostrophe in the file name.)
	
	2. Start the Setup Wizard. In the Files To Include box, include only the
	  TEST'1.TXT file, and then choose Next.
	
	3. In the Available Options box, do not select any options. Choose Next.
	
	4. In the Application Name box, type "TestIt" (without quotation marks). In the
	  Default Installation Directory box, type "C:\TESTIT" (without quotation
	  marks). Choose Next.
	
	5. Do not type anything in the Executable File Name box or the Command Line box.
	  Choose Next.
	
	6. In the Application Setup Directory box, type "C:\SETUP" (without quotation
	  marks). Select the Network Setup (Flat) option button. Choose Finish. Note
	  that the error messages appear.
	
	REFERENCES
	==========
	
	Microsoft Access Developer's Toolkit "Advanced Topics," version 2.0, Chapter 2,
	"Creating a Custom Setup Program"
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbsetup 
	Technology        : kbAudDeveloper kbAccessSearch kbAccessDevTK200 kbZNotKeyword3
	Version           : WINDOWS:2.0
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
