---
layout: page
title: "Q129648: Calling a Form as If It Were a Function to Return a Value"
permalink: /kb/129/Q129648/
---

## Q129648: Calling a Form as If It Were a Function to Return a Value

{% raw %}

	Article: Q129648
	Product(s): Microsoft FoxPro
	Version(s): 3.00
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 25-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In Visual FoxPro for Windows, a form is an object and as such cannot be called
	directly as a function can. However, by using object-oriented practices, you can
	create a class that calls a form. That class can in turn be instantiated in a
	function that returns what was entered in the form.
	
	MORE INFORMATION
	================
	
	The following instructions demonstrate how to call a form as if it were a
	function.
	
	1. Create a new form, and save it as MYFORM.SCX.
	
	2. Create a text box on the form.
	
	3. Double-click the text box to bring up the methods. Select VALID from the
	  Procedure list, and type in the following code:
	
	     STORE This.Value TO uRetValue
	     ThisForm.Release     && release the form
	
	4. Close the TEXT1.Valid dialog.
	
	5. Click in the form outside of the text box to deactivate the text box. Click
	  the right mouse button, and choose properties.
	
	6. Select the ALL tab. Scroll down in the list to the property WINDOW TYPE.
	
	7. Change the Window type to 1-Modal, and close the properties dialog. Then save
	  and close the form.
	
	8. Create and save a program file called MYTEST.PRG that contains the following
	  code:
	
	     *begin program
	     LPARAMETERS tcfilename   && t-PARAMETER c-char
	     LOCAL ofrmMyForm         && o-object (instance)
	     *create an instance of the form
	     ofrmMyForm=CREATEOBJECT("frmMyForm", tcfilename)
	     RETURN ofrmMyForm.SHOW()
	
	     DEFINE CLASS frmMyForm AS CUSTOM
	          * create property to hold the filename
	          cfilename=""
	          FUNCTION INIT(tcfilename)
	               THIS.cfilename=tcfilename
	               RETURN .T.
	          ENDFUNC
	          FUNCTION SHOW
	               PRIVATE uRetValue     && u-unknown type
	               STORE .T. TO uRetValue
	               * call the form
	               DO FORM (THIS.cfilename)
	               RETURN uRetValue
	          ENDFUNC
	     ENDDEFINE
	     *end program
	
	9. In the Command window, issue this command:
	
	     ? MYTEST("MYFORM.SCX")
	
	The program creates an instance of the class, which in turn runs the form. When
	the form is displayed, enter some data, and press ENTER. The form will close,
	and program execution, which has paused at this point because the WindowType
	property was set to Modal, will continue with the statement RETURN uRetValue.
	
	As the program terminates, ofrmMyForm will fall out of scope, and what was typed
	will show up in the active window.
	
	This is just an example of calling a function that displays a form. With simple
	modification, the procedure described here could be used for password entry,
	prompting for a search string, or various other uses.
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : 3.00
	
	=============================================================================
	

{% endraw %}
