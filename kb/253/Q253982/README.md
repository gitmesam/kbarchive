---
layout: page
title: "Q253982: BUG: MSDN Library Problems with the Windows 2000 MUI"
permalink: /kb/253/Q253982/
---

## Q253982: BUG: MSDN Library Problems with the Windows 2000 MUI

{% raw %}

	Article: Q253982
	Product(s): Microsoft Developer Network
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbHTMLHelp kbMSDN kbOSWin2000 kbVS kbDSupport kbGrpDSTools
	Last Modified: 27-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Developer Network (MSDN) 
	- the operating system: Microsoft Windows 2000 
	- Microsoft Visual Studio 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Several problems can occur when you use the Windows 2000 Multiple User Interface
	(MUI) features with the MSDN Library and Visual Studio 6.0. These problems
	include the following:
	
	- When installing Visual Studio 6.0 or the MSDN Library, Setup displays garbage
	  characters.
	
	- After the installation of the English MSDN Library, you cannot locate the
	  MSDN*.col file.
	
	- The MSDN Library displays garbage characters when started.
	
	- User-defined subset names are not displayed correctly.
	
	CAUSE
	=====
	
	These problems occur when you try to use Multiple User Interface features
	because the MSDN Library and its Setup are not Unicode enabled. Specifically,
	these problems can be traced to the following actions:
	
	- Changing the default system locale or menu and dialogs to a locale different
	  from that of Microsoft Visual Studio 6.0 or the MSDN Library.
	
	- Installing the English version of the MSDN Library to a path containing
	  non-ASCII characters.
	
	- Using non-ASCII characters to save MSDN Library subsets.
	
	RESOLUTION
	==========
	
	When installing or using the MSDN Library or Microsoft Visual Studio 6.0, verify
	that their locale (for example, the Japanese version of either) matches the
	default system locale and the locale for menus and dialogs. To check this for
	the system:
	
	1. On the Start menu, point to Settings, and then click Control Panel.
	
	2. Double-click the Regional Options icon.
	
	3. Click Set default to view or change the current default system locale under
	  Your locale (location).
	
	4. Verify that the setting for Menus and dialogs is to the same locale.
	
	When installing the MSDN Library, chose a destination path containing only ASCII
	characters. When saving a subset, select a name containing only ASCII
	characters.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbHTMLHelp kbMSDN kbOSWin2000 kbVS kbDSupport kbGrpDSTools 
	Technology        : kbOSWin2000 kbVSsearch kbAudDeveloper kbOSWinSearch kbMSDNSearch kbZNotKeyword2 kbVS600 kbVS600Search
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
