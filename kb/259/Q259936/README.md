---
layout: page
title: "Q259936: MMC Cannot Administer IIS 4.0 Through Terminal Server Client"
permalink: /kb/259/Q259936/
---

## Q259936: MMC Cannot Administer IIS 4.0 Through Terminal Server Client

{% raw %}

	Article: Q259936
	Product(s): Internet Information Server
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT version 4.0 Option Pack 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Microsoft Management Console (MMC) cannot administer Microsoft Internet
	Information Server (IIS) through a Windows NT 4.0 Terminal Server client.
	
	If you attempt to do so, DCOM error messages appear in the System log when you
	try to expand the IIS and Microsoft Transaction Server (MTS) snap-ins. Two error
	messages appear in the System log:
	
	  Event ID: 10100 Source DCOM User: <Domain Name>\Administrator The
	  server {A9E69610-B80D-11D0-B9B9-00A0C922E750} did not register with DCOM
	  within the required timeout.
	
	  Event ID 10100 Source: DCOM User: <Domain Name>\Administrator The
	  server {182C40F0-32E4-11D0-818B-00A0C9231C29} did not register with DCOM
	  within the required timeout.
	
	CAUSE
	=====
	
	This issue is caused by the IIS server security context and the remote
	communication mode through the Terminal Server client. For additional
	information, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q217144 INFO: Difficulties Using Net APIs in ISAPI and ASP COM Objects
	
	WORKAROUND
	==========
	
	There is no workaround for this issue. IIS is not intended for use on Windows NT
	Server 4.0, Terminal Server Edition, and is not supported. Microsoft recommends
	that customers running IIS 4.0 on Windows NT Server 4.0, Terminal Server
	Edition, protect their systems by uninstalling IIS 4.0.
	
	This issue does not exist in Microsoft Windows 2000 Server with Internet
	Information Services.
	
	MORE INFORMATION
	================
	
	CLSID {A9E69610-B80D-11D0-B9B9-00A0C922E750} refers to the IISADMIN object;
	{182C40F0-32E4-11D0-818B-00A0C9231C29} refers to the MTS Catalog object.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q190157 Support for Windows NT 4.0 Option Pack on Terminal Server
	
	Additional query words: tse ntop mmc mtx catalog
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNT400OptionPack
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
