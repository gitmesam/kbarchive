---
layout: page
title: "Q102301: X400: Err: TMP Variable Not Set Gives WARNING 7 Error"
permalink: /kb/102/Q102301/
---

## Q102301: X400: Err: TMP Variable Not Set Gives WARNING 7 Error

{% raw %}

	Article: Q102301
	Product(s): Microsoft Mail For PC Networks
	Version(s): MS-DOS:3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail Gateway to X.400, version 3.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If the MS-DOS SET TMP variable is not present in the AUTOEXEC.BAT file, version
	3.2 of Microsoft Mail Gateway to X.400 generates these error messages:
	
	  15:21:44 WARNING 7 (bodypart typing initialization): Environment
	  variable TMP not (or incorrectly) set.
	
	  15:21:44 WARNING 7 (bodypart typing initialization): Using m:x400
	  as working directory.
	
	The first error states that the variable is not set and the second states that
	the X400Gate executable will use the X400 directory in the Microsoft Mail
	database as the working directory.
	
	If the user running the gateway does not have sufficient network rights to write
	to the directory where the TMP variable is set, the gateway is not able to
	create messages, causing the following errors:
	
	  07:50:39 Extracting message from local message store: 0000003C
	  07:50:40 ERROR 3 (creating X.400 message envelope (P1)): opening file:
	  M:\X4_2
	  07:50:40 ERROR 3 (converting PC mail message to X.400): Creating P1
	  07:50:40 ERROR 3 (converting PC mail message to X.400): local form to X400
	  conversion
	  07:50:40 ERROR -18 (processing mail bound for X.400): Receive from local
	  message store Failed
	  07:50:40 WARNING -1 (processing mail bound for X.400): FROM:
	  JOHNLAND/JOHNPO1/Admin
	  07:50:40 WARNING -1 (processing mail bound for X.400): SUBJECT: test
	  07:50:40 ERROR -1 (collecting mail from local message store): ProcessMail()
	  07:50:40 WARNING -1 (receiving message): Failed receiving message pointer
	  count: 411; byte count: 9668
	
	RESOLUTION
	==========
	
	Set the MS-DOS TMP variable to a location with enough disk storage to store the
	largest X.400 message the gateway can reasonably be expected to receive.
	
	
	Additional query words: 3.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbMailGateSearch kbZNotKeyword3 kbMailGatex400320
	Version           : MS-DOS:3.2
	
	=============================================================================
	

{% endraw %}
