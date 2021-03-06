---
layout: page
title: "Q169637: XCON: Demand-dial Connectors using Routing and RAS"
permalink: /kb/169/Q169637/
---

## Q169637: XCON: Demand-dial Connectors using Routing and RAS

{% raw %}

	Article: Q169637
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbnetwork kbsetup kbusage exc4 exc5 exc55
	Last Modified: 12-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 4.0, 5.0 
	- Microsoft Routing and Remote Access Service Update for Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft Routing and Remote Access Service (RAS) provides normal RAS
	functionality as well as demand-dial network connectivity. Thus, Routing and
	Remote Access can be used to dynamically connect Microsoft Exchange Server
	computers via RAS, X.400 Connector, or Site Connector using the demand-dial
	feature of Routing and Remote Access. The demand-dial X.400 connector may
	increase cost of the connection and requires minor modifications to the default
	connector override settings. Because there is no scheduling ability with the
	site connector, it will hold the connection open as long as possible.
	
	Configuring Routing and Remote Access for demand-dial is covered in detail in
	Chapter 4 of the "Routing and Remote Access Administrator's Guide" included with
	the download package. Use the helpful hints listed below with the information in
	the administrator's guide to configure demand-dial for your Microsoft Exchange
	Server.
	
	MORE INFORMATION
	================
	
	Any default gateway defined in the TCP/IP configuration on the Routing and
	Remote Access server should be removed. This server is now a router and all
	routes must be manually defined or configured to use RIP of OSPF for dynamic
	updates. Default routes can be used as long as their impact is fully
	understood.
	
	When creating a demand-dial interface, the name of the interface must match the
	name of the account that is added to the accounts database of the remote router.
	This is, in effect, a service account for the router. For more information on
	configuring demand-dial interfaces, please see the "Administrator's Guide" or
	the following article in the Microsoft Knowledge Base:
	
	  Q159684 Configuring Routing and Remote Access Dial-up Interfaces
	
	
	When prompted to enter the phone number or IP address of the remote router, enter
	the phone number of the remote server. The remote network will be defined as a
	route.
	
	Network routes are defined by a network ID, subnet mask, gateway address,
	interface, and metric. For example, 10.0.0.0 is a network ID using a subnet mask
	of 255.0.0.0. The gateway address will be the address of the dial-up interface
	on the remote router. This address will be determined by the network
	configuration you provide in the Routing and Remote Access Port Configuration
	(in the Network settings dialog box). If you are using a static pool of address,
	the first IP address is excluded from the range of available IP addresses. You
	must create a static route for the remote network that uses the demand-dial
	interface.
	
	Configure the X.400 Connector as if it were making a LAN connection and make the
	following modifications on the Override tab of the connector.
	
	1. In the Association Parameters section, adjust the Lifetime (sec) value and
	  the Disconnect (sec) to a value of 15. This minimizes the amount of time the
	  connection is maintained after network traffic has ceased.
	
	2. In the Connection Retry Values section, adjust Max Transfer Retries to a
	  value of 5. Testing has shown that the connection may require more than the
	  default of 2 attempts to complete successfully.
	
	3. Adjust the Open Interval (sec) value to 15. This minimizes the amount of time
	  the MTA will wait before it attempts to reestablish a lost or disrupted
	  association.
	
	4. For the Site Connector, simply configure it as if you were on a local LAN
	  segment.
	
	Additional query words: X.400 demand-dial router rras
	
	======================================================================
	Keywords          : kbnetwork kbsetup kbusage exc4 exc5 exc55 
	Technology        : kbAudDeveloper kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2 kbRRASNTSearch kbRRASNT400
	Version           : winnt:4.0,5.0,5.5
	
	=============================================================================
	

{% endraw %}
