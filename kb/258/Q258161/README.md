---
layout: page
title: "Q258161: HOWTO: Read a DWORD From the Registry"
permalink: /kb/258/Q258161/
---

## Q258161: HOWTO: Read a DWORD From the Registry

{% raw %}

	Article: Q258161
	Product(s): Microsoft FoxPro
	Version(s): 3.0,3.0b,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbAPI kbRegistry kbvfp300 kbvfp300b kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport k
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Sometimes it is necessary to obtain information from the registry. This article
	shows how to read REG_DWORD values from an existing value in the registry.
	
	An example of this is:
	
	HKEY_CURRENT_USER  
	  \Software
	     \Microsoft
	         \Windows 
	             \CurrentVersion
	                 \Applets
	                     \Paint
	                         \Colors
	                             \NumberOfColors
	
	MORE INFORMATION
	================
	
	1. From Visual FoxPro, create a program file (.prg) with the following code:
	
	  #DEFINE HKEY_CLASSES_ROOT           -2147483648
	  #DEFINE HKEY_CURRENT_USER           -2147483647
	  #DEFINE HKEY_LOCAL_MACHINE          -2147483646
	  #DEFINE HKEY_USERS                  -2147483645
	
	  LOCAL nKey, cSubKey, cValue, nValueRead, lSuccess
	  nKey = HKEY_CURRENT_USER
	  cSubKey = "Software\Microsoft\Windows\CurrentVersion\Applets\Paint\Colors"
	  cValue = "NumberOfColors"
	
	  lSuccess = ReadRegDWORD(nKey, cSubKey, cValue, @nValueRead)
	
	  IF (lSuccess) THEN
	     =MESSAGEBOX("Function Successful. Value is: " + ALLTRIM(STR(nValueRead)))
	  ELSE
	     =MESSAGEBOX("Function Not Successful. Value is: " + ALLTRIM(STR(nValueRead)))
	  ENDIF
	
	  FUNCTION ReadRegDWORD
	  * This function reads a REG_DWORD from the registry. It will return .T.
	  * if successful and store the value in nValueRead. If not successful, it
	  * will return .F. and nValueRead will contain -1.
	     PARAMETERS  nKey, cSubKey, cValue,  nValueRead
	     * nKey The root key to open. It can be any of the constants defined below.
	     *#DEFINE HKEY_CLASSES_ROOT           -2147483648
	     *#DEFINE HKEY_CURRENT_USER           -2147483647
	     *#DEFINE HKEY_LOCAL_MACHINE          -2147483646
	     *#DEFINE HKEY_USERS                  -2147483645
	     *cSubKey The SubKey to open.
	     *cValue The value that is going to be read.
	     *nValueRead What was read from the registry
	
	     * Constants that are needed for Registry functions
	     #DEFINE REG_DWORD  4  && A 32-bit number.
	
	     * WIN 32 API functions that are used
	     DECLARE Integer RegOpenKey IN Win32API ;
	        Integer nHKey, String @cSubKey, Integer @nResult
	     DECLARE Integer RegQueryValueEx IN Win32API ;
	        Integer nHKey, String lpszValueName, Integer dwReserved,;
	        Integer @lpdwType, String @lpbData, Integer @lpcbData
	     DECLARE Integer RegCloseKey IN Win32API Integer nHKey
	
	     * Local variables used
	     LOCAL nErrCode          && Error Code returned from Registry functions
	     LOCAL nKeyHandle        && Handle to Key that is opened in the Registry
	     LOCAL lpdwValueType     && Type of Value that we are looking for.
	     LOCAL lpbValue          && The data stored in the value
	     LOCAL lpcbValueSize     && Size of the variable
	     LOCAL lpdwReserved      && Reserved Must be 0
	
	     * Initialize the variables
	     nKeyHandle = 0
	     lpdwReserved = 0           
	     lpdwValueType = REG_DWORD
	     lpcbValueSize = 4          && DWORD is 4 bytes
	     nValueRead = -1
	     lpbValue = SPACE(4)
	
	     nErrCode = RegOpenKey(nKey, cSubKey, @nKeyHandle)
	     * If the error code isn't 0, then the key doesn't exist or can't be opened.
	     IF (nErrCode # 0) THEN
	        RETURN .F.
	     ENDIF
	
	     nErrCode=RegQueryValueEx(nKeyHandle, cValue, lpdwReserved, @lpdwValueType, @lpbValue, @lpcbValueSize)
	     =RegCloseKey(nKeyHandle)
	     IF (nErrCode # 0) THEN
	        RETURN .F.
	     ENDIF
	
	     nValueRead = StrToLong(lpbValue)
	  RETURN .T.
	
	  FUNCTION StrToLong
	     * This function converts a String to a Long
	        PARAMETERS cLongStr
	        LOCAL nLoopVar, nRetval
	
	        nRetval = 0
	        FOR nLoopVar = 0 TO 24 STEP 8
	           nRetval = nRetval + (ASC(cLongStr) * (2^nLoopVar))
	           cLongStr = RIGHT(cLongStr, LEN(cLongStr) - 1)
	        NEXT
	  RETURN nRetVal
	  * End of Code
	
	2. Run the code created in step 1. A message box appears telling if the function
	  was successful and what the value is.
	
	3. You can replace nKey, cSubKey, and cValue with your information to be read
	  from the registry.
	
	(c) Microsoft Corporation 2000, All Rights Reserved. Contributions by Mark
	Barnard, Microsoft Corporation.
	
	
	REFERENCES
	==========
	
	For additional information obtaining values from the registry, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q244675 HOWTO: Use Windows Script Host to Read, Write, Delete Registry
	
	Additional query words:
	
	======================================================================
	Keywords          : kbAPI kbRegistry kbvfp300 kbvfp300b kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport kbCodeSnippet 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : :3.0,3.0b,5.0,5.0a,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
