---
layout: page
title: "Q171523: FIX: Reference to Missing Member in Enum Definition Causes Crash"
permalink: /kb/171/Q171523/
---

## Q171523: FIX: Reference to Missing Member in Enum Definition Causes Crash

{% raw %}

	Article: Q171523
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbVBp500 kbVS97sp2fix kbGrpDSVB kbvbp500sp2fix
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Trying to reference a non-existent member in an Enum definition will cause
	Visual Basic 5.0 to crash.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Studio 97 Service
	Pack 2.
	
	For more information on the Visual Studio 97 Service Pack 2, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q170365 INFO: Visual Studio 97 Service Packs - What, Where,and Why
	
	For a list of the Visual Basic 5.0 bugs that were fixed in the Visual Studio 97
	Service Pack 2, please see the following article in the Microsoft Knowledge
	Base:
	
	  Q171554 INFO: Visual Basic 5.0 Fixes in Visual Studio 97 Service Pack 2
	
	MORE INFORMATION
	================
	
	Below are two methods for reproducing the problem:
	
	Method 1
	--------
	
	1. Start Visual Basic 5.0 and create a new Standard EXE project.
	
	2. Add a new Module (Module1) to the project.
	
	3. Paste the following code into the General Declarations area of Module1:
	
	        Public Enum CrashMe
	               Crash1 = Not (Crash0)
	        End    Enum
	
	4. Invoke the Object Browser by pressing the F2 key, or press the F5 key to run
	  the application. Visual Basic will crash with an Application Error.
	
	Method 2
	--------
	
	1. Repeat steps 1, 2, and 3 from Method 1.
	
	2. Create a new subroutine named Test in the basic Module.
	
	3. Type the following in the General Declarations section of Module1:
	
	         Public Sub Test()
	            Dim X As
	
	4. Press the spacebar. Visual Basic will crash with an Application Error.
	
	NOTE: The program will not crash if you define Crash0 in the declare of the Enum
	type.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp500 kbVS97sp2fix kbGrpDSVB kbvbp500sp2fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVBA500 kbVB500 kbZNotKeyword3
	Version           : 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
