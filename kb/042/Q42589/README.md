---
layout: page
title: "Q42589: Mouse Not Supported on VGA in OS/2 Real Mode; OK in MS-DOS"
permalink: /kb/042/Q42589/
---

## Q42589: Mouse Not Supported on VGA in OS/2 Real Mode; OK in MS-DOS

{% raw %}

	Article: Q42589
	Product(s): See article
	Version(s): 6.00 6.00b 7.00 | 6.00 6.00b 7.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | SR# S890222-67 B_QuickBas | mspl13_basic
	Last Modified: 2-FEB-1990
	
	This information applies to Microsoft QuickBASIC Versions 4.00, 4.00b,
	and 4.50 for MS-DOS, to Microsoft BASIC Compiler Versions 6.00 and
	6.00b for MS-DOS and MS OS/2, and to Microsoft BASIC Professional
	Development System (PDS) Version 7.00 for MS-DOS and MS OS/2.
	
	In MS OS/2 real mode under MS OS/2 Versions 1.00 and 1.10, due to
	limitations of the MS OS/2 mouse controller, the mouse driver does not
	support operating with VGA graphics. The mouse works correctly in EGA,
	CGA, and text modes. This problem was corrected in MS OS/2 Version
	1.20.
	
	In MS OS/2 protected mode, the MS OS/2 mouse driver does not support
	the drawing of the mouse pointer in graphics modes. It is up to the
	application to draw its own pointer. The mouse driver provides
	notification of mouse movement to an MS OS/2 application, provided
	that the VioSetMode CALL (set graphics mode) is used AFTER the MouOpen
	(open the mouse) and the MouSetDevStatus (to disable pointer drawing)
	CALLs are performed.
	
	More information on the VioSetMode and MouSetDevStatus MS OS/2 API
	CALLs can be found in the "Microsoft Operating System/2: Programmer's
	Toolkit Programming Tools."

{% endraw %}
