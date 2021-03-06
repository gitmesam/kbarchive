---
layout: page
title: "Q90026: FoxView Memo Field Limitations"
permalink: /kb/090/Q90026/
---

## Q90026: FoxView Memo Field Limitations

{% raw %}

	Article: Q90026
	Product(s): Microsoft Fox Miscellaneous Products
	Version(s): MS-DOS:2.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 23-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FoxBASE+ for MS-DOS, version 2.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	FoxView memo fields have four major limitations, as follows:
	
	1. The user cannot enter a memo field (using the CTRL+HOME or CTRL+PAGE DOWN key
	  combinations) from an @ GET <memofieldname> statement, or from a format
	  file with an @ GET <memofieldname> and a READ statement.
	
	2. An application cannot display a memo field using an @ SAY
	  <memofieldname> statement. An application must use the REPORT FORM and
	  ? commands to display memo field contents.
	
	3. The PACK command does not pack the .DBT file. Only the COPY TO command packs
	  the .DBT file.
	
	4. The COPY TO DELIMITED or COPY TO SDF files create an ASCII file with the text
	  from a database. However, the text from memo fields is not included in the
	  file. The only method of copying memo field data to a text file is as
	  follows:
	
	   - SET ALTERNATE TO <textfile>
	
	   - Use the REPORT FORM or ? commands to copy the contents of the memo fields
	     into the file.
	
	  The following sample code copies data from a memo field into the JUNK.TXT
	  file:
	
	        SET ALTERNATE TO JUNK.TXT
	        SET ALTERNATE ON
	        USE <DATABASEFILE>
	        GO TOP
	        DO WHILE NOT EOF()
	           ? <MEMOFIELDNAME>
	           SKIP
	        ENDDO
	        CLOSE ALL
	        SET ALTERNATE OFF
	
	The following steps demonstrate one method of copying the data from a memo field
	into an application generated by FoxView. This method is limited because the
	control of screen formatting and color is lost. (Paging, FIND, GOTO, LOCATE, and
	so on are examples of screen formatting.) FoxBASE+ ignores SET COLOR statements
	in a format file.
	
	1. Create a format file similar to the following:
	
	     * FILENAME.FMT
	     @ 0,0 SAY "Record: SUBSTR(STR(RECNO()+1000000,7),2)
	     @ 20,0 SAY Promptbar
	     *  ---- DISPLAY memo field labels and field names.
	     @ 2,0 SAY "Enter memo1"
	     @ 3,0 SAY "Enter memo2"
	     @ 2,12 GET Memofield1
	     @ 3,12 GET Memofield2
	     @ 21,0 SAY "Press CTRL+HOME to Enter MEMO or CTRL+END Exit MEMO")
	     * EOF: FILENAME.FMT
	
	2. In the APPEND subprogram, modify the code segment that displays the APPEND
	  prompt to include a memo prompt and an additional CASE segment to implement
	  the menu option, as follows:
	
	     @ row,0 SAY "APPEND: (Return)-add Memo  Edit  Finished"
	     DO GetKey WITH choice,"MEF",Returnkey
	
	     CASE choice="M"
	        *   ----- Append memo data by using Format File and EDIT.
	        recnum = RECNO()
	        SET SCOREBOARD ON
	        *   ---- Replace <Fmtfile> with Format File name.
	        SET FORMAT TO Fmtfile
	        EDIT recnum
	        CLOSE FORMAT
	        SET SCOREBOARD OFF
	        GOTO recnum
	        DO TEST_FORM
	        DO SayRec
	     CASE ...
	
	3. Modify the EDIT subprogram to include a MEMO prompt and an additional CASE
	  segment to run the menu option in the Edit/View menu, as follows:
	
	     @ row+1,2 SAY "    Memo  Next  Previous  <Return>"
	     @ row,0 SAY "EDIT/VIEW:  Edit  Find  Goto  Locate  <Del>"
	     DO GetKey with editchoice, "EFGLMNP"+DelRecord+Returnkey
	
	     CASE editchoice ="M"
	        *   ---- Edit memo field using format file and EDIT.
	        oldrecnum = RECNO()
	        SET SCOREBOARD ON
	        *   ---- Replace <Fmtfile> with format file name.
	        SET FORMAT TO Fmtfile
	        EDIT
	        CLOSE FORMAT
	        SET SCOREBOARD OFF
	        GOTO oldrecnum
	        DO TEST_FORM
	        Do SayRec
	     CASE...
	     ENDCASE
	
	Reference(s):
	
	"FoxView-FoxCode-FoxDoc," pages 13.5-13.6
	
	Additional query words: 2.00 memo limitations fox view base
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbFoxproSearch kbFoxBASE210DOS kbFoxBASESearch
	Version           : MS-DOS:2.1
	
	=============================================================================
	

{% endraw %}
