---
layout: page
title: "Q160102: NBA Full Court Press Err Msg: Cannot Initialize Sound System"
permalink: /kb/160/Q160102/
---

## Q160102: NBA Full Court Press Err Msg: Cannot Initialize Sound System

{% raw %}

	Article: Q160102
	Product(s): Microsoft Home Games
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbsound kbimukbfaq
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft NBA Full Court Press for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start NBA Full Court Press, you may receive the following error
	message:
	
	  Cannot Initialize Sound System. Possible solutions:
	
	  - Check to see if you have a sound card installed.
	  - Close any other applications that are using sound.
	  - Restart your machine.
	
	CAUSE
	=====
	
	This behavior can occur for any of the following reasons:
	
	- Windows is running low on system resources.
	
	- Another program that is running is incompatible with NBA Full Court Press.
	
	- A Terminate-and-Stay-Resident program that is running is incompatible with
	  NBA Full Court Press.
	
	- You are using real-mode drivers for your sound card.
	
	- You need to install a newer version of the drivers for your sound card.
	
	RESOLUTION
	==========
	
	Workaround
	----------
	
	To work around the issue, disable the introductory music in NBA Full Court press.
	To do this, follow these steps:
	
	1. On the NBA Full Court Press startup screen, click Options.
	
	2. Click Sound.
	
	3. Move the Music slider bar all the way to the left (the lowest setting), and
	  then click OK.
	
	4. Restart NBA Full Court Press.
	
	Troubleshooting the Problem
	---------------------------
	
	To resolve this issue, follow these steps:
	
	1. Quit all programs that are running before you start NBA Full Court Press.
	
	  If the issue continues to occur, proceed to the next step.
	
	2. Restart the computer to increase available system resources.
	
	  If the issue continues to occur, proceed to the next step.
	
	3. Clean boot the computer to prevent any TSR programs from loading. For
	  additional information about how to clean boot your version of Windows,
	  please see the appropriate following article in the Microsoft Knowledge
	  Base:
	
	  Q177604 Multimedia: Troubleshooting Using Clean Boot of Windows 95
	
	  Q192926 How to Perform Clean-Boot Troubleshooting for Windows 98
	
	  If the issue continues to occur, proceed to the next step.
	
	4. Disable any real-mode sound drivers that are installed in your computer. To
	  do this, follow these steps:
	
	  a. Click Start, point to Programs, point to Accessories, and then click
	     Notepad.
	
	  b. On the File menu, click Open.
	
	  c. In the File Name box, type "c:\autoexec.bat" (without the quotation
	     marks), and then click Open.
	
	  d. At the beginning of each line that contains a reference to your sound
	     drivers, type "rem" (without the quotation marks), and then press the
	     SPACEBAR.
	
	  e. On the File menu, click Save.
	
	  f. On the File menu, click Open.
	
	  g. In the File Name box, type "c:\config.sys" (without the quotation marks),
	     and then click Open.
	
	  h. At the beginning of each line that contains a reference to your sound
	     drivers, type "rem" (without the quotation marks), and then press the
	     SPACEBAR.
	
	  i. On the File menu, click Exit. When you are prompted to save the changes,
	     click Yes.
	
	  j. Restart the computer.
	
	  For additional information about how to troubleshoot sound problems in
	  Microsoft Windows, please see the following article in the Microsoft
	  Knowledge Base:
	
	  Q157487 Games: Troubleshooting Sound Problems
	
	  If the issue continues to occur, proceed to the next step.
	
	5. Obtain and install the latest version of Microsoft DirectX.
	
	  For additional information about how to obtain and install the latest version
	  of DirectX, please see the following article in the Microsoft Knowledge
	  Base:
	
	  Q179113 How to Download and Install DirectX
	
	  If the issue continues to occur, proceed to the next step.
	
	6. Contact your hardware manufacturer to inquire about how to obtain and install
	  the latest version of the drivers for your sound card.
	
	Resolutions for Specific Hardware
	---------------------------------
	
	The following is a list of resolutions for specific sound cards and video
	adapters:
	
	Creative Labs Sound Blaster 16 Sound Cards:
	
	To resolve this issue with a SoundBlaster 16 sound card, remove all files that
	have names that start with "sb" from the Sysbckup folder, and then download and
	install the latest version of the drivers for the sound card. To do this, follow
	these steps:
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type the following line, and then click OK
	
	  <drive>:\windows\sysbckup
	
	  where <drive> is the drive letter for the hard disk on which Windows is
	  installed.
	
	3. In the Sysbckup window, click to highlight the first file that has a name
	  that starts with "sb," and then press and hold down CTRL as you click to
	  highlight any other files that have names that start with "sb."
	
	4. Press DELETE, and then click Yes.
	
	5. Download and install the latest version of the drivers for the sound card
	  from the following Creative Labs web site:
	
	  http://www.soundblaster.com
	
	Ensoniq Soundscape Sound Cards:
	
	To resolve this issue with an Ensoniq Soundscape sound card, download and install
	the latest version of the drivers for the sound card from the following Ensoniq
	Web site:
	
	  http://www.ensoniq.com
	
	IBM MWave Sound Cards
	
	To resolve this issue with an IBM MWave sound card, enable the Use Preferred
	Devices Only feature on the Audio tab in the Multimedia tool in Control Panel.
	To do this, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Multimedia.
	
	3. On the Audio tab, click Use Preferred Devices Only, and then click OK.
	
	STB Video Adapters:
	
	To play the introductory music in NBA Full Court Press on a computer in which an
	STB video adapter is installed, do not use the STB Vision 95 video adapter
	driver when you play NBA Full Court Press. STB also provides a video adapter
	driver with each video card that does not use the Vision 95 features. Use the
	Display tool in Control Panel to install this video adapter driver before you
	play NBA Full Court Press.
	
	When you finish playing NBA Full Court Press, you can reinstall the STB Vision 95
	video adapter driver.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft NBA Full Court Press
	for Windows, version 1.0.
	
	MORE INFORMATION
	================
	
	The third-party products that are discussed in this article are manufactured by
	companies that are independent of Microsoft. Microsoft makes no warranty,
	implied or otherwise, regarding the performance or reliability of these
	products.
	
	Microsoft provides third-party contact information to help you find technical
	support. This contact information may change without notice. Microsoft does not
	guarantee the accuracy of this third-party contact information.
	
	Additional query words: 1.00 direct x ts troubleshoot trouble shoot msgame
	
	======================================================================
	Keywords          : kbenv kberrmsg kbsound kbimu kbfaq
	Technology        : kbGamesSearch kbZNotKeyword kbNBAFullCourtPress
	Version           : WINDOWS:1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
