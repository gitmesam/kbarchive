---
layout: page
title: "Q156668: PRB: SET PATH TO Syntax for Folders with Spaces in Name"
permalink: /kb/156/Q156668/
---

## Q156668: PRB: SET PATH TO Syntax for Folders with Spaces in Name

{% raw %}

	Article: Q156668
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.6a,3.0; WINDOWS:3.0,3.0b,5.0,6.0
	Operating System(s): 
	Keyword(s): kbenv kbvfp300 kbvfp500 kbvfp600
	Last Modified: 02-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 6.0 
	- Microsoft Visual FoxPro for Macintosh, Professional Edition, version 3.0 
	- Microsoft FoxPro for Macintosh, version 2.6a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Only the first folder or directory specified in a multiple path string is set by
	the SET PATH TO command. For example, the first folder listed in the sample SET
	PATH TO command below is set in the FoxPro path:
	
	     SET PATH TO "c:\New Folder 1";"c:\New Folder 2"
	
	CAUSE
	=====
	
	The path listed after the SET PATH TO command is set only until the second
	quotation mark is found.
	
	RESOLUTION
	==========
	
	When using the SET PATH TO command with multiple folders that contain spaces,
	either place quotes around the entire path string or don't use quotes at all.
	For the example shown above, use one of the following:
	
	     SET PATH TO "c:\New Folder 1;c:\New Folder 2"
	
	  - or -
	
	     SET PATH TO c:\New Folder 1;c:\New Folder 2
	
	This applies to the Macintosh version of FoxPro and Visual FoxPro as well. The
	Macintosh syntax would be like this:
	
	     SET PATH TO "Macintosh HD:New Folder 1;Macintosh HD:New Folder 2"
	
	  - or -
	
	     SET PATH TO Macintosh HD:New Folder 1;Macintosh HD:New Folder 2
	
	The path set with the SET PATH TO command can be checked by typing the following
	in the Command window:
	
	     ? SET("PATH")
	
	It will return all folders or directories in the FoxPro path if the syntax of the
	SET PATH TO command was correct.
	
	STATUS
	======
	
	This behavior is by design.
	
	Additional query words: kbdsd vFoxWin vFoxMac
	
	======================================================================
	Keywords          : kbenv kbvfp300 kbvfp500 kbvfp600 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbFoxPro260aMac kbVFP300Mac kbVFP300 kbVFP300b kbVFP500 kbVFP600
	Version           : MACINTOSH:2.6a,3.0; WINDOWS:3.0,3.0b,5.0,6.0
	
	=============================================================================
	

{% endraw %}
