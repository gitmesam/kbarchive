---
layout: page
title: "Q128522: Replacing Carriage Return &amp; Line Feeds with Other Characters"
permalink: /kb/128/Q128522/
---

## Q128522: Replacing Carriage Return &amp; Line Feeds with Other Characters

{% raw %}

	Article: Q128522
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2.6a,3.0
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 12-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, version 2.6a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article shows by example how to have a program process a file to replace
	carriage returns and line feeds with a double dollar sign. You can modify the
	code to use a character other than the double dollar sign by replacing the
	double dollar sign ASCII value (CHR(36)) with some other appropriate ASCII
	value. The code in this article also demonstrates how to use low level file
	functions.
	
	MORE INFORMATION
	================
	
	The following program takes two parameters:
	
	- The file that needs carriage returns and line feeds removed (file1).
	
	- The file name to write to (file2).
	
	Sample Code
	-----------
	
	  PARAMETER file1,file2
	  PRIVATE fhandle_in,fhandle_out,fisize,inchar
	
	  fhandle_in=FOPEN(file1,2)
	  IF (fhandle_in#-1)                 && open read/write buffered
	     fhandle_out=FCREATE(file2)      && default read/write
	     fisize=FSEEK(fhandle_in,0,2)    && get the size of the file
	     =FSEEK(fhandle_in,0,0)          && reposition pointer to beginning of
	                                     && file
	     x=1
	     DO WHILE (x<=fisize)            && process the whole file
	        inchar=FREAD(fhandle_in,1)   && read 1 byte at a time
	        IF ((inchar = CHR(13)) .OR. ;
	            (inchar = CHR(10)))
	            *** change the replacement character '$$'
	            *** by changing the CHR value below
	           =FWRITE(fhandle_out,CHR(36)) && replace crlf with $$
	        ELSE
	           =FWRITE(fhandle_out,inchar)  && write the character to file
	        ENDIF
	        x=x+1                           && increment the variable
	     ENDDO
	     =FCLOSE(fhandle_in)                && release the file handle to close
	                                        && file1
	     =FCLOSE(fhandle_out)               && release the file handle to close
	                                        && file2
	     MODIFY FILE &file2                 && opens the target file for viewing
	  ELSE
	     RETURN .F.                         && could not open the input file
	  ENDIF
	
	How to Use the Sample Code
	--------------------------
	
	To demonstrate the code example, copy it into a new program file, and save it as
	TEST.PRG. Then from the Command Window, type:
	
	     Do TEST.PRG with "C:\TEST.TXT", "C:\TEST1.TXT"
	
	NOTE: Please note that file names passed to a program as parameters must be
	enclosed by quotation marks.
	
	Here C:\TEST.TXT is the file that needs carriage returns and line feeds removed,
	and C:\TEST1.TXT is the name of the new file.
	
	Additional query words: VFoxWin FoxWin 3.00 2.60a
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbFoxPro260a kbVFP300
	Version           : WINDOWS:2.6a,3.0
	
	=============================================================================
	

{% endraw %}
