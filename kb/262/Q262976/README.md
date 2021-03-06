---
layout: page
title: "Q262976: PRB: Err Msg &quot;Missing or Not Registered VB6tmpl.tlb&quot; in VB6"
permalink: /kb/262/Q262976/
---

## Q262976: PRB: Err Msg &quot;Missing or Not Registered VB6tmpl.tlb&quot; in VB6

{% raw %}

	Article: Q262976
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbsetup kbVBp kbVBp600bug kbGrpDSO kbDSupport
	Last Modified: 11-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start Visual Basic 6.0 under a new user account or after a new install,
	and you try to run the Visual Basic 6.0 executable file (VB6.exe), you get the
	following error message:
	
	  Visual Basic was not able to start up due to invalid system configuration.
	  Missing or not registered VB6tmpl.tlb.
	
	You are unable to continue and Visual Basic shuts down.
	
	CAUSE
	=====
	
	The main Visual Basic type library is either missing or mis-registered for the
	current user. This message reflects the original working name of this file but
	in released versions of Visual Basic this file was renamed VB6.olb and is
	located in the same directory as the Visual Basic 6.0 executable (VB6.exe).
	
	The registry should contain a path to this file under the following key:
	
	  HKEY_CLASSES_ROOT\TypeLib\{FCFB3D2E-A0FA-1068-A738-08002B3371B5}\6.0\9\win32
	
	If the key is missing or pointing to a location where the file cannot be found,
	Visual Basic returns the preceding error message during startup.
	
	RESOLUTION
	==========
	
	A missing or mis-registered type library key for VB6.olb would indicate an
	improper setup of Visual Basic. Microsoft recommends that you uninstall and
	reinstall Visual Basic.
	
	To ensure proper reinstallation of Visual Basic, uninstall the current product.
	Then proceed to reinstall Visual Basic from the original installation disks. For
	additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q248697 HOWTO: Manually Uninstall Visual Studio with MSDN Library
	
	MORE INFORMATION
	================
	
	To reproduce this error, simply find and rename the VB6.olb file, try to start
	Visual Basic 6.0, and note that the error message appears. Renaming the file
	back to VB6.olb resolves the problem.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsetup kbVBp kbVBp600bug kbGrpDSO kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : :6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
