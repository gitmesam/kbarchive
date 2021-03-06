---
layout: page
title: "Q169860: XCON: MTA Error 210 Due to Invalid ADMD Length"
permalink: /kb/169/Q169860/
---

## Q169860: XCON: MTA Error 210 Due to Invalid ADMD Length

{% raw %}

	Article: Q169860
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Server Message Transfer Agent (MTA) may produce the
	following error when a message arrives from a third-party MTA.
	
	  message NMI0210: X.400 Service Event, severity 14
	     (MTA XFER-IN(26) Proc 112) 04-28-97 01:48:11am
	     Content conversion failed
	        Object at fault     0600004D
	        Conversion error    26
	  MTS Identifier
	  C=UA;A=ADMD;P=PRMD;L=1002233servername
	        Old content type    56010A00
	        New content type    2A864886F7140501
	        PDU dump reference  1
	
	The item of direct interest is the Conversion error 26 that indicates a malformed
	P2 (Content).
	
	MORE INFORMATION
	================
	
	If a third-party X.400 system sends a message which has incorrect values for the
	P2 X.400 Originator and Recipient (O/R) addresses, Exchange Server is unable to
	convert the message to a format that can be transferred to the Exchange Server
	information store.
	
	An example of this would be a message received from a third-party X.400 system
	with an incorrect value for the administrative management domain name (ADMD).
	According to the 1988 CCITT (ITU) Blue Book, the maximum length of the ADMD
	field is 16 characters. If this length is exceeded, then the Exchange Server
	content converter will reject the message as malformed.
	
	If this behavior is found, the manufacturer of the problematic MTA should be
	consulted for a fix.
	
	
	Additional query words: metamorf convert failure ndr bf
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : WINDOWS:4.0,5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
