---
layout: page
title: "Q193123: XADM: Unable to Reply to Messages After Hotfix Is Applied"
permalink: /kb/193/Q193123/
---

## Q193123: XADM: Unable to Reply to Messages After Hotfix Is Applied

{% raw %}

	Article: Q193123
	Product(s): Microsoft Exchange
	Version(s): WinNT:5.5
	Operating System(s): 
	Keyword(s): exc55sp2fix
	Last Modified: 22-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	After you apply an Exchange Server 5.5 post-SP1 hotfix to the store component
	(any build between 2232.x and 2402.0 of Store.exe), users may be unable to reply
	to messages in their Inbox. When users reply to a message, the From: field
	automatically appears in the message header and is populated with the name of
	the originator of the message. Attempting to send this reply results in an
	"access denied" error message.
	
	CAUSE
	=====
	
	This problem was introduced by a previous fix to the store component.
	
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For more information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The English version of this fix should have a version number equal to or greater
	than shown for the following files:
	
	  Component: Information Store
	
	  File Name    Version
	  -----------------------
	  Gapi32.dll   5.5.2402.0
	  Mdbmsg.dll   5.5.2402.0
	  Store.exe    5.5.2402.0
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5. This problem was first corrected in Exchange Server 5.5 Service
	Pack 2.
	
	
	Additional query words: corrupt bad regression
	======================================================================
	Keywords          : exc55sp2fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : WinNT:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
