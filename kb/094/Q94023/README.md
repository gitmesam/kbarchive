---
layout: page
title: "Q94023: MS-DOS Kernel Is Larger Than 60K"
permalink: /kb/094/Q94023/
---

## Q94023: MS-DOS Kernel Is Larger Than 60K

{% raw %}

	Article: Q94023
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 21-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Microsoft MS-DOS MEM command (MEM /C) reports an unusually large size for
	the MS-DOS kernel under the following two conditions:
	
	- You are creating a large number of buffers in the CONFIG.SYS file.
	
	- You have a virus.
	
	MORE INFORMATION
	================
	
	The MS-DOS 5.0 kernel (simply displayed as "MS-DOS" by MEM) usually occupies
	approximately 60K of conventional memory. If you load more than 48 buffers, or
	if you do not load MS-DOS high, the buffers load in conventional memory, causing
	the MS-DOS kernel to grow.
	
	For example, increasing the "buffers=" setting in the CONFIG.SYS file from 40 to
	60 increases the size of the MS-DOS kernel by 20K. This growth occurs because
	each additional buffer takes up approximately 532 bytes of memory, and once the
	value for buffers= is increased above 48, all the buffers load into conventional
	memory.
	
	Note: One buffer is always loaded into conventional memory, so the number of
	buffers actually loaded into the high memory area (HMA) is one less than the
	number of buffers specified.
	
	If the buffers= setting is not causing the kernel to increase in size, you may
	have a virus, such as one that attaches itself to COMMAND.COM. To determine if
	this is the case, you can obtain virus-scanning software from many third-party
	vendors.
	
	For more information on memory management, query on the following words in the
	Microsoft Knowledge Base:
	
	  " ms-dos and buffers and uma " (without the quotation marks)
	
	Additional query words: 3.10 5.00 large dos
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS500
	Version           : MS-DOS:5.0
	
	=============================================================================
	

{% endraw %}
