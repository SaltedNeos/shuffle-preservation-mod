# shuffle-preservation-mod
Mod for Pokemon Shuffle 3DS which aims to keep the game as functional as possible without its servers

Installation instructions
TL;DR: BACKUP YOUR SAVE FILE, use a hex editor software of your choice to change the bytes highlighted below to 00, use flips to apply the .bps patch to your shuffle .cia dump, install the patched game on your 3DS, restore your modified save file. 

Requirements:
	⁃	A modded 3DS with an SD card luma and the following homebrew software (if you followed the instructions in 3ds hacks you should have all of these installed):
	⁃	A save manager like Checkpoint or JKSV to backup your data
	⁃	FBI to install .cia files
	⁃	godmode9 to dump and decrypt your Pokemon shuffle .cia file or a decrypted unmodified Pokemon shuffle .cia file
On your computer:
	⁃	An sd card reader
	⁃	Floating IPS (or some other IPS patcher) to apply the patch. Mac users can use this: https://media.smwcentral.net/Alcaro/bps/
	⁃	A hex editor to modify your save file to be compatible with the mod. Alternatively, you can choose to use the provided save file which will start at the tutorial and will have specials unlocked. Mac users can use this: http://hexfiend.com/

Step 0: Backing up your save file and extra data
IF YOU WANT TO KEEP YOUR ORIGINAL SAVE FILE:
**Back up your save file AND extra data using Checkpoint, JKSV or some other save manager BEFORE you do anything with this, as installing a new .cia of Shuffle will delete the save file with it!!!** You'll want to make a copy of the folder your back up is in before you make this edit, preferably save it on your computer somewhere and label it as your save file from before you edited for the mod. This backup is in case you wish to return to playing Shuffle without the patch for whatever reason. 

With checkpoint, scroll and select the Pokemon shuffle game icon and select “New”. When prompted to “Backup selected save?” click yes, and name it something that you'll remember like “premod save”. 
Now, press B two times so you're at the title selection screen again, and press X. You should see a list of titles with extra data. Again, scroll to Pokemon shuffle and make a back up like before. Your save data and extra data are now backed up! Turn off your console, remove the sd card, and plug it into your computer. 

If you need more info or to troubleshoot this process, here is a link with more detailed instructions on how to do this in checkpoint. 

Preparing your save file:
On your SD card, find the folder 3DS > Checkpoint > extdata > 0x01410 Pokemon shuffle
Your extra data backup should be here. Make a copy of this folder and save it somewhere safe on your computer. 
Return to your SD card and find the folder 3DS > Checkpoint > saves > 0x01410 Pokemon shuffle 
Your save file backup should be here. Make a copy and save it somewhere safe on your computer. 

Now, go back to the 0x01410 Pokemon Shuffle folder, make a copy of the folder with your save file, paste that copy in the 0x01410 Pokemon Shuffle folder, it should rename itself as a copy. Name it something different like “modded save” so you can distinguish it from your original file. Inside this folder there should be a file called savedata.bin. 
Open this file with Hexfiend (if you're on Mac) or HxD (if you're on windows) or another hex editor (if you prefer another). You'll want to change the highlighted bytes in this screenshot to 00 00 and save.

![image](https://github.com/SaltedNeos/shuffle-preservation-mod/assets/133167521/bdbbbf54-8246-4ba7-8dff-54acd13e50ee)

If your hex editor makes a .bak file, delete it, you don't need it for this mod, its just a backup of the file you edited, but this is why we made a different folder for the modded save data.  
Also make a copy of the folder with the modded save data in it and keep it somewhere safe. 

Thankfully, you only need to do this hex editing part of the process once when you install any version of the mod for the first time. You do however, need to BACK UP YOUR SAVE FILE EVERYTIME YOU UPDATE THE MOD!!!


IF YOU DO NOT WANT TO KEEP YOUR CURRENT SAVE DATA OR DO NOT HAVE A SAVE FILE:
Move the "modded savedata" folder to your 3DS’s SD card in 3DS > Checkpoint > saves > 0x01410 Pokemon shuffle 
If you use this save file, it's best to not play specials until after stage 11, they get pretty glitchy since they're not supposed to be unlocked yet.

Step 1: Applying the patch

First, at always, MAKE A COPY OF YOUR .cia file and save it somewhere safe. You NEED THIS FILE TO UPDATE THE GAME IN THE FUTURE OR FOR ANY OTHER MOD RELEASED. Open the flips version recommended for your OS above and select the Pokemon shuffle .cia fileas the “Base file”. Now, download the shuffle preservation.bps file in this repository and select it as the patch file. Let the program run and download your patched game! Add this to the cias folder on your SD card. 

Step 2: Removing old data from your 3DS

Once your extra data is backed up, you need to delete Shuffle's Extra Data in the 3DS System settings menu. You can also delete Shuffle’s game data. Don't make a backup here, we already did that above!

Step 2.5: Make sure you have a backup of your save file

Installing the mod's .cia file in FBI wipes the save file associated with the game, if you haven't already done it and wish to keep your save file MAKE SURE IT IS BACKED UP BEFORE GOING ANY FARTHER. Whether it be with Checkpoint or JKSV, make absolutely sure you have a backup, as you will not be getting your save file back after this if it is not backed up!

Step 3: Installing the modded game

Safely eject your SD card from your computer and plug it back into your 3DS. Turn on the console, open FBI, and navigate to the cias folder. Click on the patched .cia game file and choose “Install and delete CIA”. This will install the patched game on your console and then delete the file from your SD card as you won't need it after it's been installed. Do not run the game yet! Proceed to step 4:

Step 4: Restoring your save file

Open whatever save manager you used for your backup and select Pokemon shuffle. Scroll to the modified save you created and press R to restore. When it says “Restore selected save?” press A to confirm. Once this is done you're all set!

Step 5: Confirm installation

If all went well, you will see a starting game textbox upon opening the game, and the game will be on v1.5.0. Once you load the game, open the shop and select Special Shop. If you have the two Drop Rate Increase Items, the mod has been installed successfully. 
If you see 1.5.11 when you open the game, again, check the shop for those two items. If they're in the shop, this just means you need to delete the extra data for the game in system settings, then reload your save file's backup from checkpoint or JKSV.
