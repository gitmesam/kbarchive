---
layout: page
title: "Q110661: PRB: Windows 3.1 SDK HOOKS Sample Causes a GP Fault"
permalink: /kb/110/Q110661/
---

## Q110661: PRB: Windows 3.1 SDK HOOKS Sample Causes a GP Fault

{% raw %}

	Article: Q110661
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): kb16bitonly kbHook kbSDKPlatform
	Last Modified: 09-JUN-1999
	
	3.10
	WINDOWS
	kbprg kbprb
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An application that installs a WH_CBT hook function that is run along with the
	HOOKS sample application will cause a General Protection Fault (GPF) in the
	system if the computer-based training (CBT) hook is enabled and the hook
	procedure receives a CBT notification.
	
	CAUSE
	=====
	
	In the HOOKS sample, CBTFunc() is incorrectly casting lParam (a DWORD value) to
	a WORD when it calls CallNextHookEx() to pass the info on to the next hook in
	the hook chain. This causes the receiving hook function to receive the CBT
	notification with a modified lParam (the HIWORD stripped off), thus translating
	to an invalid pointer and eventually causing a GPF.
	
	A GPF occurs similarly when an application that installs a WH_CALLWNDPROC hook is
	run along with the HOOKS sample and the CallWndProc hook menu-item is selected.
	In the same manner, the HOOKS sample function CallWndProcFunc() incorrectly
	casts its lParam (a DWORD value) to a WORD on its call to CallNextHookEx().
	
	In addition, the HOOKs sample will GPF when the WH_JOURNALRECORD hook is
	installed and some other application calls SetSysModalWindow(). As mentioned in
	the Windows 3.1 SDK help,
	
	If a WH_JOURNALRECORD hook is in place when SetSysModalWindow is called,
	the hook is called with a hook code of <B>HC_SYSMODALON</B> (for turning on the system-modal window) or <B>HC_SYSMODALOFF</B> (for turning off the system-modal window).
	
	RESOLUTION
	==========
	
	Modify both the CBTFunc() and CallWndProcFunc() calls to CallNextHookEx() to
	correctly cast lParam to a DWORD.
	
	In the case of the journal record hook, make the following change to the function
	JournalRecordFunc in hooksdll.c:
	
	     if( nCode >= 0) {
	     // do not  record if SysModalOn or SysModalOff and let other filter know
	     // about it.
	
	        if(nCode == HC_SYSMODALON || nCode == HC_SYSMODALOFF)
	        {
	        // let other hook filters know about this
	           CallNextHookEx(hhookHooks[JOURNALRECORDINDEX], nCode, wParam,
	              lParam);
	           return;
	        }
	
	STATUS
	======
	
	This behavior is by design.
	
	Additional query words: 3.10 gpf gp-fault
	
	======================================================================
	Keywords          : kb16bitonly kbHook kbSDKPlatform 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
