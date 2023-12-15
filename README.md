# KeyJerk Reactions

## What & Why is KeyJerk Reactions?
Reactions in macOS are buried in the menu bar. Timing is everything. If you have to 1) click the Audio & Video Control menu bar item, 2) click Reactions, and 3) click the reaction you want to use, the effect may be lost as your reaction time was too long.

There are two versions of KeyJerk Reactions. One version is a full-fledged app which runs from the macOS menu bar. The other version is an AppleScript that you can use in conjuntion with other software or hardware, such as Keyboard Maestro or Stream Deck. See below for more information about how to use the KeyJerk Reactions script.

In either version KeyJerk Reactions uses AppleScript's UI scripting to quickly perform steps 1, 2, & 3 for you. In the app version, you can assign individual system-wide hot keys for each reaction. KeyJerk Reactions can also prompt you each time to select a reaction via hot key.

![alt text](https://raw.githubusercontent.com/x74353/KeyJerk-Reactions/main/images/KeyJerkReactions_Prompt.png)

### Requirements 
• macOS Sonoma<BR>
• An app running on your Mac that causes the Audio and Video Controls menu bar item to appear:<BR>
![alt text](https://raw.githubusercontent.com/x74353/KeyJerk-Reactions/main/images/VideoMenuBarIcon.png)
<BR>

## How to Download KeyJerk Reactions?
### App Version
[Click here](https://github.com/x74353/KeyJerk-Reactions/raw/main/DMG/KeyJerk%20Reactions.dmg) to download the full app's disk image.

### Script Version
[Click here](https://github.com/x74353/KeyJerk-Reactions/raw/main/Script/KeyJerk%20Reactions.scpt) to download the AppleScript only.
<BR><BR>

## How to Use the KeyJerk Reactions Script?
This script can be used in multiple ways. If you have an app like Keyboard Maestro, you can configure a macro to run the script when a global hot key is pressed. If you have a Stream Deck, you can use a plug-in to run the script when pressing a button on the Stream Deck.

_Note: For this script (or an app that executes this script) to work, you'll need to ensure the proper Accessibility permissions are set in  → System Settings → Privacy & Security → Accessibility._
<BR><BR>

## Modifying the Script
Let's say you want to create separate hot keys in Keyboard Maestro for each reaction, or map specific reactions to different buttons on your Stream Deck and therefore don't want the initial prompt to select a reaction. In such a case, all you need to do is extract portions of the script and create a new script using Script Editor (found in /Applications/Utilities). 

In the original script, find the variables named "reaction" and "reactionGroup" for the reaction you want. For example, the hearts reaction is:

```
set reaction to 1
set reactionGroup to 1
```

So, if you wanted a script to execute the Hearts reactions without any prompting, you would create a new script with the following parts extracted from the full script (code comments removed in this example):

```
set reaction to 1
set reactionGroup to 1

set foundAudioVideoControlMenuBarItem to false

tell application "System Events"
	
	tell its application process "ControlCenter"
		
		tell its menu bar 1
			
			repeat with menuBarItem in every menu bar item
				
				if description of menuBarItem is "Audio and Video Controls" then
					
					set foundAudioVideoControlMenuBarItem to true
					
					click menuBarItem
					
					set uiElementGroup to 1
					
					try
						tell application "System Events"
							click UI element 2 of group 1 of group 1 of window "Control Center" of application process "Control Center"
						end tell
					end try
					
					try
						tell application "System Events"
							click UI element 2 of group 2 of group 1 of window "Control Center" of application process "Control Center"
							set uiElementGroup to 2
						end tell
					end try
					
					try
						tell application "System Events"
							click UI element 2 of group 3 of group 1 of window "Control Center" of application process "Control Center"
							set uiElementGroup to 3
						end tell
					end try
					
					try
						tell application "System Events"
							click UI element 2 of group 4 of group 1 of window "Control Center" of application process "Control Center"
							set uiElementGroup to 4
						end tell
					end try
					
					delay 0.1
					
					tell application "System Events"
						click UI element reaction of group reactionGroup of group uiElementGroup of group 1 of window "Control Center" of application process "Control Center"
					end tell
					
					delay 0.1
					
					tell application "System Events"
						key code 53
					end tell
					
				end if
				
			end repeat
			
		end tell
		
	end tell
	
end tell

if foundAudioVideoControlMenuBarItem is false then
	
	tell me to activate
	set theDialogText to "The Audio Video Control menu bar item wasn't found. Make sure there is a running app that is actively using your camera."
	display dialog theDialogText buttons {"OK"} default button "OK" with title "KeyJerk Reactions" giving up after 30
	
end if
```

## Is KeyJerk Reactions Free?
Yes, it's free. Please keep it that way and do not try to resell it. If you want to show your appreciation and give a financial gift to me, you can do so [here](http://buymeacoffee.com/x74353).
<BR><BR>

## Why is it named KeyJerk Reactions?
It's a play on words with the phrase "knee-jerk reaction." A knee-jerk reaction is a quick, unthinking, reaction you have to something. "Knee" was changed to "Key" because you can use the keyboard to initiate a macOS Reaction using the script. Clearly, I'm very clever. 😉
<BR><BR>
