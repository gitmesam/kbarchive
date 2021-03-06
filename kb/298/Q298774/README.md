---
layout: page
title: "Q298774: How to Troubleshoot Modem Problems in Windows Dial-up Networking"
permalink: /kb/298/Q298774/
---

## Q298774: How to Troubleshoot Modem Problems in Windows Dial-up Networking

{% raw %}

	Article: Q298774
	Product(s): The Microsoft Network
	Version(s): 2.0,2.5,2.5 (OEM Release),2.51,2.52,2.6,5.0,5.1,5.2,5.3,5.4,6.0,6.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 28-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Network versions 2.0, 2.5, 2.5 (OEM Release), 2.51, 2.52, 2.6, 5.0, 5.1, 5.2, 5.3, 5.4, 6.0, 6.1 
	- The Microsoft Network Version 7.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes procedures to help you diagnose and fix issues when you
	cannot dial out by using your modem in Microsoft Windows 98 and Microsoft
	Windows 98 Second Edition.
	
	MORE INFORMATION
	================
	
	Windows-Only Modem Troubleshooting
	----------------------------------
	
	Windows-only modems require drivers that are specific to the operating system to
	function. Because of this, the modem must be recognized by the operating system
	before you can perform any troubleshooting to the operating system, associated
	applications, or via the command prompt in MS-DOS mode.
	
	Windows 98 and Windows 98 Second Edition typically detect a Windows-only modem
	and add the modem to Device Manager. If a Windows-only modem is not detected,
	there can be one of three causes:
	
	- The Windows-only modem was previously detected (whether drivers were
	  installed for it or not).
	  In this case, the Windows-only modem should be listed in Device Manager.
	  Note: You can update the driver by using the procedure that is described in
	  the "Verify Modem Type and Model" section of this article.
	
	- You installed and then uninstalled the Windows-only modem drivers, but some
	  registry entries remain.
	  You must remove the registry entries before the Windows-only modem can be
	  detected again. For 3Com US Robotics modems, use the Wmregdel.exe tool
	  included on the Windows 98/98 Second Edition CD-ROM to clear all of the
	  Windows-only modem-related registry entries, and then restart your computer.
	  The Wmregdel.exe tool is located in the Drivers\Modem\3com-usr\Winmodem
	  folder on the Windows 98/98 Second Edition CD-ROM. If Windows 98/98 Second
	  Edition still does not detect your Windows-only modem, the Wmregdel.exe tool
	  may not have removed all of the necessary registry entries. To resolve this
	  issue, contact 3Com or US Robotics to inquire about the availability of a fix
	  for this issue.
	
	- Something is physically wrong with the Windows-only modem.
	  Contact your modem manufacturer for the correct procedure to test your
	  Windows-only modem.
	
	If no default drivers exist in Windows 98 or Windows 98 Second Edition for your
	Windows-only modem, Windows 98 or Windows 98 Second Edition prompts you to
	search for drivers.
	
	Drivers for your Windows-only modem may exist in the Drivers\Modem folder on the
	Windows CD-ROM. For a complete list of additional modem drivers that are
	included on the CD-ROM, view the following article in the Microsoft Knowledge
	Base:
	
	Q190363Additional Modem Drivers Included on the Windows CD-ROM.
	If you cannot locate drivers for your Windows-only modem, Windows 98 and Windows
	98 Second Edition add it under the Other Devices branch in Device Manager. You
	can update the existing drivers in Device Manager with drivers that are provided
	by your Window-only modem manufacturer. Note that Microsoft Windows 95 drivers
	often work in Windows 98 or Windows 98 Second Edition.
	
	If you cannot locate drivers for your Windows-only modem, Windows 98 and Windows
	98 Second Edition add it under the Other Devices branch in Device Manager. You
	can update the existing drivers in Device Manager with drivers that are provided
	by your Window-only modem manufacturer. Note that Microsoft Windows 95 drivers
	often work in Windows 98 or Windows 98 Second Edition.
	
	If your Windows-only modem still does not work after you install the drivers,
	there may be a resource conflict or an issue that is specific to your
	Windows-only modem. To determine if this is the case, view one of the following
	sections, depending on your modem.
	
	For more information about Windows-only modems and how to troubleshoot them,
	obtain the US Robotics Windows-only modem FAQ from the following U.S. Robotics
	Web site:
	
	http://www.usr.com/home/online/trblshot/13011.htm
	
	Verify That You Are Using the Most Current Driver for Your Modem
	----------------------------------------------------------------
	
	Many modem issues relate to using an old or out-of-date modem driver. Because of
	this, you should verify that you are using the most current driver for your
	modem. To verify your driver, contact the manufacturer of your modem to inquire
	about the availability of a new or updated modem driver.
	
	For additional information about how to locate contact information for your modem
	manufacturer, click the article numbers below to view the articles in the
	Microsoft Knowledge Base:
	
	Q65416 Hardware and Software Third-Party Vendor Contact List, A-K
	Q60781 Hardware and Software Third-Party Vendor Contact List, L-P
	Q60782 Hardware and Software Third-Party Vendor Contact List, Q-Z
	
	Site for downloading modem drivers for Compaq
	---------------------------------------------
	
	http://www6.compaq.com/support/files/networking/modems/56K.html
	
	Driver download page for LTWin modems
	-------------------------------------
	
	http://www.lucent.com/micro/K56flex/driver2.html
	
	Errors that relate to Windows Millennium
	----------------------------------------
	
	Windows Millennium Edition (Me) Dial-Up Networking connections have software
	compression enabled by default, but the "Log on to Network" feature is not
	enabled by default.
	
	When the Log on to Network option is enabled, the Dial-Up Networking service
	attempts to find a Microsoft Windows network. If it does not find one, it times
	out. This behavior causes the delay when you log on to an Internet provider,
	since the Point-to-Point Protocol (PPP) server for the Internet Service Provider
	(ISP) will not be running a Microsoft Windows network. Disabling the Log On To
	Network option decreases this delay. In most cases, the PPP server will be
	running only the TCP/IP protocol. Removing the NetBEUI and IPX/SPX protocols
	from the connection file or "connectoid" saves a few more seconds by not trying
	to bind these protocols to the dial-up adapter.
	
	When troubleshooting , please verify "log on to network" is disabled.
	
	Dial-Up Networking "Error 630" Error Message
	--------------------------------------------
	
	When you attempt to use Dial-Up Networking, you may receive the following error
	message:
	
	  Error 630: The computer is not receiving a response from the modem. Check
	  that the modem is plugged in, and if necessary, turn the modem off, and then
	  turn it back on.
	
	You may receive this error message if the modem is using a new serial port
	assignment due to new devices that are installed by Windows 98/98 Second Edition
	hardware detection. If this occurs, change the properties of the Dial-Up
	Networking connection to use the new modem settings.
	
	Programs in the Startup folder can also cause this error message. To disable
	programs in the Startup folder, follow the steps in the "'Could Not Open Port'
	Error Message" section in this article (below).
	
	Dial-Up Networking "Error 633" Error Message
	--------------------------------------------
	
	When you attempt to use Dial-Up Networking, you may receive the following error
	message:
	
	  Error 633: The modem is not installed or configured for Dial-Up Networking.
	  To check your modem configuration, double click the Modems icon in Control
	  Panel.
	
	This error message can occur if the Telephon.ini file is absent or damaged. To
	resolve this issue, view the following articles in the Microsoft Knowledge
	Base:
	
	Q191444 Error Message: The Modem Is Not Installed or Configured for...
	Q120221 How to Rebuild the Telephon.ini File
	
	This error may also occur if the modem is in conflict with another hardware
	device. Check Device Manager for conflicting devices.
	
	Note: Device Manager may not display an actual problem with conflicting devices
	due to IRQ Steering. Look at the IRQ lists, etc., to see actual device usage.
	
	Could Not Open Port" Error Message
	----------------------------------
	
	When you try to use your modem, you may receive the following error message:
	
	  Could not open port
	
	This error message typically occurs because a resource conflict or a program
	loading from the Startup folder opens a Component serial communications (COM)
	port. Use the troubleshooting steps in the "Resource Conflicts" section in this
	article to resolve this issue.
	
	To temporarily disable programs in the StartUp folder
	
	1. Click Start, point to Programs, point to Accessories, point to System Tools,
	  and then click System Information.
	
	2. On the Tools menu, click System Configuration Utility.
	
	3. Click the Startup tab.
	
	4. For programs that may control your modem, clear the box for the program.
	  Note: If you are unsure whether or not a specific program should be disabled,
	  clear all of the check boxes except the following check boxes:
	   - ScanRegistry
	
	   - SystemTray
	
	   - LoadPowerProfile
	
	   - TaskMonitor
	
	Dial-Up Networking "Error 745" Error Message
	--------------------------------------------
	
	When you attempt to use Dial-Up Networking, you may receive the following error
	message:
	
	  Error 745: An essential file is missing. Re-install Dial-Up Networking.
	
	You may receive this error message if a Dial-Up Networking dynamic-link library
	(.dll) file is absent or damaged. To resolve this issue, view the following
	article in the Microsoft Knowledge Base:
	
	Q174579 Error Message: Error 745: An Essential File Is Missing
	
	Telephony Application Programming Interface (TAPI) Issues
	---------------------------------------------------------
	
	If your modem passes a diagnostics test but is not available in HyperTerminal,
	Dial-Up Networking, or Phone Dialer, a Telephony Application Programming
	Interface (TAPI) issue may exist--the Telephon.ini file may be absent or
	damaged.
	
	To resolve this issue
	
	- - View the following articles in the Microsoft Knowledge Base:
	
	Q191444 Error Message: The Modem Is Not Installed or Configured for...
	Q120221 How to Rebuild the Telephon.ini File
	
	Additional query words: kbimu; MSN Explorer
	
	======================================================================
	Keywords          :  
	Technology        : kbMSNSearch kbMSN600 kbMSN610 kbMSN520 kbMSN530 kbMSN510 kbMSN500 kbMSN200 kbMSN252 kbMSN251 kbMSN260 kbMSN250 kbMSN250OEM kbMSN540 kbMSN700
	Version           : :2.0,2.5,2.5 (OEM Release),2.51,2.52,2.6,5.0,5.1,5.2,5.3,5.4,6.0,6.1
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
