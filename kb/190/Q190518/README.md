---
layout: page
title: "Q190518: FIX: MFC AppWizard Generates Incorrect Toolbars and Bitmaps"
permalink: /kb/190/Q190518/
---

## Q190518: FIX: MFC AppWizard Generates Incorrect Toolbars and Bitmaps

{% raw %}

	Article: Q190518
	Product(s): Microsoft C Compiler
	Version(s): winnt:6.0
	Operating System(s): 
	Keyword(s): kbservicepack kbwizard kbide kbVC600bug kbVS600sp2 kbFAQ kbVS600SP1 kbVS600sp3fix kbvc6
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The MFC AppWizard (exe) has the following problems when generating applications
	that do not support the Document/View architecture:
	
	- SDI applications that do not support the Document/View architecture have
	  disassociations between their toolbar buttons and their images. These
	  disassociations also exist when Context-sensitive help is supported.
	
	- MDI applications that do not support the Document/View architecture but have
	  Context-sensitive Help do not have a Help toolbar image.
	
	CAUSE
	=====
	
	The MFC AppWizard uses the same toolbar bitmap for both SDI and MDI applications
	that do not support the Document/View architecture. This bitmap is also used
	when Context-sensitive help is selected in MFC AppWizard step 4. This bitmap
	does not contain the Help toolbar image.
	
	In the case of SDI applications, there is no File New toolbar button generated.
	This causes a disassociation between the toolbar buttons and their images. For
	example, the Help About toolbar button has the Print image on it. When
	Context-sensitive help is selected, the Help toolbar button has the Help About
	image on it.
	
	RESOLUTION
	==========
	
	SDI Applications That Do Not Support the Document/View Architecture
	-------------------------------------------------------------------
	
	Add a File New toolbar button by modifying the applications resource File: On the
	File menu, click Open, and open the applications resource file. Select
	<yourapp>.rc file and specify OpenAs Text. Add the following to the
	Toolbar section:
	
	        .
	        .
	
	        ////////////////////////////////////////////////////////////////// 
	        // Toolbar
	
	        IDR_MAINFRAME TOOLBAR DISCARDABLE  16, 15
	        BEGIN
	            BUTTON   ID_FILE_NEW     //<-Add the File New toolbar button.
	            SEPARATOR                //<-Add a toolbar separator.
	            BUTTON      ID_EDIT_CUT
	            BUTTON      ID_EDIT_COPY
	            BUTTON      ID_EDIT_PASTE
	            SEPARATOR
	            BUTTON      ID_FILE_PRINT
	            SEPARATOR
	            BUTTON      ID_APP_ABOUT
	        END
	        .
	        .
	
	SDI Applications Without Document/View Architecture but Support Help
	--------------------------------------------------------------------
	
	Make the above modifications as well as modifying the applications toolbar
	bitmap. You'll need to export a bitmap from the MFC AppWizard resource DLL,
	which has a Help toolbar image:
	
	1. On the File menu, click Open, and open the MFC AppWizard resource DLL.
	  Navigate to the ..\MSDev98\bin\ide directory. Select Mfcapwz.dll and specify
	  OpenAs Resources. Click Ok.
	
	2. Expand the Template directory, right-click Tbah_.bmp, and click Export.
	  Specify a name and directory for the bitmap, and click Export.
	
	3. On the File menu, click Open from the main menu and navigate to the directory
	  where you saved the bitmap. Double-click the bitmap to open it in the
	  resource editor.
	
	4. In the Graphics window, select the Rectangle Selection tool if it is not
	  already selected. Using the mouse, select the Help image by dragging the
	  mouse over it. On the Edit menu, click Copy. NOTE: Toolbar button images are
	  16x15 pixels in size. The area you select should be 16x15 and can be verified
	  in the status bar.
	
	5. In ResourceView, expand the Toolbar folder. Double-click IDR_MAINFRAME to
	  open the Toolbar editor. Select the empty button to the left of the Help
	  About button. On the Edit menu, click Paste. Click the Help About toolbar
	  button. The Help image should now be on the Help toolbar button.
	
	6. Save IDR_MAINFRAME and rebuild the application.
	
	MDI Applications Without Document/View Architecture but Support Help
	--------------------------------------------------------------------
	
	Make the above modifications to include the Help image in your applications
	toolbar bitmap.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3. For more information
	about Visual Studio service packs, please see the following articles in the
	Microsoft Knowledge Base:
	
	Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packs Are Installed
	
	MORE INFORMATION
	================
	
	SDI applications that do not support the Document/View architecture do not have
	File New menu support, because a Frame and View are always created for you when
	the application is run. You can edit the code to include a File New menu and
	handler if you like.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a project using the MFC AppWizard (exe). In step 1, select Single
	  Document and clear Document/View architecture support. Accept the defaults in
	  step 2 and 3. In step 4, select Context-sensitive help and click Finish.
	
	2. Build and run the application. Verify that the toolbar tooltips are
	  incorrect.
	
	3. Create a project using the MFC AppWizard (exe). In step 1, select Multiple
	  Document and clear Document/View architecture support. Accept the defaults in
	  step 2 and 3. In step 4, select Context-sensitive help and click Finish.
	
	4. Build and run the application. Verify that the Help toolbar button has no
	  image.
	
	REFERENCES
	==========
	
	See the following online documentation:
	
	- "Creating a Custom AppWizard:" Visual C++ Documentation, Using Visual C++,
	  Visual C++ Programmer's Guide, Beginning Your Program, Creating a Custom
	  AppWizard.
	
	- "Toolbar Editor:" Visual C++ Documentation, Using Visual C++, Visual C++
	  User's Guide, Resource Editors, Toolbar Editor.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q190977 Custom AppWizard Generates Incorrect Toolbars and Bitmaps
	
	Additional query words: kbvc600bug kbvc600 kbWizard
	
	======================================================================
	Keywords          : kbservicepack kbwizard kbide kbVC600bug kbVS600sp2 kbFAQ kbVS600SP1 kbVS600sp3fix kbvc600faq 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
