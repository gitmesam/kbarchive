---
layout: page
title: "Q138693: FIX: Error Opening .Bsc File from MRU List"
permalink: /kb/138/Q138693/
---

## Q138693: FIX: Error Opening .Bsc File from MRU List

{% raw %}

	Article: Q138693
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kbide kbVC kbVC500fix kbGrpDSTools
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.0, 4.1, 4.2 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 4.0, 4.1, 4.2 
	- Microsoft Visual C++, 32-bit Learning Edition, versions 4.0, 4.1, 4.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Attempting to open a browser database (.bsc) file from Developer Studio's Most
	Recently Used (MRU) list under the File menu, may result in an error similar to
	this:
	
	  c:\myapp\debug\myapp.bsc
	  The file is binary and cannot be read.
	
	This occurs only when the .bsc file was not previously opened by clicking Open on
	the File menu since the Developer Studio was restarted.
	
	RESOLUTION
	==========
	
	Open the .bsc file by clicking Open on the File menu.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem was corrected in Microsoft Visual C++,
	version 5.0.
	
	Visual C++ 5.0 does not automatically load .bsc files, so they do not appear in
	the Recent Files List unless they are specifically loaded as binary files.
	Visual C++ 5.0 remembers the .bsc file's binary state when it is loaded from the
	Recent Files List. No error is generated.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. In the Developer Studio, open any .bsc file by clicking Open on the File
	  menu.
	
	2. Close the Developer Studio.
	
	3. Restart the Developer Studio.
	
	4. Select the previously opened .bsc file from the Most Recently Used files
	  list. The error occurs.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbide kbVC kbVC500fix kbGrpDSTools 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbVC410 kbVC420 kbVC32bitSearch
	Version           : winnt:
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
