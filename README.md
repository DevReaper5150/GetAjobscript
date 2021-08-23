# GetAjob script
Compatible with Dayz Epoch 1.0.7

# What it does:
Allows players to select a random paying job and makes payouts based on set amount of minutes.

# Install Options

#1 Can be called from rightclick add to your clickActions >> Config.sqf 
Example: ["ItemRadio","Get a job","execVM 'scripts\GetAjob.sqf';","true"],

#2 Can be linked to a scroll wheel function >> fn_selfActions.sqf & variables.sqf
# In your fn_selfActions.sqf search for
if (Z_globalBanking) then {
			if (_isMan && {!(isPlayer _cursorTarget)} && {_typeOfCursorTarget in ZSC_bankTraders}) then {
				if (s_bank_dialog1 < 0) then {
					s_bank_dialog1 = player addAction [format["<t color='#0059FF'>%1</t>",localize "STR_CL_ZSC_BANK_TELLER"],"\z\addons\dayz_code\actions\zsc\atmDialog.sqf",_cursorTarget,3,true,true];
				};
			} else {
				player removeAction s_bank_dialog1;
				s_bank_dialog1 = -1;
			};
			if (_typeOfCursorTarget isKindOf "ATM_DZ") then {
				if (s_bank_dialog2 < 0) then {
					s_bank_dialog2 = player addAction [format["<t color='#0059FF'>%1</t>",localize "STR_CL_ZSC_BANK_ATM"],"\z\addons\dayz_code\actions\zsc\atmDialog.sqf",_cursorTarget,3,true,true];
				};
			} else {
				player removeAction s_bank_dialog2;
				s_bank_dialog2 = -1;
			};
		};
	};

# Add below it:

	_work = cursorTarget isKindOf "Notebook"; // We are using cctv Notebook here
    if ((speed player <= 1) && _job && (player distance cursorTarget < 5)) then {
    if (s_player_getjob < 0) then {
        s_player_getjob = player addAction ["Get a job","scripts\GetAjob.sqf",cursorTarget, 0, false, true, "",""];
    };
    } else {

    player removeAction s_player_getjob;
    s_player_getjob = -1;
    };
	
# Look for in same file:

player removeAction s_player_checkWallet;
s_player_checkWallet = -1;

# Add below it:
player removeAction s_player_getjob;
s_player_getjob = -1;

In your variables.sqf

# Look for:
s_player_checkWallet = -1;

# Add below that:
s_player_getjob = -1;


