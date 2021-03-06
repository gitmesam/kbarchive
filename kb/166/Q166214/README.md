---
layout: page
title: "Q166214: WD97: Sample VB Code To Determine Text Box (or Text Frame) Link"
permalink: /kb/166/Q166214/
---

## Q166214: WD97: Sample VB Code To Determine Text Box (or Text Frame) Link

{% raw %}

	Article: Q166214
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta kbdtacode kbmacroexample word8 kbwordvba word97
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	This article describes a Visual Basic for Applications macro that determines if
	one text box (or text frame) is linked to another text box (or text frame).
	
	MORE INFORMATION
	================
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	To determine and compare text box links, create a macro that uses the Parent,
	Name, and Previous properties to compare the text boxes. The following macro
	creates two text boxes, links the first text box to the second text box, and
	then displays a message indicating the link status.
	
	     Sub CompareTextBoxLinks()
	        Dim TBox1, TBox2 As TextFrame
	
	        ' Create the first text box.
	        Set TBox1 = ActiveDocument.Shapes.AddTextbox _
	        (Orientation:=msoTextOrientationHorizontal, _
	        Left:=50, Top:=50, Width:=100, Height:=100).TextFrame
	
	        ' Create the second text box.
	        Set TBox2 = ActiveDocument.Shapes.AddTextbox _
	        (Orientation:=msoTextOrientationHorizontal, _
	        Left:=50, Top:=200, Width:=100, Height:=100).TextFrame
	
	        ' Link the first text box to the second text box.
	        TBox1.Next = TBox2
	
	        ' Determine if the second text box is linked to the first.
	        ' TBox2.Previous.Parent.Name returns the name of the linked
	        ' text box. If Tbox2 matches Tbox1, then they are linked.
	        If TBox2.Previous.Parent.Name = TBox1.Parent.Name Then
	           MsgBox TBox2.Parent.Name & " is linked to" & TBox1.Parent.Name
	        End If
	     End Sub
	
	For more information about the Parent property, from the Visual Basic Editor,
	click the Office Assistant, type "Parent Property" (without the quotation
	marks), click Search, and then click to view "Parent Property."
	
	For more information about the TextFrames object, from the Visual Basic Editor,
	click the Office Assistant, type "TextFramesObject" (without the quotation
	marks), click Search, and then click to view "TextFrames Object."
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If the Assistant is not able to answer your query, please see
	the following article in the Microsoft Knowledge Base:
	
	  Q176476 OFF: Office Assistant Not Answering Visual Basic Questions
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q173707 OFF97: How to Run Sample Code from Knowledge Base Articles
	
	
	REFERENCES
	==========
	
	For more information about getting help with Visual Basic for Applications,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	
	Additional query words: wordcon vb vba vbe
	
	======================================================================
	Keywords          : kbdta kbdtacode kbmacroexample word8 kbwordvba word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
