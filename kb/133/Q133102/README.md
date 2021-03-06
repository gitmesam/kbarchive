---
layout: page
title: "Q133102: FORTRAN PowerStation 32 README.TXT: Installation"
permalink: /kb/133/Q133102/
---

## Q133102: FORTRAN PowerStation 32 README.TXT: Installation

{% raw %}

	Article: Q133102
	Product(s): Microsoft Fortran Compiler
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 02-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Fortran Powerstation 32 for Windows NT, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following information is from the Microsoft FORTRAN PowerStation 32
	README.TXT file located in the \FPSNT\README directory.
	
	This file has four parts:
	
	    Part     Contents
	    ----     --------
	     1       Installation
	     2       Debugging
	     3       Building and Running Programs
	     4       Miscellaneous
	
	MORE INFORMATION
	================
	
	=======================< Part 1: Installation >========================
	
	Installation and Windows NT User Accounts
	-----------------------------------------
	Each user account in Windows NT has a key stored in the Registry.
	This key contains the user profile and privilege level set by the
	system administrator. If your user account group membership
	(privileges) is changed after installation, the following two
	messages may appear when starting FORTRAN Visual Workbench. After
	these messages appear, FORTRAN Visual Workbench starts running.
	However, when you exit you will receive the second message again.
	
	"The options Registry Key 'FORTRAN PowerStation' is missing. A new
	 Registry Key will be created using the default settings."
	
	"Unable to write to the NT Registry. Option settings will not be
	 saved."
	
	The FORTRAN Visual Workbench profile information, contained in the
	Microsoft FORTRAN Visual Workbench key in the Windows NT registry,
	contains both program-specific information such as environment
	variables and user-specific information such as Editor options.
	Each user on a Windows NT computer has a unique key for the
	development environment, and that key cannot be shared on the same
	machine.
	
	Since the key cannot be shared, FORTRAN Visual Workbench must be
	installed at the user level. If your user account belongs to more
	than one group (Administrators, Backup Operators, Power Users,
	Users, Guests, Replicators), and you install FORTRAN Visual
	Workbench by running Setup as a member of Administrators, then you
	only have access to FORTRAN Visual Workbench via your FORTRAN Visual
	Workbench key when you are logged in the Admin group. If you intend
	to work with FORTRAN Visual Workbench as a Power User, you must
	install FORTRAN Visual Workbench as a Power User, and then use
	FORTRAN PowerStation as a Power User. FORTRAN Visual Workbench
	functionality cannot be spanned across user groups.
	
	To correct this situation, a user with Administrator privileges on
	your machine can perform the following steps to rebuild the Registry
	Key for your user account:
	
	1. Log in as Administrator and give the User of FORTRAN PowerStation
	  administrative privileges to delete the FORTRAN PowerStation entry,
	  with RegEdit32 located in \winnt\system32 directory. The FORTRAN
	  PowerStation entry is under HKEY_CURRENT_USER, Software, Microsoft,
	  FORTRAN PowerStation. Be sure not to delete any entries other than
	  FORTRAN PowerStation.
	
	2. Remove the administrative privileges for the FORTRAN PowerStation
	  User.
	
	3. Log in as the User and start FORTRAN PowerStation again. This time
	  you will only receive the first message from above and a new
	  registry entry will be created.
	
	Installation over a Network
	---------------------------
	You can set up FORTRAN PowerStation for installation across a network:
	
	1) Copy all of the disks to a directory tree on the network with the
	  directory names: ...\disk1, ...\disk2, and so on.
	
	2) From the root of this directory tree, type: COPY DISK1\SETUP.*
	
	3) You can now run Setup from the directory tree on the network.
	
	Numerical Recipes and AUTOEXEC.BAT
	----------------------------------
	The Numerical Recipes Setup program uses the directory ...\F32\BIN as
	the default location for installing the NR files. (This is the directory
	used for NR in FORTRAN PowerStation 32 for MS-DOS.) If you want to
	install the NR files with the rest of FORTRAN PowerStation 32 for
	Windows NT, change the destination directory to ...\FPSNT\BIN.
	
	At the end of the installation process, the NR Setup program asks if you
	want it to modify the AUTOEXEC.BAT file. (This is because it is the same
	program that is used to install NR under MS-DOS.) Unless you intend to
	run your programs in the MS-DOS environment, you should select the
	option of not updating the AUTOEXEC.BAT file.
	
	Additional query words: 1.00
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbFortranSearch kbZNotKeyword2 kbFORTRANPower32100NT
	Version           : :1.0
	
	=============================================================================
	

{% endraw %}
