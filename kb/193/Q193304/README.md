---
layout: page
title: "Q193304: INFO: Status Bar Shows Currently Selected Object in Designers"
permalink: /kb/193/Q193304/
---

## Q193304: INFO: Status Bar Shows Currently Selected Object in Designers

{% raw %}

	Article: Q193304
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	A new feature of Visual FoxPro 6.0 is that the status bar displays objects
	selected in the various designers. The currently selected object in the Form
	Designer or Class Designer window is displayed. Also, the currently selected
	Data Environment object is displayed in the Form Designer or Report Designer.
	When the selection is made, it displays for 5 seconds, then the status bar
	clears.
	
	MORE INFORMATION
	================
	
	In versions of Visual FoxPro prior to 6.0, there were two ways to determine the
	currently selected object. You could look at the object selection handles (the
	six small squares around a text box or other control, for instance), or look at
	the current object in the Properties Window Object List. Neither of these
	readily display the object hierarchy of the selected object on a single line.
	
	Visual FoxPro 6.0 adds an additional cue to make it easier to determine the
	selected object and where it falls in the object hierarchy. When an object is
	selected, either by clicking the object in the Form or Class Designer window, or
	selecting it from the Properties Window Object List, the object hierarchy and
	name are shown.
	
	Form or Class Designer Window
	-----------------------------
	
	If you are modifying a form, named Form1, which has a container called Container1
	with a text box named Text1, the status bar displays the following text:
	
	  form1.container1.text1.
	
	Form or Report Designer Data Environment Window
	-----------------------------------------------
	
	If you are modifying a report with a Data Environment holding a cursor called
	Cursor1, when the table is highlighted in the Data Environment window, the
	status bar displays the following text:
	
	  dataenvironment.cursor1.
	
	REFERENCES
	==========
	
	(c) Microsoft Corporation 1998, All Rights Reserved.
	Contributions by Jim Saunders, Microsoft Corporation
	
	
	Additional query words: kbVFp600 kbDesigner
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
