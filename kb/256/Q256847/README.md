---
layout: page
title: "Q256847: HOWTO: Use the WNetUseConnection API to Map a Drive in VB"
permalink: /kb/256/Q256847/
---

## Q256847: HOWTO: Use the WNetUseConnection API to Map a Drive in VB

{% raw %}

	Article: Q256847
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbAPI kbVBp kbVBp400 kbVBp500 kbVBp600 kbWNet kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article demonstrates how to use the WNetUseConnection API function to map a
	system-supplied drive letter to a network share. In addition, the
	WNetCancelConnection2 API function is demonstrated to show how to disconnect a
	mapped drive.
	
	MORE INFORMATION
	================
	
	At times, it is necessary to map a drive letter to a network share. There are
	several API functions that can be used to accomplish this, such as
	WNetAddConnection, WNetAddConnection2, WNetAddConnection3, and
	WNetUseConnection. The primary difference is that with the WNetUseConnection
	function, you do not need to specify the drive letter to be used, while it is
	required with the other API functions.
	
	Steps to Create Sample
	----------------------
	
	1. Create a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. Add three TextBox controls to Form1 and name them "txtUNC" (without the
	  quotation marks), "txtUser" (without the quotation marks), and "txtPWD"
	  (without the quotation marks).
	
	3. Set the PasswordChar property of txtPWD to an asterisk (*).
	
	4. Add two CommandButtons to Form1 and set their Captions to "CONNECT" (without
	  the quotation marks) and "DISCONNECT" (without the quotation marks).
	
	5. Paste the following code into the code window of Form1:
	
	  Option Explicit
	
	  ' CONSTANTS
	  Private Const NO_ERROR = 0
	  Private Const CONNECT_LOCALDRIVE = 256
	  Private Const CONNECT_REDIRECT = 128
	  Private Const RESOURCE_GLOBALNET = &H2
	  Private Const RESOURCETYPE_DISK = &H1
	  Private Const RESOURCEDISPLAYTYPE_SHARE = &H3
	  Private Const RESOURCEUSAGE_CONNECTABLE = &H1
	  Private Const CONNECT_UPDATE_PROFILE = 1
	
	  ' LOCAL VARIABLES
	  Private MappedDrive As String
	
	  ' CUSTOM TYPES
	  Private Type NETRESOURCE
	      dwScope As Long
	      dwType As Long
	      dwDisplayType As Long
	      dwUsage As Long
	      lpLocalName As String
	      lpRemoteName As String
	      lpComment As String
	      lpProvider As String
	  End Type
	
	  ' API DECLARATIONS
	  Private Declare Function WNetUseConnection Lib "mpr.dll" _
	     Alias "WNetUseConnectionA" ( _
	     ByVal hwndOwner As Long, _
	     ByRef lpNetResource As NETRESOURCE, _
	     ByVal lpUsername As String, _
	     ByVal lpPassword As String, _
	     ByVal dwFlags As Long, _
	     ByVal lpAccessName As Any, _
	     ByRef lpBufferSize As Long, _
	     ByRef lpResult As Long) _
	     As Long
	
	  Private Declare Function WNetCancelConnection2 Lib "mpr.dll" _
	     Alias "WNetCancelConnection2A" ( _
	     ByVal lpName As String, _
	     ByVal dwFlags As Long, _
	     ByVal fForce As Long) _
	     As Long
	
	  Private Sub Command1_Click()
	     Dim NetR As NETRESOURCE    ' NetResouce structure
	     Dim ErrInfo As Long        ' Return value from API
	     Dim buffer As String       ' Drive letter assigned to resource
	     Dim bufferlen As Long      ' Size of the buffer
	     Dim success As Long        ' Additional info about API call
	     
	     ' Initialize the NetResouce structure
	     NetR.dwScope = RESOURCE_GLOBALNET
	     NetR.dwType = RESOURCETYPE_DISK
	     NetR.dwDisplayType = RESOURCEDISPLAYTYPE_SHARE
	     NetR.dwUsage = RESOURCEUSAGE_CONNECTABLE
	     NetR.lpLocalName = vbNullString
	     NetR.lpRemoteName = txtUNC.Text
	
	     ' Initialize the return buffer and buffer size
	     buffer = Space(32)
	     bufferlen = Len(buffer)
	
	     ' Call API to map the drive
	     ErrInfo = WNetUseConnection(Me.hWnd, NetR, txtPWD.Text, txtUser.Text, _
	        CONNECT_REDIRECT, buffer, bufferlen, success)
	
	     ' Check if call to API failed. According to the MSDN help, there
	     ' are some versions of the operating system that expect the userid
	     ' as the 3rd parameter and the password as the 4th, while other
	     ' versions of the operating system have them in reverse order, so
	     ' if first call to API fails, try reversing these two parameters.
	     If ErrInfo <> NO_ERROR Then
	        ' Call API with userid and password switched
	        ErrInfo = WNetUseConnection(Me.hWnd, NetR, txtUser.Text, _
	           txtPWD.Text, CONNECT_REDIRECT, buffer, bufferlen, success)
	     End If
	
	     ' Check for success
	     If (ErrInfo = NO_ERROR) And (success = CONNECT_LOCALDRIVE) Then
	        ' Store the mapped drive letter for later usage
	        MappedDrive = Left$(buffer, InStr(1, buffer, ":"))
	
	        ' Display the mapped drive letter
	        MsgBox "Connect Succeeded to " & MappedDrive
	     Else
	        MsgBox "ERROR: " & Str(ErrInfo) & " - Connect Failed!"
	     End If
	  End Sub
	
	  Private Sub Command2_Click()
	     Dim ErrInfo As Long     ' Return value from API
	
	     ' Call API to disconnect the drive
	     ErrInfo = WNetCancelConnection2(MappedDrive, _
	        CONNECT_UPDATE_PROFILE, False)
	
	     ' Check for success
	     If ErrInfo = NO_ERROR Then
	        MsgBox "Disconnect of '" & MappedDrive & "' Succeeded"
	        
	        ' Clear the mapped drive letter
	        MappedDrive = ""
	     Else
	        MsgBox "ERROR: " & Str(ErrInfo) & " - Disconnect Failed!"
	     End If
	  End Sub
	
	6. Save and run the sample.
	
	7. In the first TextBox, type the UNC path to the share you wish to map to a
	  drive letter (such as, \\ServerName\ShareName).
	
	8. In the second TextBox, type your network logon name.
	
	9. In the third TextBox, type your password.
	
	10. Click the CONNECT button.
	
	  RESULT: Provided you have typed a valid user id, password, network share, and
	  have the appropriate network permissions, you should receive a message
	  indicating that the share was connected and the mapped drive letter is
	  given. You can verify the map by opening the Windows Explorer.
	
	11. Click the DISCONNECT button.
	
	  RESULT: The mapped drive is disconnected. Again, this can be verified with
	  the Windows Explorer.
	
	REFERENCES
	==========
	
	For additional information on creating network connections with API calls from
	Visual Basic, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q173011 HOWTO: Add and Remove Network Connections
	
	Additional query words:
	
	======================================================================
	Keywords          : kbAPI kbVBp kbVBp400 kbVBp500 kbVBp600 kbWNet kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400 kbZNotKeyword3
	Version           : WINDOWS:4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
