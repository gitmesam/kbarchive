---
layout: page
title: "Q105964: PC MAPI: Simple MAPI Common Technical Questions and Answers"
permalink: /kb/105/Q105964/
---

## Q105964: PC MAPI: Simple MAPI Common Technical Questions and Answers

{% raw %}

	Article: Q105964
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 28-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for Windows, version 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Below is a list of common technical questions and answers about Messaging
	Application Programming Interface (MAPI), from versions 3.0. 3.0b and 3.2 of
	Microsoft Mail for PC Networks.
	
	1. Q. Is it possible to send mail without presenting any type of dialog box to
	  users or at least minimizing necessary user input?
	
	  A. Yes, mail messages can be sent without providing any user interface if
	  necessary, or you can limit what is displayed. For example, you can create an
	  application that will always CC: another recipient when sending mail or
	  always send an attachment when sending mail.
	
	2. Q. How do I read messages with a MAPI application?
	
	  A. Use MAPIFindNext to get the appropriate message, then use MAPIReadMail to
	  pull up the message information.
	
	3. Q. How can I get details about a user?
	
	  A. To get address details, call MAPIResolveName on a valid user, then read the
	  MAPI Recipient structure to pull out the user's addressing information. You
	  can also call MAPIAddress to view the information. There is no call to pull
	  and display a block of information for many recipients.
	
	4. Q. Can template information on a user be pulled out as well?
	
	  A. MAPIDetails allows you to view the template information but template
	  information cannot be pulled from MAPIRecip.
	
	5. Q. Can multiple MAPI sessions with multiple users be run on one workstation?
	
	  A. No. As with mail, it cannot.
	
	6. Q. Can MAPI access folders other than the inbox, For instance, can it move or
	  copy messages from one folder to another?
	
	  A. No, this is not possible with Simple MAPI.
	
	7. Q. What is the most common reason for MAPISendMail failing?
	
	  A. An incorrectly defined MAPI Recipient, MAPI Message or MAPI File structure.
	  If any field is incorrectly defined, you receive the generic error
	  MAPI_E_FAILURE or a general protection fault.
	
	8. Q. What are the common reasons for failure when sending attachments?
	
	  A. There are three probable causes:
	
	  a. If there is more than one attachment, having more than one at a given
	     position will cause a failure.
	
	  b. An attachment that does not reside within the text of a message will cause
	     a failure.
	
	  c. An incorrectly defined MAPI file structure will cause a failure.
	
	9. Q. Why do I get an ambiguous recipient error when using MAPIResolveName or
	  MAPISendMail?
	
	  A. The ambiguous recipient error means that a user name contains characters
	  that can match more than one default address book recipient. If you use
	  MAPIResolveName to resolve a name producing an ambiguous error, you should
	  then use the MAPI_DIALOG flag or call MAPIAddress to resolve it, then use
	  MAPISendMail. Calling MAPIResolvename again will produce the same error.
	
	10. Q. Why do I get the error "Another application has denied your request" when
	  I Exit and Sign Out of Mail and have another MAPI application running?
	
	  A. Exit and Sign Out does not work when Simple MAPI applications are running.
	  Mail is "requesting" that the application log out everyone and it cannot, so
	  it fails.
	
	11. Q. What are Interprocess Communication (IPC) message types used for?
	
	  IPC messages can be used to send mail to recipients that act upon a specific
	  mail message type. These messages cannot be seen within Microsoft Mail.
	
	12. Q. Can I one-off address with MAPI applications?
	
	  A. Yes. Set the Address field in the MAPI Recipient structure to
	  MS:network/postoffice/mailbox or the Name field to
	  [MS:network/postoffice/mailbox].
	
	13. Q. How can I download messages automatically for my "new mail" routine like
	  Microsoft Mail?
	
	  A. You can force the download of messages only when using MAPILogon and the
	  MAPI_FORCE_DOWNLOAD flag. To check for mail you could keep track of unread
	  messages when reading messages and maybe include a timer routine to check
	  for messages. There are two ways to poll Mail:
	
	   - Use Mail for Windows: Select Mail, Options, and enter a time
	
	  -or-
	
	   - set PumpCycleInterval=# of seconds in the MSMAIL.INI file
	
	Additional query words: 3.00 3.00b 3.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMail320
	Version           : WINDOWS:3.2
	
	=============================================================================
	

{% endraw %}
