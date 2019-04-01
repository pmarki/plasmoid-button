# Configurable button
## A Configurable Button Plasmoid

This is a button that allows to run script when toggled (on and off scripts)
and to monitor status by status script.

## Installation

Install this plasmoid using `plasmapkg2 --install .` in the plasmoid directory.

## Configuration
The plasmoid can by configured in the settings menu:
 - *On Script* will execute a script (can be a full path to a script or bash snippet)
 when toggling from off state to on. The icon will be changed to "On" icon.
  - *Off Script* will execute a script (can be a full path to a script or bash snippet)
 when toggling from on state to off. The icon will be changed to "Off" icon.
 - *Status Script* can be used to monitor application (or the Internet connection). 
 The script should return 0 on success (to show "On" state), something else on error 
 (to show "Off" state)
 - Check status on startup: Run once "Status script" on system startup
 - Run periodically: Run "Status Script" in defined interval


## Example usage
### Configuration to monitor internet connection (or server status)
 - Disable On and Off scripts
 - Enable Status Script on startup and to run periodically 
 - set interval to your needs
 - Add status script `ping -c 2 -q example.com`
 
### Configuration to start a service
 - Enable On script
 - Add On script eg: `sudo systemctl start docker`
 (assuimg this command can be run without password)
 - disable Off and Status scripts
 
 When button will be pressed the script will be launched, if a service was started 
 sucessfully the icon will stay green, otherwise the icon will go back to red.
 
### Configuration to start, stop and monitor service
 - Enable everything :)
 
## Notes
  - On script should exit with 0, otherwise icon be change to red 
 (test it by adding On script `sleep 5; exit 1`)
  - Off script exit code is not taken into account
  - By default plasmoid shows red (Off) icon when started, this can be easily changed: 
  set Status script `exit 0` to run once on startup

## Maybe in a future
 - tooltip with custom name
 - tooltip or dialog with output from scripts
 
## Credits
  - https://github.com/neicker/on-off-switch
  - https://github.com/MakG10/plasma-applet-server-status
  
  You might also like: https://github.com/Intika-Linux-Plasmoid/plasmoid-on-off-switch-commands
