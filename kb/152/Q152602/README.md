---
layout: page
title: "Q152602: DOC: MSBV3032.DLL Incorrectly Referenced in On-Line Help"
permalink: /kb/152/Q152602/
---

## Q152602: DOC: MSBV3032.DLL Incorrectly Referenced in On-Line Help

{% raw %}

	Article: Q152602
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kb3rdparty kbusage kbdocerr kbDAOsearch kbDatabase kbMFC kbVC
	Last Modified: 04-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The DAO SDK, included with:
	   - *EDITOR Please do not choose this product*Microsoft Visual C++ 32-bit Edition* use 241, 265, 225, versions 4.0, 4.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In Visual C++ Books Online the following topic is incomplete:
	
	  Product Documentation
	   + SDKs
	      + DAO SDK
	         + Using Data Access
	            + Initializing the BTRIEVE Database Driver
	
	This topic discusses the MSBV3032.DLL, but this file is not installed by the DAO
	SDK setup. A version of this file is shipped with MS Access 7.0, but it is
	non-functional.
	
	MORE INFORMATION
	================
	
	Microsoft did not ship a BTRIEVE driver in DAO 3.0. The reference to this file
	is a documentation error.
	
	
	Microsoft Access 7.0 does not ship with a Btrieve driver. Microsoft was unable to
	obtain a 32-bit Btrieve engine in the time frame required to release Microsoft
	Access 7.0. Btrieve Technologies Inc. has a 32-bit ODBC driver available. For
	information about obtaining this driver and the 32-bit Btrieve engine, please
	contact Btrieve Technologies Inc at 1-800-287-4383.
	
	NOTE: The third-party contact information included in this article is provided to
	help you find the technical support you need. This contact information is
	subject to change without notice. Microsoft in no way guarantees the accuracy of
	this third-party contact information.
	
	REFERENCES
	==========
	
	For more information, please see the following Access article on the Microsoft
	Knowledge Base:
	
	  Q141623 INF: Btrieve ISAM Not Available in Microsoft Access 7.0
	
	Additional query words:
	
	======================================================================
	Keywords          : kb3rdparty kbusage kbdocerr kbDAOsearch kbDatabase kbMFC kbVC 
	Technology        : kbAudDeveloper kbDAOsearch kbSDKDAOSearch kbSDKSearch
	Version           : winnt:
	
	=============================================================================
	

{% endraw %}
