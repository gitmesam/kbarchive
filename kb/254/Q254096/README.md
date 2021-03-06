---
layout: page
title: "Q254096: OEM Support Tools Phase 2 Service Release 2 Availability"
permalink: /kb/254/Q254096/
---

## Q254096: OEM Support Tools Phase 2 Service Release 2 Availability

{% raw %}

	Article: Q254096
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.51,4.0
	Operating System(s): 
	Keyword(s): kbDebug kbgraphxlinkcritical
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51, 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Original Equipment Manufacturer (OEM) Support Tools are troubleshooting and
	development tools provided for Windows NT 3.51 x86-based and Windows NT 4.0 x86-
	and Alpha-based computers; including all service pack revisions. These tools are
	available in English language only. These tools extend the functionality of
	existing debugging tools such as a kernel debugger, provide new features upon
	which new debugging methodologies can be based, and provide development support.
	This article provides information about these tools, and how to install them.
	
	IMPORTANT: OEM Support Tools Phase 3 Service Release 0 is also available and
	replaces OEM Support Tools Phase 2 Service Release 2. Phase 3 SR0 supports
	Windows NT 4.0 (x86 only) and Windows 2000. For additional information, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q253066 OEM Support Tools Phase 3 Service Release 1 Availability
	
	Phase 2 SR2 is still applicable to any of the following users:
	
	- Phase 2 tools (any tools) users working on Windows NT 3.51 on x86 platform
	  (Phase 3 no longer supports Windows NT 3.51)
	
	- Phase 2 tools (any tools) users working on Windows NT 4.0 on Alpha platform
	  (Phase 3 no longer supports Windows NT 4.0 on Alpha)
	
	- Phase 2 Pool Enhancements users working on Windows NT 4.0 on x86 platform
	  (Pool Enhancements were retired in Phase 3)
	
	MORE INFORMATION
	================
	
	The following four tools/set of tools are available in OEM Support Tools Phase 2
	Service Release 2:
	
	Kernel Debugger Extensions
	--------------------------
	
	New debugger extensions to facilitate examination and analysis of a wider range
	of kernel data structures than is conveniently possible today, especially when
	dealing with crash dumps.
	
	Pool Enhancements
	-----------------
	
	Tools for memory pool caller-tracking/tail-checking, pool logging, pool free
	block pattern fill, and increasing available pool statistics.
	
	Kernel Memory Space Analyzer
	----------------------------
	
	A heuristics-based kernel memory crash dump analysis tool to aid in diagnosing
	memory corruption problems. This tool discovers and analyzes anomalies in the
	kernel memory space.
	
	User Mode Process Dump
	----------------------
	
	A tool that allows users to create dump files from any Win32 process, such as
	Csrss.exe or Explorer.exe, that can be examined using Windows Debugger. The tool
	allows for manual creation of dump files via the command line or hot-key, or
	automatic creation when exceptions occur in monitored processes.
	
	To install the OEM Support Tools:
	---------------------------------
	
	1. The following files are available for download from the Microsoft Download
	  Center:
	
	  Windows NT 3.51 and Windows NT 4.0 x86: DownloadDownload Oem202i.zip now
	  (http://download.microsoft.com/download/winntsrv40/utility/2.0/nt4/en-us/oem202i.zip)
	  Windows NT 4.0 Alpha: DownloadDownload Oem202a.zip now
	  (http://download.microsoft.com/download/winntsrv40/Utility/2.0/ALPHA/EN-US/oem202a.zip)
	
	  For additional information about how to download Microsoft Support files,
	  click the article number below to view the article in the Microsoft Knowledge
	  Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	  Microsoft used the most current virus detection software available on the date
	  of posting to scan this file for viruses. Once posted, the file is housed on
	  secure servers that prevent any unauthorized changes to the file.
	
	2. Click "Save this program to disk", and then use the WinZip.exe tool to unzip
	  the files to your computer.
	
	3. Refer to the Relnote.txt file for information regarding this release. Refer
	  to the \Doc\Userdocs.doc file for installation and usage instructions.
	
	NOTE: Debug symbol files are required by an administrator to do both kernel and
	user mode debugging, providing a method to resolve global variables and function
	names in the loaded executable file. Click the file names below to download the
	symbol files:
	
	  Windows NT 3.51 and Windows NT 4.0 x86: DownloadDownload Oem202is.zip now
	  (http://download.microsoft.com/download/winntsrv40/utility/2.0/nt4/en-us/oem202is.zip)
	  Windows NT 4.0 Alpha: DownloadDownload Oem202as.zip now
	  (http://download.microsoft.com/download/winntsrv40/Utility/2.0/ALPHA/EN-US/oem202as.zip)
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDebug kbgraphxlinkcritical 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : winnt:3.51,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
