
ckSurf 1.5 Beta
Based on KZTimer (https://forums.alliedmods.net/showthread.php?t=223274)

Installation
1. Extract everything from the csgo folder to your servers csgo folder
2. Edit addons/sourcemod/configs/databases.cfg
	- Add in a value called "cksurf"
	- sqlite and mysql supported
	- Example:
		"cksurf"
		{
			"driver"			"sqlite"
			"host"				"localhost"
			"database"			"cksurf-sqlite"
			"user"				"root"
			"pass"				""
		}

Optional steps:
3. You can either: 
	- Install the premade zones and map tiers to your database by importing the SQL files in the DatabaseFiles folder
   OR
   	- Run the commands sm_insertmapzones and sm_insertmaptiers (Notice: Requires you to have the root flag (z) in addons/sourcemod/configs/admins.cfg)
4. Restart the server / Change map

Notes:
ALWAYS keep mapcycle.txt updated, as that is used to check which maps are on your server.



Changelog 
- 1.5b
	- Bonus bot support added!
		- CVars: ck_bonus_bot (0/1) & ck_bonus_bot_color (R G B 0/255)
	- Spec lists should now always be under other menus. (Needs testing)
	- Active scoreboard improvements!
		- Kills: Show the amount of seconds in players times.
		- Assists: Show how many percent a player has completed of current map.
		- MVP: How many times a player has completed the current map.
		- Points: How many players have a smaller rank than the mentioned player
		- Order: Players with highest server ranks are the highest in the list.



- 1.4b
	- Fixed a bunch of bugs from last version
	- Made changes to the ranking system. Might be too easy to get ranks atm.
	- Improved !insertmapzones and !insertmaptiers. Actually usable now.
	- Removed useless stuff
	- !r / !s / !tele / !goto all now spawn the player, if the command is used while spectating
	- New CVar: ck_colored_chatnames 0/1
		- Colors players names with their rank color.
		

- 1.3b
 	- Fixed bug where bInStartZone was left to True, if player was in start zone when map changed / disconnect
	- Fixed bug where speedCapType2 didnt cap speed when leaving the start zone, causing an exploit with noclip
	- Improved checkpoints to be more informative
	- Improved chat command filters
	- Removed some useless stuff left over from KZTimer in the database

	- New Zones
		- Validator						-	When a player passes this zone, his run gets flagged as valid
		- Checker						-	Checks if the passing player has his run flagged as valid, if not he gets teleported back to the start
			- These are used to fix unwanted skips

	- New Commands:
		- !teleport / !stuck			-	Teleports player back to the start of the stage, doesn't stop timer
		- !howto						-	Displays a youtube video by Adren on surfing basics


- 1.2 b
	- New CVars bo Roy
		- ck_startzone_sound_path 		- 	The path to the sound file that plays after the client leaves the start zone..
		- ck_startzone_sound_enabled	- 	Enable the sound after leaving the start zone.
		- ck_spawn_to_start_zone 		- 	1 = Automatically spawn to the start zone when the client joins the team.
		- ck_pre_speed_cap_type 		- 	1 = Speed cap applies when user leaves start zone. 2 = Speed cap applies when user hits the ground in the start zone
		- ck_pre_speed_speed 			- 	The prespeed for Speed Zones
		- ck_pre_start_speed 			- 	The prespeed for Start Zones
	- New Zone, TeleToStart
		- Teleports players to the start zone
		- Easy fix for jails, etc
	- Fonts and colors of timer changed
	- Added record and rank to timer
	- Added indicators to show if client has the bonustimer running
	- Cleared .cfg's
	- Hid mode chat commands

TODO:
- Add bonus rankings to !top
- Record bonus bots(?)
- Multiple bonus support
- Code optimizations & organizing


Features:
1. 9 Different zone types that are created from the !zones menu.
	- Start
		- Starts the timer and caps players movement speed to 400u/s
		- Can be teleported to by using the !r/!start commands
	- End
		- Ends the timer
	- BonusStart
		- Starts the bonus stage timer
		- Can be teleported to using the !bonus/!b command
	- BonusEnd
		- Ends the bonus timer
	- Stage
		- Marks the start of a stage
		- Can be teleported to by users using the !stages/!s command
		- You can only use stages OR checkpoints in a map
	- Checkpoint
		- Used in linear maps to get checkpoint times displayed to the user
		- You can only use stages OR checkpoints in a map
	- Speed
		- Same as start, but doesn't have the speed cap
	- Stop
		- Stops a players timer
		- Used to fix exploits with stage selectors usually at the start of a map
	- TeleToStart
		- Teleports player to the start zone
	- Validator
		- When a player passes this zone, his run gets flagged as valid
	- Checker
		- Checks if the passing player has his run flagged as valid, if not he gets teleported back to the start

	- Local record bot
	- Informative checkpoints
	- Premade Zones & Maptiers
	- Ranking system
	etc.

Transitioning from KZTimer:
- ckSurf can use the same database as KZTimer to keep all your old data. 
	- BACKUP YOUR OLD DATABASE as ckSurf does changes to your old database!

- ckSurf is also compatible with KZTimers replays, just move them to the addons/sourcemod/data/ckReplays/ folder


