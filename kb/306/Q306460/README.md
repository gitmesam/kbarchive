---
layout: page
title: "Q306460: Hfnetchk.exe Returns NOTE Messages for Installed Patches"
permalink: kb/306/Q306460/
---

## Q306460: Hfnetchk.exe Returns NOTE Messages for Installed Patches

	Article: Q306460
	Product(s): Microsoft Windows NT
	Version(s): 2000,2000 SP1,2000 SP2,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5,4.0 SP6a
	Operating System(s): 
	Keyword(s): kbenv kbtool
	Last Modified: 24-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 2000, 2000 SP1, 2000 SP2 Advanced Server 
	- Microsoft Windows versions 2000, 2000 SP1, 2000 SP2 Professional 
	- Microsoft Windows versions 2000, 2000 SP1, 2000 SP2 Server 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0, 4.0 SP4, 4.0 SP5, 4.0 SP6a 
	- Microsoft Windows NT Workstation versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5, 4.0 SP6a 
	- Microsoft Windows NT Server versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5, 4.0 SP6a 
	- Microsoft Internet Information Server 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Microsoft Network Security Hotfix Checker (Hfnetchk.exe) tool determines a
	computer's patch status by evaluating the presence of specific registry keys,
	file versions, and file checksums that are associated with a given hotfix. There
	are some instances where Hfnetchk.exe is not able to determine the patch
	installation status because the detailed file and registry key information is
	not available for the specified security bulletin or patch. A NOTE message that
	is similar to the following NOTE message is generated in instances where the XML
	data file does not contain this information:
	
	  NOTE MS01-022 Q296441
	  Please read KB article 306460
	
	MORE INFORMATION
	================
	
	NOTE messages do not indicate that the computer that is being scanned is
	insecure, they indicate that Hfnetchk.exe is technically not able to determine
	if the appropriate patch or workaround has been applied. Remediation of these
	issues usually involves a configuration change or workaround rather than a
	patch. You may ignore NOTE messages once you have applied the patch or evaluated
	your system and made any needed configuration changes. NOTE messages are
	returned for the following security bulletins:
	
	Windows 2000 and Windows NT 4.0 Computers
	-----------------------------------------
	
	MS01-022 (Q296441): This patch updates the Msdaipp.dll file to version
	8.103.4004. In a typical patch situation, the Mssecure.xml file would contain
	this file name, file version and checksum. If the system that is being scanned
	contained this file, but didn't match the exact file version and checksum, the
	patch would be considered to be not found. However, with respect to this
	particular patch, these details cannot be stored in the XML file without
	generating false positives during the scan. Specifically, several Microsoft
	Office programs include non-vulnerable versions of this file that are versioned
	greater than 8.103.4004. Hfnetchk.exe would interpret this higher version number
	as a fileversion and checksum mismatch and would report a WARNING message that
	states that the fileversion was greater than expected. To reduce the number of
	false positive WARNING messages that are generated by this tool, the file
	details were not entered into the XML database. To verify that you are not
	vulnerable to this issue, you should verify that you are running a version of
	this file that is 8.103.4004 or greater. If this is the case, you may ignore
	this NOTE message.
	
	Windows NT 4.0 Computers
	------------------------
	
	MS98-001 (Q169556): This security bulletin describes a tool you can run to
	provide increased security over Windows NT 4.0 local groups. The use of this
	tool does not modify any files on the computer, and it does not create any
	registry keys. Because of this, Hfnetchk.exe is not able to determine if this
	tool has been run. You are encouraged to read the security bulletin to determine
	if you should run this tool. After you make this determination and take the
	appropriate actions, you may disregard this NOTE.
	
	MS99-036 (Q155197): This security bulletin describes a potential vulnerability on
	Windows NT 4.0 computers that were installed by using unattended installation
	mechanisms. Specifically, sensitive information may have been written to one of
	two files (%windir%\system32\$nt4pre$.inf or %windir%\system32\$winnt$.inf).
	There is no patch for this issue and nothing that Hfnetchk.exe can validate
	during its checks. Instead, you are encouraged to review these files (if they
	exist) and delete any references to sensitive information (such as user names
	and passwords). If neither of these files exist, or they do not contain
	sensitive information, you may ignore this NOTE.
	
	MS99-041 (Q242294): This security bulletin describes a vulnerability in the
	RASMAN service on Windows NT 4.0 computers. A patch was not issued for this
	bulletin, instead, a tool was released. This tool modifies a security descriptor
	for the RASMAN service, but does not modify any system files or create any
	registry keys. Hfnetchk.exe does not examine security descriptors that are
	related to services and is not able to determine if the tool has been run. You
	are encouraged to review the security bulletin and run the tool as appropriate.
	You may ignore this NOTE message once you have executed the tool or determined
	that this is not necessary for your system.
	
	IIS 4.0 Computers
	-----------------
	
	MS99-025 (Q184375): This security bulletin describes a vulnerability in the MDAC
	components on an IIS 4.0 Web server. As the bulletin states, the solution to
	this issue involved a configuration change rather than a specific patch. Several
	different workarounds are available for this vulnerability. As this is not
	rectified by a standard patch, Hfnetchk.exe is not able to determine if this
	vulnerability has been addressed, or if the suggested workarounds have been
	applied. You are urged to read the security bulletin and follow the suggestions
	in it. Once you have taken the appropriate measures on this computer, you may
	disregard this NOTE.
	
	MS00-025 (Q259799): This security bulletin describes a vulnerability in the
	Dvwssr.dll file. A patch was not issued to correct this issue, however, the
	bulletin describes a workaround you can follow to correct this issue.
	Specifically, the bulletin suggests that you delete this file if it is not
	needed on your computer. You are encouraged to read the security bulletin for
	more information about this issue and take the necessary steps to resolve the
	issue. Once you review the bulletin and take the appropriate steps, you may
	ignore this NOTE.
	
	MS00-028 (Q260267): This security bulletin is similar to the preceding MS99-025
	security bulletin. Once you have followed the actions for either MS00-028 or
	MS99-025, you may disregard this NOTE message.
	
	Internet Explorer and SQL Server Computers
	------------------------------------------
	
	NOTE messages may appear for specific Internet Explorer or SQL bulletins. The
	file and registry key details for some of these bulletins have not yet been
	entered into the XML file. These details will be populated in future versions of
	the XML file. Missing data for Internet Explorer bulletins relate primarily to
	Internet Explorer 4.x and Internet Explorer 5.0 patches. Internet Explorer 5.01
	and Internet Explorer 5.5 patches should contain full patch details.
	
	How to Suppress NOTE Messages
	-----------------------------
	
	Once you have reviewed each of the security bulletins that are associated with
	NOTE messages and have taken the appropriate steps to rectify the issues, you
	may choose to suppress NOTE messages from Hfnetchk.exe output. To suppress these
	messages, use the "-S 1" (without the quotation marks) switch as with the
	"hfnetchk -v -s 1" (without the quotation marks) command.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbtool 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000Serv kbWinNTW400sp5 kbWinNTW400sp4 kbWinNTW400sp3 kbWinNTW400sp2 kbWinNTW400sp1 kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp5 kbWinNTSEnt400sp4 kbWinNTSEnt400 kbWinNTS400sp6 kbWinNTS400sp5 kbWinNTS400sp4 kbWinNTS400sp3 kbWinNTS400sp2 kbWinNTS400sp1 kbWinNTS400search kbWinNTS400 kbwin2000ServSearch kbwin2000Search kbwin2000ProSearch kbwin2000Pro kbiisSearch kbiis400 kbWinAdvServSearch kbWin2000AdvServSP2 kbWin2000AdvServSP1 kbWin2000ProSP2 kbWin2000ProSP1 kbwin2000ServSP1 kbwin2000ServSP2 kbWinNTSEnt400SP6a kbWinNTW400SP6a
	Version           : :2000,2000 SP1,2000 SP2,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5,4.0 SP6a
	Issue type        : kbinfo
	
	=============================================================================
	