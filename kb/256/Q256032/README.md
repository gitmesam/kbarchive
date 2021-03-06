---
layout: page
title: "Q256032: XFOR: Exchange Server 5.5 Post-SP3 Connector Fixes Available"
permalink: /kb/256/Q256032/
---

## Q256032: XFOR: Exchange Server 5.5 Post-SP3 Connector Fixes Available

{% raw %}

	Article: Q256032
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): exc55kbfixlist
	Last Modified: 16-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article lists the article numbers for the Exchange Server version 5.5
	Exchange Connector for Lotus Notes, Exchange Connector for SNADS, Exchange
	Connector for IBM OfficeVision/VM (PROFS), and Exchange Connector for Novell
	GroupWise bugs that were fixed after Exchange Server 5.5 Service Pack 3 (SP3)
	was released. For information about how to obtain the fixes listed in this
	article, click the article number next to the title of the article about that
	issue to view the article in the Microsoft Knowledge Base.
	
	NOTE: Exchange Server fixes for a particular component are cumulative and contain
	all of the previous fixes for that component. Fixes with a particular version
	number contain all of the fixes that have an earlier version number.
	
	MORE INFORMATION
	================
	
	Exchange Server connector fixes include the following files:
	
	+--------------------------------+
	| File name    | Current version | 
	+--------------------------------+
	| Ctreestd.dll | 5.5.2651.86     | 
	+--------------------------------+
	| Dispatch.exe | 5.5.2651.86     | 
	+--------------------------------+
	| Dxagwise.dll | 5.5.2652.0      | 
	+--------------------------------+
	| Dxamex.dll   | 5.5.2652.0      | 
	+--------------------------------+
	| Dxanotes.dll | 5.5.2652.0      | 
	+--------------------------------+
	| Exconmsg.dll | 5.5.2651.86     | 
	+--------------------------------+
	| Gw2mex.exe   | 5.5.2652.0      | 
	+--------------------------------+
	| Gwhc.dll     | 5.5.2652.0      | 
	+--------------------------------+
	| Gwrouter.exe | 5.5.2651.83     | 
	+--------------------------------+
	| Lscms.dll    | 5.5.2652.0      | 
	+--------------------------------+
	| Lsdiamex.exe | 5.5.2652.0      | 
	+--------------------------------+
	| Lsdxa.exe    | 5.5.2652.0      | 
	+--------------------------------+
	| Lsldew.dll   | 5.5.2652.0      | 
	+--------------------------------+
	| Lsmexdia.exe | 5.5.2652.0      | 
	+--------------------------------+
	| Lsmexhc.dll  | 5.5.2652.0      | 
	+--------------------------------+
	| Lsmexif.dll  | 5.5.2652.0      | 
	+--------------------------------+
	| Lsmexin.exe  | 5.5.2652.0      | 
	+--------------------------------+
	| Lsmexnts.exe | 5.5.2652.0      | 
	+--------------------------------+
	| Lsntshc.dll  | 5.5.2652.0      | 
	+--------------------------------+
	| Lsntsmex.exe | 5.5.2652.0      | 
	+--------------------------------+
	| Lsqview.dll  | 5.5.2651.86     | 
	+--------------------------------+
	| Lsvmdia.exe  | 5.5.2652.0      | 
	+--------------------------------+
	| Lsvmhc.dll   | 5.5.2652.0      | 
	+--------------------------------+
	| Lsxfm.dll    | 5.5.2652.0      | 
	+--------------------------------+
	| Mex2gw.exe   | 5.5.2652.0      | 
	+--------------------------------+
	| Ntsperf.dll  | 5.5.2651.86     | 
	+--------------------------------+
	| Ntspxgen.dll | 5.5.2651.86     | 
	+--------------------------------+
	
	Fixes Released on April 12, 2000
	--------------------------------
	
	The following files are modified:
	
	- Gwrouter.exe added and incremented to version 5.5.2651.83
	- Lsxfm.dll added and incremented to 5.5.2652.0
	- Dxagwise.dll, Dxamex.dll, Dxanotes.dll, Gw2mex.exe, Gwhc.dll, Lscms.dll,
	  Lsdiamex.exe, Lsdxa.exe, Lsldew.dll, Lsmexdia.exe, Lsmexhc.dll, Lsmexif.dll,
	  Lsmexin.exe, Lsmexnts.exe, Lsntshc.dll, Lsntsmex.exe, Lsvmdia.exe,
	  Lsvmhc.dll, and Mex2gw.exe incremented to 5.5.2652.0
	
	The following fixes are included:
	
	  Q254916 XFOR: Line Is Overwritten When Sending Files to an Exchange Server
	  Recipient by Using Exchange PROFS Connector
	
	Fixes Released on March 7, 2000
	-------------------------------
	
	NOTE: The Gwrouter.exe and Lsxfm.dll files are not included with these fixes.
	These files are added later.
	
	The following files are modified:
	
	- All files incremented to version 5.5.2651.86
	
	The following fixes are included:
	
	  Q236601 XADM: Notes Proxy Address Generation Fails on Some Eastern Extended
	  Characters
	  Q238487 XCON: Exchange Notes Connector May Stop Responding with Bad SMTP
	  Address
	  Q240236 XFOR: Ctkeepdays Only Works with a Value of 1 or 7
	  Q240913 XFOR: PROFS AT Command Fails When Forwarding Meeting Requests
	  Q241086 XFOR: GroupWise Directory Synchronization Update Does Not Create
	  Objects in GroupWise
	  Q241213 XFOR: Possible Message Looping with the SNADS/PROFS/GroupWise/Notes
	  Connectors
	  Q242384 XFOR: DBCS Message Sent Through Notes Connector Is Not Displayed
	  Properly
	  Q244129 XFOR: Notes Connector Rejects Incoming Messages with the Apostrophe
	  (') Character in the SMTP Address
	  Q244467 XFOR: GroupWise Delivery Receipt Does Not Work on Long Orig-Msg-ID
	  Attribute
	  Q245458 XCON: Notes Delegate Cannot See Meetings from Outlook User
	  Q246385 XFOR: Directory Entries Not Imported From Novell GroupWise
	  Q246434 XFOR: Internet Messages from Lotus Notes to Exchange Server Need
	  Address Format of SMTP_ADDRESS@DOMAIN
	  Q247182 XFOR: Exchange Notes Connector Directory Synchronization Deletes the
	  Custom Recipients Propagated by Linkage Directory Exchange
	  Q248056 XCON Bad NDR or DR with no intended recipient stops Notes Connector
	  Q248383 XFOR: Notes R5 Recipient Cannot Reply to SMTP Message Sent Through
	  Internet Mail Service or SMTP Connector
	  Q248664 XFOR: Cannot Reply All to SMTP Reply Received from Notes R5 User
	  Q249112 XFOR: Filter Rule Is Ignored by Directory Synchronization Process and
	  All Notes Users Without Domain Name Are Synchronized to Exchange Server
	  Q249113 XFOR: Exchange Connector for Lotus Notes Extracts Filter Rule
	  Incorrectly
	  Q249861 XCON: Microsoft Exchange Connector for Novell GroupWise Does Not
	  Process Non-Delivery Report for Message with Long Subject
	  Q249878 XFOR: Notes Dirsync Does Not Catch All Changes While Using Mapping
	  Rules
	  Q249884 XFOR: Last Name Is Truncated by Exchange Connector for Lotus Notes
	  Directory Synchronization Process
	  Q250342 XFOR: SNADS Connector Causes Host To Abend During Directory
	  Synchronization
	  Q250400 XFOR: DXANOTES Writes Mail Server Data to the Personal Document of the
	  Target Address
	  Q250450 XFOR: Using Notes Document Type Cause Address Books to Reload
	  Q250671 XFOR: Notes Group Type Attribute Does Not Synchronize to Exchange
	  Server Directory
	  Q251049 XFOR: Lotus Notes Directory Synchronization Allows Specification of
	  Read Only Field for Selected Attributes
	  Q252689 XCON: Extended Characters in Attachment Names Are Mishandled by
	  Exchange Connector for Novell GroupWise
	  Q252819 XFOR: Read Receipt from cc:Mail Loses Content
	  Q253011 XFOR: Exchange Connector for Lotus Notes Does Not Use the StartDate
	  Property
	  Q253018 XFOR: Exchange Connector for Lotus Notes Appends
	  @SMTP@<Connector_for_Lotus_Notes_Domain> to the From Address When
	  Receiving Mail for a Notes User from the Internet Mail Service
	  Q253029 XFOR: Exchange Connector for Lotus Notes to Support Attachments Inside
	  Embedded Messages
	  Q253261 XFOR: Large Temporary Proxy Address Tables Become Corrupted and
	  CTCleanup Procedure Cannot Clean up Tables
	  Q253347 XCON: Comments File in Gw2mexa Folder Stops Calendar Items from Being
	  Sent to Exchange Server
	  Q253348 XCON: Exchange Server Cannot Reply All to Notes Recipients that Only
	  Have a Last Name and No Notes Proxy Address
	  Q253349 XCON: Response Files from GroupWise Are Put in Badfiles Folder
	  Q253350 XCON: Perflib Module Reports that the Exchange Connector for Lotus
	  Notes Performance Monitor Will Not Return Data on Windows 2000 Server
	  Q253712 XFOR: Problems with Attachments Sent over the Exchange Notes
	  Connector
	  Q253867 XFOR: URL Links Not Active When HTML Message Routed to Notes
	  Q254064 XFOR: Exchange Connector for SNADS Delivery Receipt Does Not Work in
	  Exchange Server 5.5 Service Pack 2 and Service Pack 3
	  Q254540 XCON: GroupWise Router Has Trouble with Multiple Messages with Same
	  Attachment Name
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 kbfixlist
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
