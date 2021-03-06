---
layout: page
title: "Q216492: XFOR: Extra Space in Notes Proxy Address Causes Mail to NDR"
permalink: /kb/216/Q216492/
---

## Q216492: XFOR: Extra Space in Notes Proxy Address Causes Mail to NDR

{% raw %}

	Article: Q216492
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55 EXC55SP3Fix
	Last Modified: 30-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Lotus Notes users may receive a non-delivery report (NDR) when replying to an
	e-mail message originating from Exchange Server. This NDR might result from
	recent changes made on the Exchange Server, particularly to the Notes proxy
	address of the Exchange Server user.
	
	CAUSE
	=====
	
	The Exchange Notes Connector does not know how to handle extra spaces in the
	Notes proxy address of Exchange Server users. This might be a result of
	modifying the Notes proxy address generation rule under Site Addressing to a
	format that might generate a space.
	
	For example:
	
	  &g &i &s/Site/Org@Exchange)
	
	A user that did not have a middle initial would contain a Notes proxy address of
	similar to the following:
	
	  "John Smith/Site/Org@Exchange"
	
	Note the extra space between John and Smith.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the latest Exchange Server 5.5 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Notes Mail Connector
	
	+---------------------------+
	| File name    | Version    | 
	+---------------------------+
	| Ntspxgen.dll | 5.5.2533.0 | 
	+---------------------------+
	
	
	WORKAROUND
	==========
	
	To work around this problem, specify a Notes proxy address generator rule that
	does not result in any addresses with an extra space. Administrators can also
	manually correct the user's Notes proxy address by removing the extra space.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5.. This problem was first corrected in Exchange Server 5.5 Service
	Pack 3.
	
	MORE INFORMATION
	================
	
	This issue might still be a problem if modifications to the Notes proxy address
	were accomplished through some other mechanism, such as importing/exporting CSV
	files, or through a dirsync mapping rule. Microsoft is aware of this problem.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 EXC55SP3Fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
