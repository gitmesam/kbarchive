---
layout: page
title: "Q185454: HOWTO: Shutdown an Instance of VFP with a Window Caption"
permalink: /kb/185/Q185454/
---

## Q185454: HOWTO: Shutdown an Instance of VFP with a Window Caption

{% raw %}

	Article: Q185454
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides code that demonstrates how to programmatically close an
	instance of Visual FoxPro that has the Caption property set to a specific value.
	
	MORE INFORMATION
	================
	
	1. Start one instance of Visual FoxPro.
	
	2. In the Command window, type the following command:
	
	        _screen.caption = "Test"
	
	3. Start a second instance of Visual FoxPro.
	
	4. Create a program named Shutdown that contains the following code:
	
	        * Shutdown.prg
	        * Example: DO Shutdown with "Test"
	        *          Shuts down Exe containing window caption "Test".
	        *          Not case sensitive.
	
	        PARAMETERS m.text2find
	
	        DECLARE INTEGER GetWindow IN Win32API INTEGER HWND, ;
	        INTEGER wCmd
	        DECLARE INTEGER GetWindowText IN Win32API INTEGER HWND, ;
	        STRING @lpString, INTEGER aint
	        DECLARE INTEGER GetWindowTextLength IN Win32API INTEGER HWND
	        DECLARE INTEGER SendMessage IN Win32API INTEGER HWND, ;
	        INTEGER Msg, Short WParam, INTEGER LPARAM)
	
	        #DEFINE GW_HWNDFIRST  0
	        #DEFINE GW_HWNDNEXT 2
	        #DEFINE WM_CLOSE 16
	
	        SET LIBRARY TO SYS(2004) + "foxtools.fll"
	        * Find the window handle for the current instance of Visual FoxPro.
	        m.mainhwnd = mainhwnd()
	
	        m.currwnd = GetWindow(m.mainhwnd, GW_HWNDFIRST)
	
	        DO WHILE m.currwnd # 0
	        * Determine how large a buffer to use, adding one space for the
	        * terminating Null, and
	        * get the window caption for each window on the desktop.
	           m.length = GetWindowTextLength(m.currwnd) + 1
	           m.windowtext = SPACE(m.length)
	           m.length = GetWindowText(m.currwnd, @m.windowtext, m.length)
	
	        * Uncomment this line to see the window captions it's checking.
	        * A number of the system processes have no window caption associated
	        * with them, so there will be a number of blanks.
	        * WAIT WINDOW "Checking window " + m.windowtext TIME .5
	
	        * The upper() and $ statements would also shutdown windows with the
	        * name of Test1, Test2, Mytest, and so forth.
	           IF UPPER(m.text2find) $ UPPER(m.windowtext)
	        * Uncomment these two lines
	        * to see the hWnd of the found window.
	        * WAIT WINDOW "Found window we're looking for. hWnd is: " ;
	        * + LTRIM(STR(m.currwnd)) TIME .5
	        * Send it a message to close.
	              =SendMessage (m.currwnd, WM_CLOSE, 0, 0)
	              EXIT
	           ENDIF
	        * Not found, continue with the next window on the desktop.
	           m.currwnd = GetWindow(m.currwnd, GW_HWNDNEXT)
	        ENDDO
	
	5. Execute the program with the window caption from step 2 as an argument. For
	  instance:
	
	        DO Shutdown with "Test"
	
	6. The instance of Visual FoxPro started in step 1 terminates.
	
	Additional query words: vfoxwin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP500a
	Version           : WINDOWS:5.0,5.0a
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
