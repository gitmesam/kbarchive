---
layout: page
title: "Q163249: HOWTO: Use Usercontrolmode with Wizstyle Button Classes in VFP"
permalink: /kb/163/Q163249/
---

## Q163249: HOWTO: Use Usercontrolmode with Wizstyle Button Classes in VFP

{% raw %}

	Article: Q163249
	Product(s): Microsoft FoxPro
	Version(s): 
	Operating System(s): 
	Keyword(s): kbDesigner kbOOP kbvfp500 kbvfp600
	Last Modified: 24-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The txtbtns and pictbtns classes contained in the Wizstyle.vcx library of
	Microsoft Visual FoxPro for Windows version 5.0 have a new custom property that
	controls the enabled/disabled property of a ComboBox, ListBox, or Spinner
	control placed on the same form.
	
	The Form wizard automatically drops a txtbtns object named "BUTTONSET1" on any
	form it builds. All TextBox controls populated from fields in tables are
	disabled until the Edit button of the BUTTONSET1 collection is clicked. Clicking
	Save or Revert again disables those controls.
	
	In Visual FoxPro 3.0 and 3.0b the developer had to add code to the click methods
	of those buttons to control the enabled/disabled status of an additional
	ComboBox, ListBox, or Spinner control in order to control whether event methods
	of those would be allowed to modify values elsewhere in a table or property.
	
	When set to .F. the new "Usercontrolmode" property of the txtbtns and pictbtns
	classes let the affected controls (ComboBox, ListBox, or Spinner) work the same
	as they did in Visual FoxPro 3.0.
	
	When Usercontrolmode is set to .T. the "Edit," "Save," and "Revert" buttons
	enable and disable those controls the same way they enable/disable the TextBox
	controls on that form.
	
	MORE INFORMATION
	================
	
	Steps to Demonstrate the Usercontrolmode Property
	-------------------------------------------------
	
	1. Issue the following command in the Command window:
	
	        SET DEFAULT TO HOME()+"\samples\data"
	
	  In Visual FoxPro 6.0, issue the following command:
	
	        SET DEFAULT TO HOME(3)+"samples\data"
	
	2. Open the Testdata database.
	
	3. Select Wizards and then Form from the Tools menu.
	
	4. In the Wizard Selection dialog box, click OK for the Form Wizard.
	
	5. In the Form Wizard dialog box, click the double arrow button to select all
	  fields from the customer table, then click Finish.
	
	6. Select the "Save form and modify it in the Form Designer" option, then click
	  Finish. (The form is saved as Customer.scx by default.)
	
	7. Click Save in the Save As dialog box.
	
	8. Size the form so that you can see the buttons at the bottom.
	
	9. From the Form Controls toolbar select a ComboBox, and place it on the form.
	
	10. In the property sheet for the ComboBox set RowSourceType to "5 - Array."
	
	11. Set RowSource to Thisform.myarray.
	
	12. Click New Property from the Form menu. Define a new property by typing
	  "myarray(20)" (without the quotes) into Name field and click "Add." Then
	  click Close.
	
	13. In the Init event method of the ComboBox enter the following:
	
	         SELECT DISTINCT country FROM customer ;
	            INTO ARRAY thisform.myarray NOCONSOLE
	         This.DisplayValue = Thisform.country1.value  && the textbox
	         This.refresh
	
	14. Run the form. Note that the ComboBox is enabled. Click Exit.
	
	15. Back in the development mode, select the BUTTONSET1 control.
	
	16. In the property sheet for BUTTONSET1 scroll down to the custom properties
	  and find "Usercontrolmode." Set that to .T. (True). (It is not a toggled
	  property, so type the string ".T." without quotes in the property setting
	  combo box at the top of the sheet.)
	
	17. Run the form. Note that the combo box is disabled. Click Edit and notice
	  that the combo box, and all of the text boxes, are enabled. Click Revert and
	  notice that the controls are disabled.
	
	Using this feature in a project, the developer may want to change the
	DisabledBackColor property to white to match the backcolor of all of the other
	controls on the form.
	(c) Microsoft Corporation 1997, All Rights Reserved.
	Contributions by Chris Jensen, Microsoft Corporation
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDesigner kbOOP kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
