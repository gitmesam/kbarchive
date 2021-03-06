---
layout: page
title: "Q70144: DOCERR: PWB Error Messages Not Included in C 6.0 Help Files"
permalink: /kb/070/Q70144/
---

## Q70144: DOCERR: PWB Error Messages Not Included in C 6.0 Help Files

{% raw %}

	Article: Q70144
	Product(s): Microsoft Programming Utilities
	Version(s): MS-DOS:1.0; OS/2:1.0
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 30-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Programmer's Workbench for MS-DOS, version 1.0 
	- Microsoft Programmer's Workbench for OS/2, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The descriptions for some PWB errors do not appear in the online help files that
	shipped with C version 6.0. These errors are U1350, U1351, U1352, U1353, U1354,
	and U1355. The online help for C version 6.0a does contain the information on
	these errors.
	
	MORE INFORMATION
	================
	
	The following is a list of PWB errors and accompanying explanations that are not
	in the C 6.0 online help:
	
	PWB.COM Error U1350
	-------------------
	
	  PWB.COM could not find or load PWBED.EXE.
	
	  Make sure PWBED.EXE can be found on the PATH environment variable,
	  and that there is sufficient memory to operate PWB.
	
	  Check that your environment contains the recommended settings from
	  the NEW-VARS.BAT file created by the Setup program when you
	  installed PWB.
	
	  PWBED.EXE is the executable file for the PWB editor and
	  environment. PWB.COM processes the command line at start-up, and
	  handles all system-level commands when building projects and
	  executing Shell, User, Print, and Compile commands.
	
	PWB.COM Error U1351
	-------------------
	
	  There is not enough available memory to complete the operation.
	
	  You may have too many TSR programs installed. Remove some TSRs.
	
	  A previous command may not have released memory when it terminated.
	  This can happen if you attempt to run a TSR from within PWB.
	
	  You may have too many active command shells. Leave the current
	  shell with the operating-system Exit command.
	
	PWB.COM Error U1352
	-------------------
	
	  The COMPSEC environment variable is not defined.
	
	  PWB requires COMSPEC to be set to the full path name of the
	  operating system command processor.
	
	PWB.COM Error U1353
	-------------------
	
	  PWB.COM encountered an error while reading the file that contains a
	  script of commands to execute during a shell or build operation.
	
	  This can be caused by a CTRL+BREAK or a disk error while reading
	  the script file.
	
	PWB.COM Error U1354
	-------------------
	
	  PWB.COM was unable to execute the given command.
	
	  Some possible causes for this error are:
	
	- The executable file for the command was not found.
	
	- The path name of the command was not found.
	
	- The operating system denied access to the file; it is in use by another
	  program.
	
	- There is not enough available memory to execute the command.
	
	- A previous command may not have released memory when it terminated. This can
	  happen if you attempt to run a TSR from within PWB.
	
	- The environment is corrupt.
	
	- The executable file is corrupt.
	
	PWB.COM Error U1355
	-------------------
	
	  An operating system command or executable program could not be
	  executed.
	
	  The command may be spelled incorrectly, or it does not exist on the
	  paths specified in the PATH environment variable. Make sure that
	  your environment contains the recommended settings from the
	  NEW-VARS.BAT file created by the Setup program when you installed
	  PWB.
	
	Additional query words: 1.00 docerr
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbPWBSearch kbZNotKeyword3 kbPWB100DOS kbPWB100OS2
	Version           : MS-DOS:1.0; OS/2:1.0
	
	=============================================================================
	

{% endraw %}
