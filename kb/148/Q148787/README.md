---
layout: page
title: "Q148787: FIX: Run Out of Memory or Assertion in GetBufferSetLength()"
permalink: /kb/148/Q148787/
---

## Q148787: FIX: Run Out of Memory or Assertion in GetBufferSetLength()

{% raw %}

	Article: Q148787
	Product(s): Microsoft C Compiler
	Version(s): 4.00 4.10
	Operating System(s): 
	Keyword(s): kbcode kbDatabase kbMFC kbODBC kbVC kbVC400bug kbVC410bug kbVC420fix
	Last Modified: 03-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), included with:
	   - Microsoft Visual C++, 32-bit Editions, versions 4.0, 4.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An error can occur when mapping a CString to a SQL_LONGVARCHAR, SQL_VARCHAR, or
	other SQL data type fields if a driver returns a large precision value from
	SQLDescribeCol() for the column.
	
	A bug in the MFC ODBC Database classes results in MFC trying to allocate a large
	chunk of memory to store data that might have this large precision.
	
	In some cases, such as using a memo field with the FoxPro Desktop ODBC driver, a
	memory allocation of 1 gigabyte may be attempted. Or, as is the case with the
	Visual FoxPro driver, the MFC Database Classes will try to allocate a negative
	number of bytes because the return value of the driver is 2 gigabytes and then
	MFC adds 1 which causes the signed variable to wrap into a negative value. In
	this case, an assertion occurs in GetBufferSetLength() on line 447 of
	Strcore.cpp:
	
	      ASSERT(nNewLength >= 0);
	
	SQL Server text fields produce the same result.
	
	The problem occurs only when mapping CString variables to variable length fields
	using the RFX_Text() function.
	
	CAUSE
	=====
	
	The fourth argument of the RFX_Text() function takes a value for the
	user-defined maximum length of the CString. The MFC ODBC database classes fail
	to constrain the CString buffer to this maximum length.
	
	The following code exists at line 527 of Dbrfx.cpp:
	
	     // Determine string pre-allocation size
	     if (cbColumn < (UINT)nMaxLength)
	        cbColumn = nMaxLength;
	
	It should be:
	
	     if (cbColumn > (UINT)nMaxLength)
	        cbColumn = nMaxLength;
	
	RESOLUTION
	==========
	
	Do one of the following:
	
	- Don't bind to a CString. For example, use a CLongBinary object.
	
	-or-
	
	- Write your own RFX_Text() function that corrects the problem with the
	  existing RFX_Text(). To do this, copy the contents of the RFX_Text() function
	  from Msdev\Mfc\Src\Dbrfx.cpp, change the name, and modify the code from
	  this:
	
	        if (cbColumn < (UINT)nMaxLength)
	            cbColumn = nMaxLength;
	
	  to this:
	
	        if (cbColumn > (UINT)nMaxLength)
	           cbColumn = nMaxLength;
	
	You'll need to replace the RFX_Text() function call in your CRecordset's
	DoFieldExchange() function with a call to your new function. You'll want to copy
	the RFX_Text() function prototype from Afxdb.h as well so that you are sure to
	use the correct default parameters.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in Visual C++ 32- bit Edition
	version 4.2.
	
	It is also fixed in the Visual C++ 4.1a patch. For information on this patch, see
	the following Microsoft Knowledge Base article:
	
	  Q150937 Visual C++ Version 4.1 Patch
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbDatabase kbMFC kbODBC kbVC kbVC400bug kbVC410bug kbVC420fix 
	Technology        : kbAudDeveloper kbMFC
	Version           : 4.00 4.10
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
