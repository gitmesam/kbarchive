---
layout: page
title: "Q246157: FS2000: Kneeboard Is Not Displayed"
permalink: /kb/246/Q246157/
---

## Q246157: FS2000: Kneeboard Is Not Displayed

{% raw %}

	Article: Q246157
	Product(s): Microsoft Home Games
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kb3rdparty kbdisplay kbimu msgame
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Flight Simulator 2000 
	- Microsoft Flight Simulator 2000 Professional Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you play Microsoft Flight Simulator 2000, the Kneeboard may not be
	displayed.
	
	CAUSE
	=====
	
	This behavior can occur if the following conditions are true:
	
	- A video adapter based on a 3Dfx Voodoo1, Voodoo2, or Voodoo Graphics chip set
	  is installed in your computer.
	
	- Hardware acceleration is enabled in Flight Simulator 2000.
	
	RESOLUTION
	==========
	
	To work around this issue, use one of the following methods.
	
	Disable Hardware Acceleration
	-----------------------------
	
	To disable hardware acceleration in Flight Simulator 2000:
	
	1. On the Options menu, point to Settings, and then click Display.
	
	2. Click to clear the "Enable hardware acceleration" check box, and then click
	  the CHECK MARK.
	
	If game performance slows to unacceptable levels:
	
	1. On the Options menu, point to Settings, and then click Display.
	
	2. Click to select the "Low resolution mode" check box, and then click the CHECK
	  MARK.
	
	Use Notepad to View the Kneeboard Text Files
	--------------------------------------------
	
	If you do not want to disable hardware acceleration in Flight Simulator 2000,
	open the appropriate Kneeboard text file in Notepad or Wordpad.
	
	Kneeboard information is saved in a set of text files in the Aircraft folder:
	
	- The Kneeboard_Keys.txt file contains the information on the Key Commands tab
	  in the Kneeboard. This file is located in the following folder:
	
	  \Program Files\Microsoft Games\FS2000\Aircraft
	
	- The <aircraft>_Check.txt files contain the information for each
	  aircraft on the Checklist tab in the Kneeboard.
	
	- The <aircraft>_Ref.txt files contain the information for each aircraft
	  on the Reference tab in the Kneeboard.
	
	- The <aircraft>_Notes.txt files contain the information for each
	  aircraft on the Notes tab in the Kneeboard.
	
	  The <aircraft>_Check.txt, <aircraft>_Ref.txt, and
	  <aircraft>_Notes.txt files for each aircraft are stored in the
	  following folder
	
	  \Program Files\Microsoft Games\FS2000\Aircraft\<aircraft>
	
	  where <aircraft> is the folder name for an aircraft.
	
	Additional query words: flightsim fsim fs fs2k fs2000 msgame
	
	======================================================================
	Keywords          : kb3rdparty kbdisplay kbimu msgame 
	Technology        : kbGamesSearch kbFlightSimSearch kbFlightSim2000 kbSimSearch
	Version           : WINDOWS:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
