# xdv-shell

Command Line Shell for XDV OS, following Implementation Plan v4.

## Overview

The XDV Shell provides the command line interface for XDV OS, featuring:

- Interactive shell loop
- Command lexer and parser
- Builtin commands (cd, ls, cat, mkdir, rm, echo, ps, help, exit)
- Tab completion
- Process management

## Architecture

This implementation follows the K-Domain only approach (classical x86-64 hardware), with Q/Φ domains stubbed to return ERR_DOMAIN_NOT_AVAILABLE (100).

## Source Files

```
src/
├── shell_main.ds            # Entry point
├── shell_main_tests.ds      # Main tests
├── shell_loop.ds            # Main loop
├── shell_loop_tests.ds      # Loop tests
├── shell_prompt.ds          # Prompt generation
├── shell_prompt_tests.ds    # Prompt tests
├── shell_lexer.ds           # Tokenizer
├── shell_lexer_tests.ds     # Lexer tests
├── shell_parser.ds          # Command parser
├── shell_parser_tests.ds    # Parser tests
├── shell_executor.ds        # Command execution
├── shell_executor_tests.ds  # Executor tests
├── shell_completion.ds      # Tab completion
├── shell_completion_tests.ds # Completion tests
└── shell_builtin/
    ├── builtin_cd.ds         # cd command
    ├── builtin_cd_tests.ds
    ├── builtin_ls.ds        # ls command
    ├── builtin_ls_tests.ds
    ├── builtin_cat.ds       # cat command
    ├── builtin_cat_tests.ds
    ├── builtin_mkdir.ds     # mkdir command
    ├── builtin_mkdir_tests.ds
    ├── builtin_rm.ds        # rm command
    ├── builtin_rm_tests.ds
    ├── builtin_echo.ds     # echo command
    ├── builtin_echo_tests.ds
    ├── builtin_ps.ds        # ps command
    ├── builtin_ps_tests.ds
    ├── builtin_help.ds      # help command
    ├── builtin_help_tests.ds
    ├── builtin_exit.ds      # exit command
    └── builtin_exit_tests.ds
```

## Builtin Commands

| Command | Description |
|---------|-------------|
| cd      | Change directory |
| ls      | List directory contents |
| cat     | Display file contents |
| mkdir   | Create directory |
| rm      | Remove files/directories |
| echo    | Print text |
| ps      | Process status |
| help    | Show help |
| exit    | Exit shell |

## Domain Support

| Domain | Status |
|--------|--------|
| K      | Full implementation |
| Q      | Stubbed (returns ERR_DOMAIN_NOT_AVAILABLE) |
| Φ      | Stubbed (returns ERR_DOMAIN_NOT_AVAILABLE) |

## Error Codes

- 0: Success
- 1-99: Module-specific errors
- 100: ERR_DOMAIN_NOT_AVAILABLE (Q/Φ domains)

## Dependencies

- dustlib (../dustlib)
- dustlib_k (../dustlib_k)
- xdv_runtime (../xdv-runtime)
- xdv_xdvfs (../xdv-xdvfs)

## Building

This project uses the DPL build system. Ensure dependencies are available in sibling directories.

## Testing

Each module has corresponding test files. Run tests to verify functionality.

## Version

0.2.0
