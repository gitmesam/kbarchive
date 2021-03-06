---
layout: page
title: "Q28499: DOS 2.xx Does Not Recognize &#92;Mouse1&#92;Mouse"
permalink: /kb/028/Q28499/
---

## Q28499: DOS 2.xx Does Not Recognize &#92;Mouse1&#92;Mouse

{% raw %}

	Article: Q28499
	Product(s): See article
	Version(s): 1.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | | mspl13_basic
	Last Modified: 26-APR-1988
	
	Problem:
	   After running the mouse setup routine and rebooting my machine, the
	mouse driver will not install.
	
	Response:
	   Because DOS Version 2.xx does not recognize the path statement in
	command lines, such as /mouse1/mouse in the AUTOEXEC.BAT file, the
	mouse driver never installs.
	   To work around this, edit your AUTOEXEC.BAT file to change the
	directory to your MOUSE1 subdirectory. Then, directly call the MOUSE
	and CPANEL as follows:
	
	  CD \MOUSE1
	  MOUSE
	  CPANEL
	  CD\

{% endraw %}
