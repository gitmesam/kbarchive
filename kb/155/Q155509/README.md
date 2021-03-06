---
layout: page
title: "Q155509: XADM: Restore Exchange When Site or Organization Name Is Unknown"
permalink: /kb/155/Q155509/
---

## Q155509: XADM: Restore Exchange When Site or Organization Name Is Unknown

{% raw %}

	Article: Q155509
	Product(s): Microsoft Exchange
	Version(s): 4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage exc4 exc5 exc55
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Sometimes it is necessary to reinstall Microsoft Exchange Server and then
	restore the Exchange Server data from backup. This restore process requires that
	the computer running Exchange Server be installed with the original organization
	and site names.
	
	If the server that stopped responding was the only server in the site, the
	administrator needs the organization and site names. Without these names, it is
	not possible to recover the Exchange Server data from backup.
	
	This article explains how to determine the organization and site names and
	restore Exchange Server.
	
	MORE INFORMATION
	================
	
	Four procedures are listed below. There are two procedures for determining the
	organization and site names; the one you use depends on whether the Exchange
	registry keys are available. This article also explains how to restore a
	computer running Exchange Server after you have determined the organization and
	site names. This can be done from either an online or an offline backup.
	
	If Exchange Registry Keys Are Available
	---------------------------------------
	
	If the Exchange registry keys in the Microsoft Windows NT registry are available,
	the organization and site names can be determined from the "X500 DN" registry
	value under the following registry key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\
	  MSExchangeMTA\Parameters
	
	This value has the following string:
	
	  /o=<org name>/ou=<site
	  name>/cn=Configuration/cn=Servers/cn=<server name>/cn=Microsoft MTA
	
	Where <org name> and <site name> are the organization and site
	names.
	
	After you have determined the organization and site names, follow the steps below
	to restore Exchange Server data from an offline or online backup.
	
	If Exchange Registry Keys Are Not Available
	-------------------------------------------
	
	If the Exchange registry keys referenced above are not available, and backups of
	the Priv.edb and Pub.edb files (offline backup) are available, determine the
	organization and site names as follows:
	
	1. Install Exchange Server using NewOrg as the organization name and NewSite as
	  the site name.
	
	2. Stop the Exchange Server services.
	
	3. Delete all the files in the Mdbdata subdirectory.
	
	4. From the Mdbdata directory of the offline Exchange Server backup, copy the
	  files Priv.edb and Pub.edb into the Exchsrvr\Mdbdata subdirectory of the new
	  installation.
	
	5. Start the directory service.
	
	6. From a command prompt, go to the Exchsrvr\Bin directory.
	
	7. Run "Isinteg -patch" (without the quotation marks).
	
	8. Start the information store service.
	
	9. The information store service stops responding with an error 1276. In the
	  application event log in Windows NT Event Viewer, the following error message
	  is logged:
	
	  Event ID: 1088
	  Source: MSExchangeIS
	  Type: Error
	  Category: General
	  Description:
	  The information store could not be loaded because the distinguished name (DN)
	  of the message database
	  /O=OldOrg /OU=OldSite /CN=RECIPIENTS /CN=
	  does not match the DN of the directory
	  /O=NewOrg /OU=NewSite /CN=RECIPIENTS /CN=
	
	  The database may have been restored to a computer that is an organization or
	  site different than the original database.
	
	  OldOrg and OldSite are the original organization and site names and NewOrg and
	  NewSite are the new names entered when Exchange Server was reinstalled in
	  step 2.
	
	10. Note the original organization and site names.
	
	11. Run the Server Setup program and remove the existing installation.
	
	After you have determined the organization and site names, follow the steps below
	to restore Exchange Server from an offline or online backup.
	
	Restoring from an Offline Backup
	--------------------------------
	
	After you have determined the organization and site names, follow these steps to
	restore the Exchange Server system.
	
	These steps assume that an offline backup of the entire Exchsrvr directory is
	available.
	
	1. Run Exchange Server Setup to install Exchange Server using the original site
	  and organization names.
	
	2. Stop all the Exchange Server services.
	
	3. In the Dsadata subdirectory of the Exchsrvr directory, copy Dir.edb to
	  Dir.sav.
	
	4. Proceed to step a if the machine name of the computer running Exchange Server
	  has not been changed and if the Windows NT domain accounts have not been
	  re-created after the server stopped responding. Proceed to step b if the
	  server name has changed or the Windows NT domain accounts information had to
	  be re-created.
	
	  a. Restore the entire Exchsrvr directory from the offline backup.
	
	     -or-
	
	  b. Delete all files from the Exchsrvr\Mdbdata subdirectory. Copy the files
	     Priv.edb and Pub.edb from the Mdbdata of the offline backup to the
	     Exchsrvr\Mdbdata subdirectory.
	
	5. Start the directory service.
	
	6. From a command prompt, go to the Exchsrvr\Bin directory.
	
	7. Run "Isinteg -patch" (without the quotation marks).
	
	8. Start the information store.
	
	9. Start the Exchange Server Administrator program.
	
	10. On the Advanced tab of the Server object properties, start the DS/IS
	  Consistency Checker.
	
	11. Redefine any connectors. Re-create all custom recipients and distribution
	  lists. If, in step 4, only the Priv.edb and Pub.edb were restored, reassign
	  the primary Windows NT account associated with each mailbox.
	
	Restoring from an Online Backup
	-------------------------------
	
	After you have determined the organization and site names, follow these steps to
	restore the Exchange Server system. These steps assume that an online backup of
	the entire Exchsrvr directory is available.
	
	1. Run Exchange Server Setup to install Exchange Server using the original site
	  and organization names.
	
	2. Stop all the Exchange Server services.
	
	3. In the Dsadata subdirectory of the Exchsrvr directory, copy Dir.edb to
	  Dir.sav.
	
	4. If the machine name of the computer running Exchange Server has not been
	  changed and if the Windows NT domain accounts have not been re-created after
	  the server stopped responding, proceed to step a. If the server name has
	  changed or the Windows NT domain accounts information had to be re-created,
	  proceed to step b.
	
	  a. Restore the directory and the information store from the online backup.
	
	     -or-
	
	  b. Restore only the information store from the online backup.
	
	  When you restore, do select the option to restart the services.
	
	5. Start the Exchange Server Administrator program.
	
	6. Run the DS/IS Consistency Checker (Advanced page of the Server object
	  properties).
	
	7. Redefine any connectors. Re-create all custom recipients and distribution
	  lists. If, in step 4, only the information store was restored, the primary
	  Windows NT account associated with each mailbox must be reassigned.
	
	Additional query words: incorrect wrong naming context
	
	======================================================================
	Keywords          : kbusage exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : :4.0,5.0,5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
