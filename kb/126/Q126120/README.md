---
layout: page
title: "Q126120: MS POWERPOINT 4 FOR WIN SBS: Corrections and Comments"
permalink: /kb/126/Q126120/
---

## Q126120: MS POWERPOINT 4 FOR WIN SBS: Corrections and Comments

{% raw %}

	Article: Q126120
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 25-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS Microsoft PowerPoint 4 for Windows Step by Step ISBN 1-55615-622-7 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains information on known errors, corrections, and comments
	relating to the Microsoft Press book "Microsoft PowerPoint 4 for Windows Step by
	Step."
	
	The following topics are covered:
	
	- Page 167: Org Chart Colors Unreadable on 16-Color VGA Display
	
	MORE INFORMATION
	================
	
	In addition to a description of the book's problems, this document might also
	include sections labeled "Correction" and "Comments." Please note that the
	"Correction" section is worded for correcting the book and does not necessarily
	address the problem introduced by the book error. The "Comments" section
	contains specific information for working around problems.
	
	Page 167: Org Chart Colors Unreadable on 16-Color VGA Display
	-------------------------------------------------------------
	
	Page 167 shows an organization chart. On a computer with a standard VGA driver
	(16 colors) installed, the background of the chart appears as yellow and red
	dots, and the text is displayed as unreadable, white blotches.
	
	  NOTE: This problem does not exist on computers running an SVGA driver (256
	  colors).
	
	Correction:
	
	The master color scheme in the file LESSON10.PPT should be altered to use only
	standard VGA colors.
	
	Comments:
	
	To make Lesson 10 readable, modify the filler color and the text/line color so
	that each is a solid color. To make these modifications, follow these steps:
	
	1. In PowerPoint, open LESSON10.PPT.
	
	2. From the View menu, choose Master, and then choose Master Slide.
	
	3. From the Format menu, choose Slide Color Scheme.
	
	  A dialog box showing the currently-assigned colors will appear.
	
	4. Select the Fills color box (third box on top row), choose the Change Color
	  button, and choose a solid color. For example, choose Yellow (fifth box on
	  top row).
	
	5. After you select the desired color, choose OK to return to the Slide Color
	  Scheme dialog box.
	
	6. Select the Text & Lines color box (first box on bottom row) and choose
	  the Change Color button.
	
	7. Select the Black bar at the bottom of the Color Selection dialog box, and
	  then choose OK.
	
	8. Choose the Apply To All button.
	
	  A readable color scheme is applied to the entire presentation.
	
	9. From the View menu, choose Slides.
	
	Save your file with the changes as LESSON10.PPT. Now you can complete lesson 10
	as described in the book.
	
	
	Microsoft Press is committed to providing informative and accurate books. All
	comments and corrections listed above are ready for inclusion in future
	printings of this book. If you have a later printing of this book, it may
	already contain most or all of the above corrections.
	
	Additional query words: mspress ms_press press bookbug sbs
	
	======================================================================
	Keywords          :  
	Technology        : kbMSPressSearch
	Version           : :
	
	=============================================================================
	

{% endraw %}
