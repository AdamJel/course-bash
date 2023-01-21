# Notes on Bash course

## shebang

Every script should start with a shebang line:

```bash
# preferably:
#!/bin/bash

# acceptable:
#!/usr/bin/env bash
```

To make script executable, run:

```bash
sudo chmod u+x <script>
```

Without it, it still may be run, but it need to be run with `bash` command.
Otherwise it is possible to run it with `./<script>`.

Bash scripts don't need to have `.sh` extension. Shebang line is enough. But it is good for (human) readability.

## variables

- `var=value` - set variable
  - there must be no spaces around `=`
  - type does not have to be specified

- `unset var` - unset variable
  - QUESTION: does Bash have garbage collector?

- `<command> $var` - reference variable
  - `$` is required
  - `${var}` is optional, but recommended

- `export var` - export variable to child processes
  - `export var=value` - set and export variable
  - `export -f <function>` - export function
  - `export -p` - list exported variables
  - `export` - list all variables in current shell environment

- `readonly var` - make variable read-only

### grouping

- running stuff in `( <stuff> )` runs it in a subshell
  - variables set in subshell are not visible in parent shell
  - variables set in parent shell are visible in subshell

- running stuff in `{ <stuff> }` does not create a subshell, it is just a grouping

## programs

- `enable <command>` - enable/disable shell builtins
  - `enable` - list all builtins

- `compgen -k` - list all shell keywords

- `sleep <seconds>` - sleep for given number of seconds

- `var=<value> <command>` - set variable and run command, where var is visible to the command

### time

- `time` - run program and print time it took to run
  - e.g. `time sleep 1`

