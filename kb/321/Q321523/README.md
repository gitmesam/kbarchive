---
layout: page
title: "Q321523: TN3270 Clients May Receive Error From Host When Pressing AID Key"
permalink: /kb/321/Q321523/
---

## Q321523: TN3270 Clients May Receive Error From Host When Pressing AID Key

{% raw %}

	Article: Q321523
	Product(s): Microsoft SNA Server
	Version(s): 4.0 SP3,4.0 SP4
	Operating System(s): 
	Keyword(s): kbsna400sp3 kbhis2000 kbhis2000bug kbsna400sp4
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0 SP3, 4.0 SP4 
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When a user who connects to a host application by using TN3270 Server presses an
	Attention Identifier (AID) key, the user may receive an error message from the
	host application.
	
	The error that may occur depends upon the host application to which the user is
	trying to connect. The error message may give an indication that a terminal
	input error has occurred.
	
	CAUSE
	=====
	
	The TN3270 Server that is included with SNA Server 4.0 SP3 includes a change
	that corrects the problem described in the following Knowledge Base article:
	
	  Q236785 TN3270 Client Sessions Fail with sec_rc=0x00000320 (LUA_BRACKET)
	
	The change that was implemented permits the TN3270 server to change the keyboard
	restore bit in the Write Control Character (WCC) so that the keyboard remains
	locked when the user's computer receives a Request Unit (RU) from the host
	application that has the End Chain (EC) flag set, but does not have the End
	Bracket (EB) flag or the Change Direction (CD) flag set.
	
	The problem described here occurs when the TN3270 server changes the keyboard
	restore bit so that the keyboard remains locked when the user's computer
	receives an RU from the host application that has the EC flag set. In this case,
	the RU from the host application is in response to an AID key that the user
	entered in the TN3270 emulator.
	
	RESOLUTION
	==========
	
	The TN3270 server was updated in SNA Server 4.0 SP4 to allow an option to turn
	off all keyboard restore modifications that occur by default. You can prevent
	the problem described here by setting the following registry entry.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	To set the registry entry, follow these steps:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Click the following registry key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\TN3270\Parameters
	
	3. On the Edit menu, click Add Value, and then add the following registry
	  value:
	
	  Value name: ModifyWCC
	  Data type: REG_SZ
	  Value data: NO
	
	  NOTE: You must enter the NO value in uppercase letters.
	
	4. Quit Registry Editor.
	
	The ModifyWCC registry entry is also a valid option when you run Host Integration
	Server (HIS) 2000. For additional information about why the ModifyWCC registry
	option was added, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q268171 TN3270 Application May Process a Screen of Host Data Twice
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server 4.0 SP3,
	SP4, and Host Integration Server 2000.
	
	MORE INFORMATION
	================
	
	In the reported instance of this problem, users pressed the Program Attention 2
	(PA2) key, which is an AID key, while connected to a host application, to
	perform an application-specific function. After they upgraded to SNA Server 4.0
	SP3, when they pressed the PA2 key, these users received the following error
	message from the host application:
	
	  "DR1R9805 Terminal input error. Press Enter to recover."
	
	This problem did not occur when using a previous version of SNA Server 4.0.
	
	The following is a sample data flow that shows the failing scenario:
	
	+------------------------------------------------------------------------------+
	| TN3270 Emulator    | TN3270 Server               | Host                      | 
	+------------------------------------------------------------------------------+
	| PA2 Key(x'6E') ->  |                             |                           | 
	+------------------------------------------------------------------------------+
	|                    | PA2 Key(x'6E') ->           |                           | 
	+------------------------------------------------------------------------------+
	|                    |                             | <- x'F182' (Write, WCC -  |
	|                    |                             |       Keyboard Unlocked)  | 
	+------------------------------------------------------------------------------+
	|                    | <- x'0180' (Write, WCC -    |                           |
	|                    |         Keyboard Locked)    |                           | 
	+------------------------------------------------------------------------------+
	|                    |                             | <- x'F6' (Read Modified)  | 
	+------------------------------------------------------------------------------+
	|                    | <- x'06' (Read Modified)    |                           | 
	+------------------------------------------------------------------------------+
	| PA2 Key (x'6E') -> |                             |                           | 
	+------------------------------------------------------------------------------+
	|                    | PA2 Key (x'6E') ->          |                           | 
	+------------------------------------------------------------------------------+
	|                    |                             | <- -RSP                   | 
	+------------------------------------------------------------------------------+
	|                    | <- NACK-1 (x'1003')         |                           | 
	+------------------------------------------------------------------------------+
	|                    |                             | <- Terminal Input         | 
	|                    |                             |     Error message         | 
	+------------------------------------------------------------------------------+
	
	The problem occurs because the TN3270 server changes the keyboard restore bit in
	the WCC that the host application sends in the RU that contains the 3270 Write
	Command and WCC, after the application receives the PA2 key.
	
	The keyboard restore bit in the WCC also resets the AID byte and unlocks the
	keyboard (when the keyboard restore bit is set to 1). The host application has
	set the keyboard restore bit (Bit 6 in the WCC byte) to reset the AID byte in
	the display buffer of the TN3270 emulator. The problem occurs when the AID byte
	is not reset because the keyboard restore bit was set to 0. The following 3270
	Read Modified command reads the previous AID byte (PA2 key) in the display
	buffer of the emulator, and then the PA2 key is sent to the host application a
	second time, which causes the -RSP and the terminal input error message.
	
	The following Knowledge Base articles describe some additional issues that
	resulted in changes to the TN3270 server to allow modifications of the keyboard
	restore bit:
	
	  Q175384 TN3270 Client Hangs with Keyboard Locked on Some Host Screens
	
	  Q275896 SNA Server Rejects TN3270 Client Data with Sense Code 200D
	
	For more details about the 3270 Data Stream commands and AID keys, see the
	following:
	
	  IBM 3270 Information Display System Data Stream Programmer's Reference
	  (GA23-0059)
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna400sp3 kbhis2000 kbhis2000bug kbsna400sp4 
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ400SP3 kbSNAServ400SP4
	Version           : :4.0 SP3,4.0 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
