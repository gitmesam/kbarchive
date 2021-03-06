---
layout: page
title: "Q95081: INF: How the dBASE Driver Performs Locking"
permalink: /kb/095/Q95081/
---

## Q95081: INF: How the dBASE Driver Performs Locking

{% raw %}

	Article: Q95081
	Product(s): Open Database Connectivity (ODBC)
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-JUL-2001
	
	1.00
	
	MS-DOS
	
	kbusage
	
	SUMMARY
	=======
	
	This article discusses the locking mechanisms of the dBASE driver in single and
	multiuser modes.
	
	MORE INFORMATION
	================
	
	The ODBC dBASE driver is capable of using a dBASE data source in single and
	multiuser modes. The data source is in single user mode by default, after setup
	of the data source is done. There is an entry called
	
	  SingleUser=TRUE
	
	in the ODBC.INI file, under the section for that data source. Changing the value
	of this entry to FALSE will put the data source in multiuser mode.
	
	As far as the dBASE driver is concerned, a "dBASE data source" is a directory
	containing dBASE files (data files, index files, and so on). In single user
	mode, all the tables in the data source (that is, all the .DBF files in the
	directory) are exclusively locked by the dBASE driver. Also, no other user can
	connect to the data source. In multiuser mode, multiple users can access the
	same data source and the same table (file) simultaneously. If a user wants to
	update a record(s), then it is exclusively locked. Whether other users can read
	the record depends on the whether the table is a dBASE III or a dBASE IV table.
	In a dBASE III table, other users cannot read the record. In a dBASE IV table,
	other users can read this record ("dirty reads" are permitted).
	
	The fact that record locking is done in multiple user mode does not imply that
	any kind of transaction serializability is available. The dBASE driver is not
	transaction capable and does not provide any kind of transaction isolation
	options. So, if you are browsing through a table and want to update a record,
	there is no guarantee that the record will not be updated behind your back.
	
	Additional query words: 1.00
	
	======================================================================
	Keywords          :  
	
	=============================================================================
	

{% endraw %}
