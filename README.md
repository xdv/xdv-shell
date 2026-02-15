# xdv-shell

Version: 0.3.0  
Status: Active  
Language: Dust Programming Language (DPL)

## Purpose

`xdv-shell` is the interactive command shell for XDV OS.

The shell remains an independent workspace and integrates with `xdv-runtime` for console input/output, process control, and command execution.

## Prompt

The classic interactive prompt is:

`#:`

The prompt is rendered by `src/shell_prompt.ds` via console character output.

## Operational Flow

1. `ShellMain::K::main()` initializes the shell.
2. Builtins are registered by the executor bridge.
3. `ShellLoop::K::run_loop()` renders `#:` and reads command input.
4. The command is lexed/parsing-normalized and dispatched to the executor.
5. Builtins execute and the next prompt cycle begins until `exit`.

## Builtins

- `cd`
- `ls`
- `cat`
- `mkdir`
- `rm`
- `echo`
- `ps`
- `help`
- `exit`

## Source Layout

`src/shell_main.ds`  
Shell entrypoint and lifecycle.

`src/shell_loop.ds`  
Interactive prompt loop and command read/dispatch cycle.

`src/shell_prompt.ds`  
Prompt generation and `#:` rendering.

`src/shell_lexer.ds`  
Command tokenization layer.

`src/shell_parser.ds`  
Command parsing and normalization layer.

`src/shell_executor.ds`  
Builtin and process execution dispatch.

`src/shell_completion.ds`  
Completion workflows.

`src/shell_builtin/*`  
Builtin command implementations.

## Build

```bash
dust check xdv-shell/src
```
