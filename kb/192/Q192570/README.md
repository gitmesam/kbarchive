---
layout: page
title: "Q192570: Message-Oriented TCP and Multithreaded Client/Server"
permalink: /kb/192/Q192570/
---

## Q192570: Message-Oriented TCP and Multithreaded Client/Server

{% raw %}

	Article: Q192570
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kbfile kbnetwork kbAPI kbMFC kbVC500 kbOSWin95 kbOSWin98 kbWinsock kbGrpDSNet
	Last Modified: 03-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC) 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	MFCAsync.exe contains a Visual C++ 5.0 project sample that shows the
	communication techniques between a client (AsyncClient) and a server
	(AsyncServer) application using MFC CAsyncSocket class on each sides.
	
	Here are some highlights of this sample:
	
	- MFCAsync.exe follows KB article Q175668, showing the use of Transmission
	  Control Protocol (TCP) socket communication in a separate thread other than
	  the Graphics User Interface (GUI) thread; as such, the blocking of the GUI
	  message pump does not affect the delivery of socket messages. Multiple
	  instances of AsyncClient can talk to the same instance of AsyncServer.
	
	- MFCAsync.exe also complies with KB Article Q185728 in issuing of socket Send
	  and Receive calls.
	
	- MFCAsync.exe adds message boundary on top of the stream-oriented TCP. Each
	  message is sent with a 4-byte-length packet header followed by the body of
	  the message. Users can append more customized packet header fields to this
	  length field.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	MFCAsync.exe
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	The flow of logic:
	
	1. AsyncServer listens on port 9898.
	
	2. AsyncClient spawns a thread, which connects to the AsyncServer.
	
	3. AsyncServer accepts the connection and spawns a thread to handle the socket
	  communication.
	
	4. AsyncClient sends data packet to AsyncServer.
	
	5. AsyncServer receives and sends the same data packet back to AsyncClient.
	
	6. AsyncClient receives data packet, reverses the data packet and sends back to
	  AsyncServer.
	
	7. Repeat steps 5 and 6 until being disconnected either by the AsyncClient or
	  AsyncServer.
	
	Steps to run the sample:
	
	1. Run AsyncServer.exe on machine A.
	
	2. Run AsyncClient.exe either on machine A or machine B.
	
	3. On the AsyncClient side, enter the server machine name where AsyncServer is
	  running. Click Connect. Enter text in the Send edit box. Click Send.
	
	4. When you are done with the test, click Disconnect on the AsyncClient side.
	
	REFERENCES
	==========
	
	For more information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q175668 FILE: MultiSoc: Illustrates Using Sockets in Multiple Threads
	
	For more information about downloading files from the Microsoft Software Library,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q185728 SAMPLE: MFCSocs.exe Avoids Two Common MFC Socket Mistakes
	
	Additional query words: CAsyncSocket multithreaded socket thread message
	
	======================================================================
	Keywords          : kbfile kbnetwork kbAPI kbMFC kbVC500 kbOSWin95 kbOSWin98 kbWinsock kbGrpDSNet 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
