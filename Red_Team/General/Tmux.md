## Hot Keys

### Sessions
```

Tmux new -s <session-name>

Tmux switch -t <session-name>        // while in tmux

Tmux attach -t <session-name>         // from outside tmux

tmux kill-session -t sessionname

CB d     // detach session (still runs)

CB $   // rename season 

```
### Window


```
CB c   // new window

CB ,    // rename window 

CB p  // last active window


```  

### Pane
```

CB % // new pane vertical

CB “   // split vertical 

CB [  // copy mode

CB w  // se all windows

CB ;   // jump to last active pane

CB o  // cycle panes

CB ctrl up arrow or down arrow 

  

CB ?   // show all keybindings 

```  

### Plug-In manage

```
CB I    // instal new plug added to config

CB R  // reload session

tmux source ~/.tmux.conf   // reload session 
```
  

### Copy
```
CB y     // copy line
CB Y   // copy PWD
```
  

### Logging
```
CB shift p   // start logging

CB Alt shift p   // save logging

CB Alt p   // screenshot
```
  
  
  

## Links

[https://tmuxcheatsheet.com/tmux-plugins-tools/](https://tmuxcheatsheet.com/tmux-plugins-tools/)

https://github.com/tmux-plugins/tmux-logging?tab=readme-ov-file