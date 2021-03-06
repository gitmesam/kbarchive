---
layout: page
title: "Q169791: PRB: Query Bases Result Set Field Size On Non-Included Values"
permalink: /kb/169/Q169791/
---

## Q169791: PRB: Query Bases Result Set Field Size On Non-Included Values

{% raw %}

	Article: Q169791
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.5b,2.5c,2.6a,3.0b; MS-DOS:2.0,2.5,2.5a,2.5b,2.6,2.6a; WINDOWS:2.5,2.5a,2.5b
	Operating System(s): 
	Keyword(s): kbHWMAC kbvfp
	Last Modified: 11-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5, 2.5a, 2.5b, 2.6, 2.6a 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b, 2.6, 2.6a 
	- Microsoft FoxPro for Macintosh, versions 2.5b, 2.5c, 2.6a 
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A query may result with truncated values in an expression columns.
	
	CAUSE
	=====
	
	The expression column is basing its width on the first record value of the
	source table.
	
	RESOLUTION
	==========
	
	Change the expression to use an IIF() function that returns a value of necessary
	width. This forces FoxPro to create a column wide enough to hold the results of
	the expression column. NOTE: The example code uses the table created at the
	bottom of this article in the MORE INFORMATION section. Here's an example:
	
	     SELECT *, IIF(ISNULL(fld2),SPACE(15),TTOC(fld2,1)) AS test ;
	     FROM temp WHERE fld2 is NOT NULL
	
	-or-
	
	Change the source table's order so that the first record's value in the source
	table is wide enough to hold the expression columns output. An index order
	cannot be used here, since FoxPro opens the source table in another workarea.
	Using an additional query can do this. Here's an example:
	
	     SELECT * FROM temp ORDER BY fld2 DESCEND INTO CURSOR temp2
	     SELECT *, TTOC(fld2,1) AS test FROM temp2
	
	STATUS
	======
	
	Microsoft is researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Execute the following five lines to create and populate a table:
	
	        CREATE TABLE temp (fld1 C(3), fld2 T NULL, fld3 C(3))
	        INSERT INTO temp (fld1, fld2, fld3) VALUES ('aaa',NULL,'aaa')
	        INSERT INTO temp (fld1, fld2, fld3) VALUES ('bbb',datetime(),'bbb')
	        INSERT INTO temp (fld1, fld2, fld3) VALUES ('ccc',NULL,'ccc')
	        INSERT INTO temp (fld1, fld2, fld3) VALUES ('ddd',datetime(),'ddd')
	
	2. Execute the following lines from the Command window:
	
	        SELECT *, TTOC(fld2,1) AS test FROM temp
	        SELECT *, TTOC(fld2,1) AS test FROM temp WHERE fld2 IS NOT NULL
	
	Note that the test column comes up improperly sized for both queries. The test
	column is based solely on the width of the source table's first record, a 1 byte
	NULL character. Thus, the column shows only a 1 from the result of the TTOC()
	function.
	
	This occurs even when records that contain NULL are not included in the result
	set, per the second query.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbHWMAC kbvfp 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro250bMac kbFoxPro260aMac kbFoxPro250cMac kbFoxPro200DOS kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro260DOS kbFoxPro260aDOS kbFoxPro260 kbFoxPro250 kbFoxPro250a kbFoxPro250b kbFoxPro260a kbVFP300bMac kbVFP300 kbVFP300b kbVFP500 kbVFP500a
	Version           : MACINTOSH:2.5b,2.5c,2.6a,3.0b; MS-DOS:2.0,2.5,2.5a,2.5b,2.6,2.6a; WINDOWS:2.5,2.5a,2.5b,2.6,2.6a,3.0,3.0b,5.0,5.0a
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
