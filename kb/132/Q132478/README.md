---
layout: page
title: "Q132478: PRB: Grid Column's CurrentControl Reverts to Text1 Default"
permalink: /kb/132/Q132478/
---

## Q132478: PRB: Grid Column's CurrentControl Reverts to Text1 Default

{% raw %}

	Article: Q132478
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 15-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the SQL SELECT command, and set the grid's RecordSource property to
	the newly queried cursor file, the grid column's current control (Check1 for
	example) reverts to Text1 (the default control).
	
	CAUSE
	=====
	
	The SQL SELECT code includes a SELECT ... INTO CURSOR TESTCURSOR command, which
	is the RecordSource for the grid. When this happens, the original cursor must be
	destroyed before the new cursor can be created. When the orginal cursor is
	destroyed, the grid columns and the controls in the columns are also destroyed,
	as well as the check box. In this case, the check box is destroyed. The SQL
	SELECT code sets the grid's RecordSource to the new cursor. At this point, the
	columns are automatically created with the default settings. There is no code to
	recreate the check box.
	
	WORKAROUND
	==========
	
	To retain the controls in the grid columns, add the following statement prior to
	executing the SQL SELECT command:
	
	        THISFORM.Grid1.RecordSource = ""
	
	For more information, please see the example workaround in the More Information
	section of this article.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Issue the following commands:
	
	     CREATE TABLE Testdbf (id N(1), region C(10))
	     INSERT INTO Testdbf VALUES (0, "North")
	     INSERT INTO Testdbf VALUES (1, "South")
	     INSERT INTO Testdbf VALUES (0, "North")
	     INSERT INTO Testdbf VALUES (1, "South")
	
	2. Create a form named Test.
	
	3. Add the Testdbf table to the Test form's Data Environment.
	
	4. Drag the Testdbf table to the form. A grid is added to the form.
	
	5. Set the following PEMs (properties, events, and methods) for the grid:
	
	     .ColumnCount = 2
	     .RecordSource = "testcursor"
	
	6. Select Grid1.Column1 in the Properties window.
	
	7. Click the check box tool on the toolbar. On the grid, Check1 should appear
	  under Grid1.Column1 in the Properties window.
	
	8. Change the Grid1.Column1.CurrentControl property to Check1.
	
	9. Add a text box to the form.
	
	10. Add a command button to the form, and set the following PEMs:
	
	      .Caption = "SQL"
	      .Click
	         SELECT * FROM Testdbf ;
	            WHERE region = ALLTRIM(thisform.text1.value) ;
	            INTO CURSOR testcursor
	         THISFORM.Grid1.RecordSource = "testcursor"
	         THISFORM.Grid1.SetFocus
	
	11. In the Form1.Load event, add this line of code:
	
	      SELECT * FROM Testdbf WHERE region = "North" ;
	         INTO CURSOR testcursor
	
	12. Save and run form. The grid is populated with "North" records only, and
	  Grid1.Column1 displays a check box.
	
	13. Type "South" (without the quotation marks) in the text box.
	
	14. Click the SQL button.
	
	15. Widen the ID column. The grid is populated with the "South" records only,
	  and Grid1.Column1 no longer displays a check box control. It now displays
	  the default control, which is a text box with a value of 1 for both records.
	
	Example Workaround
	------------------
	
	1. Modify the Test form.
	
	2. In the Command1.Click event, add the following statement prior to executing
	  the SQL SELECT command:
	
	        THISFORM.Grid1.RecordSource = ""
	
	  For example:
	
	        THISFORM.Grid1.RecordSource = ""
	        SELECT * FROM Testdbf ;
	           WHERE region = ALLTRIM(thisform.text1.value) ;
	           INTO CURSOR testcursor
	        THISFORM.Grid1.RecordSource = "testcursor"
	        THISFORM.Grid1.SetFocus
	
	3. Type the "CLEAR ALL" (without the quotation marks) command in the Command
	  window.
	
	4. Save and run the form.
	
	5. Type "South" (without the quotation marks) in the text box.
	
	6. Click the SQL button. Now the grid is populated with the "South" records
	  only, and Grid1.Column1 redisplays the check box control.
	
	Additional query words: VFoxWin refresh
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
