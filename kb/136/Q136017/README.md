---
layout: page
title: "Q136017: PRB: Cannot Update Cursor Error Occurs as Buildapp Builds .EXE"
permalink: /kb/136/Q136017/
---

## Q136017: PRB: Cannot Update Cursor Error Occurs as Buildapp Builds .EXE

{% raw %}

	Article: Q136017
	Product(s): Microsoft FoxPro
	Version(s): 3.00
	Operating System(s): 
	Keyword(s): kbvfp kbvfp300 kbvfp600
	Last Modified: 20-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When Buildapp.prg is used to build an .exe file, the following error may occur:
	
	  Cannot update the cursor. Method: build Line: 9 BUILD EXE (this.cAPPFile)
	  FROM (this.cProjectFile)
	
	CAUSE
	=====
	
	The application name parameter passed to Buildapp included an .app extension.
	
	RESOLUTION
	==========
	
	If Buildapp is being used to build an .exe file, the application name parameter
	should either have no extension or have an .exe extension.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Located in the Visual FoxPro Tools\Buildapp directory, Buildapp.prg strips the
	method and event code of .scx and .vcx files from .app and .exe files for
	distribution purposes.
	
	In Visual FoxPro, source code is usually stored in the Methods field of all .scx
	and .vcx tables. When you build an application, these fields are included in the
	build, and the code is included in the .app file. Buildapp strips the code from
	the methods field before the final application build and restores files to their
	original state following the build. By building files without source code, your
	.app files are smaller and more secure. The syntax is:
	
	  DO BUILDAPP WITH cProjectName, cAppFileName, lDebugMode, lBuildEXE
	
	The cAppFileName parameter should either have no extension or reflect the
	extension of the type of file you are building (.app for application, or .exe
	for executable). In the process of building an executable, FoxPro builds a
	temporary .app file with the name you specified in the cAppFileName parameter.
	This will cause a problem in the next step when it tries to create an executable
	file with a .app extension from the temporary .app file it has already created.
	
	Steps to Reproduce Behavior
	---------------------------
	
	The following example uses the Tastrade.pjx file in the Samples\Mainsamp
	directory under the Visual FoxPro directory.
	
	Issue the following commands in the Command window:
	
	     SET DEFAULT TO SYS(2004)+'SAMPLES\MAINSAMP'
	
	     DO SYS(2004)+'TOOLS\BUILDAPP\BUILDAPP.PRG' ;
	        WITH "tastrade.pjx", "tastrade.app", .F., .T.
	
	At this point, the error occurs. To prevent the error, use one of the following
	commands to build the executable:
	
	     DO SYS(2004)+'TOOLS\BUILDAPP\BUILDAPP.PRG' ;
	        WITH "tastrade.pjx", "tastrade", .F., .T.
	
	  -or-
	
	     DO SYS(2004)+'TOOLS\BUILDAPP\BUILDAPP.PRG' ;
	        WITH "tastrade.pjx", "tastrade.exe", .F., .T.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp kbvfp300 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP600
	Version           : 3.00
	
	=============================================================================
	

{% endraw %}
