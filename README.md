# KeyJerk Reactions

## What & Why is KeyJerk Reactions?
Reactions in macOS are buried in the menu bar. Timing is everything. If you have to 1) click the Audio & Video menu bar item, 2) click Reactions, and 3) click the reaction you want to use, the effect may be lost as your reaction time was too long.

KeyJerk Reactions is a straight forward AppleScript that, upon execution, will prompt you to select a reaction and then, using UI scripting, will quickly perform steps 1, 2, & 3 for you.
<BR><BR>

## How to Download KeyJerk Reactions?
[Click here](https://github.com/x74353/KeyJerk-Reactions/raw/main/KeyJerk%20Reactions.scpt) to download the script
<BR><BR>

## How to Use KeyJerk Reactions?
This script can be used in multiple ways. If you have an app like Keyboard Maestro, you can configure a macro to run the script when a global hot key is pressed. If you have a Stream Deck, you can use a plug-in to run the script when pressing a button on the Stream Deck.

_Note: For this script or an app that executes this script to work, you'll need to ensure the proper Accessibility permissions are set in  → System Settings → Privacy & Security → Accessibility._
<BR><BR>

## Is KeyJerk Reactions Free?
Yes, it's free. Please keep it that way do not try to resell it. If you want to show your appreciation and give a financial gift to me, you can do so [here](http://buymeacoffee.com/x74353).
<BR><BR>

## Why is it named KeyJerk Reactions?
It's a play on words with the phrase "knee-jerk reaction." A knee-jerk reaction is a quick, unthinking, reaction you have to something. "Knee" was changed to "Key" because you can use the keyboard to initiate a macOS Reaction using the script. Clearly, I'm very clever. 😉
<BR><BR>

## Modifying the Script
Let's say you want to create separate hot keys in Keyboard Maestro for each reaction, or map specific reactions to different buttons on your Stream Deck and therefore don't want the initial prompt to select a reaction. In such a case, all you need to do is extract portions of the script and create a new script using Script Editor (found in /Applications/Utilities). 

In the original script, find the variables named "reaction" and "reactionGroup" for the reaction you want. For example, the hearts reaction is:

```
set reaction to 1
set reactionGroup to 1
```

So, if you wanted a script to execute the Hearts reactions without any prompting, you would create a new script with the following parts extracted from the full script:

```
set reaction to 1
set reactionGroup to 1

tell application "System Events"
	
	tell its application process "ControlCenter"
		
		tell its menu bar 1
			
			repeat with menuBarItem in every menu bar item
				
				if description of menuBarItem is "Audio and Video Controls" then
					
					-- CLICK THE "Audio and Video Controls" MENU BAR ITEM
					click menuBarItem
					set timeoutSeconds to 2.0
					set uiScript to "click UI Element 2 of group 4 of group 1 of window \"Control Center\" of application process \"Control Center\""
					my doWithTimeout(uiScript, timeoutSeconds)
					
					delay 0.1
					
					-- CLICK THE REACTIONS UI ELEMENT
					set uiScript to "click UI Element " & reaction & " of group " & reactionGroup & " of group 4 of group 1 of window \"Control Center\" of application process \"Control Center\""
					my doWithTimeout(uiScript, timeoutSeconds)
					
					delay 0.1
					
					tell application "System Events"
						key code 53
					end tell
					
				end if
				
			end repeat
			
		end tell
		
	end tell
	
end tell

on doWithTimeout(uiScript, timeoutSeconds)
	set endDate to (current date) + timeoutSeconds
	repeat
		try
			run script "tell application \"System Events\"
" & uiScript & "
end tell"
			exit repeat
		on error errorMessage
			if ((current date) > endDate) then
				error "Can not " & uiScript
			end if
		end try
	end repeat
end doWithTimeout
```


