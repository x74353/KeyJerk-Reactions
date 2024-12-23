![alt text](https://raw.githubusercontent.com/x74353/KeyJerk-Reactions/main/images/KeyJerk-Reactions-App-Icon.png)

# KeyJerk Reactions
KeyJerk Reactions speeds up choosing a Reaction and makes it so you don't have to perform any gestures in front of the camera. By assigning a system-wide hot key to each macOS Reaction, you can trigger any Reaction immediately, right there in the moment. You can also trigger a Reaction through AppleScript, Shortcuts, or by calling up a HUD with a system-wide hot key where you can quickly choose your desired Reaction. 
<BR><BR>

## Installation
**[Download the latest version here.](https://github.com/x74353/KeyJerk-Reactions/raw/main/DMG/KeyJerk%20Reactions.dmg)**

![alt text](https://raw.githubusercontent.com/x74353/KeyJerk-Reactions/main/images/KeyJerkReactions_Prompt.png)
<BR><BR>

## How does it work?
KeyJerk Reactions uses macOS Accessibility APIs to control your Mac. When you trigger a Reaction with a system-wide hot key or another method such as AppleScript, Shortcuts, etc., KeyJerk Reactions will quickly click all of the buttons and menus needed to apply the Reaction in the active/frontmost app that is using your Mac's camera. If the active/frontmost app is not using your Mac's camera, a App Priorities list (configured in Settings) will be used to determine which running app to apply the Reaction in.
<BR><BR>

## What's New in KeyJerk Reactions 2?
- Uses macOS Accessibility APIs instead of AppleScript to trigger Reactions<BR>
- Compatibility when sharing screen<BR>
- Non-English language support (additional setup required)<BR>
- AppleScript support (e.g., ```tell application "KeyJerk Reactions" to react with "Hearts"```)<BR>
- Shortcuts support<BR>
- Option to hide KeyJerk Reactions in menu bar<BR>
- Updated user interface and app icon<BR>
- Closed source<BR>

### 2.1 Update
- KeyJerk Reactions now tries to apply macOS Reactions in the active/frontmost app
- Added App Priorities section in Settings to define which apps to apply macOS Reactions in if active app is not using camera
- Added Camera section in Settings to define camera name for external 3rd party camera (e.g., MX Brio)
- Added Stats section in Settings to track most used macOS Reactions
- Redesigned Settings window
- Added additional error/alert messages
- Resolved incompatibility with macOS Audio Extensions such as ARK from Rouge Amoeba
- Added Documentation link in menu under Feedback/Suppot section

### 2.1.1 Update
- Fixed an issue that caused the Welcome window to always appear at launch

### Requirements 
- macOS Sonoma or later, and a Mac with [Apple silicon](https://support.apple.com/en-us/116943) or a Mac using [Continuity Camera](https://support.apple.com/en-us/102546) with iPhone 12 or later
- macOS Accessibility Features access<BR>
- macOS Camera access (for non-English setup only)<BR>
- An app running on your Mac that accesses your Mac's camera and causes the Audio and Video Controls menu bar item to appear:<BR><BR>
![alt text](https://raw.githubusercontent.com/x74353/KeyJerk-Reactions/main/images/VideoMenuBarIcon.png)

### Known Issues/Incompatibilities
- Attempting to execute the same Reaction repeatedly will not work - a delay of ~5½ seconds in-between duplicate Reactions is required.
<BR><BR><BR>



# More Information<BR>
## Why Use KeyJerk Reactions?
Available in macOS Sonoma and later, Reactions are video effects such as floating hearts or fireworks that can be applied to the camera feed of most, if not all, apps. This includes FaceTime, Zoom, Slack, and many other apps. 

To trigger a Reaction, you typically need to perform a gesture with your hand(s) in front of your Mac's camera, such as a peace sign ✌🏼 or a thumbs-up 👍🏼. Most of the time this works well, though you look kind of silly while doing it. When it doesn't work, others might wonder what the heck you're doing flashing double peace signs at everyone. To trigger a Reaction without a gesture, you have to click a series of buttons and menus which is a slow and tedious process. By the time you've manually chosen your Reaction, it's too late - the effect is lost. KeyJerk Reactions solves this problem by making triggering a Reaction as quick and simple as pressing a system-wide hot key.

KeyJerk Reactions can also integrate with other workflows and automations since it supports AppleScript and Shortcuts. With a simple AppleScript, osascript, or Shortcut you can trigger a Reaction from another app, workflow, or hardware device such as a Stream Deck.
<BR><BR>

## How to Trigger a Reaction with AppleScript?
When KeyJerk Reactions is running, you can trigger a Reaction using AppleScript with the following command:
```
tell application "KeyJerk Reactions" to react with "Thumbs-up"
```
Reaction titles:

<table>
	<tr>
		<td valign="middle"><img src="https://fonts.gstatic.com/s/e/notoemoji/latest/2764_fe0f/512.gif" alt="❤️" width="32" /></td>
		<td valign="middle" style="width: 75px;">Hearts</td>
	</tr>
</table>

<table>
	<tr>
		<td valign="middle"><img src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f44d_1f3fc/512.gif" alt="👍" width="32" /></td>
		<td valign="middle" style="width: 75px;">Thumbs-up</td>
	</tr>
</table>

<table>
	<tr>
		<td valign="middle"><img src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f44e_1f3fc/512.gif" alt="👎" width="32" /></td>
		<td valign="middle" style="width: 75px;">Thumbs-down</td>
	</tr>
</table>

<table>
	<tr>
		<td valign="middle"><img src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f388/512.gif" alt="🎈" width="32" /></td>
		<td valign="middle" style="width: 75px;">Balloons</td>
	</tr>
</table>

<table>
	<tr>
		<td valign="middle"><img src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f327_fe0f/512.gif" alt="🌧" width="32" /></td>
		<td valign="middle" style="width: 75px;">Rain</td>
	</tr>
</table>

<table>
	<tr>
		<td valign="middle"><img src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f389/512.gif" alt="🎉" width="32" /></td>
		<td valign="middle" style="width: 75px;">Confetti</td>
	</tr>
</table>

  <table>
	  <tr>
		  <td valign="middle"><img src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f6a8/512.gif" alt="🚨" width="32" /></td>
		  <td valign="middle" style="width: 75px;">Lasers</td>
	  </tr>
  </table>

  <table>
		<tr>
			<td valign="middle"><img src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f386/512.gif" alt="🎆" width="32" /></td>
			<td valign="middle" style="width: 75px;">Fireworks</td>
		</tr>
	</table>
<BR>
	
## Why is it named KeyJerk Reactions?
It's a play on words with the phrase "knee jerk reaction." A knee jerk reaction is a quick, unthinking, reaction you have to something. "Knee" was changed to "Key" because you can use the keyboard to initiate a macOS Reaction using the app. Clever, right? 😑
<BR><BR>

## Is KeyJerk Reactions Free & Safe to Use?
Yes, it's 100% free. You can download and install KeyJerk Reactions on any compatible Mac for personal use. You may not redistribute for profit or otherwise sell KeyJerk Reactions in any form. There are no advertisements or in-app purchases in KeyJerk Reactions, nor are there any analytics or other 'spyware' type functions. KeyJerk Reactions.app is code-signed with a valid Apple Developer ID and is notarized by Apple.

If you want to show your appreciation and give a financial gift to support its development, you can do so [here](http://buymeacoffee.com/x74353).
<BR><BR>

## License
```
All Rights Reserved

Copyright © 2024 William Gustafson

THE CONTENTS OF THIS PROJECT ARE PROPRIETARY AND CONFIDENTIAL.
UNAUTHORIZED COPYING, TRANSFERRING OR REPRODUCTION OF THE CONTENTS OF THIS PROJECT,
VIA ANY MEDIUM IS STRICTLY PROHIBITED.

The receipt or possession of the source code and/or any parts thereof does not
convey or imply any right to usethem for any purpose other than the purpose for
which they were provided to you.

The software is provided "AS IS", without warranty of any kind, express or implied,
including but not limited to the warranties of merchantability, fitness for a
particular purpose and non infringement. In no event shall theauthors or copyright
holders be liable for any claim, damages or other liability, whether in an action of
contract, tort or otherwise, arising from, out of or in connection with the software
or the use or other dealings in thesoftware.

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the software.
```
