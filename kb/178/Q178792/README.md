---
layout: page
title: "Q178792: Tutor: Error Message: Unable to Initialize Direct Draw"
permalink: /kb/178/Q178792/
---

## Q178792: Tutor: Error Message: Unable to Initialize Direct Draw

{% raw %}

	Article: Q178792
	Product(s): Microsoft Home Kids Products
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): kbdisplay kbenv kberrmsgkbfaq
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft My Personal Tutor: Preschool Workshop, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to start My Personal Tutor: Preschool Workshop, you may receive
	the following error message:
	
	  Unable to initialize Direct Draw. Try running setup again. If the problem
	  persists, you may need to contact your display card manufacturer for new
	  display drivers. Workshop will now exit.
	
	
	CAUSE
	=====
	
	You can receive this error message for one or more of the following reasons:
	
	- Incorrect or mismatched versions of the DirectDraw .dll files are installed.
	
	- Your video driver is incompatible with your video adapter.
	
	- The display settings in Microsoft Windows 95 are incorrect.
	
	RESOLUTION
	==========
	
	To resolve this issue, use the troubleshooting sections below. After you
	complete the steps in each section, test My Personal Tutor: Preschool Workshop
	to determine if the issue is resolved.
	
	NOTE: Incorrect or mismatched versions of the DirectDraw .dll files is the most
	common cause of this error message. Try the "Remove and Then Reinstall the
	DirectDraw .dll Files" troubleshooting section first; if it does not resolve the
	issue, proceed to the troubleshooting sections later in this article.
	
	Remove and Then Reinstall the DirectDraw .dll Files
	---------------------------------------------------
	
	To remove and reinstall the DirectDraw .dll files, follow these steps:
	
	1. Click Start, point to Find, and then click Files Or Folders.
	
	2. In the Named box, type "ddraw.dll, ddraw16.dll, ddhelp.exe" (without the
	  quotation marks), and then press ENTER.
	
	3. On the Edit menu, click Select All.
	
	4. Press the DELETE key. If you are prompted to confirm the file deletion, click
	  Yes.
	
	5. Restart your computer, and then reinstall My Personal Tutor: Preschool
	  Workshop.
	
	Check Your Windows 95 Display Settings
	--------------------------------------
	
	Change your display resolution to 640 x 480 and your color display setting to 256
	colors. To do this, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Display.
	
	3. Click the Settings tab.
	
	4. In the Color Palette box, click 256 Color.
	
	5. Move the Desktop Area slider all the way to the left. ("640 x 480 pixels" is
	  displayed under the slider.)
	
	6. Click OK.
	
	7. Click Yes if you are prompted to restart your computer. If your settings did
	  not change, you do not need to restart your computer.
	
	Reduce the Graphics Hardware Acceleration
	-----------------------------------------
	
	To reduce the graphics hardware acceleration, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System.
	
	3. Click the Performance tab, and then click Graphics.
	
	4. Move the Hardware Acceleration slider until it is one notch to the right of
	  None (the Basic acceleration setting).
	
	5. Click OK, and then click OK.
	
	6. Click Yes to restart the computer.
	
	Install the VGA Video Driver and Then Install Your Original Video Driver
	------------------------------------------------------------------------
	
	To install the standard VGA video driver, and then install your original video
	driver, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Display.
	
	3. Click the Settings tab, and then click Change Display Type.
	
	  NOTE: If you are using Microsoft Windows 95 OEM Service Release 2 (OSR2),
	  click Advanced Properties.
	
	4. Click Change next to the Adapter Type box.
	
	  NOTE: If you are using OSR2, click Change on the Adapter tab.
	
	5. Click Show All Devices.
	
	6. In the Manufacturers box, click Standard Display Types.
	
	7. In the Models box, click Standard Display Adapter (VGA), and then click OK.
	
	8. Click Close, and then click Close.
	
	9. Click Yes to restart the computer.
	
	10. When Windows 95 starts, reinstall your original video driver from the CD-ROM
	  or floppy disk provided by your computer manufacturer, or contact your video
	  adapter manufacturer to obtain the latest video driver available for your
	  video adapter.
	
	  For additional information about how to install a video driver in Windows 95,
	  please see the following article in the Microsoft Knowledge Base:
	
	  Q131806 Windows 95/98: How to Install or Change a Display Driver
	
	Additional query words: 1.00 MPT kids mskids
	
	======================================================================
	Keywords          : kbdisplay kbenv kberrmsg kbfaq
	Technology        : kbHomeProdSearch kbZNotKeyword kbKidsSearch kbMPTPreschool
	Version           : WINDOWS:1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
