Use this button at the right top for a better experience.  

![image](https://github.com/erenkarakal/SkriptHarbor/assets/67760502/f0f6e108-ae8a-4976-9263-1a3c470c81c2)


# Expressions

## New Scoreboard
Creates and returns a new TAB scoreboard.
```
a new scoreboard (with name|named|with id) %string% (titled|with title) %string% with lines %strings%
```
Available Operations: `get`
Example:
```
set {_scoreboard} to a new scoreboard with id "my_scoreboard" titled "&aMy Title" with lines ("Line 1", "Line 2" and "Line 3")
```

## All Registered Scoreboards
Returns all TAB scoreboards.
```
all [registered] scoreboards
```
Available Operations: `get`
Example:
```
set {_scoreboards::*} to all scoreboards
```

## Scoreboard from ID
Gets a scoreboard by ID
```
scoreboard with id %string%
```
Available Operations: `get`
Example:
```
set {_scoreboard} to scoreboard with id "blub"
```

## Scoreboard Visibility
Returns true if the player has a scoreboard enabled, else false.
```
%player%'s scoreboard visibility
scoreboard visibility of %player%
```
Available Operations: `get`, `set (boolean)`
Example:
```
set scoreboard visibility of {_p} to false
send "Turned off your scoreboard!" to {_p}
```

## Active Scoreboard
Returns the active scoreboard of a player.
```
%player%'s active scoreboard
active scoreboard of %player%
```
Available Operations: `get`

## ID of Scoreboard
Returns the name (ID) of a scoreboard.
```
(name|id) of scoreboard %tab scoreboard%
```
Available Operations: `get`
Example:
```
set {_scoreboard} to player's active scoreboard
broadcast id of scoreboard {_scoreboard}
```

## Title of Scoreboard
Returns the title of a scoreboard.
```
title of scoreboard %tab scoreboard%
```
Available Operations: `get`, `set (string)`

## Lines of Scoreboard
Returns the lines of a scoreboard as a list of strings. Placeholders stay raw and are not parsed.
```
lines of scoreboard %tab scoreboard%
```
Available Operations: `get`, `add (string)`, `remove (integer)`
Example:
```
loop lines of scoreboard {_scoreboard}:

add "This is a new line" to lines of {_scoreboard}

remove 5 from {_scoreboard} # Deletes line 5
```

## Line of Scoreboard
Returns a specific line of a scoreboard.
```
line %integer% of scoreboard %tab scoreboard%
```
Available Operations: `get`, `set (string)`
Example:
```
set {_lines::5} to line 5 of scoreboard {_scoreboard}

set line 5 of scoreboard {_scoreboard} to "Hello"
```

## TAB Prefix
Returns the TAB prefix of a player.
```
%player%'s tab prefix
tab prefix of %player%
```
Available Operations: `get`, `reset`, `set (string)`
Example:
```
set tab prefix of player to "&c&lADMIN "
```

## TAB Suffix
Returns the TAB suffix of a player.
```
%player%'s tab suffix
tab suffix of %player%
```
Available Operations: `get`, `reset`, `set (string)`
Example:
```
set tab suffix of player to " &e%{level:%player's uuid%}%"
```

## TAB Name
Returns the TAB name of a player.
```
%player%'s tab name
tab name of %player%
```
Available Operations: `get`, `set (string)`
Example:
```
set player's tab name to arg-1
```

## Original TAB Prefix
Returns the original TAB prefix of a player.
```
%player%'s original tab prefix
original tab prefix of %player%
```
Available Operations: `get`
Example:
```
set player's tab prefix to player's original tab prefix
send "Your prefix has been reset" to player
```
## Original TAB Suffix
Returns the original TAB suffix of a player.
```
%player%'s original tab suffix
original tab suffix of %player%
```
Available Operations: `get`
Example:
```
set player's tab suffix to player's original tab suffix
send "Your suffix has been reset" to player
```

## Original TAB Name
Returns the original TAB name of a player.
```
%player%'s original tab name
original tab name of %player%
```
Available Operations: `get`
Example:
```
set player's tab name to player's original tab name
send "Your name has been reset" to player
```

## Tag Prefix
Returns the tag prefix of a player.
```
%player%'s tag prefix
tag prefix of %player%
```
Available Operations: `get`, `reset`, `set (string)`
Example:
```
set tag prefix of player to "&c&lADMIN "
```

## Tag Suffix
Returns the tag suffix of a player.
```
%player%'s tag suffix
tag suffix of %player%
```
Available Operations: `get`, `reset`, `set (string)`
Example:
```
set tag suffix of player to " &e%{level:%player's uuid%}%"
```

## Tag Name
Returns the tag name of a player.
```
%player%'s tag name
tag name of %player%
```
Available Operations: `get`, `set (string)`
Example:
```
set player's tag name to arg-1
```

## Original Tag Prefix
Returns the original tag prefix of a player.
```
%player%'s original tag prefix
original tag prefix of %player%
```
Available Operations: `get`
Example:
```
set player's tag prefix to player's original tag prefix
send "Your prefix has been reset" to player
```
## Original Tag Suffix
Returns the original tag suffix of a player.
```
%player%'s original tag suffix
original tag suffix of %player%
```
Available Operations: `get`
Example:
```
set player's tag suffix to player's original tag suffix
send "Your suffix has been reset" to player
```

## Original Tag Name
Returns the original tag name of a player.
```
%player%'s original tag name
original tag name of %player%
```
Available Operations: `get`
Example:
```
set player's tag name to player's original tag name
send "Your name has been reset" to player
```

## TAB Header
Returns the TAB header of a player.
```
%player%'s tab header
tab header of player
```
Available Operations: `set (string)`, `reset`
Example:
```
set player's tab header to "This is a TAB header."
```

## TAB Footer
Returns the TAB footer of a player.
```
%player%'s tab footer
tab footer of player
```
Available Operations: `set (string)`, `reset`
Example:
```
set player's tab footer to "This is a TAB footer."
```

## Collision Rule
Returns the collision rule of a player.
```
%player%'s collision rule
collision rule of %player%
```
Available Operations: `get`, `set (boolean)`
Example:
```
set player's collision rule to false
```

# Effects

## Show Scoreboard
Shows a scoreboard to a player.
```
show scoreboard %tab scoreboard% to %player%
```
Example:
```
set {_scoreboard} to a new scoreboard with id "my_scoreboard" titled "&aMy Title" with lines ("Line 1", "Line 2" and "Line 3")
show scoreboard {_scoreboard} to {_p}
```

## Hide Scoreboard
Hides a scoreboard of a player.
```
hide scoreboard of %player%
```
Example:
```
hide scoreboard of {_p}
```

## Announce Scoreboard
Gets a scoreboard by ID and shows it to everyone for a duration.
```
announce scoreboard %string% for %timespan%
```
Example:
```
announce scoreboard "warning" for 5 seconds
```

## Unregister Scoreboard
Unregisters a scoreboard.
```
unregister scoreboard %tab scoreboard%
```
Example:
```
unregister scoreboard {_scoreboard}
```

## Hide Nametag
Hides a nametag of a player. Optionally hides it from a specific player.
```
hide %player%'s nametag [from %-player%]
```
Example:
```
loop {_enemies::*}:
  hide player's nametag from loop-value
send "You are hidden from your enemies." to player
```

## Show Nametag
Shows a nametag of a player. Optionally shows it to a specific player.
```
show %player%'s nametag [to %-player%]
```
Example:
```
show player's nametag to {_viewer}
```

## Pause Team Handling
Pauses team handling of a player. Rarely useful.
```
pause team handling of %player%
```

## Resume Team Handling
Continues team handling of a player. Rarely useful.
```
resume team handling of %player%
```

# Conditions

## Has Custom Scoreboard
Checks if a player has a custom scoreboard enabled.
```
%player% has custom scoreboard [enabled]
```
Example:
```
if {_p} has custom scoreboard enabled:
  send "You have a scoreboard" to {_p}
```

## Has Hidden Nametag
Checks if a player has a hidden nametag. Optionally checks if it is hidden to a specific player.
```
%player%'s nametag is hidden [from %player%]
```
Example:
```
if player's nametag is hidden from arg-1:
  send "You are hidden from %arg-1%" to player
```

## Has Team Handling Paused
Checks if a player has their team handling paused. Rarely useful.
```
%player%'s team handling is paused
```

# Notes
- A scoreboard ID can be a TAB Hook generated scoreboard, a scoreboard defined in the config or a scoreboard that is created by another plugin that hooks into TAB.
- If a syntax conflicts with Skript or a Skript addon, simply prefix it with `tabhook`. Example:
```
broadcast tabhook scoreboard visibility of player

if tabhook player has custom scoreboard enabled:

tabhook hide scoreboard of player
```
