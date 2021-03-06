---
layout: page
title: "Q196855: WD97: How to Extend Form Field Underlines to a Fixed Point"
permalink: /kb/196/Q196855/
---

## Q196855: WD97: How to Extend Form Field Underlines to a Fixed Point

{% raw %}

	Article: Q196855
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbualink97 kbdta kbfield word97 kbform kbForms
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	This article describes four methods for underlining form fields and extending
	the underline to a fixed point.
	
	MORE INFORMATION
	================
	
	Method 1: Create a Table That Resembles the Printed Form
	--------------------------------------------------------
	
	When you either insert or draw a table, it automatically has a border. If you
	want the border to be only at certain places within your table, you first need
	to remove the border. To do this, follow these steps:
	
	1. Place your insertion point anywhere in the table.
	
	2. On the Table menu, click Select Table.
	
	3. On the Format menu, click Borders and Shading, and then select the Borders
	  tab.
	
	4. Under Setting, click None and then click OK.
	
	  NOTE: You may see the gridlines of the table; however, they will not be
	  printed.
	
	5. Place the form field at an appropriate spot in the table.
	
	Method 2: Set an Underlined Tab
	-------------------------------
	
	Set a left-aligned, underlined leader tab at the position where you will start
	typing, and set a right-aligned, underlined leader tab at the position where the
	underlining will end. Insert the form field between the two tabs and underline
	the form field.
	
	To set one of these tabs, follow these steps:
	
	1. On the Format menu, click Tabs.
	
	2. In the Tab Stop Position box, enter the place where you want the first tab to
	  stop.
	
	3. In the Alignment list, click Left.
	
	4. In the Leader list, click 4.
	
	5. Click Set.
	
	6. In the Tab Stop Position box, enter the place where you want the second tab
	  to stop.
	
	7. In the Alignment list, click Right.
	
	8. In the Leader list, click 4.
	
	9. Click Set.
	
	10. Click OK.
	
	Method 3: Insert Nonbreaking Spaces
	-----------------------------------
	
	Unlike regular spaces, you can underline nonbreaking spaces.
	
	1. Turn on display of nonprinting characters so that you can see the characters
	  once you type them:
	
	  a. On the Tools menu, click Options.
	
	  b. Select the View tab.
	
	  c. In the Nonprinting Characters category, click to select the All check box.
	
	  d. Click OK.
	
	2. Place the insertion point where you want the underline to begin.
	
	3. Press CTRL+SHIFT+SPACEBAR for each space that you want to underline. Unlike
	  regular spaces, which appear as dots, these nonbreaking spaces appear as
	  small circles.
	
	4. Highlight each nonbreaking space and click the Underline button on the
	  Formatting toolbar or press CTRL+U.
	
	5. Insert the form field in the center of the nonbreaking spaces to assure equal
	  line space before and after the form field.
	
	You can repeat steps 3 and 4 on the other side of the form field.
	
	Method 4: Draw a Line
	---------------------
	
	Use the Drawing Toolbar to draw a line beneath the area to be underlined.
	
	NOTE: Do not use this method in documents that are not protected, because users
	may accidentally select and move the drawn lines.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q145149 How to Create Blank Underlines in Microsoft Word
	
	Additional query words: underlining forms layout lines howto text 8.0 8.00
	
	======================================================================
	Keywords          : kbualink97 kbdta kbfield word97 kbform kbForms 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
