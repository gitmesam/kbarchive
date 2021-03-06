---
layout: page
title: "Q180015: PRB: Stored Procedures Slower with MS Oracle ODBC Driver 2.0"
permalink: /kb/180/Q180015/
---

## Q180015: PRB: Stored Procedures Slower with MS Oracle ODBC Driver 2.0

{% raw %}

	Article: Q180015
	Product(s): Open Database Connectivity (ODBC)
	Version(s): 5.0,Build 2.573.2927,Build 2.73.7269,Build 2.73.7283.01,Build 2.73.7283.03
	Operating System(s): 
	Keyword(s): kbATM kbDatabase kbDriver kbODBC kbOracle kbRDO kbVBp500 kbGrpDSMDAC kbDSupport kbADO25
	Last Modified: 11-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft ODBC for Oracle version 2.0, versions Build 2.73.7269, Build 2.73.7283.01, Build 2.73.7283.03 
	- Microsoft ODBC for Oracle version 2.5 Build 2.573.2927 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you call an Oracle stored procedure through Remote Data Objects (RDO) or
	through ActiveX Data Objects (ADO) using Command.Refresh, the Microsoft Oracle
	ODBC Driver version 2.0 is slower than version 1.0.
	
	CAUSE
	=====
	
	The underlying ODBC API call (SQLProcedureColumns) was changed in version 2.0 of
	the MS Oracle ODBC Driver to accommodate Oracle package support. By making this
	change, the SQL for the API call increased ten-fold. The larger SQL statement
	results in the slower execution of Oracle stored procedures.
	
	RESOLUTION
	==========
	
	When using RDO there is no workaround. SQLProcedureColumns is always called.
	With ADO, if all of the Command attributes are set, the parameters collection is
	defined and Command.Refresh is not used, then SQLProcedureColumns is not called.
	For an example of how to use ADO so that SQLProcedureColumns is not called,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q176936 INFO: Visual Basic Accessing an Oracle Database Using ADO
	
	
	STATUS
	======
	
	Microsoft is researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Following is the SQL statement that SQLProcedureColumns creates on Oracle
	(captured through Oracle SQL trace):
	
	     select null,owner,decode(package_name,NULL,object_name,
	     package_name||'.'||object_name),decode(position,0,
	     'RETURN_VALUE',nvl(argument_name,chr(0))),
	     decode(data_type,'REFCURSOR',3,decode(in_out,
	     'IN',1,'IN/OUT',2,'OUT',decode(argument_name,null,5,4)
	     ,0)), decode(data_type, 'CHAR', 1, 'DATE', 11, 'FLOAT'
	     , 8, 'LONG', -1, 'LONG RAW', -4, 'NUMBER', 3, 'RAW', -3,
	     'VARCHAR2', 12, 0), data_type, decode(data_type, 'CHAR',
	     decode(data_length, null, 255, data_length), 'DATE', 19,
	     'FLOAT', 15, 'LONG', 2147483647, 'LONG RAW', 2147483647,
	     'NUMBER', decode(data_precision, null, 38, data_precision),
	     'RAW', decode(data_length, null, 255, data_length),
	     'VARCHAR2', decode(data_length, null, 2000, data_length),
	     data_length), decode(data_type, 'CHAR', decode(data_length,
	     null, 255, data_length), 'DATE', 16, 'FLOAT', 8, 'LONG',
	     2147483647, 'LONG RAW', 2147483647, 'NUMBER', decode(
	     data_precision, null, decode(data_scale, 0, 40, 40), 40),
	     'RAW', decode(data_length, null, 255, data_length),
	     'VARCHAR2', decode(data_length, null, 2000, data_length),
	     data_length), decode(data_type, 'DATE', 0, 'FLOAT', null,
	     'NUMBER', 0, data_scale), decode(data_type, 'NUMBER', 10,
	     'FLOAT', 10, 'DATE', 10, null), 2, null, overload,  sequence
	     from all_arguments where data_level = 0 and
	     decode(package_name,NULL,object_name,package_name||'.'||
	     object_name) like 'PACKPERSON.ONEPERSON' escape '\'
	     order by 2,3,14,15
	
	If you use ADO (as demonstrated in KB article Q176936) instead of RDO, the above
	statement is never issued to Oracle. Because of this, ADO can execute an Oracle
	stored procedure much faster than RDO.
	
	(c) Microsoft Corporation 1998, All Rights Reserved.
	Contributions by Sam Carpenter, Microsoft Corporation
	
	
	Additional query words: MS Oracle ODBC Driver rdo ado stored procedure
	
	======================================================================
	Keywords          : kbATM kbDatabase kbDriver kbODBC kbOracle kbRDO kbVBp500 kbGrpDSMDAC kbDSupport kbADO250 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbODBCSearch kbVB500 kbODBCOracle2737269 kbODBCOracle273728303 kbODBCOracle25732927 kbODBCOracle273728301 kbODBCOracle200Search kbODBCOracle250Search
	Version           : :5.0,Build 2.573.2927,Build 2.73.7269,Build 2.73.7283.01,Build 2.73.7283.03
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
