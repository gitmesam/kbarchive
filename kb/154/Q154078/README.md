---
layout: page
title: "Q154078: HOWTO: Send Raw Data to a Printer Using the Win32 API from VB"
permalink: /kb/154/Q154078/
---

## Q154078: HOWTO: Send Raw Data to a Printer Using the Win32 API from VB

{% raw %}

	Article: Q154078
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbprint kbAPI kbPrinting kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbDSupport
	Last Modified: 11-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Visual Basic Printer object allows for printing through printer drivers, but
	there may be times when it is desirable to use the Win32 API to send information
	more directly to the printer. The code sample to follow shows how to achieve
	this by using API functions that bypass printer drivers to communicate directly
	with the print spooler.
	
	MORE INFORMATION
	================
	
	1. Start a new project in Visual Basic. Form1 is created by default.
	
	2. Place a Command Button on the form.
	
	3. Add the following code to the Form1 code window:
	
	        Option Explicit
	
	        Private Type DOCINFO
	            pDocName As String
	            pOutputFile As String
	            pDatatype As String
	        End Type
	
	        Private Declare Function ClosePrinter Lib "winspool.drv" (ByVal _
	           hPrinter As Long) As Long
	        Private Declare Function EndDocPrinter Lib "winspool.drv" (ByVal _
	           hPrinter As Long) As Long
	        Private Declare Function EndPagePrinter Lib "winspool.drv" (ByVal _
	           hPrinter As Long) As Long
	        Private Declare Function OpenPrinter Lib "winspool.drv" Alias _
	           "OpenPrinterA" (ByVal pPrinterName As String, phPrinter As Long, _
	            ByVal pDefault As Long) As Long
	        Private Declare Function StartDocPrinter Lib "winspool.drv" Alias _
	           "StartDocPrinterA" (ByVal hPrinter As Long, ByVal Level As Long, _
	           pDocInfo As DOCINFO) As Long
	        Private Declare Function StartPagePrinter Lib "winspool.drv" (ByVal _
	           hPrinter As Long) As Long
	        Private Declare Function WritePrinter Lib "winspool.drv" (ByVal _
	           hPrinter As Long, pBuf As Any, ByVal cdBuf As Long,  _
	           pcWritten As Long) As Long
	
	        Private Sub Command1_Click()
	            Dim lhPrinter As Long
	            Dim lReturn As Long
	            Dim lpcWritten As Long
	            Dim lDoc As Long
	            Dim sWrittenData As String
	            Dim MyDocInfo As DOCINFO
	            lReturn = OpenPrinter(Printer.DeviceName, lhPrinter, 0)
	            If lReturn = 0 Then
	                MsgBox "The Printer Name you typed wasn't recognized."
	                Exit Sub
	            End If
	            MyDocInfo.pDocName = "AAAAAA"
	            MyDocInfo.pOutputFile = vbNullString
	            MyDocInfo.pDatatype = vbNullString
	            lDoc = StartDocPrinter(lhPrinter, 1, MyDocInfo)
	            Call StartPagePrinter(lhPrinter)
	            sWrittenData = "How's that for Magic !!!!" & vbFormFeed
	            lReturn = WritePrinter(lhPrinter, ByVal sWrittenData, _
	               Len(sWrittenData), lpcWritten)
	            lReturn = EndPagePrinter(lhPrinter)
	            lReturn = EndDocPrinter(lhPrinter)
	            lReturn = ClosePrinter(lhPrinter)
	        End Sub
	
	REFERENCES
	==========
	
	The Win32 SDK Help files give a more detailed description of the APIs used in
	the sample.
	
	For information on the same procedure for VC++, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q138594 : HOWTO: Send Raw Data to a Printer by Using the Win32 API
	
	Additional query words: raw receipt
	
	======================================================================
	Keywords          : kbprint kbAPI kbPrinting kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : :4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
