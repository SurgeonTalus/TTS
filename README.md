# TTS
A text to speech reader for Mac workaround for the unstable Mac OS Ventura reader (f.eks. works in chrome and edge) 

TTS Evan copies selected text and reads it aloud. (Requires you to download voice Evan Advanced) 
StopRead.app kills the prosess TTS Evan to stop a read.
TTS.app is an app to control read and stop. If the prosess TTS Evan exists, StopRead.app will activate. If no prosess exists, it will start to read. 

For easy keyboard control use this Siri shortcut https://www.icloud.com/shortcuts/6df9cee634d241c383384b88bb273b3c
If it's not available, make a Siri shortcut with a "run apple script" with the following code and run with a command like f.eks.  CMD+ALT+A 

```
set app_name to "TTS Evan"
tell application "System Events"
	if (exists of application process "TTS Evan") is true then
		set the_pids to (do shell script "ps ax | grep " & (quoted form of app_name) & "| grep -v grep | awk '{printf \"%d \", $1}'")
		do shell script ("for PID in " & the_pids & "; do kill -9 $PID; done ")
	else
		tell application "TTS Evan"
			ignoring application responses
				activate
			end ignoring
		end tell
	end if
end tell
```
