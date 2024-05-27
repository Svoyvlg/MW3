======================================================[ READ ME ]======================================================

[ INTRODUCTION ]
================
This is a Call of Duty: Modern Warfare 3 MOD, allowing users to play the game on custom dedicated servers
that enable advanced scripting and B3-based administrative features.

01. The release files contain no copyrighted material.
02. Currently supported game version is 1.4.382, so make sure you collect all the neccessary files on your own.
03. We suggest getting the latest version on Steam, then using a "downgrade data pack" to get it back to 1.4.382.


[IMPORTANT NOTES - CLIENT]
==========================
01. Start the game using "TeknoMW3_Client_Launcher.exe" (don't use the old "TeknoMW3.exe" loader).
02. If one day Steam updates and the "TeknoMW3_SteamPlugin.dll" plugin stops working for some reason, or you do not wish to have
    your presence known, delete / rename the "TeknoMW3_SteamPlugin.dll".


[IMPORTANT NOTES - SERVER]
==========================
01. Start the server using "TeknoMW3_Server_Launcher.exe" (yes, edit your batch files to use this instea of "iw5mp_server.exe")
02. Linux/WINE Users: You need to hex-edit "iw5mp_server.exe" string "steam_api.dll" to "teknomw3s.dll" and start the server using that.
03. If your server becomes unstable after a while, blame it on plugin(s). They are often riddled with memory-leaks.
    You might use "Intel Inspector" for memory leak detection or "Intel VTune" for code heat-zone detection. Saved analysis logs
	can be sent to us.
04. Since MONO-2 and MONO-5 are now supported, after you write proper configs to your "server.cfg", remember to choose a correct
    "mono-2.0.dll" ("2.0" in the name is extra confusing, I know). There are 2 dlls packed with this release:
	"mono-2.0.dll__2109" -- default, required for mono 2.10.9
	"mono-2.0.dll__5011" -- optional, required for mono 5.0.1.1
	Selected dll should be copied/renamed into "mono-2.0.dll" and placed in main installation directory of the server.


[SPECIAL THANKS]
================

Special thanks go to our testers & bug-reporters @Discord: 

Musta, CoNNoUK, Kenshin, Benjah, AHMED-DANTI, AndroiderPwNz, RektInator, Andrew

... and many more that I might have forgotten.



====================================================[ CHANGE LOG ]=====================================================

v2.8.1.2 - 2024-02-26
=====================

[CLIENT]
========
01.[FEATURE] Improved readability for the FPS counter: Added a new DVAR "cg_drawFpsUpdateInMs" to specify after how many milliseconds the displayed FPS should be updated
02.[MISC] cl_packetdup and cl_maxpacket are no longer locked to a certain value
03.[MISC] Various minor changes and improvements



v2.8.1.1 - 2023-12-02
=====================

[CLIENT]
========
01.[FEATURE] Added significant FPS improvements
02.[FEATURE] Added DVAR suggestions/hints and basic auto completion to the ingame console
03.[MISC] Various minor changes and improvements



v2.8.1.0 - 2023-10-11
=====================

[CLIENT]
========
01.[MISC] Fixed loading missing DLC maps: If you don't have the DLC map which is running on a server, you will get disconnected from the server with a corresponding notice. The game will no longer close or crash in that case.
02.[MISC] Fixed DLC map names being displayed in white when map is installed / red when map is not installed (Server List)
03.[MISC] Added ability to toggle the FPS counter using the DVAR "cg_drawFPS" (e.g. via ingame console). The value of "cg_drawFPS" will be saved to "config_mp.cfg" file.



v2.8.0.9 - 2023-09-18
=====================

[CLIENT]
========
01.[MISC] Performance improvements: This mainly fixes a performance issue when selecting a class ingame, but it will improve overall performance too.
02.[MISC] Minor changes and improvements



v2.8.0.8 - 2023-04-23
=====================

[CLIENT]
========
01.[FEATURE] Reimplemented in-game console to process DVARs
02.[MISC] Made DVARs "cg_fov", "cg_fovScale" and "com_maxFps" archived
03.[MISC] Lowered min. value of DVAR "cg_fov" to 40
04.[MISC] Increased max. value of DVAR "cg_fovScale" to 3.0



v2.8.0.7
=====================

[CLIENT] - 2023-04-17
=====================
01.[BUGFIX] Fixed a rarely occurring crash related to clantags in the killfeed
02.[MISC] Changes to DVAR "cg_weaponCycleDelay" by servers will no longer be written to the config_mp.cfg
03.[MISC] Various internal changes/improvements


[SERVER] - 2024-01-05
=====================
01.[MISC] Stability improvements



v2.8.0.6
=====================

[CLIENT] - 2023-04-03
=====================
01.[BUGFIX] Fixed Direct Connect
02.[BUGFIX] Fixed a potential performance issue
03.[MISC] Added another check for invalid clantags
04.[MISC] Minor changes and improvements


[SERVER] - 2023-12-31
=====================
01.[MISC] Various stability improvements



v2.8.0.5 - 2023-04-01
=====================

[CLIENT]
========
01.[BUGFIX] Fixed security and stability issues
02.[BUGFIX] Fixed bugs in the game that have been abused by malicious clients/servers to crash clients games
03.[FEATURE] Added fovScale option: cg_fov and cg_fovScale can be set and changed separately now (via Launcher or teknogods.ini)
04.[FEATURE] Added FPS counter (toggle-able via Launcher or teknogods.ini)
05.[FEATURE] Added sensitivity option to easily set precise values (via Launcher or teknogods.ini)
06.[FEATURE] Added option to disable the music in the main menu (via teknogods.ini)
07.[MISC] Various minor changes and improvements



v2.8.0.4 - 2017-08-14
=====================

[CLIENT]
========
01.[MISC] Adjusted maxfps to minimum of 46 (in loader and in-game).
02.[MISC] Spaces in nickname/title are now allowed (again).
03.[BUGFIX] Fixed yet another IW bug when class was set to one that had no weapon-data loaded (crashing the client in result).
04.[FEATURE] Added a security list of dvars that servers will not be able to set for clients. They are:
             "sec_sv_blocked_dvars" and "sec_cfg_blocked_dvars" - both can be set in "config_mp.cfg", for example:
			 seta sec_sv_blocked_dvars "cg_hudChatPosition;cg_chatHeight"   --this would protect those 2 dwords against changes from done by the server
			 seta sec_cfg_blocked_dvars "cg_hudChatPosition;cg_chatHeight"  --this on the other hand, would allow servers (assuming same dvars
			                                                                  wouldnt be also blocked using the feature above) to be changed at runtime,
																			  but any writes to "config_mp.cfg" for them would be replaced with their
																			  default values.
			 This basically means you can now protect against some rogue dvar-changes initiated by the game servers (using "sec_sv_blocked_dvars") or,
			 allow servers to change some risky dvars, but instead, block their write(s) to "config_mp.cfg" (using "sec_cfg_blocked_dvars").
			 Default blocked values:
			 "sec_sv_blocked_dvars": Only "compassSize" for now.
			 "sec_cfg_blocked_dvars": All dvars starting with: "con_", "cg_Scores", "cg_chat", "compass".

[SERVER]
========
01.[FEATURE] Added a new dvar "sv_current_dsr" that is automatically updated whenever a new DSR is loaded.
02.[MISC] Nicknames/titles with spaces are now allowed (again).
03.[FEATURE] Scripts: Added Utilities.SetConnectErrorMsg(string) function - use this to set error message that will be sent to clients that got denied entry
             via another new feature:
04.[FEATURE] Scripts: Added a callback/event: OnClientConnect(Func<Dictionary<string, string>, bool> func)
             How it works: Once server gets a connection-attempt request, this event will be fired up with a dictionary containing all client info.
			               Callback should by default return FALSE. If you return TRUE (eatIt?), it will tell the server to deny entry to the client.
						   For example: if (args["name"].ToLower().Contains("hax")) { Utilities.SetConnectErrorMsg("you hax bruh!"); return true; }
05.[BUGFIX] Scripts: Entity.IP fixed, again. Hopefully for good this time.
06.[MISC] While B3 normally uses "net_authPort" (that can be used for another service, in which case we increase that port by 1), we have added a new
          server param "-b3port XXXX" (where XXXX is a port of your choice of course).


v2.8.0.3 - 2017-08-11
=====================

[CLIENT]
========
01.[BUGFIX] TeknoMW3_SteamPlugin now properly recognizes the Steam-Beta mode. On top of that, there is an error handler added in case something goes wrong.
02.[FEATURE] Client now has 2 news feed channels (1st, when current version is the "latest" and 2nd, when an update is required).
03.[FEATURE] Added in-game update checks.
04.[FEATURE] Loader -> Settings menu now has options allowing users to set emblem/tag/title.
05.[BUGFIX] HWID Generator, again, has been fixed. It's the last time, we promise.

[SERVER]
========
01.[MISC] B3 is now disabled by default. Run server with "-enable_b3" to enable it.
02.[MISC] Added extra security features to B3 that might break some plugins. They are disabled by default. Run server with "-secure_b3" to enable them.
03.[MISC] RCON (in-game) is now disabled by default. Run server with "-enable_rcon" to enable it.
04.[MISC] cLog class for server logging now does not ouput anything except for "Dedicated.log". This should vastly improve the server performance.
05.[MISC] Server binary is now compiled with performance optimizations. Like above, this should improve the server performance.
06.[MISC] Servers can now be started with disabled integrity checks via "-no_integrity". This vastly improves load times of FF files/maps.
07.[BUGFIX] InfinityScript had a memory leak on SetText API. On top of that, it is recommended to use SetText API instead of SetField in order to change text.
08.[BUGFIX] B3 console was incorrectly freeing certain tokenized parameters, causing random crashes.
09.[BUGFIX] B3 socket-check interval was too low, leading to higher CPU usage.
10.[BUGFIX] InfinityScript API "OnServerCommand" now receives a proper command string. Use Cmd_Argv2/Cmd_Argc2 to get the params.
11.[BUGFIX] InfinityScript API "OnClientCommand" now receives a proper command string. Use Cmd_Argv/Cmd_Argc to get the params. PS. Client commands 
            (in-game -> say -> /somecommand param1 param2) will be seen as "SAY" command @ the API, hence Argv(0)=="SAY", Argv(1)=="/somecommand", etc.
12.[BUGFIX] Loading of newer mono versions should now work properly.
13.[FEATURE] Added a new server dvar: "sv_path_for_ban_dbs", using it you can set a path used to store BAN Databases. Default: ".\\BanDB\\"
14.[FEATURE] Added 3 new server dvars: "sv_ban_by_guid" (default: true), "sv_ban_by_ip" (default: false), "sv_ban_by_nick" (default: false).
15.[BUGFIX] Banning now works properly (for temp-bans, remember to set "sv_kickBanTime"):
             - ban <case sensitive nickname> <reason (optional)>
             - banclient <client number> <reason (optional)>
             - tempban <case sensitive nickname> <reason (optional)>
             - tempbanclient <client number> <reason (optional)>
             - unban <nickname or IP or GUID>  (unbans from selected DB-type, IP, Nick or GUID - [read NOTE below])
			 - unban -p <optional: filter string>  (lists permanent bans, optionally filtered via filter string)
			 - unban -t <optional: filter string>  (lists temporary bans, optionally filtered via filter string)
			 - unban -a <optional: filter string>  (lists all bans, optionally filtered via filter string)
             NOTE: When you ban someone, ban-data gets stored for each active ban method separately. For example, IP and GUID bans are in different
			       files, hence to unban, you need to issue 2 unban commands, 1st "unban <ip>" and 2nd "unban <guid/hwid>".
16.[FEATURE] Server window now prints the enabled/disabled command line options.
17.[BUGFIX] HWID Generator, again, has been fixed, this may invalidate the existing BAN DBs. It's the last time, we promise.
18.[BUGFIX] BanDB folder is now created automatically in case it does not exist.


v2.8.0.2 - 2017-08-02
=====================

[CLIENT]
========
01.[BUGFIX] Fixed FPS lock at 60.
02.[BUGFIX] Fixed Client renderer lag.
03.[BUGFIX] Fixed Client HWID generator.


[SERVER]
========
01.[MISC] You can now specify custom MONO version for the server via server.cfg dvar settings.
          Values in the example below are DEFAULTS, so no need to set them, add some of these only if you need to change something.
			seta mono_script_lib_folder "mono-2.10.9\\lib"
			seta mono_script_cfg_folder "mono-2.10.9\\cfg"
			seta mono_runtime_version "v4.0.30319"  
			seta mono_default_config_parse "true"
			seta mono_assembly_name "InfinityScript.dll"
			seta mono_config_file "anything.config"  -- this is mainly needed for latest MONO, where using SQL or NET libs triggers "exePath" error.

02.[MISC] Due to Mono 5.0.1.1 instability, we reverted to official Mono 2.10.9 in this release. All plugins should work again and server should not crash randomly.
03.[FEATURE] Added a new InfinityScript function: GI_SetSectionProtection(int section, bool protect)
             It is exported under: Utilities.SetSectionProtection(int section, bool protect)
             How does it work:
                1st param = executable section to change protection of, section 0 = ".text" (code section)
                2nd param = protect true/false; to enable patching, make it "true", to disable patching, make it "false"
             Currently server will automatically unprotect ".text" section for any call to Mono/Script, however, if you need to change something
             while the protection is still enabled, this API might come in handy. 
             Important note: REMEMBER to set the protection back after doing whatever was needed: Utilities.SetSectionProtection(?, true)
04.[BUGFIX] InfinityScript function getter Entity.IP now utilizes 2 new TeknoMW3S.dll exports: GetClientAddressIP & GetClientAddressPORT.
            This should fix the issue with 64bit-value error when reading IP+PORT via GetClientAddress().
05.[BUGFIX] Disabled GScr_SetSlowMotion, to re-enable it, run server with "-enable_slow_motion".




v2.8.0.2 - 2017-08-01
=====================

[CLIENT]
========
01.[BUGFIX] Fixed string parser on the Client side. Now servers/clients can send the "^\x01" or "^\x02"-type messages and they wont crash.
02.[BUGFIX] Fixed invalid memory reference in the Weapon-handler.
03.[BUGFIX] Fixed protocol handler of the Server Browser.
04.[MISC] Client no longer uses the same library name "TeknoMW3.dll", it is now known as "TeknoMW3C.dll".
          Together with new loader executables, Client and Server binaries can be safely copied onto the same installation directory of MW3.
05.[MISC] Added "Latest News" screen to the main menu (client binary).
06.[FEATURE] Added "TeknoMW3_SteamPlugin.dll". If Steam is ON, it will set your presence to "In-Mod TeknoMW3 - Call of Duty: Modern Warfare 3".


[SERVER]
========
01.[BUGFIX] Fixed MSG_ReadBitsCompress stack overflow. This bug was actively exploited to achieve "God Mode" or to crash/destroy server installations.
02.[BUGFIX] Fixed various command injections in OOB packet-handler, RCON and B3-RCON.
03.[BUGFIX] Fixed infinite loop bug in B3 RCON.
04.[BUGFIX] Fixed UDP packet handling in B3 RCON.
05.[BUGFIX] Changed memory access rights for the code section on the server binary. Previously it was set to Read-Write-Execute, allowing easy exploitation of certain bugs.
06.[FEATURE] Re-enabled B3 RCON. By default, it is using "net_authPort" 8766.
07.[FEATURE] Added "-disable_b3" commandline param to server executable, in case B3 RCON is not neeeded.
08.[FEATURE] Re-enabled in-game RCON. If server has the "rcon_password" set and you know it, you can open RCON using ` or Shift+` and connect to it (rcon login <pass>).
09.[FEATURE] Added "-disable_rcon" commandline param to server executable, in case RCON is not neeeded.
10.[FEATURE] Added "sv_serverFullMsg" server config dvar. It is loaded only once, when the server starts. Standard \n \t \x?? (hex) char encodings are allowed.
11.[FEATURE] Added "sv_protectedDvars" server config dvar. All dvars listed under it will be read-only & write-protected once the first map is loaded. For example:
             seta sv_protectedDvars "sv_serverFullMsg sv_hostname rcon_password sv_privatePassword g_password sv_privateClients sv_maxclients"
12.[MISC] Server no longer use the same library name "TeknoMW3.dll", it is now known as "TeknoMW3S.dll".
          Together with new loader executables, Client and Server binaries can be safely copied onto the same installation directory of MW3.
13.[MISC] Ban database is again based on text file format. SQL database is no longer used (due to stability and security reasons).
14.[MISC] It is recommended to set these DVARs in "server.cfg", for EXAMPLE:
          seta sv_clanWebsite "http://www.somesuper.clan/plz?join"
          seta sv_Discord "https://discord.gg/k5ghe7q"
          seta sv_serverFullMsg "Some message when the server is full.\nPlease join our server XYZ or visit out website blabla.com"
          seta sv_maxping "500"
15.[UPGRADE] Mono has been updated from 4.0 to 4.5. Network, SQL, etc. functionalities are now possible from within scripts!




v2.7.3.11 - 201?-??-??
======================

(old release - no change log available)
