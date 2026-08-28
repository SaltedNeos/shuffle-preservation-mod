# shuffle-preservation-mod
Mod for Pokemon Shuffle 3DS, which aims to keep the game as functional as possible without its servers.

# Installation instructions:

TL;DR: BACKUP YOUR SAVE FILE, use a hex editor software of your choice to change the bytes highlighted below to 00, use flips to apply the .bps patch to your shuffle .cia dump, install the patched game on your 3DS, restore your modified save file.

## Prework/things you'll need:

- **Hacked 3DS with the latest version of Luma** - See https://3ds.hacks.guide/ for how to do that. This will also install some tools you'll need, namely: Checkpoint, FBI, godmode9, and FTPD.
- **Checkpoint** - to backup and restore save files. JKSV or any other save manager can also work.
- **FBI** - to install cia files.
- **godmode9** - to dump and decrypt cia files.
- **An SD card reader in your computer, or FTPD on your 3DS**  - to transfer files to your computer. For FTPD, your computer can receive the files in the file browser (just type in the address your 3DS gives you). Alternatively, you can use an FTP client like WinSCP to receive the files from FTPD.
- **Floating IPS, also known as Flips** - for applying the patch. You can get that here: https://www.romhacking.net/utilities/1040/. Mac users can use this: https://media.smwcentral.net/Alcaro/bps/.
- **A hex editor** - to modify your existing save file (if you have one). For example, HxD: https://mh-nexus.de/en/hxd/. Mac users can use this: http://hexfiend.com/.
- **7-zip** - to unzip zip files: https://7-zip.org/.

---

## Step 0: Back up existing save data and extra data.

**IMPORTANT: If you have played Shuffle before, then you MUST back up your save data to keep your progress in the mod. You also MUST backup your extra data if you ever want to switch back to vanilla Shuffle.**

Note: This is for people who have played Shuffle before. **If you have NOT played Shuffle before, skip to step 1b.**

