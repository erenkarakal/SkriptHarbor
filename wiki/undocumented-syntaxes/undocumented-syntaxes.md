# Undocumented Skript Syntaxes
This wiki contains vanilla Skript syntaxes that can't be found in the documentation.\
Some of these syntaxes might not work properly on a normal server.\
All information was written for Skript 2.12.

# Test Mode Syntaxes
All of the syntaxes below require Test / Dev mode to be enabled. See [Enabling Test / Dev Mode](#enabling-test--dev-mode).
Some of them might require a JUnit test to be running.

## Debug (Effect)
**Since:** 2.7\
Debug an expression by printing its data to the console. Can also debug what class an input is parsed as for Conditions and Effects. Useful for dealing with conflict debugging.\
**Patterns:**
```
debug [:verbose] %objects%
debug-effect <.+>
debug-condition <.+>
```
```
executing 'debug console'
[Skript] --------------------
[Skript] RUNTIME
[Skript]       Expression ch.njol.skript.expressions.LitConsole
[Skript]       toString: the console
[Skript]       Changers: []
[Skript]       And: true
[Skript]       Return type: interface org.bukkit.command.ConsoleCommandSender
[Skript]       isDefault: false
[Skript]       isSingle: true
[Skript] --------------------
[Skript] Literal Values: [com.destroystokyo.paper.console.TerminalConsoleCommandSender@5ef6fc39]
[Skript] --------------------
```

## Check JUnit (Condition)
Returns true if the test runner is currently running a JUnit test. Useful for the EvtTestCase of JUnit exclusive syntaxes registered from within the test packages.\
**Pattern:** `running junit`

## JUnit Test Name (Expression)
Returns the currently running JUnit test name, otherwise nothing.\
**Pattern**: `[the] [current[[ly] running]] junit test [name]`

## Parse Section (Section)
Parse code inside this section and use 'parse logs' to grab any logs from it.\
**Pattern:** `parse`

## Parse Structure (Structure)
Parses the code inside this structure as a structure. Use 'parse logs' to grab any logs from it.
**Example:**
```
parse:
  results: {a::*}
  code:
    on load:
      set {_values::*} to event-tree

on load:
  broadcast {a::*} # There's no tree type in an on script load/unload event
```

## Experimental Only (Expression)
A do-nothing syntax that only parses when `example feature` is enabled.
```
using example feature

on load:
  broadcast experimental only   # true
```

## Parse Logs (Expression)
Returns the last known parse logs from a parse section, if any.\
**Pattern**: `[the] [last] parse logs`

## Test String Literal (Expression)
Accepts only a string literal. Used for testing correct parsing & literal treatment. Returns the value.\
**Pattern**: `test string literal %*string%`

## Test Case (Event)
No description.\
**Pattern**: `test %string% [when <.+>]`\
**Example**:
```
test "test name" when running minecraft "1.20.4":
	assert 1 isn't 2 with "1 should've been 2"
```

## Method Exists (Condition)
Checks if a method exists.\
**Pattern**: `method[s] %strings% [dont:do(esn't|n't)] exist[s]`\
**Example**: `if method "org.bukkit.Bukkit#getPluginCommand(java.lang.String)" exists`

## Assert (Effect)
Assert that the condition is true. The test fails when it is not.\
**Patterns:**
```
assert <.+> [(1:to fail)] with [error] %string%
assert <.+> [(1:to fail)] with [error] %string%, expected [value] %object%, [and] (received|got) [value] %object%
assert <.+> [(1:to fail)]
```

## Returnable (Section) / Last Returned Value (Expression)
**Since:** unknown\
**Description:** No description.\
**Patterns:**
```
returnable [:plural] %*classinfo% section
[the] last return[ed] value[s]
```
Example:
```
on load:
  returnable int section:
    return 5
  broadcast last returned value   # 5
```

## Objectives (Effect)
An effect to set up the required objectives for JUnit tests to complete.\
**Patterns:**
```
ensure [[junit] test] %string% completes [(objective|trigger)[s]] %strings%
complete [(objective|trigger)[s]] %strings% (for|on) [[junit] test] %string%
```

## Runnable (Section Expression)
Creates a new Runnable.\
**Pattern**: `[a] new runnable`
```
on load:
  set {_runnable} to a new runnable:
    broadcast "hello"
```

## Run Runnable (Effect)
Runs a runnable.\
**Pattern**: `run %object%`
```
run {_runnable}
```

## Test Objects
**Patterns**:
```
[the] test(-| )world
[the] test(-| )block
[the] test(-| )location
```

## Test Key Value Set (Expression)
No Description.\
**Patterns:**
```
test key values of %~objects%
test key values
```

## Test Plural Class Infos
Tests that the plural class infos are identified correctly. Not meant to be used for anything.
```
classinfo test for %testgui%
classinfo test for %testguis%
classinfo test for %exemplus%
classinfo test for %exempli%
classinfo test for %aardwolf%
classinfo test for %aardwolves%
classinfo test for %hoof%
classinfo test for %hooves%
```
Also registers 3 types named `example1`, `example2` and `example3`

# Other Syntaxes
These are syntaxes that can be used without enabling test/dev mode.

## Cause Exception (Effect)
Causes an exception.\
**Pattern**: `cause exception`

## At (Expression)
Returns a direction that doesn't point anywhere.\
**Pattern**: `at`

## Event (Structure)
Represents all event listeners.\
**Pattern**: `[on] [:uncancelled|:cancelled|any:(any|all)] <.+> [priority:with priority (:(lowest|low|normal|high|highest|monitor))]`

## Event Expression (Expression)
Represents all event values.\
**Pattern**: `[the] event-%*classinfo%`

## Example (Structure)
Examples are structures that are parsed but will never be run. They are used as miniature tutorials for demonstrating code snippets in the example files. Scripts containing an example are seen as 'examples' by the parser and may have special safety restrictions.
```
using examples

example:
  broadcast "hello"   # never ran
```

# Enabling Test / Dev Mode
To enable test/dev mode, you'll need to add some Skript startup flags before `-jar server.jar`:
```
java ^
  -Dskript.testing.enabled=true ^
  -Dskript.testing.verbosity=LOW ^
  -Dskript.testing.dir="" ^
  -Dskript.testing.results="" ^
  -Dskript.testing.devMode="true" ^
  -jar ./server.jar ^
  --nogui
```
Do this at your own risk!
