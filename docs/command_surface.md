# Command Surface

`xdv-shell` currently maps commands to numeric IDs in shell core modules.

## Command IDs

- `1`: `cd`
- `2`: `ls`
- `3`: `cat`
- `4`: `mkdir`
- `5`: `rm`
- `6`: `echo`
- `7`: `ps`
- `8`: `help`
- `9`: `exit`
- `10`: `edx`

These IDs are used across:

- `src/shell_main.ds`
- `src/shell_loop.ds`
- `src/shell_parser.ds`
- `src/shell_executor.ds`
- `src/shell_completion.ds`

## Routing

- `shell_loop` decodes input into command IDs.
- `shell_parser` normalizes command IDs.
- `shell_executor` routes IDs to builtin exec functions or spawn path.
- `edx` is routed through process spawn/join execution.

## Current Limits

- Loop command read currently uses direct key/character decode and line-consume
  model; full tokenized argv capture is limited in current module behavior.
- Lexer/parser/completion are present and wired as normalized shell layers, but
  are not yet full POSIX-style shell semantics.
- `exit` handling is routed through executor (`exec_exit`) and loop stop logic;
  underlying runtime implementation is expected to be provided by linked runtime
  symbols in integration environments.
