---
layout: page
title: "Q185715: CPI-C Side Information Does Not Allow &quot;.&quot; (period) in TP Name"
permalink: /kb/185/Q185715/
---

## Q185715: CPI-C Side Information Does Not Allow &quot;.&quot; (period) in TP Name

{% raw %}

	Article: Q185715
	Product(s): Microsoft SNA Server
	Version(s): 2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 25-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1, 2.11 SP2, 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are configuring CPI-C Side Information in SNA Server Manager, using a
	"." (period) in the partner TP name causes the name to be rejected with the
	error message "The TP Name is invalid". The error message includes an
	explanation of what constitutes a valid TP name.
	
	CAUSE
	=====
	
	SNA Server is not designed to support TP names that include a "." (period).
	
	Valid characters for a TP name are the letters A through Z (lowercase letters are
	converted to uppercase), the numerals 0 through 9, and the special characters
	"$", "#", and "@".
	
	RESOLUTION
	==========
	
	SNA Server 3.0
	--------------
	
	To resolve this problem, obtain the latest service pack for SNA Server version
	3.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q184307 How to Obtain the Latest SNA Server Version 3.0 Service Pack
	
	
	
	SNA Server 4.0
	--------------
	
	This problem has been corrected in the latest U.S. Service Pack for SNA Server
	version 4.0. For information on obtaining the Service Pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	WORKAROUND
	==========
	
	To work around this problem, do not use a "." in the partner TP name.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server versions 2.11, 2.11
	SP1, 2.11 SP2, 3.0, 3.0 SP1, 3.0 SP2, and 3.0 SP3. This problem was first
	corrected in SNA Server 3.0 Service Pack 4.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ211 kbSNAServ400 kbSNAServ211SP1 kbSNAServ211SP2 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ300SP2
	Version           : :2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
