---
layout: page
title: "Q195514: FIX: Error Loading File When Converting a 2.6 Form in VFP 6.0"
permalink: /kb/195/Q195514/
---

## Q195514: FIX: Error Loading File When Converting a 2.6 Form in VFP 6.0

{% raw %}

	Article: Q195514
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kberrmsg kbContainer kbCtrl kbMiscTools kbvfp600 kbvfp600bug kbVS600sp3fix
	Last Modified: 14-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you open a converted 2.6 form in Visual FoxPro 6.0, the following error
	message appears if the converted 2.6 form has a radio button control or a line
	object:
	
	  Error Loading File - record number<n>...ColorSource: Expression
	  evaluated to an illegal value.
	
	CAUSE
	=====
	
	The value three (3) is assigned to ColorSource for both the option group control
	and the line object during the conversion. A ColorSource property of three is
	invalid for both of the controls in Visual FoxPro 6.0.
	
	Invisible buttons have this problem, too.
	
	Shape objects might also have this problem.
	
	RESOLUTION
	==========
	
	There are at least three methods for resolving this problem. They are listed
	below.
	
	NOTE: Before attempting any of these resolutions, back up your files.
	
	Method 1
	--------
	
	1. Open up the form file (.scx) as a table.
	
	2. Go to the Properties column of the offending record, and change the
	  ColorSource value from three to four.
	
	  For further information, refer to step 4 in the following Steps to Reproduce
	  Behavior section.
	
	Method 2
	--------
	
	This method works for Invisible Buttons as well as Option Groups.
	
	Modify the Convert.app as follows:
	
	NOTE: The source code for Convert.app is located in the ..\VFP98\Tools\Convert
	folder.
	
	1. Open the Convert.pjx and click the Other Files tab.
	
	2. Under Text Files, open the convert file. This is a header file (.h) that
	  defines constants used in the Convert.app.
	
	3. Search for I_DEFCOLORSOURCE. Your search should find the following line:
	
	        #DEFINE I_DEFCOLORSOURCE   3&& default color source
	
	4. Change the 3 to a 4, and save and close the file.
	
	5. Rebuild the Convert.app from the Project Manager.
	
	6. Copy the new Convert.app to the ..\VFP98 folder. Be sure to verify that the
	  _converter system memory variable points to the correct file. You can also
	  check this in the Options dialog box by clicking the File Locations tab and
	  looking at the path listed under Converter.
	
	Method 3
	--------
	
	Use the Visual FoxPro Transformer application.
	
	NOTE: This is probably the best solution because other aspects of converted forms
	can be changed with the Transformer, many forms at one time. The Transfrm.app is
	located in the ..\VFP98\Tools\Transfrm folder.
	
	Note that as the Help file states:
	
	  "The Transformer is not supported by Microsoft Support Services either
	  electronically or via telephone."
	
	To learn more about the Transformer, go to the Transformer topic in Visual FoxPro
	Help. "Help Transformer," without quotes, typed in the Command window should
	bring it up.
	
	To use the Transformer to resolve the problem described in this article, follow
	these steps after doing a Functional conversion on the form(s):
	
	1. Run the Transfrm.app. It might be easier to copy it to the VFP98 directory
	  first and use DO HOME()+"transfrm.app" to start it.
	
	2. On the Files tab, add your .scx file or the directory that contains the .scx
	  files that need transformed.
	
	3. In the Rules tab, fill in the following:
	
	  Property: colorsource
	  Value: 4
	  Files: *.scx
	  Classes: OptionGroup
	
	4. Click Add to add this rule. Do the same for Invisible Buttons and Line and
	  Shape objects if the converted forms contain them.
	
	5. To save these rules for use at a later time, click the save button and type a
	  table name.
	
	6. On the Log tab, deselect the Create Log Only check box and click Transform.
	
	7. The converted form(s) should now open without errors.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3 for Options Groups.
	
	This problem was not corrected for Invisible Buttons.
	
	For more information about Visual Studio service packs, please see the following
	articles in the Microsoft Knowledge Base:
	
	Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packs Are Installed
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. In FoxPro for Window 2.6, create a screen, place a radio button on the
	  screen, and save the screen.
	
	2. Open the 2.6 screen in Visual FoxPro 6.0. When Visual FoxPro prompts you for
	  a conversion, select functional conversion.
	
	3. After conversion, the following error message appears:
	
	  Error loading file - record number 5. opgOpt1 <or one of its
	  members>.ColorSource: Expression evaluated to an illegal value.
	
	4. To open the form in Visual FoxPro 6.0, open the .scx as a table with the USE
	  command, for example:
	
	  USE myscreen.scx.
	
	5. In the command window, perform a BROWSE, go to the Properties column of the
	  offended record (as described in the error message), and double- click to
	  open the memo window.
	
	6. Change the ColorSource value from 3 to 4.
	
	7. Save the changes, and close the table.
	
	8. Open the form in Visual FoxPro 6.0.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbContainer kbCtrl kbMiscTools kbvfp600 kbvfp600bug kbVS600sp3fix 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
