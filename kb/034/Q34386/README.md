---
layout: page
title: "Q34386: Maximum of 40 File Handles in C 5.10 Multi-Thread Programs"
permalink: /kb/034/Q34386/
---

## Q34386: Maximum of 40 File Handles in C 5.10 Multi-Thread Programs

{% raw %}

	Article: Q34386
	Product(s): See article
	Version(s): 5.10   | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 12-OCT-1988
	
	Question:
	   Can I increase the number of file handles to more than 40
	in a multi-threaded application produced by C Version 5.10?
	
	Response:
	   The maximum number of file handles available for multiple-threaded
	applications is 40 by default; this number cannot be increased because
	the multi-threaded startup code is unavailable. Consequently, the C
	startup code constant _NFILE_, which is used to specify the number of
	available file handles, cannot be changed from its default of 40, even
	though the default number of file handles in OS/2 is 255.

{% endraw %}
