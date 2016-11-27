=> This will teach you how to config most of the setting

//-----------------------------------------------------------------------------------------------
-> Color clip 

Color of -------------------->	Message(0)	Blanket(1)	NPC Name(2)	Zeny(3)
setarray $@COLOR_CHIP$[0],	"^000000",	"^004080",	"^0080FF",	"^0000FF",

				//For display map status message color
				//On Battle(4)	Waiting(5)	Empty(6)
				"^FF0000",	"^00FF00",	"^808080";

(X) - The number inside X which mean the color on which array position
Dont understand how to set the color? Read the doc/script_commands.txt inside your SVN.

//-----------------------------------------------------------------------------------------------

-> How to setting maps and coordinate
You have set your battle map is "battlemap" at position 2,
then you have to set the coordinate for "battlemap" same position with "battlemap",
which mean at position 2.

 = Example using fake map name :
// setarray $@PVS_B_MAP$[1],"battlemap1","battlemap2";
// setarray $@PVS_BMAPX_P1[1],111,222 <--- The first one is for battlemap1 and the second one is for battlemap2

//Below is following the setting as example above given
//Set battle maps
	setarray $@PVS_B_MAP$[1],"map/gat";
//The battle maps name
	setarray $@PVS_B_MN$[1],"Fake map name";

//Set warp position for first party
	setarray $@PVS_BMAPX_P1[1],<value>;
	setarray $@PVS_BMAPY_P1[1],<value>;

//Set warp position for second party
	setarray $@PVS_BMAPX_P2[1],<value>;
	setarray $@PVS_BMAPY_P2[1],<value>;

//Set the position for spectator
	setarray $@PVS_SMAPX[1],<value>;
	setarray $@PVS_SMAPY[1],<value>;

//Set the map and position after battle
//Only one value for the map coordinate
	set $@PVS_W_MAP$,"map/gat";
	set $@PVS_WMAPX,<value>;
	set $@PVS_WMAPY,<value>;

//-----------------------------------------------------------------------------------------------

-> Set the npc name
	set $@PVS_NPC_N$,"PVS Employee";

//-----------------------------------------------------------------------------------------------

-> Set the battle payment,0 to disable
	set $@PVS_ENTRY,<value>;

//-----------------------------------------------------------------------------------------------

-> Pay back for the party who register
 0 = No pay back
 1 = Give back the zeny
	set $@PVS_PAYBACK,<value>;

//-----------------------------------------------------------------------------------------------

-> Set the spectator payment
 0 = Disable
	set $@PVS_SPECZ,<value>;

//-----------------------------------------------------------------------------------------------

-> Enable or disable sound
 0 = Disable
 1 = Enable
	set $@PVS_SOUND,<value>;

//-----------------------------------------------------------------------------------------------

-> Which prize you would like to give? Description for each one as below
 0 = Disable
 1 = Stat point
 2 = Item
 3 = Exp
 4 = Zeny
	set $@PVS_PRIZE_TYPE,<value>;

/////////////////////////////////////////////////////////////////////////////////////////////////

If set 1...
-> Set the giving stat point for each party 
   Formula for calculation will be "(bonus stat point)/(party number)"
	set $@PVS_STPOINT,<value>;

/////////////////////////////////////////////////////////////////////////////////////////////////

If set 2...
-> Just like setting the map and coordinate
//Set the given item
	setarray $@PVS_ITEM[0],<Item ID>;
//and ammount
	setarray $@PVS_ITEM_NUM[0],<value>;

/////////////////////////////////////////////////////////////////////////////////////////////////

If set 3...
-> Set the given exp 
   Formula as "(bonus exp)/(party number)"
	set $@PVS_EXP,<value>;

/////////////////////////////////////////////////////////////////////////////////////////////////

If set 4...
-> Set the given zeny
   Formula as "(bonus zeny)/(party number)"
	set $@PVS_ZENY,<value>;

//-----------------------------------------------------------------------------------------------

-> Get the PVS Employee NPC map
   Just need to change the NPC name incase you change the NPC name
	getmapxy($@PVS_NPC_N$,$@PVS_NPC_X,$@PVS_NPC_Y,1,"PVS Employee#Prize");
	getmapxy($@PVS_BACK_N$,$@PVS_BACK_X,$@PVS_BACK_Y,1,"PVS Employee#warper");

//===============================================================================================

=> For mapflag part

I think most people know how to set this part but there is another thing to do for 100% making
the script work

This part...
force_1-1	mapflag	loadevent

-> Set the mapflag for the warp back map, if you don't do this, the script will perform
   like broken a leg (ow!)
