---
layout: page
title: "Q131868: How to Troubleshoot PCMCIA Modems in Windows NT"
permalink: /kb/131/Q131868/
---

## Q131868: How to Troubleshoot PCMCIA Modems in Windows NT

{% raw %}

	Article: Q131868
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.51,4.0
	Operating System(s): 
	Keyword(s): kbhw kbHardware
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51, 4.0 
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them.
	Microsoft cannot guarantee that any problems resulting from the use of
	Registry Editor can be solved. Use this tool at your own risk.
	
	SUMMARY
	=======
	
	This article describes how to troubleshoot a PC Card (PCMCIA) modem in Windows
	NT. The following topics are discussed:
	
	- Windows NT does not recognize the modem
	
	- Terminal or HyperTerminal stops responding (hangs)
	
	- Remote Access Service (RAS) does not function properly
	
	- The modem makes no sound when dialing
	
	MORE INFORMATION
	================
	
	Windows NT Does Not Recognize the Modem
	---------------------------------------
	
	To resolve this issue, follow these steps:
	
	1. Verify that the PC Card modem you are trying to install is on the Windows NT
	  Hardware Compatibility List (HCL). If the PC Card modem is not on the HCL,
	  Microsoft has not tested it and it is not supported by Microsoft.
	
	2. Verify that the PC Card modem is fully inserted into the PC card socket
	  before you turn on your computer. If necessary, turn off your computer,
	  insert the PC Card modem into the PC Card socket, and then turn on your
	  computer.
	
	3. Verify that the PC Card modem is functioning properly by using a
	  manufacturer-provided diagnostics program or the Pcmcmd.exe support program.
	  The Pcmcmd.exe support program displays the hardware information from the PC
	  Card modem. If the Pcmcmd.exe support program is unable to display any
	  hardware information for the PC Card modem, the PC Card modem may be
	  defective.
	
	  NOTE: The Pcmcmd.exe support program is located on the Windows NT CD-ROM in
	  the \Support\Debug\<hardware platform> folder.
	
	4. In Control Panel, double-click Ports to see if an additional COM port is
	  listed. If an additional COM port is listed, the PC Card modem is enabled.
	  Verify that the IRQ settings and the I/O addresses are correct. Use Event
	  Viewer to view the System log and check for I/O or IRQ conflicts.
	
	  NOTE: If possible, use the following standard settings for your COM ports:
	
	  SERIAL 1   COM1:  I/O Address = 3F8h   IRQ = 4
	  SERIAL 2   COM2:  I/O Address = 2F8h   IRQ = 3
	  SERIAL 3   COM3:  I/O Address = 3E8h,  IRQ = 4
	  SERIAL 4   COM4:  I/O Address = 2E8h,  IRQ = 3
	
	  Many manufacturers include a configuration program that configures the PC
	  Card's IRQ, slot location, and sound settings. This program can be used to
	  modify the PC Card's settings so that conflicts do not occur.
	
	5. In Control Panel, double-click Devices to determine if the PCMCIA driver
	  startup is configured as Boot. The PCMCIA driver activates all PC Card
	  devices , and if this driver does not start, no PC Card can work. If the
	  driver is set to start automatically but does not start automatically, use
	  Event Viewer to view the System log and check for errors.
	
	
	6. Because there are many different PC Card chipsets available, some PC Cards do
	  not work properly with some computers. To determine if this is the case, test
	  your PC Card in a different computer, or test a different PC Card in your
	  current computer.
	
	
	Terminal or HyperTerminal Stops Responding (Hangs)
	--------------------------------------------------
	
	To resolve this issue, follow these steps:
	
	1. Verify that Windows NT recognizes your modem by following the steps in the
	  "Windows NT Does Not Recognize the Modem" section of this article.
	
	2. If first in, first out (FIFO) is not supported by your PC Card modem, you
	  must disable FIFO. To do so, follow these steps:
	
	  a. In Control Panel, double-click Ports, click Settings, click the port that
	     your PC Card modem is configured for, and then click Settings.
	
	  b. Click Advanced, click the FIFO Enabled check box to clear it, click OK,
	     and then restart your computer when you are prompted to do so.
	
	Remote Access Service (RAS) Does Not Function Properly
	------------------------------------------------------
	
	To resolve this issue, follow these steps:
	
	1. Verify that the Terminal or HyperTerminal program functions properly. If your
	  PC Card modem works with these programs, verify that the modem type is being
	  detected correctly, and that the speed setting is correctly configured.
	
	2. If you experience dropped connections or noisy phone lines, lower your
	  modem's connection speed and then test to see if the issue is resolved.
	
	3. Verify that your phone cable is functioning properly by using a different
	  cable, and then test to see if the issue is resolved.
	
	4. Change the Logging value in the following registry key to 1:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\RasMan\Parameters
	
	  Restart your computer, try to connect again, and then view the Device.log file
	  in the %SYSTEMROOT%\SYSTEM32\RAS folder for information about commands that
	  the modem is sending and errors that are reported.
	
	The Modem Makes No Sound When Dialing
	-------------------------------------
	
	To resolve this issue, follow these steps:
	
	1. Consult the manufacturer's documentation or contact the manufacturer to
	  verify that your modem normally makes a dialing sound. Some modems emit a
	  series of clicks when waiting for a dial tone, dialing, or waiting for an
	  answer.
	
	2. To verify that your modem's speaker is not disabled, consult the modem
	  manufacturer's documentation. On some modems, the speaker is disabled by
	  default.
	
	  NOTE: The AT command "AT M1" (without the quotation marks) usually enables the
	  modem speaker.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbhw kbHardware 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : winnt:3.51,4.0
	
	=============================================================================
	

{% endraw %}
