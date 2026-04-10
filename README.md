# xdv-shell

Version: 0.3.x  
Status: Active  
Language: Dust Programming Language (DPL)

`xdv-shell` is the shell subsystem for XDV OS runtime bring-up and command
dispatch.

## Current Behavior

The current implementation provides:

- shell lifecycle entry (`main -> init -> run`)
- boot-bridge emit path for xdv-os integration (`shell_bridge` + boot units)
- interactive loop structure and prompt render (`#:`)
- command-code decode and dispatch to builtin/external execution
- builtin command modules for `cd`, `ls`, `cat`, `mkdir`, `rm`, `echo`, `ps`,
  `help`
- `edx` command dispatch path through executor process spawn

Command surfaces include:

- `cd`
- `ls`
- `cat`
- `mkdir`
- `rm`
- `echo`
- `ps`
- `help`
- `exit`
- `edx`

## Source Layout

- `src/shell_main.ds`
- `src/shell_loop.ds`
- `src/shell_prompt.ds`
- `src/shell_lexer.ds`
- `src/shell_parser.ds`
- `src/shell_executor.ds`
- `src/shell_completion.ds`
- `src/shell_bridge.ds`
- `src/shell_boot_units.ds`
- `src/shell_builtin/*.ds`
- `src/*_tests.ds`

## Build

```bash
dust check xdv-shell/src
```

## Documentation

- `docs/README.md`
- `docs/runtime_flow.md`
- `docs/module_reference.md`
- `docs/command_surface.md`
- `changelog.md`
