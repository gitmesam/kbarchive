---
layout: page
title: "Q265208: Determining LU Pool Usage Across Servers"
permalink: /kb/265/Q265208/
---

## Q265208: Determining LU Pool Usage Across Servers

{% raw %}

	Article: Q265208
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0,4.0 SP1,4.0 SP2,4.0 SP3; :
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3 
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	SNA Server and Host Integration Server 2000 allow administrators to define 3270
	and/or LUA Pools that span LUs owned by more than one server in the subdomain.
	An LU Pool can then be assigned to one or more groups of users for host access.
	Although the administrator can determine the number of Pooled LUs that are in
	use by using the SNA Manager or Microsoft Management Console (MMC) snap-in tool
	(on a server-by-server basis), there is no automated facility for monitoring the
	aggregate number of in-use LUs across all servers that support the LU Pool.
	
	However, Host Integration Server 2000 provides a programmable interface to access
	server configuration and status information through the SNA WMI Provider. See
	the "More Information" section of this article for a WMI script that can be used
	to access LU Pool usage information.
	
	MORE INFORMATION
	================
	
	Microsoft has received customer requests to provide an automated means of
	determining the percentage of in-use Pooled LUs to make it easier to determine
	when additional 3270 or LUA LUs are needed for an LU Pool. This feature is under
	consideration for a future version of Host Integration Server 2000. In the mean
	time, Host Integration Server 2000 does provide a WMI interface to access LU
	Pool usage information. The following WMI script demonstrates how to do this for
	a specific LU Pool name on a specific SNA Server:
	
	
	  strPoolTargeted   = "LUPOOL"
	  ' this next should be the name of ONE of the SNA Servers in the subdomain
	  strDomainComputer = "SnaServer"
	
	  GrandTotalOfActiveLU = 0
	
	  Set WmiLocator = CreateObject("WbemScripting.SWbemLocator")
	  Set WmiNamespaceDomain = WmiLocator.ConnectServer(strDomainComputer,"root\MicrosoftHIS")
	
	  Set objServersInThisPool = WmiNamespaceDomain.ExecQuery("ASSOCIATORS OF {MsSna_Pool.Name='" & strPoolTargeted & "'} where ResultClass=MsSna_Server")
	
	  Set objLuInThisPool = WmiNamespaceDomain.ExecQuery("ASSOCIATORS OF {MsSna_Pool.Name='" & strPoolTargeted & "'} where ResultClass=MsSna_Lu3270")
	
	  for each xServer in objServersInThisPool 
	  	'
	  	' Look at all InSession or SSCP LUs on Remote SnaStatus namespace
	  	Set WmiNameSpaceStatusBox = WmiLocator.ConnectServer(xServer.Name,"root\MicrosoftHIS")
	  	Set objLUActives = WmiNameSpaceStatusBox.ExecQuery("Select Name from MsSnaStatus_Lu3270 where StatusText='InSession' or StatusText='SSCP'" )
	  	
	  	' Verify that the LU is in the POOL and belong to the SERVER
	  	for each xLUActive in objLUActives
	  		for each xLuInPool in objLuInThisPool
	  			if xLuInPool.Name = xLUActive.Name then
	  				GrandTotalOfActiveLU = GrandTotalOfActiveLU + 1
	  				exit for
	  			end if
	  		next
	  	next
	  next
	
	  Wscript.Echo "Total active LU "& GrandTotalOfActiveLU
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ400 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3
	Version           : WINDOWS:4.0,4.0 SP1,4.0 SP2,4.0 SP3; :
	
	=============================================================================
	

{% endraw %}
