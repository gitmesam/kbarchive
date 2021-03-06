---
layout: page
title: "Q66989: KbHook.exe Demos Keyboard Hook Function Keyboard Filter"
permalink: /kb/066/Q66989/
---

## Q66989: KbHook.exe Demos Keyboard Hook Function Keyboard Filter

{% raw %}

	Article: Q66989
	Product(s): Microsoft Windows Software Development Kit
	Version(s): 3.0,3.1
	Operating System(s): 
	Keyword(s): kbfile kbsample kbHook kbGrpDSUser kbOSWin310 kbOSWin300 kb16bitonly
	Last Modified: 23-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	KbHook.exe is a file in the Microsoft Download Center that contains sample code
	to demonstrate the installation and use of a system-wide keyboard filter
	function (otherwise known as a keyboard hook function). This code monitors the
	status of the CAPS LOCK key. Whenever the CAPS LOCK key is pressed, its status
	is displayed on the application's icon. Terminating the application removes the
	keyboard filter from the system.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  KbHook.exe
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	NOTE: The KbHook.exe sample uses the SetWindowsHook() function. Applications
	written for Windows 3.1 should use the SetWindowsHookEx() function.
	
	KbHook.exe contains an application program, KEYAPP, and a dynamic-link library
	(DLL), KEYHOOK, that implements the keyboard filter function.
	
	KEYAPP calls KEYHOOK to install the keyboard filter function and then makes
	itself iconic. Windows calls KEYHOOK each time a key is pressed. When the CAPS
	LOCK key is pressed, KEYHOOK posts a message to KEYAPP. KEYAPP processes the
	message by painting its icon to display the current state of CAPS LOCK. When
	KEYAPP is terminated, the KEYHOOK filter is removed from the system.
	
	Because the keyboard filter function is called regardless of the application that
	is currently active, the code must be in memory at all times. When Windows 3.0
	is running in real mode with extended memory, code for inactive applications can
	be placed into extended memory banks that are switched out of memory. Windows's
	memory management scheme is defined so that code in fixed DLLs will remain in
	memory at all times and will remain available for execution.
	
	For more information on the keyboard filter function, see the documentation for
	the SetWindowsHook() function on pages 4-419 through 4-427 in the "Microsoft
	Windows Software Development Kit Reference Volume 1" for the Windows SDK version
	3.0. For additional information on the SetWindowsHookEx() function see pages
	896-899 of "Programmer's Reference, Volume 2: Functions" from the Windows SDK
	version 3.1. The "Microsoft Windows Software Development Kit Guide to
	Programming" provides additional information on DLLs.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbfile kbsample kbHook kbGrpDSUser kbOSWin310 kbOSWin300 kb16bitonly 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : :3.0,3.1
	
	=============================================================================
	

{% endraw %}
