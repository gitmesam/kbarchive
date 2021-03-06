---
layout: page
title: "Q234822: MOD2000:Undo Check Out Doesn't Update the VSS SCC Status Window"
permalink: /kb/234/Q234822/
---

## Q234822: MOD2000:Undo Check Out Doesn't Update the VSS SCC Status Window

{% raw %}

	Article: Q234822
	Product(s): Microsoft SourceSafe
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdta modSSafe
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Office 2000 Developer 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you click Undo Check Out to cancel a check out operation to abandon changes
	to a module, the SCC Status window is not updated to show that that module is no
	longer checked out.
	
	RESOLUTION
	==========
	
	On the Add-ins menu, point to VBA Source Code Control, and then click Refresh
	File Status to update the SCC Status window.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create and save a new workbook in Excel.
	
	2. Press ALT+F11 to open the Visual Basic Editor.
	
	3. On the Insert menu, click Module.
	
	4. Use the Add-in Manager to load the VBA Source Code Control add-in if it is
	  not already loaded.
	
	5. On the File menu, click Save <projectname>.
	
	6. On the Add-ins menu, point to VBA Source Code Control, and then click Add
	  Project to SourceSafe.
	
	7. On the Add-ins menu, point to VBA Source Code Control, and then click Check
	  Out. Check out the module that you created in step 3.
	
	8. On the Add-ins menu, point to VBA Source Code Control, and then click Undo
	  Check Out. Notice that the SCC Status window still reports that the module is
	  checked out.
	
	Additional query words: pra OFF2000
	
	======================================================================
	Keywords          : kbdta modSSafe 
	Technology        : kbOfficeSearch kbAudDeveloper kbOffice2000Search kbOffice2000 kbOffice2000DevSearch
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
