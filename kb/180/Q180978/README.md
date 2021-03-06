---
layout: page
title: "Q180978: SMS: Security Considerations for SMS Service Accounts"
permalink: /kb/180/Q180978/
---

## Q180978: SMS: Security Considerations for SMS Service Accounts

{% raw %}

	Article: Q180978
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbConfig kbsmsAdmin smsadmin smsgeneral smsconfig kbArtTypeINF
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Systems Management Server service account is used by the Site Configuration
	Manager, Hierarchy Manager, and Systems Management Server Executive services.
	This account is also used for the Package Command Manager (PCM) client component
	service on Systems Management Server logon servers in the site. Because this
	account sets up and maintains directories and shares, installs services, and
	writes to the registry, it requires local Administrator rights on the computers
	it maintains (including logon servers, distribution servers, and helper
	servers). Additionally, if the "Auto-detect All Logon Servers" option is
	enabled, every member server will also have the Systems Management Server
	Inventory Agent and the PCM service installed on them. The PCM service on these
	servers uses the Systems Management Server service account.
	
	When security boundaries must be drawn to fit into an organizational or
	administrative model, Systems Management Server hierarchies should be developed.
	Each site should contain its own service account and password. When a site
	hierarchy is developed along security divisions, it is necessary to not have
	multiple sites in a single domain, because the account for each site must reside
	in the domain.
	
	MORE INFORMATION
	================
	
	Generally speaking, the less secure the environment, the easier it is to
	administer, in terms of deployment and password changes. A secure environment
	requires more complex administration.
	
	Normally, the Systems Management Server service account is granted Domain
	Administrator rights to the domains within the site. When this is done, there is
	an assumption made that the local administrator of the site server and logon
	servers is also a Domain Administrator, and visa versa.
	
	It is possible to have a multiple site hierarchy and have all sites use the same
	account and password. If Systems Management Server is configured this way,
	account maintenance is simplified. Multiple sites with unique passwords require
	more account maintenance. It is also possible to create a user account for the
	sender (a thread of the Systems Management Server Executive service) to use for
	inter-site communications. The sender account does not need to be a Domain
	Administrator, rather a Domain User with limited rights. The only requirement of
	the sender account is that it must have Administrator rights on each site
	server's SMS_SITE share (<SMS_root>\Sms\Despooler.box\Receive). After
	creating a user account, you can configure the sender to use a specified account
	in the Addresses portion of the Site Properties.
	
	For more information, refer to the Concepts and Planning Guide in the online
	documentation.
	
	Additional query words: prodsms admin admins
	
	======================================================================
	Keywords          : kbConfig kbsmsAdmin smsadmin smsgeneral smsconfig kbArtTypeINF 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
