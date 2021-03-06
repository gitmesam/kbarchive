---
layout: page
title: "Q262824: SMS: A Program May Run Twice Because It Appears in Bold"
permalink: /kb/262/Q262824/
---

## Q262824: SMS: A Program May Run Twice Because It Appears in Bold

{% raw %}

	Article: Q262824
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Operating System(s): 
	Keyword(s): kbsms200preSP4fix
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2, 2.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you advertise a program that is based on a mandatory assignment to a client
	and you use the "Allow users to run the program independently of assignments""
	option, the program may be run twice. This problem may occur if the Advertised
	Programs client agent is configured to display a notification message when new
	advertised programs are available.
	
	For example, this problem occurs in the following scenario:
	
	The Offer Data Providers (ODPs) on the client refresh the offers and determine
	that a new advertisement is available. A notification appears to inform the user
	that a new advertised program is available. However, the user is away from the
	computer. The advertised program is mandatory, so Advertised Program Manager
	(APM) schedules the program to run at the appropriate time. The scheduled run
	time occurs before the user returns to the computer and APM runs the program.
	However, the notification remains visible.
	
	The user returns and sees the notification. The user is not aware that the
	program has already been run, so the user clicks Yes to run the new advertised
	program. This displays the Advertised Programs Wizard, which displays in bold
	text the advertised program that has already run. The bold text typically
	indicates that the program has not been run. The Last Run field in the program's
	properties indicates that the program has already been run, but the user may not
	notice this field.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, click the following article
	number to view the article in the Microsoft Knowledge Base:
	
	  Q288239 SMS: How to Obtain the Latest Systems Management Server 2.0 Service
	  Pack
	
	
	WORKAROUND
	==========
	
	To work around this problem, users can check the Last Run field to determine if
	a program has already been run.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	Systems Management Server 2.0 Service Pack 4.
	
	MORE INFORMATION
	================
	
	After you apply Service Pack 4 (SP4):
	
	- The Advertised Programs Wizard does not use bold text to display a program
	  that has already been run.
	
	- The New Advertised Program Available notification dialog box is automatically
	  closed when all advertisements have been addressed either by the user or by a
	  mandatory program being run.
	
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200preSP4fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2 kbSMS200SP3
	Version           : :2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
