---
layout: page
title: "Q139594: Meaning of &quot;DLCST UPSN&quot; in a SNA Server Data Link Control Trace"
permalink: /kb/139/Q139594/
---

## Q139594: Meaning of &quot;DLCST UPSN&quot; in a SNA Server Data Link Control Trace

{% raw %}

	Article: Q139594
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.0,2.1,2.11,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Operating System(s): 
	Keyword(s): kbinterop kbnetwork kbsetup kbsna300sp1 kbsna300sp2 kbsna300sp3 sna4
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 4.0, 4.0 SP1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	A special mechanism is used to track SDLC statistics in the SDLC link service.
	The generation of statistics is controlled by byte dataru[s+27] in the
	Open(LINK) request messages. An Open (LINK) request message flows between the
	SNA Server service and each link service whenever the SNA Server service
	initializes. Its basic purpose it to set the link characteristics. The
	dataru[s+27] byte is defined by the SNA Device Interface Specification (SNADIS)
	as "reserved", and causes the Microsoft written SDLC link services to generate
	statistic messages when set to x01. Link services written by IHVs will ignore
	this byte, and therefor, not log these link statistics in a trace.
	
	The following trace excerpt may appear in an SNA Server Data Link Control trace.
	This trace represents messages that flow between the SNA Server service and the
	underlying link services:
	
	  ...
	  DLC    04161000->01110101 DLCST UPSN
	  DLC                       UPTYPE:3 UPCNTR:7 COUNT:0
	  ...
	
	The definitions of the UPTYPE and UPCNTR fields are as follows. The COUNT field
	is not used.
	
	UPTYPE              UPCNTR
	==========================
	
	Type 1
	            1 Number of Test cmds rcvd
	                 2 Number of Test rsps sent
	
	Type 3
	                 1 Non productive receive timeout
	                 2 Idle Timeout
	                 3 Write retry
	                 4 Receiver character overrun
	                 5 Transmitter underrun
	                 6 Connection problem
	                 7 FCS error
	                 8 Primary station abort received
	                 9 SDLC Command reject
	                10 DCE error
	                11 Write timeout
	                12 Not used
	                13 I-frame received out of sequence
	                14 I-frame discarded (primary)
	                15 No response timeout (primary)
	                16 Remote busy timeout (primary)
	
	Because the trace excerpt has UPTYPE = 3 and UPCNTR = 7, the observer of the
	trace could conclude that this is an FCS (Frame Check Sequence) error detected
	by the link service.
	
	NOTE: For earlier versions of SNA Server, theThe SNADIS guide can be found on the
	SNA Server cd in Help file format. To find the Open(Link) Request format, do the
	following:
	
	1. Run SNA.HLP.
	
	2. Select SNA Device Interface Specification.
	
	3. Select "Chapter 4 SNA Device Interface Specification Message formats."
	
	4. Select 4.1 Open(Link).
	
	5. Select 4.1.1 Open(Link) Request.
	
	For SNA Server versions 3.0 and 4.0, the SNADIS Guide is located in the SDK
	Documentation, which is a component that may be installed during SNA Server
	setup. To find the Open(Link) Request format, do the following:
	
	1. Run the SDK Documentation from the Start menu in Windows NT.
	
	2. Expand SNA Device Interface Specification.
	
	3. Expand Reference.
	
	4. Expand Message Formats.
	
	5. Expand Open(LINK), and then select Open(LINK) Request.
	
	Additional query words: prodsna
	
	======================================================================
	Keywords          : kbinterop kbnetwork kbsetup kbsna300sp1 kbsna300sp2 kbsna300sp3 sna4 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ200 kbSNAServ211 kbSNAServ400 kbSNAServ210 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ300SP2
	Version           : WINDOWS:2.0,2.1,2.11,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	
	=============================================================================
	

{% endraw %}
