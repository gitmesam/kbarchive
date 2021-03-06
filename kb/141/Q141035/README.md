---
layout: page
title: "Q141035: Magic School Bus: Err Msg: CD Audio in Use by Another App"
permalink: /kb/141/Q141035/
---

## Q141035: Magic School Bus: Err Msg: CD Audio in Use by Another App

{% raw %}

	Article: Q141035
	Product(s): Microsoft Home Kids Products
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): kbfaq
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Scholastic's Magic School Bus series: Explores the Ocean for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores Inside the Earth for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to run or install the programs listed at the top of this article,
	you may receive the following error message:
	
	  The CD Audio device is in use by another application.
	  Please close that application and try again.
	
	When you click Cancel, Setup quits.
	
	CAUSE
	=====
	
	This error can occur for one of two reasons:
	
	- You are using the PowerToys FlexiCD program.
	
	  -or-
	
	- You are currently using another program that uses CD Audio.
	
	RESOLUTION
	==========
	
	To resolve the error messages, use the resolution below that is appropriate for
	your error message:
	
	Computers Running Windows 95/98 With FlexiCD
	--------------------------------------------
	
	1. With your right mouse button, click the FlexiCD icon (a compact disc),
	  located next to the clock on the taskbar.
	
	2. On the FlexiCD menu, click Exit FlexiCD.
	
	3. Run Magic School Bus Setup again.
	
	NOTE: To prevent FlexiCD from running when you start Windows, remove the icon
	from the Startup group.
	
	Computers Running Windows 95/98 Without FlexiCD
	-----------------------------------------------
	
	1. Press CTRL+ALT+DELETE to open the Close Program dialog box.
	
	2. Select an item that may be using CD Audio, and then click End Task.
	
	3. Repeat steps 1 and 2 for each item that may be using CD Audio.
	
	NOTE: Several items that often appear in the Close Program dialog box, but do not
	use CD Audio include Explorer, Systray, Sage. Don't select and click End Task
	for these items.
	
	Windows 3.x
	-----------
	
	1. Press and hold down the ALT key while you press the TAB key to cycle through
	  open programs.
	
	2. Select and close any programs that may be using CD Audio.
	
	NOTE: Do not close Program Manager.
	
	After following these steps, Magic School Bus should set up and run successfully.
	
	MORE INFORMATION
	================
	
	About FlexiCD
	-------------
	
	NOTE: The following information comes from the FlexiCD online documentation.
	
	FlexiCD is a quick, convenient audio CD control applet designed for use with
	Windows 95. When running, FlexiCD appears as an icon on the Windows Taskbar.
	
	FlexiCD.exe is available on the Microsoft World Wide Web (WWW) Homepage,
	address:
	
	  http://www.microsoft.com/windows/software/powertoy.htm
	
	The PowerToys warning states:
	
	  WARNING!
	
	  The software and documentation distributed on the PowerToy World-
	  Wide Web site is provided for your personal use and may not be
	  distributed. The entire risk arising out of the use or performance
	  of such products and documentation remains with you. In no event
	  shall Microsoft or its suppliers be liable for any damages
	  whatsoever (including, without limitation, damages for loss of
	  business profits, business interruption, loss of business
	  information, or other pecuniary loss) arising out of the use of or
	  inability to use the products or documentation, even if Microsoft
	  has been advised of the possibility of such damages. Because some
	  states/jurisdictions do not allow the exclusion or limitation of
	  liability for consequential or incidental damages, the above
	  limitation may not apply to you.
	
	Magic School Bus Explores in the Age of Dinosaurs (MSB Dinosaurs) does not
	utilize CD Audio the same way MSB Ocean and MSB Earth do. MSB Dinosaurs
	exclusively uses wave files for sound output. As a result, MSB Dinosaurs does
	not generate the error message described in this article.
	
	Additional query words: 1.00 frizz kbmm multimedia multi-media multi media hang install installation runs hangs msbo cd cd-rom cdrom flexcd flex-cd flexi-cd power toys msbocean msboceans oceans homekids homekid msbearth geology dino dinos dinosaurs msbdinos winmsbdinos
	
	======================================================================
	Keywords          :  kbfaq
	Technology        : kbHomeProdSearch kbZNotKeyword kbKidsSearch kbScholasticOcean kbScholasticEarth kbMSBSearch
	Version           : WINDOWS:1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
