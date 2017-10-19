---
layout: page
title: "Q99295: Harvard Graphics Load Failure Caused by Set Archive Bit"
permalink: kb/099/Q99295/
---

## Q99295: Harvard Graphics Load Failure Caused by Set Archive Bit

	Article: Q99295
	Product(s): Microsoft LAN Manager
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-JUL-2001
	
	SUMMARY
	=======
	
	Problems loading Harvard Graphics and old versions of Lotus 1-2-3 may be caused
	by the archive bit on the user directory. If the bit is set, these programs
	can't find the directory.
	
	Use the ATTRIB command to remove the archive bit:
	
	  attrib -a <dir name>
	
	SYMPTOMS
	========
	
	A client could not install Harvard Graphics. The problem was with one server
	(only) out of several. This was the sequence of attempts:
	
	1. Logon as ADMIN.
	
	2. Execute Harvard Graphics from a batch file; if the data directory does not
	  exist, create it.
	
	3. Run Harvard Graphics.
	
	Up to here, everything was OK. The directory had "RX" access.
	
	1. Revoke access (net access x:\users /revoke).
	
	2. Add access (net access x:\users /grant users:rx).
	
	Harvard Graphics responded at this point that the directory did not exist.
	
	This problem seemed to concern only the Harvard Graphics server and the
	modification of access privileges, not just the revoke and grant example above.
	The usual solutions (reformatting the drives, reinstalling Harvard Graphics,
	copying it from another working install, etc.) failed.
	
	CAUSE
	=====
	
	The archive bit on the user directory was set, so Harvard Graphics couldn't find
	the directory.
	
	Note: The cause for this problem in the reported instance was further hidden by
	the fact that the NET ACCESS command sets the archive attribute on LAN Manager
	servers, but NOT on 3+Open servers.
	
	RESOLUTION
	==========
	
	Use the ATTRIB command to remove the archive bit:
	
	  attrib -a <dir name>
	
	Additional query words: 2.00 2.0 2.10 2.1 2.10a 2.1a 2.20 2.2
	
	======================================================================
	Keywords          :  
	
	=============================================================================
	