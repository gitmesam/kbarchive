---
layout: page
title: "Q158074: XCLN: Using ShivaRemote w/ Exchange (MS-DOS/Real-Mode IPX)"
permalink: /kb/158/Q158074/
---

## Q158074: XCLN: Using ShivaRemote w/ Exchange (MS-DOS/Real-Mode IPX)

{% raw %}

	Article: Q158074
	Product(s): Microsoft Exchange
	Version(s): MS-DOS:4.0,5.0
	Operating System(s): 
	Keyword(s): kbenv kbsetup kbusage
	Last Modified: 14-JAN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange MS-DOS client, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	ShivaRemote software can be used with the Microsoft Exchange MS-DOS client to
	allow users to remotely access a computer running Microsoft Exchange Server
	(either by means of a computer running Windows NT with RAS or Shiva LanRover).
	This article discusses the steps necessary to install and configure the
	ShivaRemote software that ships with Microsoft Exchange Client to work
	specifically over the IPX protocol. (For information about setting up Shiva for
	use over other protocols, see the Reference section below).
	
	When using ShivaRemote with the Microsoft Exchange MS-DOS client, you must first
	run Connect.exe from the Microsoft Exchange Client directory, establish the
	remote connection, and then start the Microsoft Exchange MS- DOS client. This is
	necessary because the Microsoft Exchange MS-DOS client does not have any
	built-in remote functionality. Therefore, with the Microsoft Exchange MS-DOS
	client, there is no way to download only the message headers (remote mail
	functionality).
	
	MORE INFORMATION
	================
	
	You may see the following error message:
	
	  Warning: Your IPX network number changed during connection. IPX services may
	  not function properly.
	
	This error should not cause a problem using the Microsoft Exchange MS-DOS client.
	Simply press ENTER and continue. In the Microsoft Exchange Windows 3.x client,
	the IPX network number assigned to your computer changed while you were
	connected to the remote access server. This can happen if you dial in to two
	different remote networks in one session without restarting your computer
	between connections. If you are using the Novell NetWare VLMs Version 1.2 or
	later and ShivaRemote 3.5, you can ignore this error message and your
	IPX-dependent software will function without errors. The later versions of the
	VLMs have been designed to handle this problem better than earlier versions.
	This warning message can be turned off by editing the Sremote.ini file and
	changing the following line:
	
	  [Options] NotifyIPXAddress=No
	
	If you are not using the NetWare VLMs, or if you are using a version of VLMs
	earlier than version 1.2, close the Dial-In connection and restart your
	computer. Then dial in to the remote network again.
	
	Installation of the Software
	----------------------------
	
	During installation of the Microsoft Exchange MS-DOS client there is a dialog box
	to select whether or not ShivaRemote should be installed. There is not a
	separate Setup program for the MS-DOS version of ShivaRemote. Therefore, if you
	are an MS-DOS-based user and you install the Microsoft Exchange MS-DOS client
	without ShivaRemote, and at a later date require it, you will need to rerun
	Setup of the Microsoft Exchange MS-DOS client. For MS-DOS, all of the
	ShivaRemote files are copied to the Microsoft Exchange client directory.
	
	Follow these steps to configure ShivaRemote for dial-in:
	
	1. Manually edit your Autoexec.bat and Config.sys files as follows:
	
	     Config.sys
	     ----------
	     device=c:\dos\setver.exe
	     device=c:\dos\himem.sys
	     device=c:\dos\emm386.exe noems
	     shell=c:\dos\command.com /p
	     dos=high,umb
	     lastdrive=z
	
	     autoexec.bat
	     ------------
	     c:\<path>\lsl.com
	     c:\exchange_dir\dialodi.exe
	     c:\<path>\ipxodi
	     c:\<path>\vlm (or netx)
	     set exchange=c:\exchange_dir
	     set RPC_Binding_Order=ncacn_np,ncalrpc,ncacn_spx,netbios
	
	  The net.cfg (nwclient directory)
	  --------------------------------
	
	     preferred server=servername
	     Link Driver DIALODI
	
	  Make sure you receive no error messages when starting with the newly
	  configured Autoexec.bat and Config.sys files.
	
	2. Run Connect.exe from the Microsoft Exchange install directory.
	
	3. On the Tools menu, click Port Setup, and select the appropriate modem and com
	  port.
	
	4. Click the Options button and select the IPX (only) check box.
	
	5. Specify a Description, Dial-in-Name (a Windows NT account that has been
	  granted dial-in access on the server), Password (a password for the Windows
	  NT account you are dialing in on), and Phone number. Note the account does
	  not necessarily have to be the Exchange Mailbox Primary Windows NT account.
	
	6. Dial the computer running RAS. (Microsoft Exchange Server supports dialing
	  into either a Windows NT RAS server or a Shiva LanRover.)
	
	7. Once connected, quit ShivaRemote Connect (on the File menu, click Exit).
	
	  NOTE: The connection is maintained until you start Connect.exe again and click
	  Disconnect.
	
	8. Start the Microsoft Exchange MS-DOS client. Type the User Name (Exchange
	  Mailbox Name), the Password (Windows NT Domain Password), and the Domain
	  (Windows NT Domain Name that your Account is in).
	
	REFERENCES
	==========
	
	Updated modem scripts for use with ShivaRemote can be found on Shiva's Web page
	at www.shiva.com under "support"/modem scripts.
	
	Additional configuration information may also be found in the config.hlp file
	installed during installation of the ShivaRemote software.
	
	For additional information on supported Shiva configurations for use with
	Microsoft Exchange Server, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q158124 ShivaRemote with Exchange - RAS Server Considerations
	
	  Q158095 Using ShivaRemote with Exchange (Windows 3.x/LanMan NetBEUI)
	
	  Q157740 Using ShivaRemote with Exchange (DOS/LanMan TCP/IP)
	
	  Q158077 Using ShivaRemote with Exchange (Windows 3.x/real-mode IPX)
	
	For additional information on server configuration, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q158124 XCLN: ShivaRemote with Exchange - RAS Server Considerations
	
	A white paper on ShivaRemote is located on Microsoft TechNet and can also be
	found on the following World Wide Web location:
	
	  http://www.microsoft.com/ExchangeSupport/
	
	
	Additional query words: remote mail
	
	======================================================================
	Keywords          : kbenv kbsetup kbusage 
	Technology        : kbExchangeSearch kbExchangeClientSearch kbZNotKeyword3 kbExchange400DOS kbExchange500DOS
	Version           : MS-DOS:4.0,5.0
	
	=============================================================================
	

{% endraw %}