- Open up Checkpoint, then use the D-pad to navigate to Shuffle on the top screen (if you don't see Shuffle, hold B for a couple seconds to make Checkpoint refresh the list). Press A to select it, which will then move control to the bottom screen.
- Navigate to "new" and select "Backup" to create a backup of your current save file. Name it something you'll remember, like "premod-save".
- After the save is backed up, press B a couple times to go back to the top-screen navigation. Press X to switch to extra data selection (the word "extdata" on the top screen should become red).
- Navigate to Shuffle again and back up the extra data. Again, anme it something you'll remember, like "premod-ex".
- Press Start or Home to exit Checkpoint.
- Congrats, your data has been backed up! Now, turn off your 3DS and put your SD card into your computer (or you can use FTPD to transfer the file).

Put the backups somewhere safe on your computer - for example, a folder called "shuffle premod materials".
- Your save file is located in the folder 3ds -> Checkpoint -> saves -> 0x01410 Pokemon shuffle
- Your extra data is located in the folder 3ds -> Checkpoint -> extdata -> 0x01410 Pokemon shuffle

After you've done that, put your SD card back into your 3DS.

---

## Step 1a: Dump your Shuffle cia.

If Shuffle is already installed on your 3DS, but you don't have a cia on hand, you'll need to make a dump of it:

- If your 3DS is on, turn it off, then hold Start as you turn it on to enter godmode9. Follow the instructions here to dump your Shuffle cia: https://3ds.hacks.guide/dumping-titles-and-game-cartridges#dumping-an-installed-title .
- You now have a decrypted cia in /gm9/out/ on your SD Card. Hold R and press Start at the same time to power off your 3DS.

## Step 1b: Make sure your cia is decrypted.

If you already have a cia (I won't ask how), you need to make sure it is decrypted. **The patch will ONLY work on a DECRYPTED cia. Encrypted will not work, you'll need to decrypt it first!**

- Put your cia in the "cias" folder on the root of your SD card, then follow the instructions here to decrypt it with godmode9: https://3ds.hacks.guide/dumping-titles-and-game-cartridges#encrypting--decrypting-a-cia-file . 
- If your cia is already decrypted, then godmode9 will tell you that. Doesn't hurt to make sure!
- You now have a decrypted cia in /gm9/out/ on your SD Card. Hold R and press Start at the same time to power off your 3DS.

---

## Step 2: Move the save file and cia to your computer. Verify the cia's hash.
- Move your save file and decrypted cia from your SD card to your computer, if you haven't already.
- We need to make sure your cia file is a good dump by calculating the hash. There are multiple ways to do this, pick whichever works best for you:

Using 7-zip:
- Right-click the cia, then select "show more options" -> "7-zip" -> "CRC SHA" -> "*". This will generate several different hashes for the file.

Using an online hasher:
- Go to https://www.romhacking.net/hash/
- Select "Load a ROM" and upload your cia. This will generate the SHA-1 and CRC32 hashes for it.

Once you have your hashes, make sure they match one of the following sets of hashes that are verified to work with the patch:

dump A:
- SHA1: d26ab084d87ff5494dd6391498f157d0f8630447
- CRC32: 90CD2870

dump B:
- SHA-1: DA0FECDF78B1B94FDC30FA008D69AADBEF783672
- CRC32: 684A4A51

---

## Step 3: Patch the cia.

Make a copy of your cia, and keep the original in a safe place, such as a "shuffle premod materials" folder. Put the copy somewhere else, like a "shuffle postmod materials" folder.

**IMPORTANT: If the mod is updated in the future, you MUST still have a copy of the PREMOD CIA. Keep it safe!!!**

The patch you use will depend on your dump, as we identified earlier:
- If you have dump A, your patch will be "shufflepreservation12.bps"
- If you have dump B, your patch will be "shufflepreservation12 use if patch 1 fails.bps"

Now to apply the patch:
- Open up Flips.
- Click "Apply patch", then navigate to the correct patch file to select it.
- Select the file you want to patch.
- Name the post-patch file (it'll default to the patch name with .cia).

You've now patched the cia! Keep it in a "shuffle postmod materials" folder for now.

---

## Step 4: Hex-edit the save file

Note: If you didn't backup a save file earlier, skip to step 5.
- Make a copy of your save file, and keep the orginal in a safe place, such as a "shuffle premod materials" folder. Put the copy somewhere else, like a "shuffle postmod materials" folder.
- Open up your hex editor (such as HxD) and select the copied save file.
- Using the image below, make sure all the cells in red boxes (0x46, 0x47, 0x61...0x67) are set to zeroes, and the one cell in a blue box (0x6B) is set to 40.
<img width="493" height="138" alt="image" src="https://github.com/user-attachments/assets/3bbcd15b-2dd6-43a7-93fe-da6cad0c7fe9" />

- Save, and exit the hex editor.
- If your hex editor made a .bak file, that's just a copy of the file before you made the edit. We already made a copy, so you don't need this - delete it.
- Rename the folder containing your now-modded save to a name that indicates it is modded. For example, "postmod-save". This will make it easier to find it in Checkpoint later.

You now have a modded save! Keep it in a "shuffle postmod materials" folder for now.

---

## Step 5: move patched cia and modded save to 3DS

- Move the patched cia into the "cias" folder on the root of your SD card.
- Move the modded save into the folder 3ds -> Checkpoint -> saves -> 0x01410 Pokemon shuffle. If you did step 4, then this should be the save that you hex-edited.
- If you skipped step 4, use the "modded savedata" folder included with the patches instead (this is a blank save with special stages unlocked).

---

## Step 6: Delete existing extra data

**IMPORTANT: Make sure you have a backup of your extra data BEFORE you do this!**

- Open up System Settings, go to "Data Management" -> "Nintendo 3DS" -> "Extra Data".
- Select Shuffle's data, then Delete.

---

## Step 7: Install patched cia with FBI

- Open up FBI, select "SDCARD", then navigate to the patched cia in your "cias" folder.
- Select the cia, then select "Install and delete CIA" (we won't need the cia after it installs).

---

## Step 8: Restore save file

- Note: everyone must do this! Both people using a backup, and people using the provided save.
- Open up Shuffle, but then quit out once you get to the title screen. Checkpoint only lists a game after you've opened it once, so that's why we do this.
- Open up Checkpoint, and select Shuffle. If you don't see it, hold B for a few seconds to refresh the game list.
- Navigate to "Restore", then restore the postmod save file.
- Press Start or Home to exit Checkpoint.

---

## Step 9: Confirm installation

We're almost done! We just need to make sure the mod installed correctly:
- When you start up Shuffle, there will be a textbox that says "starting game"
- The title screen should say 1.5.0, instead of 1.5.11.
- You should get a pop-up in-game saying to check in. Don't check in (the game servers are dead, you can't), this is just a sign that the mod is working.
- Once you're in-game, open the Special Shop (bottom-right button -> "Special Shop" yellow button). Scroll down, and if there are two "Drop Rate Increase" items, then the installation was a success!
- If you see the items but your title screen says 1.5.11, that means you forgot to delete the old extra data. In this case, go into System Settings to delete the extra data, then go into Checkpoint to restore the save file again.

Congrats! The mod has been successfully installed. Happy Shuffling!

---

## (Bonus) How to switch back to vanilla Shuffle

If you ever want to switch back to vanilla Shuffle, you can do so while keeping your modded save's progress (the game will naturally undo the hex edit we made).

To switch:
- Make sure your old extra data backup is on your SD card, in the folder 3ds -> Checkpoint -> extdata -> 0x01410 Pokemon shuffle
- Put the premod cia into the "cias" folder on the root of your SD card.
- Backup your current save in Checkpoint.
- Use FBI to install the premod cia.
- Open up Checkpoint, and restore both your old extra data and the current save data.

And you're done! Shuffle is back to its vanilla version.


--- 

## Extra information

### Changing the system clock / Help, my special stages are locked out!

If you ever want to change your system clock (such as for Daylight Savings), **DO NOT use the 3DS settings menu!** Instead, use the Rosalina menu.

(Why do this?) The time on your 3DS is calculated by adding RTC + Offset, where RTC is the "Real Time Clock", while the offset is the "user time offset".
- RTC is assigned by the factory, and the user usually can't change it.
- The offset is the thing you change in the 3DS settings menu.
- Lots of games (such as Animal Crossing) save the last known offset into the save file. When you open the game, it checks whether the last saved offset matches your current offset. If they're different, the game thinks you time traveled.
- The Rosalina menu instead changes the RTC, leaving the offset alone. This prevents your games from detecting time travel.

How to change time in the Rosalina menu:
- From the Home Menu, hold L + down on D-pad + Select to open the Rosalina menu.
- Scroll down to "Miscellaneous options"
- Select "Update time and date via NTP". This will update the RTC clock on your 3DS to match the server.
- Select "Nullify user time offset" to set your offset to 0. (Note that the 3DS hacks guide had you do this during setup; but this is how you change the offset back to 0, if you've changed time in the 3DS settings menu at any point after you hacked your 3DS.)

Note that if your offset wasn't already 0, then Shuffle will now detect the change and lock out your special stages
- You can fix this by repeating the hex edit we did earlier. One of those zeroes was the saved offset.
- Delete your extra data again, and then boot up the game so it recreates the extra data using your edited save. This should convince the game that you have special stage access.

### What does the mod change?

Content changes:
- Data from versions 1.5.1 - 1.5.11 are available without needing Extra Data. This includes:
  - Main stages 641-700
  - UX stages 1-700
  - Expert stages 52-53
  - All special stages
- Competitive stages are now boss stages, using historical HP amounts from H-class ranking tiers. Specifically, their HP is as follows:
  - M-Banette: 23,770
  - M-Garchomp: 24,890
  - M-Steelix: 32,890
  - M-Manectric: 21,860
  - M-Gyarados: 18,310
  - M-Alakazam: 28,900
  - M-Pinsir: 31,720
  - M-Camerupt: 34,440
  - M-Beedrill: 24,700
  - M-Houndoom: 29,980
  - M-Gardevoir: 34,550
  - M-Charizard X: 32,340
- To compensate for Check-In and Competition ranking rewards no longer working, the items are distributed among other stages:
  - Clearing a competitive stage gives 25 banked Hearts, the mega stone (or 1 Level Up, if you already have the stone), and 1 Jewel.
  - The weekend Victini stage has a chance to drop Raise Max Levels (RMLs). It can drop up to 3 boxes, with each box containing 2 RMLs. The rates for each box are 100%, 50%, and 12.5%.
  - To balance the drops added to Victini, you can no longer spend Jewels for additional plays on it. You only get the one free play per week.
- Galvantula's stage no longer appears during Survival Mode stages 45-49, as it was frequently a run-killer.
- The Drop Rate Increase (8 hours) and Drop Rate Increase & No Hearts Needed (45 min) items have been ported over from the Mobile version, and can be bought in the Special Shop for Jewels (1 Jewel for DRI, 2 Jewels for DRI+NHN). DRI+NHN re-uses DRI's description to ensure compatibility with all languages.
- (Week 2) Meganium and Emboar have switched their Heart costs and drop rates, to make Meganium a less-tedious farm. Specifically, this doubles the play cost to 2 Hearts, but also doubles the drop rate, meaning the amount of plays to max the skill is halved.

Visual and music changes:
- (Week 7) Salazzle's stage now uses the "expert stage" music instead of the "hard stage" music, to decrease the chance of not realizing it's a timed stage.
- Vivillon's icon has been swapped to its unused fixed version from the game's files. Previously, it used its old icon from Battle Trozei. This bug (pun not intended) is already fixed on Mobile.
- Shiny Genesect (EX 51) now uses its unused large moving sprite from the game's files. Additionally, the Pokemon List now lists its form name as "Shiny" (previously, nothing was displayed).

Known bugs:
- Main stages 1-11 give incorrectly-low coin rewards for their first clears.
- Special stages act glitchy if accessed before beating main stage 11 (workaround: just beat main stage 11 before touching special stages).
- The 12 Celebration Pikachu (normally from checking in 10 times per month) are unobtainable by legitimate means. The only way to get them would be by editing your save file.
- Most Ultra Beasts do not give their first-clear reward of 5 Exp Booster Larges (EBLs). Xurkitree is the only one that works correctly.
- Guzzlord gives 5 EBLs for every time it is defeated, instead of only the first time. This allows for obtaining 50 EBLs across its 10 plays.
