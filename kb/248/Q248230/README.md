---
layout: page
title: "Q248230: IPX Clients with Session ID &gt; 4,095 Can Cause &quot;Stop 0x1E&quot;"
permalink: /kb/248/Q248230/
---

## Q248230: IPX Clients with Session ID &gt; 4,095 Can Cause &quot;Stop 0x1E&quot;

{% raw %}

	Article: Q248230
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are running many Microsoft Windows 95, Microsoft Windows 98, or
	Microsoft Network 3.0 clients on your network over IPX, and the clients access
	Windows NT-based servers by using Direct Hosting over IPX, you may receive "Stop
	0x1E in Srv.sys" error messages on the server.
	
	
	CAUSE
	=====
	
	Direct Hosting support is limited to 4,096 session IDs (SIDs), and Windows NT
	does not handle exceeding this limit properly.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date      Time    Size     File name  Platform
	  ----------------------------------------------
	  11/09/99  05:06p  460,720  Srv.sys    Alpha
	  11/09/99  05:07p  231,088  Srv.sys    Intel
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
