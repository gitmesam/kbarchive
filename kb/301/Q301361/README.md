---
layout: page
title: "Q301361: XGEN: Incorrect Attachment Processing in Exchange Server 5.5 OWA"
permalink: /kb/301/Q301361/
---

## Q301361: XGEN: Incorrect Attachment Processing in Exchange Server 5.5 OWA

{% raw %}

	Article: Q301361
	Product(s): Microsoft Exchange
	Version(s): 5.5,5.5 SP1,5.5 SP2,5.5 SP3,5.5 SP4
	Operating System(s): 
	Keyword(s): kbExchange550preSP5fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 5.5 SP1, 5.5 SP2, 5.5 SP3, 5.5 SP4 
	-------------------------------------------------------------------------------
	
	
	For additional information about a similar problem that can occur in Exchange 2000 Server, click the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q299535 XGEN: Incorrect Attachment Processing in Exchange 2000 Outlook Web
	  Access Can Run Script
	
	SYMPTOMS
	========
	
	Microsoft Outlook Web Access (OWA) is a service of Exchange Server 5.5 and
	Exchange 2000 Server that a user can use to gain access to an Exchange mailbox
	by using a Web browser. However, vulnerability exists in the interaction between
	OWA and Microsoft Internet Explorer for message attachments. If an attachment
	contains Hypertext Markup Language (HTML) code that includes script, the script
	is run when the user opens the attachment, regardless of the attachment type.
	Because OWA requires that scripting be enabled in the zone where the OWA server
	is located, this script can take action against the user's Exchange mailbox.
	
	An attacker might use this vulnerability to construct an attachment that contains
	malicious script code. The attacker can then send the attachment in a message to
	a user. If the user opens the attachment in OWA, the script runs and can take
	action against the user?s mailbox as if the script is the user, including, under
	certain circumstances, manipulation of messages or folders.
	
	The following are mitigating factors:
	
	- The vulnerability can only be exploited if the user is using OWA in
	  conjunction with Internet Explorer.
	
	- The vulnerability can only be exploited by attachments that are received by
	  using OWA. In general, an attacker has no way to determine whether a user
	  will open an attachment by using OWA rather than Microsoft Outlook.
	
	- An attacker's ability to exploit this vulnerability requires that the
	  attacker entice the user to open an attachment from an untrusted source. The
	  best practice is not to open any attachment from an unknown or untrusted
	  source.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems that are determined to be at risk of attack. Please evaluate your
	computer's physical accessibility, network and Internet connectivity, and other
	factors to determine the degree of risk to your computer. Please see the
	associated Microsoft Security Bulletin
	(http://www.microsoft.com/technet/security/bulletin/MS01-030.asp) to help make
	this determination. This fix may receive additional testing at a later time, to
	further ensure product quality. If your computer is sufficiently at risk,
	Microsoft recommends that you apply this fix now. Otherwise, wait for the next
	Microsoft Exchange Server 5.5 service pack that contains this fix.
	
	To resolve this problem immediately, download the fix as instructed below or
	contact Microsoft Product Support Services to obtain the fix. For a complete
	list of Microsoft Product Support Services phone numbers and information on
	support costs, please go to the following address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  DownloadDownload Q301361i386.exe now
	  (http://www.microsoft.com/Downloads/Release.asp?ReleaseID=30568)
	
	Release Date: June 8, 2001
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. After it is posted, the file is housed on
	secure servers that prevent any unauthorized changes to the file.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: OWA
	
	+---------------------+
	| File name | Version | 
	+---------------------+
	| Read.asp  | na      | 
	+---------------------+
	
	NOTES
	
	- Because of file dependencies, this fix requires Microsoft Exchange Server
	  version 5.5 Service Pack 4.
	
	- You need to apply this fix to all servers that run the OWA components. With
	  Exchange Server 5.5, you can install the OWA components on a computer that is
	  separate from the Exchange Server. If you install OWA separately, you need to
	  run this patch on the separate computer.
	
	- Sometimes, after applying this fix, users may get a blank window when they
	  open their messages using OWA. If this occurs, please review the following
	  Knowledge Base article
	
	  Q314532 XWEB: Troubleshooting Blank Message Bodies in Outlook Web
	
	
	
	STATUS
	======
	
	Microsoft has confirmed that this problem could result in some degree of
	security vulnerability in Microsoft Exchange Server version 5.5.
	
	MORE INFORMATION
	================
	
	For more information about this security vulnerability, see the following
	Microsoft Web site:
	
	  http://www.microsoft.com/technet/security/bulletin/MS01-030.asp
	
	Additional query words: security_patch
	
	======================================================================
	Keywords          : kbExchange550preSP5fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2 kbExchange550SP1 kbExchange550SP2 kbExchange550SP3 kbExchange550SP4
	Version           : :5.5,5.5 SP1,5.5 SP2,5.5 SP3,5.5 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
