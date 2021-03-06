---
layout: page
title: "Q67673: How to Determine When Another Application Has Finished"
permalink: /kb/067/Q67673/
---

## Q67673: How to Determine When Another Application Has Finished

{% raw %}

	Article: Q67673
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.0,3.1
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 05-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Two separate applications sometimes need to cooperate in the Windows
	environment. Two Windows-based applications may work in tandem, or a
	Windows-based application may require the services of a an application that is
	not based on Windows.
	
	This article examines the issues involved when a Windows-based application
	requires notification that another application has completed processing.
	
	MORE INFORMATION
	================
	
	First, the following constraints should be considered:
	
	1. Windows was not designed to synchronize the operation of a Windows-based
	  application with an MS-DOS-based application in any mode (real, standard, or
	  386 enhanced).
	
	2. Windows does not provide any automatic way to determine if another
	  application finished, or ran correctly.
	
	
	This first section included below discusses techniques that can be included in
	code that is written for cooperating applications (for example, when both are
	Windows-based applications and when one is for Windows and the other is not).
	The second section listed below discusses techniques to apply when the other
	application is beyond the programmer's direct influence.
	
	Techniques to Use for Cooperating Applications
	----------------------------------------------
	
	The following are two options that can be used if the programmer is developing
	both applications and each runs under Windows:
	
	1. The two applications can communicate through a dynamic data exchange (DDE)
	  messaging protocol that the programmer establishes.
	
	2. Each application can register the same application-specific message text with
	  Windows via the RegisterWindowMessage() function and receive a numeric value
	  for the message. The terminating application then sends this value to the
	  other application. This can be accomplished by broadcasting the message to
	  all windows in the system. See the documentation for PostMessage().
	
	When one of the cooperating applications that is being developed does not run
	under Windows, the following must occur:
	
	1. When the MS-DOS-based application completes or encounters a fatal error, it
	  should write a message into a specified file in the TEMP directory.
	
	2. The Windows-based application should then perform the following steps:
	
	  a. Use the SetTimer() function to create a system timer that will fire at
	     desired intervals. The estimated completion time of the function is one
	     possible interval. Another would be "estimated time to first possible
	     failure" if the MS-DOS-based application will be writing an error string
	     for the Windows-based application to display.
	
	  b. Initiate the execution of the MS-DOS-based application with the WinExec()
	     function and continue with any normal processing.
	
	  c. Upon receipt of the timer message, the TEMP directory can be checked to
	     determine if a message file is present. If the file is present, the
	     message in the file is parsed to see if termination was due to success or
	     failure.
	
	Techniques to Use for Third-Party Applications
	----------------------------------------------
	
	For a third-party application, the steps taken must access information that is
	entirely external to the MS-DOS-based application. One possible way to implement
	this method is to use the title of the WINOLDAP window to determine if the
	application is still running. In this case, the following steps should be
	taken:
	
	1. Use the SetTimer() function to create a system timer. Timer messages should
	  be at least a few seconds apart. This allows WINOLDAP to create its window
	  and begin processing.
	
	2. In real and standard modes, Windows-based application processing stops while
	  the MS-DOS-based application is processing. In enhanced mode, Windows'
	  behavior depends on the settings in the program information file (PIF) that
	  corresponds with the MS-DOS application. For more information about the
	  allocation of the processor when an MS-DOS-based application is running,
	  query on the following keywords:
	
	  prod(winsdk) and WinExec() and dependent
	
	
	1. When the timer message is received, the FindWindow() function is then used to
	  search for the caption of the MS-DOS-based application's window. The caption
	  is created from the "Window Title" section of its PIF file, or if it is blank
	  or not found, the filename of the old application. If the caption is no
	  longer present, the application is deemed to have completed its processing.
	
	Another possible solution is to create a batch file in MS-DOS that checks for
	error level information returned from the program, and then creates files in the
	TEMP directory. The Windows-based application can then check for these "result"
	files to determine the MS-DOS-based application's status.
	
	The following batch file creates a sentinel file named BEGIN.TMP. Until this file
	is deleted, the MS-DOS-based application is considered to be running. Successful
	completion creates the result file, END.TMP, and then BEGIN.TMP is deleted. An
	execution error creates the result file named STOP.TMP, and then removes
	BEGIN.TMP.
	
	        1:  echo start > %TEMP%\begin.tmp
	       2:  MyDosApp
	       3:  if errorlevel 1 goto bad
	       4:  if errorlevel 0 goto good
	       5:  goto end
	       6:  :bad
	       7:  echo bad > %TEMP%\stop.tmp
	       9:  goto end
	       10: :good
	       11: echo good > %TEMP%\end.tmp
	       12: goto end
	       13: :end
	       14: del begin.tmp
	       15: goto end
	
	A system timer is employed as above to direct the Windows-based application to
	check for the existence of the sentinel and result files.
	
	Additional query words: 3.00 3.10
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : WINDOWS:3.0,3.1
	
	=============================================================================
	

{% endraw %}
