---
layout: page
title: "Q41553: scanf, sscanf, fscanf Fail on the Regular Expression"
permalink: /kb/041/Q41553/
---

## Q41553: scanf, sscanf, fscanf Fail on the Regular Expression

{% raw %}

	Article: Q41553
	Product(s): See article
	Version(s): 2.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | buglist2.00 | mspl13_c
	Last Modified: 28-FEB-1989
	
	The scanf() function fails when the left bracket ([) and caret (^) are
	immediately followed by a right bracket (]) in a regular expression.
	This problem also occurs in the scanf and fscanf functions.
	
	Microsoft has confirmed this to be a problem in Version 2.00. We are
	researching this problem and will post new information as it becomes
	available.
	
	Consider the following program:
	
	   #include <stdio.h>
	
	   void main (void)
	    { char string[20];
	
	      sscanf ("Blibbet Fever!", "%9[^]", string); /* Does not Work */
	
	      printf ("string=%s\n", string);
	    }
	
	The sscanf function fails to parse the buffer correctly and so the
	output of this program is unpredictable. The output should be as
	follows:
	
	   string=Blibbet F
	
	The workaround to this problem is to follow the caret with a character
	you know will not be in the string you are scanning. A working version
	of the above program follows:
	
	   #include <stdio.h>
	
	   void main (void)
	    { char string[20];
	
	      sscanf ("Blibbet Fever!", "%9[^\xff]", string); /* Does work */
	
	      printf ("string=%s\n", string);
	    }
	
	Note: The format string "%9s" is not adequate because it stops
	scanning when white space is encountered.

{% endraw %}
