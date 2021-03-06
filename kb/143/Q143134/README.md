---
layout: page
title: "Q143134: OEMSETUP.INF Modifications for Automated Windows NT Setup"
permalink: /kb/143/Q143134/
---

## Q143134: OEMSETUP.INF Modifications for Automated Windows NT Setup

{% raw %}

	Article: Q143134
	Product(s): Microsoft Windows NT
	Version(s): 3.5,3.51
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 20-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	- MSPRESS Microsoft Windows NT Resource Kit, versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If you install an Original Equipment Manufacturer (OEM) network adapter in an
	unattended setup or a Computer Profile Setup (CPS) of Windows NT, the following
	error message appears:
	
	  A network card of this type is already installed in the system. Do you want
	  to continue?"
	
	If you click OK, you may make changes or accept the network adapter
	configuration. If you click Continue, the following error message appears:
	
	  The dependency service or group failed to start. This error prevented the
	  network from starting.
	
	If you click OK, the following error message appears:
	
	  The network software failed to start successfully. Choose YES to return to
	  the Network dialog to reconfigure the software. If you choose NO to continue
	  with the installation you will be unable to join a domain at the present
	  time.
	
	CAUSE
	=====
	
	The OEMSETUP.INF file for many OEM network adapters do not support unattended
	setup or CPS.
	
	WORKAROUND
	==========
	
	A few tips for customizing OEMSETUP.INF files are included below. For more
	information, refer to the Programmer's Guide included in the Windows NT DDK,
	contact Microsoft Consulting Services or contact a Solution Provider.
	
	The Enterprise Customer Unit does not support the modification of OEMSETUP.INF
	files.
	
	WARNING: Modification of Setup files can cause serious, system-wide problems
	before and after Setup and may require you to reinstall Windows NT to correct
	them. Microsoft cannot guarantee that any problems resulting from the
	modification of the Setup files can be solved. Make Setup file modifications at
	your own risk.
	
	To prevent user interaction during Setup, either skip the code fragments using
	the GOTO function or comment out code fragments by adding a semicolon (;) to the
	beginning of a line.
	
	You can skip code using the GOTO function. Many Network INF files in Windows NT
	are designed by using this method. This can be considered a solution suitable
	for CPS or Unattended Setup, as well as manual or interactive Setup. Make sure
	you understand the implications of skipping code - results in the symptoms
	mentioned above.
	
	Example
	-------
	
	     installadapter = +
	     Debug-Output "At installadapter"
	     ;
	     ;  First, check whether the same version of the software exists
	     ;
	     ;; As a workaround for CPS and Unattended Setup, the below lines have
	     ;  been added:
	     ifstr(i) $(!STF_GUI_UNATTENDED) == "YES"
	       goto skipoptions
	     endif
	
	  NOTE: In many cases, the skipoptions section may be called nextstep.
	  Look at your OEMSETUP.INF file to verify the appropriate section name.
	
	Commenting Out Code:
	
	Commenting out code fragments should only be considered a workaround for CPS and
	Unattended Setup. Subsequent manual installation or configuration of the Network
	adapter software may result in symptoms mentioned above. Make sure you
	understand the implications of commenting out code. When possible, skip code
	using the method described above.
	
	Example 1
	---------
	
	     installadapter = +
	     Debug-Output "At installadapter"
	     ;
	     ;  First, check whether the same version of the software exists
	     ;
	     ;; As a workaround for CPS and Unattended Setup, the below lines are
	     ;  commented out by prepending a semicolon.
	     ;    OpenRegKey $(!REG_H_LOCAL) "" $(ProductKeyName) $(MAXIMUM_ALLOWED)
	     KeyProduct
	     ;    Ifstr $(KeyProduct) != $(KeyNull)
	     ;
	     ; Same version already existed in the local machine
	     ; Popup the dialog and ask the user whether he wants to continue
	     ;
	     ;   CloseRegKey $(KeyProduct)
	     ; ifstr(i) !(NTN_RegBase) == $(ProductKeyName)
	     ;
	     ; Cannot Install the same software again
	     ;
	     ;   Shell $(UtilityInf), VerExistedDlg, $(ProductSoftwareTitle),+
	     ;   $(ProductVersion)
	     ;   ifint $($ShellCode) != $(!SHELL_CODE_OK)
	     ;     Debug-Output "ShellCode error: cannot get an error string."
	     ;     goto ShellCodeError
	     ;   endif
	     ;   goto end
	     ; else
	     ;
	     ; Add a new adapter card?
	     ;
	     ;   Shell $(UtilityInf), CardExistedDlg
	     ;   ifint $($ShellCode) != $(!SHELL_CODE_OK)
	     ;     Debug-Output "ShellCode error: cannot get an error string."
	     ;     goto ShellCodeError
	     ;   endif
	     ;     ifstr(i) $($R1) != "OK"
	     ;       goto end
	     ;     endif
	     ;     set OldVersionExisted = $(TRUE)
	     ;   endif
	     ; endif
	
	Example 2
	---------
	
	     ;===================================================
	     ;  Netcard Detection logic
	     ;
	     ;   Check that this card's parameters can be
	     ;   fully detected.
	     ;
	     ;; As a workaround for CPS and Unattended Setup, the below line is
	     ;  commented out by prepending a semicolon.
	     ; Shell $(ParamInf) Param_ParameterConfidence
	       Ifstr(i) $($R0) != STATUS_SUCCESSFUL
	       Debug-Output "OEMNADIN.INF: parameter confidence too low to bypass
	       configuration"
	
	Example 3
	---------
	
	     ;; As a workaround for CPS and Unattended Setup, the below lines are
	     ;  commented out by prepending a semicolon.
	     ;===================================================
	     ;Display configuration dialog if confidence is too low. This is to
	     ;provide
	     ;the user the opportunity to verify or modify the settings manually.
	     ;
	     ; ui start "InputDlg"
	     ;    ifstr(i) $(DLGEVENT) == "CONTINUE"
	     ;     Set IRQValue = $(Combo1Out)
	     ;        Set IOAddrValue = $(Combo2Out)
	     ;   Set IOReadyValue = ~($(IOReadyListExt),$(Combo3Out))
	     ;        Set IOReadyValue = ~($(IOReadyList),$(Combo3Out))
	     ;   Set TransceiverValue = ~($(TransceiverList),$(Combo4Out))
	     ;   ui pop 1
	     ;    else-ifstr(i) $(DLGEVENT) == "BACK"
	     ;   set CommonStatus = STATUS_USERCANCEL
	     ;   Debug-Output "Action: exit. Bye."
	     ;   ui pop 1
	     ;   goto end
	     ;    else
	     ;   Debug-Output "Action: unknown. Bye."
	     ;   ui pop 1
	     ;   goto end
	     ;    endif
	
	Example 4
	---------
	
	     ;   Verify parameter values selected. Give the user a chance to retry
	     ;   or force the options given.
	     ;
	     Set from = adapteroptions
	     Set to = skipoptions
	     ;; As a workaround for CPS and Unattended Setup, the below lines are
	     ;  commented out by prepending a semicolon.
	     ;  Shell $(UtilityInf),RegistryErrorString,VERIFY_WARNING
	     ;  ifint $($ShellCode) != $(!SHELL_CODE_OK)
	     ;    Debug-Output "ShellCode error: cannot get an error string."
	     ;    goto ShellCodeError
	     ;  endif
	     ;  set Error = $($R0)
	     ;  Goto Warning
	
	To retrieve adapter parameters from an answer file, you must modify the
	OEMSETUP.INF file. The Unattended Setup answer file is called UNATTEND.TXT. The
	CPS answer file is located in %SystemRoot%\SYSTEM32\DEFAULTS.INF on the
	distribution share.
	
	Example
	-------
	
	     writeparameters = +
	     Debug-Output "At writeparameters"
	     ;
	     ;   Add the rest of the parameters to the Services area
	     ;
	     Ifstr(i) $(MachineType) == "MCA"
	        set NewValueList =
	
	     {{BusType,$(NoTitle),$(!REG_VT_DWORD),$(BusTypeNum)},+
	        {McaPosId,$(NoTitle),$(!REG_VT_DWORD),$(NETCARD_ID)},+
	        {SlotNumber,$(NoTitle),$(!REG_VT_DWORD),$(SlotNum)},+
	        {MediaType,$(NoTitle),$(!REG_VT_DWORD),1}}
	
	     else
	
	        Set IOAddrValue = *($(IOAddrValues),
	        ~($(IOAddrList),$(IOAddrValue)))
	
	        Shell "" DebugConfiguration "Before Writing Parameters"
	        set NewValueList =
	
	     {{INTERRUPT,$(NoTitle),$(!REG_VT_DWORD),$(IRQValue)},+
	
	        {BusType,$(NoTitle),$(!REG_VT_DWORD),$(BusInterfaceType)},+
	        {BusNumber,$(NoTitle),$(!REG_VT_DWORD),$(BusNumber)},+
	        {MediaType,$(NoTitle),$(!REG_VT_DWORD),1},+
	        {IoChannelReady,$(NoTitle),$(!REG_VT_DWORD),$(IOReadyValue)},+
	        {Transceiver,$(NoTitle),$(!REG_VT_DWORD),$(TransceiverValue)},+
	        {IOADDRESS,$(NoTitle),$(!REG_VT_DWORD),$(IOAddrValue)}}
	
	     endif
	
	     Shell  $(UtilityInf), AddValueList, $(KeyParameters), $(NewValueList)
	     ;;  Following lines added for CPS or Unattended Setup
	     ifstr(i) $(!STF_GUI_UNATTENDED) == "YES"
	
	       Shell $(UtilityInf),AddDefaultNetCardParameters,$(KeyParameters)
	
	     endif
	
	
	
	Additional query words: automate
	
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbMSPressSearch kbWinNTS351search kbWinNTS350search kbZNotKeyword6 kbZNotKeyword2 kbZNotKeyword5
	Version           : :3.5,3.51
	
	=============================================================================
	

{% endraw %}
