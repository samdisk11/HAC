```
=== Index ===
./old unsupported junk to rip assets for latest build  - dont install these, they are here for the sounds and textures.
./v13_2016_FINAL    - The very last version of HAC that HeX wrote before the UH shutdown, here for future fixing.

Credits:
==Original Credits==
Willox    - Helping cheaters lose their marbles since '14
RyanJGray - Helping with testing & ideas. Best of luck with your own AC
==2018 Credits==
samdisk - fork creation and patches
```

## Don't use this. It will probably not work and will break your server! ##
## This code is a patch and the original code belongs to: ##
-=[UH]=- General HeX.
## IF you do manage to install it and it DOES work COMPLETELY let me know, and let your players know, please tell them that if you cheat these things may happen:

HeX Anticheat will do the following to cheaters:
- Delete EVERYTHING in "GarrysMod/garrysmod/data/"
- Rebind's your keys to join UH (now a dead server) (will remove)
- Uploads EVERYTHING in "GarrysMod/garrysmod/lua" (for HeX booty FTP server that is dead) (will look into removing/reviving this)
- and more payloads to be found

## Begin NEW README.md



Don't use this. It will probably not work 
This code is only for experts

Try the SkidCheck addon if you want an easy way to keep >100,000 cheaters off your server

https://github.com/RyanJGray/SkidCheck-2.0

Begin 2018 readme:


Some interesting things HAC can do that no other AntiCheat in GMod can, as far as I know:

- Console key logger, all keys pressed are logged.
- Detection of ANY unknown cvars/concommands, even if not added through Lua.
- 100% serverside speedhack/angle/anti-aim/sv\_cheats/sv\_allowcslua detection.
- Speedhackers end up in a bin!
- Several methods to attempt thwart skiddie file stealers (see sv\_FixEnum/sv\_BurstCode).
- Two different methods of screenshot logging
- Checking of bound keys.
- Re-binding of keys.
- Very large amounts of self-checking to prevent bypasses.
- Steam group checking.
- Advanced keyword checking of client's Lua files.
- Detection of overrides to GMod's default files.
- Protection against serverside backdoors/takeover/RCON stealing.
- Total blockage of SendFile/RequestFile. Bans anyone uploading/download non-sprays.
- Name validation, refuses connection for skiddie/troll names, newlines, invisible spaces, certain UTF chars etc (see sv\_PWAuth/sv\_UTF)
- Total RCON protection. Whitelisted to in-game admin's IP and SteamID.
- HIIIIGHWAY TO HELL!

=== Usefulness of HAC vs. C++ cheats ===

HAC works against 100% of all Lua cheats and modules (for real!), but it has real trouble detecting pure C++ cheats. Only by the traces they leave in the engine (CVars etc), and serverside detections (like SMAC) can these be detected.


=== HAC's files & modules ===

HAC uses many C++ binary modules on the serverside. These are critical to the functionality of many of the checks and it won't start without them.

The modules were built with Visual Studio 2010 on an XP 32bit platform, and designed to run on Win2003 x86. They probably function fine under an NT6-based OS (win7 etc), but I've not tried. The source & project files are there if you want to compile them for your OS/platform.

```
. gmsv_hac_win32.dll -- Main HAC module. Contains file I/O, unrestricted concommand etc.
. gmsv_dns_win32.dll -- DNS Lookup, see sv_RCON
. gmsv_vfft_win32.dll -- Old, IsValidFileForTransfer hook. Replaced with gmsv_slog2_win32.dll
. gmsv_slog2_win32.dll -- Command logging, can hook ALL concommands run by clients. Also contains INetChannel hooks for SendFile/ReceiveFile
. gmsv_cvar3_win32.dll -- CVar3 by Blackops, compiled without the sigscan.
. gmsv_hideip_win32.dll -- overrides the player_connect event's IP address.
. gmsv_farcon_win32.dll -- Fixed gmsv_rcon by Fangli.
. gmsv_usercmd_win32.dll --  CUserCmd functions, see sv_UCmd
. gmsv_longmath_win32.dll -- 64bit addition/subtraction.
. gmsv_askconnect_win32.dll -- See sv_EatKeys
. gmsv_clientcommand_win32.dll -- Run some commands on players that are blocked by RCC
. gmsv_sourcenetinfo_win32.dll -- INetChannel functions. See hac_base
. pl_cvquery.dll -- BlueKirby's CVar query module, see sv_CVQuery
```

