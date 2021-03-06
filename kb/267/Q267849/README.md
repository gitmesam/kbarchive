---
layout: page
title: "Q267849: PRB: Using Color Cursors in a Visual Basic Application"
permalink: /kb/267/Q267849/
---

## Q267849: PRB: Using Color Cursors in a Visual Basic Application

{% raw %}

	Article: Q267849
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): _IK920 kbAddIn kbColor kbCursor kbVBp kbVBp600 kbGrpDSVB kbDSupport
	Last Modified: 13-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use a color cursor for a form's MousePointer, it appears in black and
	white rather than in color.
	
	CAUSE
	=====
	
	Visual Basic does not provide any support for color cursors and, therefore, a
	color cursor cannot be used while running in the Visual Basic IDE. However, a
	color cursor can be used in compiled Visual Basic applications. Please see the
	"More Information" section for details.
	
	RESOLUTION
	==========
	
	There are two ways to get color cursors in the compiled application:
	
	- You can use Icons instead of actual cursors. These display in color, but the
	  Hot Spot is always at the center of the image and you cannot change it.
	
	- The best solution is to use the LoadResPicture function to load the color
	  cursor(s) from a Resource file. This way the Operating System provides the
	  support and the colors do appear when running the compiled application.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The Resource file can be created with the Visual Basic 6.0 Resource Editor
	Add-In, and the cursor files can be created with the ImagEdit.exe tool included
	with Visual Basic 6.0. The ImagEdit.exe tool is located on Disk 1 of Visual
	Basic, Disk 2 of Microsoft Visual Studio Professional, or Disk 3 of Microsoft
	Visual Studio Enterprise in the following folder:
	
	  \Common\Tools\Vb\Imagedit
	
	This tool also allows you to set the Hot Spot for the cursor, which determines
	the exact point of the image for purposes of clicking, MouseOver event, and so
	forth. When you have the cursor file open, you should have an icon that looks
	like an arrow with lines emanating from the tip in the lower-right of the
	Toolbox. When you click on this icon to select it and then click on the image
	where you want the hot spot to be, you see the coordinates listed in the Toolbar
	where it says "Hotspot."
	
	Step-by-Step Example of Loading Color Cursors from a Resource File
	------------------------------------------------------------------
	
	1. Start a Standard EXE project in Visual Basic. Form1 is created by default.
	
	2. On the Add-Ins menu, click to select Add-In Manager. From the list of
	  Add-Ins, click to select VB 6 Resource Editor, check Loaded/Unloaded in the
	  lower-right of the dialog box, and then click OK.
	
	3. On the Project menu, click to select Add New Resource File. In the Open
	  dialog box, type "ColorCursors.res" (without the quotation marks) for
	  FileName, and then click OK. Click OK again on the dialog box that asks to
	  create this file.
	
	4. On the Properties window, expand Related Documents, and double-click on
	  ColorCursors.res to open the file in the Resource Editor.
	
	5. On the Toolbar, click on the button that looks like an arrow pointer over an
	  hourglass (the Tooltip displays Add cursor...)
	
	6. In the Open dialog box, navigate to the Cursors folder and select a color
	  cursor. By default, Visual Basic creates this folder at this location:
	
	  C:\Program Files\Microsoft Visual Studio\Common\Graphics\Cursors\
	
	  If you are unable to locate this folder it is probably because these graphics
	  were not installed. Either use four other cursors, create four cursors using
	  the ImagEdit.exe tool, or follow instructions in "Steps to Install the Visual
	  Studio Graphics Files" later.
	
	7. Add three more color cursors in this same way. Note that these are numbered
	  101 - 104 in the editor. This is the Resource ID. Close the Editor window.
	
	8. Add a CommandButton control to Form1.
	
	9. Place the following code into the code window of Form1:
	
	  Option Explicit
	
	  Dim ResID As Integer
	
	  Private Sub Command1_Click()
	      If ResID = 104 Then   ' last cursor
	          ResID = 101   ' start over
	      Else
	          ResID = ResID + 1
	      End If
	      Me.MouseIcon = LoadResPicture(ResID, vbResCursor)
	  End Sub
	
	  Private Sub Form_Load()
	      Me.MousePointer = vbCustom
	      ResID = 100   ' Starting value. We add 1 right away before it is used.
	  End Sub
	
	10. Save and compile the project.
	
	11. Press the F5 key to run the project. Each time you click on Command1, the
	  cursor changes, but it is always monochrome (black and white.)
	
	12. Start the Windows Explorer and run the .exe file. Again, each time you click
	  on Command1, the cursor changes, but the cursors now display in their proper
	  colors.
	
	Steps to install the Visual Studio Graphics files
	-------------------------------------------------
	
	1. Make sure that Visual Basic is not running. On the Start menu, locate
	  Settings, select Control Panel, and then double-click on Add/Remove Programs.
	
	2. Select your product from the list. It will either be Microsoft Visual Studio
	  6.0 or Microsoft Visual Basic 6.0 (Professional or Enterprise). Click on the
	  Add/Remove Programs button.
	
	3. From the Setup Maintenance window, click on the Add/Remove Programs button.
	
	4. Select Graphics from the list of Options, and press either Continue or Change
	  Option to select only the types of graphics you want to install. Click OK.
	  Click Continue and follow the instructions on the screen.
	
	The ...\Cursors folder should now be available.
	
	REFERENCES
	==========
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q138529 PRB: Visual Basic 4.0 Does Not Support Color Cursor Files
	
	  Q194409 RESFILE.EXE Stores Any File Type in a Resource File
	
	MSDN Help topic: "Anatomy of a Resource Block" from Hardcore Visual Basic.
	
	Additional query words:
	
	======================================================================
	Keywords          : _IK920 kbAddIn kbColor kbCursor kbVBp kbVBp600 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : :6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
