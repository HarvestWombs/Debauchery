# Debauchery v1.0
By: Harvest

# What does this Plugin do?     
This plugin was originally a rewrite of the CharStart plugin by RicFaith, but soon after it was
completed, I noticed there was some extra potential. So I gave it some mega steroids, and watched it beat the shit out of charstart.

This plugin lets you do the following upon character creation:
1. Add/Set stats
2. Add Skills
3. Set Level
4. Add Waypoints
5. Set an entire character "template"
6. Add Items
7. Set Quest States

# Installation

1. Add this line to your D2Mod.ini.
	`Debauchery=Debauchery.dll`
	
2. If you haven't already installed the NewTxt plugin, then also add
	`NewTxt=NewTxt.dll`

3. Copy the .txt files to your data\global\excel\ folder.


# Uninstall
To remove the plugin you just have to delete the entries you made
in your mod ini and the .txt files from your data\gloabl\excel\ folder.


# DebauchedCharacter file Columns		
|Column     | Description|
|-----------|----------------------------------------------------------------|
|HcIDx      | Incremental line value (keep your shit in order)               |
|Function   | Choose which type of function to use (See Below)               |
|Name		| Set Name for Templates                                         |
|Class		| Choose Class this works for (ama, bar, dru, ass, sor, pal, nec)|
|			| If no class is specified, it works for all.                    |
|StatID		| Statname from ItemStatCost.txt                                 |
|SkillName	| Skillname from Skills.txt                                      |
|Value		| Value or Group to use                                          |
|eol		| End of Line                                                    |

This is the key component to the functionality of this plugin.
Each function takes a variety of parameters but most become self explanatory.

AddStat - Adds *Value to *StatID specified.
SetStat - Sets *StatID to *Value.
AddSkill - Allows you to put points into class skill
Level - Character will level up to *Value
Waypoint - Uses *Value Waypoint group
ItemGroup - Uses *Value Item group
QuestGroup - Uses *Value Quest group
Templates - Create a character with *Name to get *value template group

# DebauchedTemplate file Columns		
|Column         | Description|
|---------------|------------------------------------------------------------------------------|
|HcIdx          | Keep in line                                                                 |
|Template       | Comment field                                                                |
|Group	        | Define groups of classes                                                     |
|Class	        | What class is this for?                                                      |
|Level          | Sets character level                                                         |
|Str	        |                                                                              |
|Dex            | Define how many points to put into stat (If there are available stat |points)|
|Vit            |                                                                              |
|Enr            |                                                                              |
|SkillGroup     | Define group of skills to give to that class                                 |
|ItemGroup      | Define group of items to give to that class                                  |
|WaypointGroup	| Define group of waypoints to give to that class                              |
|eol            | End of Line                                                                  |


# DebauchedSkills file Columns

| Column     | Description                                                             |
| ---------- | ----------------------------------------------------------------------- |
| HcIdx      | Keep in line                                                            |
| Group      | What group does this belong to                                          |
| Skill      | Insert Class Skill Name (Non Class Skills are not possible)             |
| SkillLevel | How many Points to put into Skill (If there are available skill points) |
| eol        | End of Line                                                             |


# DebauchedWaypoints file Columns

| Column               | Description                                             |
| -------------------- | ------------------------------------------------------- |
| HcIdx                | Keep in line                                            |
| Group                | What group does this belong to                          |
| WaypointID           | Insert Waypoint ID                                      |
|                      | -If set to 255 grants all waypoints -> skips next lines |
| Comment...hmm...yes  |                                                         |
| AllDiffs?            | Boolean if true sets waypoint in all difficulties.      |
| eol                  | End of Line                                             |


# DebauchedItems file Columns

| Column      | Description                                      |
| ----------- | ------------------------------------------------ |
| HcIdx       | Keep in line                                     |
| Group       | What group does this belong to                   |
| Item        | Insert Item code here                            |
| ItemLoc     | Linker to body location (use bodyloc.txt naming) |
| ItemQuality | Define the Quality of Item (See Appendix)        |
| ItemCount   | Number of Item to spawn                          |
| eol         | End of Line                                      |

if ItemQuality is set to 255, it will generate a random quality between 2 and 9.

# DebauchedQuests file Columns

| Column       | Description                                                                            |
| ------------ | -------------------------------------------------------------------------------------- |
| HcIdx        | Keep in line                                                                           |
| Group        | What group does this belong to                                                         |
| Quest        | Insert Quest here (See below for naming conventions)                                   |
| Granted      | Quest is given to player                                                               |
| Started      | Quest has been started by player                                                       |
| GoalAchieved | Quest has been completed but not finished                                              |
| Completed    | Quest marked finished                                                                  |
| Difficulty   | Max Difficulty to set flags (1 = normal 2 = normal and nightmare 3 = all difficulties) |
| eol          | End of Line                                                                            |

Quest naming:
a1q1 = Den of Evil
a1q6 = Andariel and so on

You can also specify whole acts as "a#all" or simply "all" for every quest completed.

# Appendix 
Qualities:
```
ITEMQUALITY_NONE = 0,
ITEMQUALITY_CRACKED = 1,
ITEMQUALITY_NORMAL = 2,
ITEMQUALITY_SUPERIOR = 3,
ITEMQUALITY_MAGIC = 4,
ITEMQUALITY_SET = 5,
ITEMQUALITY_RARE = 6,
ITEMQUALITY_UNIQUE = 7,
ITEMQUALITY_CRAFTED = 8,
ITEMQUALITY_TEMPERED = 9
```

# Changelog 

v1.0
Nothing special, just realeasing

v0.7b
-DebauchedQuests.txt QuestID column has been changed to Quest and now accepts strings (See Readme for quest naming conventions)

v0.6b:
-DebauchedItems.txt: Item has been changed to work as CubeOutput field, meaning it can accept parameters such as "rin,uni" etc.
Huge thanks to FireHawk and Szumigajowy for dealing with my ignorance while getting this to work.

v0.5b:
-Added DebauchedQuests.txt
-Added new DebauchedCharacter function for QuestGroups
-Added DebauchedTemplate column for QuestGroups

v0.4b:
-EnableTemplates changed back to Template because it makes more sense now that you can have more than one active at a time.
--Still takes Value for Template->Group

v0.3b:
-Added ItemGroup function to DebauchedCharacter.txt
--Value is ItemGroup to load

v0.2b:
-Templates changed to EnableTemplates, only one can be active at a time. Takes Name and Value for Template->Group
-Added DebauchedSkills.txt
-Added DebauchedWaypoints.txt
-Added DebauchedItems.txt

v0.1:
Initial release

# Credits
Firehawk - For helping me immensely getting things started, as well as helping through out the entire development process.
Necrolis - For moral support, code examples, code locations, advice, and help fixing things.
Szumigajowy - For a lot of functions used here.
Kingpin - For example code and advice.
RicFaith - Inspiration for expanding his current CharStart plugin.