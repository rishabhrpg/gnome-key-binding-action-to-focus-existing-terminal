# gnome-key-binding-action-to-focus-existing-terminal
Focus on existing terminal with given key binding or open a new one if none exists.
## Prerequisites
Install `wmctrl` ( `sudo apt-get install wmctrl` )
## Create `raise-terminal.sh` file
```
#!/bin/sh

terminal_wm_class="gnome-terminal"
terminal_exec="gnome-terminal"

# no terminal started, so start one
if [ -z "`wmctrl -lx | grep gnome-terminal`" ]; then
    $terminal_exec &
else
   echo  "else case";
   wmctrl -xa 'gnome-terminal-server.Gnome-terminal'
fi;
```

## Settings
Place this script in the bin folder in your home folder and make it executable. Then under Keyboard Shortcuts (Settings - Keyboard), disable the existing hotkey for "Launch terminal" under the section "Launchers": click on it, then press Backspace to disable the current assignment. Then, in the section "Custom Shortcuts" (scroll down till last in shortcuts listing), create a new custom shortcut by clicking the + icon. Fill out the name of your script as the "command" and assign it the Ctrl+Alt+t shortcut.

## References
* (http://icculus.org/pipermail/openbox/2008-April/005611.html)
* (https://askubuntu.com/questions/200929/focus-existing-terminal-with-ctrl-alt-t-shortcut)
