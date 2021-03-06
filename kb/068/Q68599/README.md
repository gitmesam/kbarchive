---
layout: page
title: "Q68599: Integer Divide by 0 Only on 8088/86 Machine"
permalink: /kb/068/Q68599/
---

## Q68599: Integer Divide by 0 Only on 8088/86 Machine

{% raw %}

	Article: Q68599
	Product(s): See article
	Version(s): 6.00 6.00a
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | s_quickc | mspl13_c
	Last Modified: 24-JAN-1991
	
	The code below produces an error on computers with Intel 8088/86
	processors, but runs correctly on later versions of the Intel
	processors, such as the 80286. When the program is run on an 8088/8086
	machine, the following error will occur:
	
	   run-time error R6003
	   - integer divide by 0
	
	The problem is caused by the difference between the IDIV instruction
	on the processors. The Intel programmer's reference manual for the
	8088/86 processor states the following:
	
	   For word integer division, the maximum positive quotient is +32767
	   and the minimum negative quotient is -32767. If the quotient is
	   positive and exceeds the maximum, or is negative and is less than
	   the minimum, the quotient and remainder are undefined, and a type 0
	   interrupt is generated.
	
	A type 0 (zero) interrupt is an "Integer Divide By 0" error, which
	means that the lowest negative number that can be used on an 8088/86
	CPU machine for integer division is -32767. The developer should not
	allow an integer to become -32768. This limitation has changed with
	later versions of the Intel processors, which allow integer division
	with a quotient of -32768.
	
	Note: This is not a problem with the code generated by the compiler.
	Because the problem is exhibited at execution time, it is up to the
	programmer to ensure that an integer will not take on a value of
	-32768 before it is used as a quotient.
	
	Sample Code
	-----------
	
	#include <stdio.h>
	void main(void)
	{
	  int numerator=-32768;
	  int denominator=1;
	  int result;
	  result=numerator/denominator;
	}

{% endraw %}
