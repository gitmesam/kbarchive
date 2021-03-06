---
layout: page
title: "Q182619: XCON: MTA Terminates with 9404 Error"
permalink: /kb/182/Q182619/
---

## Q182619: XCON: MTA Terminates with 9404 Error

{% raw %}

	Article: Q182619
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 03-JUL-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The message transfer agent (MTA) terminates with error 9404. The following error
	is observed in the application log for all versions of Microsoft Exchange
	Server:
	
	  9215
	  A sockets error 10061 on a connect() call was detected. The MTA will
	  attempt to recover the sockets connection. Control block index: 6. [BASE
	  ILTCP/IP DRVR 10 274] (12)
	
	
	If you are running Exchange Server version 5.0, the text of the 9404 error
	message is as follows:
	
	  9404
	  A fatal MTA error has occurred. An illegal buffer request has been made.
	  The request was for 30 headers and 30 elements. [BASE TCP/IP DRVR 10]
	  (16)
	
	If you are running Exchange Server version 5.5, the text of the 9404 error
	message is as follows:
	
	  A fatal MTA error has occurred. An illegal buffer request has been made.
	  The request was for 29 headers and 29 elements. [BASE TCP/IP DRVR 8]
	  (16)
	
	CAUSE
	=====
	
	The 9404 error is generated when the MTA receives an illegal TPKT request from
	the buffer manager.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	versions 4.0 and 5.0.
	
	
	A supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information.
	
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server version
	5.5. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 5.5. For information about obtaining the
	Service Pack, query on the following word in the Microsoft Knowledge Base
	(without the spaces):
	
	  S E R V P A C K
	
	Additional query words: 9404 illegal buffer mta terminates crash
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : WINDOWS:4.0,5.0,5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
