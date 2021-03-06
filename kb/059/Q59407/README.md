---
layout: page
title: "Q59407: PRB: Inaccurate Representation of Large Double Values"
permalink: /kb/059/Q59407/
---

## Q59407: PRB: Inaccurate Representation of Large Double Values

{% raw %}

	Article: Q59407
	Product(s): Microsoft C Compiler
	Version(s): 1.0,1.5,2.0,4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbCompiler kbVC100 kbVC150 kbVC200 kbVC400 kbVC500 kbVC600
	Last Modified: 29-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft C for MS-DOS 
	- Microsoft C for OS/2 
	- Microsoft C/C++ for MS-DOS 
	- Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5 
	- Microsoft Visual C++, 32-bit Editions, versions 1.0, 2.0, 4.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft C, subtracting double values greater than or equal to 1.0E+025 may
	return inaccurate results.
	
	CAUSE
	=====
	
	This is expected behavior and is due to the imprecise nature of floating-point
	math. Anytime floating-point math uses large numbers, there will be
	rounding/truncation errors and errors introduced due to imprecise representation
	of a result in binary format.
	
	MORE INFORMATION
	================
	
	Because double values are only 15-digit precise, simple subtraction of two large
	numbers can give unexpected results. The following sample code demonstrates this
	behavior.
	
	Double values less than 1.0E+25 may not experience the same problem.
	
	Sample Code
	-----------
	
	  #include <stdio.h>
	
	  double a = 1E+28, tmp = 9E+28;
	
	  void main (void)
	  {
	
	     printf ("a = %le    tmp = %le\n", a, tmp);
	
	     while (tmp >= 1E+25) {
	        tmp -= a;
	        printf ("a = %le    tmp = %le\n", a, tmp);
	     }
	  }
	
	The above sample code produces the following output:
	
	a = 1.000000e+028    tmp = 9.000000e+028
	a = 1.000000e+028    tmp = 8.000000e+028
	a = 1.000000e+028    tmp = 7.000000e+028
	a = 1.000000e+028    tmp = 6.000000e+028
	a = 1.000000e+028    tmp = 5.000000e+028
	a = 1.000000e+028    tmp = 4.000000e+028
	a = 1.000000e+028    tmp = 3.000000e+028
	a = 1.000000e+028    tmp = 2.000000e+028
	a = 1.000000e+028    tmp = 1.000000e+028
	a = 1.000000e+028    tmp = 1.319414e+013
	
	Additional query words: 8.00 8.00c 9.00
	
	======================================================================
	Keywords          : kbCompiler kbVC100 kbVC150 kbVC200 kbVC400 kbVC500 kbVC600 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbZNotKeyword8 kbvc150 kbvc100 kbCCompSearch kbZNotKeyword3 kbVC500 kbVC600 kbVC200 kbVC32bitSearch kbVC16bitSearch kbVC500Search
	Version           : :1.0,1.5,2.0,4.0,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
