---
layout: page
title: "Q189086: HOWTO: Create Context-Sensitive HTML Help in a Visual Basic App"
permalink: /kb/189/Q189086/
---

## Q189086: HOWTO: Create Context-Sensitive HTML Help in a Visual Basic App

{% raw %}

	Article: Q189086
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:1.1,1.3,4.0,5.0
	Operating System(s): 
	Keyword(s): kbHTMLHelp kbVBp400 kbVBp500 kbGrpDSVB kbHTMLHelp110 kbDSupport kbHTMLHelp130
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft HTML Help, versions 1.3, 1.1 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, versions 4.0, 5.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article shows you how to implement context-sensitive HTML Help in a Visual
	Basic application.
	
	Also, this article assumes that you have created an HTML Help (.chm) file to use
	with context-sensitive help.
	
	For additional information on creating HTML help files, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q191118 : HOWTO: Create Context-Sensitive HTML Help in an MFC Application
	
	The information in this article is most useful for Visual Basic 4.0 and 5.0
	applications. Visual Basic 6.0 has added support for HTML Help files that
	eliminates the need for calling the API directly. See Visual Basic's online help
	for more information.
	
	MORE INFORMATION
	================
	
	Perform the following steps in your Visual Basic application:
	
	1. Create a new project, Form1 is created by default. Add a few controls to the
	  form.
	
	2. Add a module to the project, and add the following constants to the
	  declaration section of the module:
	
	        Public Const HH_HELP_CONTEXT = &HF
	
	        Public Const MYHELP_FILE = "myfile.chm"
	
	  NOTE: "myfile.chm" is the path and name of the HTML Help file (.chm) you
	  created earlier.
	
	3. Add the following HTML Help API declaration to the module:
	
	        Public Declare Function HtmlHelpLongArg Lib "hhctrl.ocx" _
	            Alias "HtmlHelpA" (ByVal hwndCaller As Long, _
	            ByVal pszFile As String, ByVal uCommand As Long, _
	            ByVal dwData As Long) As Long
	
	4. Intercept the form's KeyUp method to capture the F1 key using the following
	  sample code in the Form KeyUp event procedure:
	
	        Private Sub Form_KeyUp(KeyCode As Integer, Shift As Integer)
	           dim iRetCode As Long
	           If KeyCode = vbKeyF1 Then
	               iRetCode = HtmlHelpLongArg(Me.ActiveControl.hWnd,_
	                MYHELP_FILE,HH_HELP_CONTEXT,Me.ActiveControl.HelpContextID)
	           End If
	        End Sub
	
	5. Set the form's KeyPreview, WhatsThisHelp, and WhatsThisButton properties to
	  TRUE.
	
	6. Set the HelpContextID property of each control on the form to a value from
	  the help project file's MAP section.
	
	7. Run the Visual Basic application. Select a control on the form and press the
	  F1 key. The appropriate context-sensitive help topic should appear on the
	  screen.
	
	REFERENCES
	==========
	
	Microsoft Visual Basic Help, version 4.0, 5.0
	
	Additional query words:
	
	======================================================================
	Keywords          : kbHTMLHelp kbVBp400 kbVBp500 kbGrpDSVB kbHTMLHelp110 kbDSupport kbHTMLHelp130 
	Technology        : kbVBSearch kbHTMLHelpSearch kbAudDeveloper kbVB400Search kbVB400 kbHTMLHelp110 kbHTMLHelp130
	Version           : WINDOWS:1.1,1.3,4.0,5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
