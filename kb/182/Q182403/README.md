---
layout: page
title: "Q182403: XFOR: Store Causes Access Violation in NdrServerUnmarshall"
permalink: /kb/182/Q182403/
---

## Q182403: XFOR: Store Causes Access Violation in NdrServerUnmarshall

{% raw %}

	Article: Q182403
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): exc4 exc5 exc55
	Last Modified: 22-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Server information store may unexpectedly terminate with
	an access violation. If Windows NT Server and Microsoft Exchange Server symbols
	are installed and correct, the Drwtsn32.log may look similar to the following:
	
	  Application exceptionoccurred:
	  App: store.DBG (pid=166)
	  When: 11/10/1997 @ 16:17:26.516
	  Exception number: c0000005 (access violation)
	
	The call stack will look like following:
	
	  kb
	  FramePtr  RetAddr   Param1   Param2   Param3       Function Name
	  0ba9fb38  77e8e9cb  00000000 0ba9ff10 0ba9fc64
	  RPCRT4!NdrServerUnmarshall+0x1d3
	  0ba9fe28  77e8e876  00000000 00000000 0ba9ff10  RPCRT4!NdrStubCall+0x14f
	  0ba9fe40  77e61438  0ba9ff10 0ba9fec8 00000000
	  RPCRT4!NdrServerCall+0x15
	  0ba9fe7c  77e61374  02002b34 0ba9ff10 0ba9ff3c
	  RPCRT4!DispatchToStubInC+0x34
	  0ba9fed0  77e6162d  0ba9ff10 00000000 0ba9ff3c
	  RPCRT4!?DispatchToStubWorker@RPC_INTERFACE@@AAEJPAU_RPC_MESSAGE@@IPAJ@Z+
	  0xd6
	  0ba9fef0  77e6c005  0ba9ff10 00000000 0ba9ff3c
	  RPCRT4!?DispatchToStub@RPC_INTERFACE@@QAEJPAU_RPC_MESSAGE@@IPAJ@Z+0x5f
	  0ba9ff40  77e68657  0aa14608 00000054 77e91180
	  RPCRT4!?ReceiveOriginalCall@OSF_SCONNECTION@@QAEHPAUrpcconn_common@@I@Z+
	  0xdb
	  0ba9ff60  77e6acb1  0aa14608 00000054 00166c10
	  RPCRT4!?spatchPacket@OSF_SCONNECTION@@QAEHPAUrpcconn_common@@IPAVOSF_ADD
	  RESS@
	  @@@Z+0x1f8
	  0ba9ff8c  77e6aa73  77e649cc 00166c10 0019cff8
	  RPCRT4!?ReceiveLotsaCalls@OSF_ADDRESS@@QAEXXZ+0x7f
	  0ba9ff90  77e649cc  00166c10 0019cff8 001e82c0
	  RPCRT4!?ReceiveLotsaCallsWrapper@@YGXPAVOSF_ADDRESS@@@Z+0x9
	  0ba9ffac  77e64a03  0aa06cf8 00000024 77f46c2e
	  RPCRT4!?BaseCachedThreadRoutine@@YGXPAVCACHED_THREAD@@@Z+0xae
	  0ba9ffb8  77f46c2e  001e82c0 0019cff8 00000024
	  RPCRT4!?ThreadStartRoutine@@YGJPAVTHREAD@@@Z+0x16
	  0ba9ffec  00000000  77e649ed 001e82c0 00000000
	  KERNEL32!BaseThreadStart+0x61
	
	
	CAUSE
	=====
	
	An exception was thrown during the unmarshalling process because of a corrupted
	buffer. During the exception handling, an attempt was made to try and free the
	memory block, which was invalid and therefore resulted in an access violation.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 4.0 and 5.0.
	
	
	A supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information.
	
	
	Additional query words: store rpcrt4
	
	======================================================================
	Keywords          : exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	
	=============================================================================
	

{% endraw %}
