---
layout: page
title: "Q315456: FP: Error: Unable to Open Jet Temporary Key Connecting to DB"
permalink: /kb/315/Q315456/
---

## Q315456: FP: Error: Unable to Open Jet Temporary Key Connecting to DB

{% raw %}

	Article: Q315456
	Product(s): Word Front Page
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 14-JAN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 2002 
	- Microsoft FrontPage 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to browse to an Active Server Page (ASP) database results page
	created with Microsoft FrontPage, you may receive an error message similar to
	one of the following:
	
	  Database Results Error
	  [Microsoft][ODBC Microsoft Access Driver]
	  General error
	  Unable to open registry key 'Temporary (volatile) Jet DSN for process 0x3f8
	  Thread 0x764 DBC 0x2150064 Jet'.
	
	  -or-
	
	  Database Results Error
	  [Microsoft][ODBC Microsoft Access Driver]
	  The Microsoft Jet database engine cannot open the file '(unknown)'. It is
	  already opened exclusively by another user, or you need permission to view
	  its data.
	
	
	CAUSE
	=====
	
	This behavior can occur if incorrect NTFS permissions are defined for your
	system %TEMP% folder.
	
	RESOLUTION
	==========
	
	To resolve this problem, correct the permissions to the folder specified in your
	system's %TEMP% variable.
	
	NOTE: The Microsoft Jet database engine uses the System %TEMP% environment
	variable to specify the location to place temporary files that are created
	during Jet operations. On Microsoft Windows NT 4.0 these environment variables
	are defined for users and are not system-wide settings by default. For more
	information, please see the "More Information" section later in this article.
	
	To correct the permissions of your systems %TEMP% variable, follow these steps:
	
	1. Locate your system's TEMP folder:
	
	  a. Follow the appropriate steps for your version of Windows:
	
	      - For Windows XP: On the Start menu, click Control Panel, click the
	        Performance and Maintenance icon, click the System icon, click the
	        Advanced tab, and then click the Environment Variables button.
	
	      - For Windows 2000: right-click My Computer on your desktop, click
	        Properties on the menu that appears, click the Advanced tab, and then
	        click the Environment Variables button.
	
	      - For Windows NT: right-click My Computer on your desktop, click
	        Properties on the menu that appears, and then click the Environment
	        tab.
	
	  b. Find the %TEMP% variable in the list of System variables and take note of
	     the folder that your system is using.
	
	2. Start Windows Explorer.
	
	3. In Folders view, expand the path to your temporary folder.
	
	4. Right-click the folder and click Properties on the shortcut menu.
	
	5. On the Security tab, add Everyone to the existing permissions, assign it
	  Change permissions, and apply these new settings to all files and subfolders.
	
	6. Click OK.
	
	MORE INFORMATION
	================
	
	Windows NT 4.0 and TEMP Folders:
	
	To set up a system variable on a Windows NT 4.0 computer, follow these steps:
	
	1. Right-click My Computer, and then click Properties on the shortcut menu.
	
	2. Click the Environment tab.
	
	3. Inspect the list to see whether the %TEMP% variable is present and correctly
	  identified. If not, skip to step 4.
	
	4. Select an entry in the System Variables List box, and then click New.
	
	5. In the Variable box, type "TEMP" (without the quotation marks), and in the
	  Variable Value box, type a valid path for your Windows Temp directory. (For
	  example, type "C:\Temp" (without the quotation marks).)
	
	6. Click OK to save the new variable.
	
	7. Reboot your computer to apply the change.
	
	REFERENCES
	==========
	
	For additional information about troubleshooting ASP and Internet Information
	Service errors when working with the database connectivity features of
	FrontPage, click the article numbers below to view the articles in the Microsoft
	Knowledge Base:
	
	  Q265161 FP: Errors Appear When You Attempt to Connect to Database Results
	  Page
	
	  Q219170 FP2000: Error Browsing Database Results Pages After Publishing from
	  Disk-Based Web
	
	
	For additional information about troubleshooting IIS permissions, click the
	article numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q185874 How to Troubleshoot Permissions in Internet Information Server 4.0
	
	  Q309051 HOW TO: Troubleshoot ASP in IIS 5.0
	
	
	
	Additional query words: front page
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbFrontPageSearch kbFrontPage2002 kbFrontPage2000Search kbFrontPage2002Search kbZNotKeyword5
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
