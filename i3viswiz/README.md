`i3viswiz` - Professional window focus for i3wm

SYNOPSIS
--------

`i3viswiz` [`-v`|`-h`] [`-p`] [`-g` GAPSIZE] [*DIRECTION*]

DESCRIPTION
-----------

`i3viswiz` lists all visible windows with their positions (X,Y) and
dimensions (width,height). If `-p` flag is passed, the list will be
printed to `stdout`. If a *DIRECTION* (left|right|up|down) is passed
`i3wizvis` will shift the focus to the window closest in the given 
DIRECTION, or warp focus if there are no windows in the given direction.

OPTIONS
-------

`-v`  
  Show version and exit.

`-h`  
  Show help and exit.

`-p`  
  Print list of windows to `stdout`. The first line is either
  the *con_id* of the window receiving focus . The second line 
  are the x and y coordinates where receiving window is searched.
  Remaining lines are the list. The first field is marked with a 
  `*` if the line contains the active window. Second field is the 
  *con_id* of a visible window. Floating windows are excluded from
  the list. If the active window is floating, the first line will 
  have the text "floating".

  Example output:  

``` text
  $ i3paint -p -g 20 down
    94369749033328
    tx: 319.5 ty: 227
    - 94369749098704  x: 1349  y: 243  w: 125  h: 656  
    * 94369748807120  x: 0     y: 0    w: 639  h: 207  
    - 94369749033328  x: 0     y: 208  w: 1222 h: 691  
    - 94369748768416  x: 1223  y: 0    w: 376  h: 242  
    - 94369749326096  x: 640   y: 0    w: 582  h: 207  
    - 94369749166496  x: 1475  y: 243  w: 124  h: 656  
    - 94369749106512  x: 1223  y: 243  w: 125  h: 656
```

`-g` GAPSIZE
  Set GAPSIZE (defaults to 5). GAPSIZE is the distance in pixels
  from the current window where new focus will be searched.

*DIRECTION*
  Can be either (left|right|up|down) OR (l|r|u|d). DIRECTION needs
  to be the last argument of the command. If no DIRECTION is given,
  focus will not shift.

EXAMPLE
-------

replace the normal i3 focus keybindings with viswiz like this:
``` text
Normal binding:
bindsym Mod4+Shift+Left   focus left

Wizzy binding:
bindsym Mod4+Left   exec --no-startup-id i3viswiz l 
```
