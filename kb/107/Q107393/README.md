---
layout: page
title: "Q107393: Fax Modem Class Required for Binary File Transfers"
permalink: /kb/107/Q107393/
---

## Q107393: Fax Modem Class Required for Binary File Transfers

{% raw %}

	Article: Q107393
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): WINDOWS:3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups version 3.11 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	With Microsoft At Work PC Fax version 1.0 (supplied with Microsoft Windows for
	Workgroups 3.11), if you want to perform binary file transfers or use the
	advanced security features, you must use a Class 1 fax modem at both ends of the
	communication. This article provides instructions to determine what class of fax
	modem you have.
	
	MORE INFORMATION
	================
	
	Use the following procedure to determine what class of fax modem you are using:
	
	1. Load the Terminal application provided with Windows for Workgroups and
	  configure it with the correct settings for your modem.
	
	2. In the Terminal window, type the following:
	
	  AT+FCLASS=?
	
	The modem should respond with one of the following strings of numbers:
	
	  0
	
	  -or-
	
	  0,1
	
	  -or-
	
	  0,1,2
	
	  -or-
	
	  0,2
	
	These strings can be interpreted as follows:
	
	  0 = Data
	
	  1 = Class 1
	
	  2 = Class 2
	
	Class 1 and Class 2 are standards that define an interface with an asynchronous
	serial bidirectional data stream between the computer and the fax modem. Fax
	modems can be members of more than one fax class. For example, if the result of
	the above procedure was "0,1,2," the fax modem would belong to the Data, Class
	1, and Class 2 categories.
	
	Microsoft At Work PC Fax software can send a fax as a graphical image (facsimile
	format) or as a Microsoft Mail message in binary form (electronic mail format).
	
	The ability to send a fax in binary form allows you to send attachments, such as
	Word for Windows documents or Microsoft Excel spreadsheets, to remote locations
	without having to use communications software (such as Terminal). These
	attachments can also be edited, whereas a fax transmitted in the facsimile
	format cannot be edited.
	
	Without a Class 1 fax modem on both the sending and receiving ends of a fax
	transmission made with At Work PC Fax, faxes always transfer as graphical images
	that can be viewed and printed only.
	
	At Work PC Fax also provides advanced security features to ensure the security of
	faxes by encrypting them. An encrypted fax cannot be read by anyone except the
	intended recipient. These security features include password encryption, key
	encryption, and the ability to apply a digital signature to the fax.
	
	To use the security features provided by At Work PC Fax, both the sender and the
	recipient of the fax must be using Microsoft At Work PC Fax and Class 1 fax
	modems so that the fax can be transmitted in the electronic mail binary file
	format.
	
	Additional query words: 3.11 type E-Mail
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch kbWFW311
	Version           : WINDOWS:3.11
	
	=============================================================================
	

{% endraw %}
