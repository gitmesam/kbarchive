---
layout: page
title: "Q181512: XFOR: Lsccmmex.exe Access Violates When Processing Delivery Repo"
permalink: /kb/181/Q181512/
---

## Q181512: XFOR: Lsccmmex.exe Access Violates When Processing Delivery Repo

{% raw %}

	Article: Q181512
	Product(s): Microsoft Exchange
	Version(s): 3.2,4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	- LinkAge Message Exchange, version 3.2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Lsccmmex.exe process causes an access violation when processing delivery
	reports from Exchange Server to cc:Mail.
	
	If the Linkage and Windows NT symbols are loaded correctly then the call stack
	will look like the following:
	
	  > kb
	  FramePtr  RetAddr   Param1   Param2   Param3   Function Name
	     0012f2d4  004032d9  0012f334 0025d370 00000010
	  LSMEXCCM!CCMMessageItem::wrapAndPut+0x96
	  0012f338  00402c6c  00d42520 0012fa84 0012f3b0
	  LSMEXCCM!writeMessageBody+0x28b({...}, {...})
	  0012fa98  0040384e  00d7cf30 00d42520 0012feb8
	  LSMEXCCM!transformMessage+0xeb
	  0012fbec  004029b2  00d7cf30 00d42520 00000000
	  LSMEXCCM!transformDRBody+0x2f7
	  0012fe2c  00402456  00d7cf30 0012feac 0012feb8
	  LSMEXCCM!transformMEXtoCCM+0x3d4
	  0012fec0  00246d02  008b7e90 0012ff44 0455e5d7
	  LSMEXCCM!checkForNewMail+0x436
	  00000050  00000000  00000000 00000000 00000000 0x00246d02
	
	CAUSE
	=====
	
	The Lsccmmex.exe process is responsible for transforming a mail item from
	Exchange format to cc:Mail format. A temporary file is created to hold the
	report while Lsccmmex.exe processes it. If the process fails to open the file,
	an incorrect parameter is passed, which causes the access violation.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Linkage Message Exchange version
	3.2.
	
	
	A supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information.
	
	
	
	Additional query words: ccmail linkage lsmexccm
	
	======================================================================
	Keywords          :  
	Technology        : kbZNotKeyword6 kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2 kbLinkAgeSearch kbLinkAge320
	Version           : :3.2,4.0,5.0,5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