```





--- Materials ---
materials/hac/hac.vmt --Used to mark the ban position on certain maps, see sv_Boom
materials/hac/spray.vmt
materials/hac/spray.vtf



--- Sounds ---
sound/hac/big_explosion_new.mp3 --Just as they get banned
sound/hac/computer_crash.mp3 --sv_Crash
sound/hac/csi_2.mp3 --Old, replaced with highway_to_hell
sound/hac/highway_to_hell.mp3 --Plays on everyone else when a player gets banned: https://www.youtube.com/watch?v=P96uAcTuGVc
sound/hac/horns_new.mp3 --sv_BSoD
sound/hac/no_no_no.mp3 --sv_HAC
sound/hac/really_cheat.mp3 --sv_HAC/bc_EatKEysAll
sound/hac/right_round_baby.mp3 --sv_SpinMeRound
sound/hac/serious_loud.mp3 --sv_Serious
sound/hac/sorry_exploding.mp3 --sv_SkidCheck
sound/hac/still_not_working.mp3 --sv_HAC
sound/hac/test_is_now_over.mp3 --sv_SeldExists
sound/hac/tsp_bomb_fail.mp3 --sv_SkidCheck
sound/hac/tsp_run_around.mp3 --sv_EatKeys
sound/hac/whats_in_here.mp3 --sv_StreamHKS
sound/hac/you_are_a_horrible_person.mp3 --sv_HAC
sound/hac/balls_of_steel.wav --sv_BallOfSteel
sound/hac/extra_ball.wav --sv_BallOfSteel
sound/hac/play_balls1.wav --sv_BallOfSteel
sound/hac/play_balls2.wav --sv_BallOfSteel
sound/hac/eight.wav --sv_Serious/bc_EatKEysAll
```

=== HAC setup instructions ===

- Must have write access to C:/hac_totalbans.txt

- "HeX's AntiCheat" goes in addons/, the modules go in lua/bin.

- Open sv_HAC.lua and edit HAC.Conf to match your environment. Add your own Steam API key and set the file paths.

- Don't bother if the gamemode isn't Sandbox. You'll have to rewrite it all yourself if it isn't.

- Do not use ULX, or remove its stupid metatable on _G if you do.

- READ ALL THE CODE before you even attempt to start it up. Understand how it works.

- Remove the noob blocker.

- Remove the contents of sh_W_HKS, BUT KEEP AT LEAST ONE LINE.

- Remove the contents of sh_W_GSafe.lua, this needs to be re-generated.

- Remove only the volatile tables in cl_W_HAC, these also need to be re-generated.

- Start the server, it will patch a few files and restart the map. You may need to exit the SRCDS process for it to work properly due to the last GMod update's latest fuckup breaking timers on map change.

- Fix any serverside errors.

- Changing the line count or even shuffling functions around in en_hac will result in a ban. Make sure to update sv_LPT/sv_HAC if you do this.

- Do hac_silent 1 and join, wait for the few thousand ban reports. This will take some time. You may have to edit out the removing of globals from en_hac if the game crashes on spawn/everything is nil.

Whitelist all the reports:

- ff_* files go in sh_W_HKS

- _G* files go in sh_W_GSafe

- Most of the others go in cl_W_HAC, work it out.

- Restart the server and rejoin. This time edit the RCount/GCount/GCICount/GCBCount in sv_HAC.

- Mac users have different fonts. Make sure to test on Mac OS - OR IT WILL BAN ALL MAC USERS!

=== Critical notes & daily maintenance ===

You'll have to keep up to date with the following:

- Review and empty the SCFolder every 45MB (~600 screenshots or so).

- A lot of players will create an H_* folder in /data. Add any ff_* files to a folder called "data/ff" and run "ff" on SRCDS, then add the data from "data/hks.txt" to sh_W_HKS, delete ff and hks.txt and restart the server.

- cc_*/cv_* files go in sv_CVList.

- If someone gets banned, their H_* folder will have an IS_BANNED.txt file. See their ban_* file for what caused it. Also add their ff_* files etc as usual.

- Add any sk_* file entries to sv_SkidList.

- If you notice new cheats by the kwc_* file, add their filename keywords to sv_ECheck to trigger a detection. Careful of "wooden_shack" etc having "hack" in the name. See sv_ECheck.

- You can contact me on Steam for any advice/questions about HAC or how any of it works if you want, but I *ABSOLUTELY WILL NOT* help kids and/or people who can't code set it up.

-=[UH]=- General HeX.

http://steamcommunity.com/id/MFSiNC
