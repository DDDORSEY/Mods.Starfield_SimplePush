# Mods.Starfield_SimplePush

=== **The 1st Starfield entity push mod, SimplePush** ===========================================================================
**/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////**

**•  ChangeLog:**

  - <date> : 
    
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

 • Requirements:
  - 
  - 
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

**• Features:**

  - Push people down. It's great fun.

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

**• How to Use:**

- Press *F3* to activate and deactivate
(_Yes, I know everyone hates things bound to F-keys. This will hopefully ensure that people configure the key themselves. It's also my own keybind, so let me just have this one selfish thing. It's so easy to change, so please don't post "It's bad practice to set this to F-keys" as I fully understand this. List of Possible Keybinds_)

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

**• INSTALLATION:**

  _**There are many possible install methods but easiest is the following:**_
  -1. Download and install Starfield Hotkeys, Baka Achievement Enabler﻿, and SFSE﻿
  -2. Put both "GetPushTarget.txt" and "PushTarget.txt" from the mod download into your main Starfield directory (where Starfield.exe lives)
  -3. Open the StarfieldHotkeys.ini file located in "User/MyDocuments/MyGames/Starfield"
  -4. Open the SimplePushHotkeys﻿.txt file from the mod
  -5. Copy the contents from SimplePushHotkeys.txt and paste them under their respective headers. Lines under [Macros] in the mod file go under [Macros] in your Hotkeys.ini. Lines under [Hotkeys] in the mod file go under [Hotkeys] in your Hotkeys.ini
  -6. Change "F3" to whatever key you want. List of Possible Keybinds
  -7. Save your StarfieldHotkeys.ini file

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
**•  Acknowledgements:**
  
  - Inspired by the Fallout 4 mod, Get Out Of My Face
  
  - Shoutout to GrumpyGoose, SlinkyD, RowdyBeans, and The Scott for assisting in one way or another

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

**• Philosophy and Methodology**

  _**Why?**_
  Because sometimes you just want to be a jerk

  _**How?**_
  Installing Starfield Hotkeys allows setting custom hotkeys in StarfieldHotkeys.ini in your /MyDocuments/MyGames/Starfield folder.
  Installing SFSE allows Baka Achievement Enabler to function correctly 
  Installing Baka Achievement Enabler suppresses the console warning when first opening the console. Otherwise, you must open console and click through the warning before running the commands.

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

**Now, here's what's interesting**. If I were to manually launch each of these commands separately and sequentially in the console, it would totally work. But, when launched as one command from a hotkey, it fails. I had one hell of a time finding a way to fire the "PushActorAway" or "GetSelectedRef" command after "PickNextActor"; console commands appear to fire each command simultaneously. To circumvent this, I tired artificially incurring a delay by utilizing batch file launch. I would kill for a wait or delay command and WaitBatchFile doesn't seem to work in any arrangement I've tried out (nor does it have documentation).

``
﻿StarfieldHotkeys.ini
[Macros]

SimplePush=PickNextRef; bat GetPushTarget



[Hotkeys]

F3=SimplePush

"PickNextRef" grabs reference ID from any object in crosshairs. I used it here simply because the console has a hard time selecting a picked reference without a reference ID already in console. "PickNextRef" will grab any reference ID, not just actors. It's pretty liberal in its selection, so I used to to essentially prime the console for the next commands. Plus, non-NPCs are not affected by the "PushActorAway" command.

﻿GetPushTarget.txt
﻿;
PickNextActor;
Bat PushTarget;

"PickNextActor" grabs the reference ID for any actors in the crosshair. This only seems to work (it sometimes will but it is highly inconsistent) if there is already a reference ID in console 

﻿PushTarget.txt
﻿;
PushActorAway "GetSelectedRef" 2;

"GetSelectedRef" used in this manner only correctly returns the value if surround by quotes. Without them, you will get a notification that GetSelectedRef is not a valid ObjectID. I also probably don't need those blank lines included but it's currently working and I'm afraid to change it again as sometimes it will not work without them.

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Note: **Please note that this is all just conjecture, based on pain-staking trial-and-error**

**To other modders out there**
Someone more talented than I please, please take anything you want from this and run with it. I'm an artist and musician with ideas, not as much a programmer and would love to see this expanded while we wait for Creation Kit release.

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

**TWEAKING:**

DO NOT ADJUST OR MOVE THE COMMANDS IN THE TEXT FILES. THE CONSOLE REQUIRES THEM EXACTLY AS I HAVE THEM TO FUNCTION. ONLY CHANGE THE FOLLOWING VARIABLE UNDER "PUSHTARGET.TXT":
﻿PushActorAway "GetSelectedRef" 2;
Changing 2 to something higher will only make the NPC lay on the ground longer
Changing 2 to any negative value will allow them to get up instantaneously

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

**Limitations:**

Currently, with the lack of development tools for Starfield, we're stuck either until the Creation Kit is released or xEdit or SFSE get updated with relevant script extensions. As such, actors currently play an animation upon being pushed before engaging ragdoll. The animation also prevents the force factor (currently set to 2) from actually meaning anything, except how long the NPC is going to lay on the ground. Setting it to 50 will result in same force but longer down time. I'm guessing the game is reading the NPC as being affected by the force (more force = more downtime) but the force itself is being blocked by the NPC animation. I'm still working on a way to strip the animation and stack other parameters, so hold tight for future updates.

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

**Future Implementation Ideas:**

- Check distance before firing script
- Remove animation tied to target NPC so that they instantly ragdoll
- Push from player direction. They currently only can be pushed forward or backward, based on the NPC's orientation.
- MOAR PUSH

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

**WARNINGS**

**YOU MAY HAVE TO PRESS THE HOTKEY TWICE TO FIRE CORRECTLY. THIS IS DUE TO A LIMITATION WITHIN THE CONTEXT OF CONSOLE COMMANDS BUT I'M STILL EXPLORING OPTIONS**

**!! F3 IS ABLE TO BE CHANGED TO ANYTHING YOU WANT SO PLEASE READ THE DAMN INSTRUCTIONS BEFORE POSTING !!**

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
**/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////**
