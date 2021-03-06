---
layout: page
title: "Q158734: SMS: Using Execute.exe to Install Applications"
permalink: /kb/158/Q158734/
---

## Q158734: SMS: Using Execute.exe to Install Applications

{% raw %}

	Article: Q158734
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbtool kbusage kbPCM kbsmsUtil smspcm smsutil
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	Execute.exe is used to run a two-phase Setup program under the Package Command
	Manager (PCM) program of SMS. A two-phase Setup is one that is actually two
	different programs; the first program starts the second one, and then it stops
	itself. When the first program ends, PCM severs its network connection, leaving
	the second program without a network connection.
	
	MORE INFORMATION
	================
	
	Execute.exe runs the command-line for a Windows program, and then polls for its
	end. When it ends, it temporarily pauses, and waits until no window possessing a
	given window title and window class can be found. Use the Spy.exe program
	(distributed with Microsoft Visual C++ 1.5) to determine the Window class and
	title for the second phase of a Setup application.
	
	The Execute.exe program must reside in either the root directory of the package
	share, or the logon server MSTEST directory (logon.srv\MSTEST).
	
	NOTE: Execute is only for 16-bit applications running under Windows 3.1, Windows
	NT, or Windows 95.
	
	The syntax of Execute.exe is:
	
	     Execute.exe "command_line" "window_caption" "window_classname"
	
	where:
	
	- Command_line is the command line to be executed.
	
	- Window_caption is the string to appear in the title bar of the window running
	  command_line.
	
	- Window_classname is the name of a window class.
	
	Either or both of window_caption or window_classname may be blank by specifying
	an empty double quote string (""). Do not omit the quotes even if they are
	empty; the double quotes around each parameter are required syntax.
	
	The following lines are examples of Execute.exe:
	
	     Execute "Setup.exe /B4" "Microsoft PowerPoint" "PPApplicationClass"
	
	  -or-
	
	     Execute "Setup.exe /B4" "" "PPApplicationClass"
	
	Additional query words: prodsms visual basic wizard synchronous asynchronous
	
	======================================================================
	Keywords          : kbtool kbusage kbPCM kbsmsUtil smspcm smsutil 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
