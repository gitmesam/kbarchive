---
layout: page
title: "Q287093: INFO: DB2OLEDB Supports UPDATE/DELETE from SQL Linked Server"
permalink: /kb/287/Q287093/
---

## Q287093: INFO: DB2OLEDB Supports UPDATE/DELETE from SQL Linked Server

{% raw %}

	Article: Q287093
	Product(s): Microsoft SNA Server
	Version(s): 4.0 SP4,7.0 Service Pack 2,7.0 Service Pack 3
	Operating System(s): 
	Keyword(s): kbGrpDSVCDB kbDSupport kbGrpDSODBC kbGrpDSOLEDB kbhis2000
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Host Integration Server 2000 
	- Microsoft SNA Server, version 4.0 SP4 
	- Microsoft SQL Server 2000 (all editions) 
	- Microsoft SQL Server versions 7.0 Service Pack 2, 7.0 Service Pack 3 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Microsoft OLE DB Provider for DB2 (DB2OLEDB) that ships with Host
	Integration Server 2000 or SNA Server 4.0 Service Pack 4 supports SELECT,
	INSERT, UPDATE, and DELETE statements from SQL Server Linked Server.
	
	All earlier versions of DB2OLEDB support only SELECT and INSERT statements when
	used with SQL Server Linked Server.
	
	MORE INFORMATION
	================
	
	For an UPDATE or DELETE, the minimum requirements are as follows:
	
	- Host Integration Server 2000 or SNA Server 4.0 Service Pack 4
	
	- SQL Server 2000 or SQL Server 7.0 Service Pack 2
	
	To execute INSERT, UPDATE, and DELETE statements using four-part linked server
	queries, the SQL Server Distributed Query Processor (DQP) feature uses bookmark
	support in the underlying OLE DB provider. The OLE DB Provider for DB2 does not
	support bookmarks. However, when DQP loads the provider using service
	components, the client cursor engine (CCE) is invoked. The CCE provides
	scrollable cursors and bookmarks.
	
	INSERT, UPDATE, and DELETE statements when using four-part linked server queries
	can be supported using the CCE. However, some statements may fail or may update
	incorrect columns when there is no unique key column on the target tables, or
	when there are not enough unique values for the CCE to accurately determine
	which columns to update. In these cases, unpredictable results may occur, or DQP
	may fail to perform the update.
	
	SELECT, INSERT, UPDATE and DELETE are also supported with passthrough query using
	OpenQuery syntax.
	
	
	REFERENCES
	==========
	
	For additional information on DB2OLEDB and Linked Server, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q218590 INF: Configuring Data Sources for the Microsoft OLE DB Provider
	
	  Q222937 INF: Creating a Linked Server to DB2 using Microsoft OLE DB Provider
	  for DB2
	
	  Q235213 BUG: Four-part Name Linked Server Queries Fail Against DB2 for OS/390
	
	  Q216810 Creating Packages for Use with ODBC Driver for DB2 and OLE DB
	  Provider for DB2
	
	  Q269626 INFO: Permissions Needed to Create Packages Using DB2OLEDB on DB2 and
	  DB2/400
	
	  Q274160 FIX: Four-Part Inserts to DB2 Through LinkedServer Fail
	
	  Q277871 Linked Server SELECT's to DB2/400 Tables with a DBCS Character Field
	  Fail
	
	Additional query words:
	
	======================================================================
	Keywords          : kbGrpDSVCDB kbDSupport kbGrpDSODBC kbGrpDSOLEDB kbhis2000 
	Technology        : kbSQLServSearch kbAudDeveloper kbSQLServ2000Search kbSNAServSearch kbHostIntegServ2000 kbSQLServ700SP2 kbSQLServ700SP3 kbSQLServ2000 kbSNAServ400SP4
	Version           : :4.0 SP4,7.0 Service Pack 2,7.0 Service Pack 3
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
