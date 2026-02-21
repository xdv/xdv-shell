# Module Reference

## Core lifecycle

- `src/shell_main.ds`
  - shell startup, builtin registration, banner, and loop entry.
- `src/shell_loop.ds`
  - interactive prompt cycle, command decode, and stop handling.
- `src/shell_prompt.ds`
  - prompt generation and rendering (`#:`).

## Parse and completion

- `src/shell_lexer.ds`
  - token classifier and tokenize entry.
- `src/shell_parser.ds`
  - command normalization and parse routing by command IDs.
- `src/shell_completion.ds`
  - completion interface and command completion seed list.

## Executor and integration

- `src/shell_executor.ds`
  - builtin dispatch, external process spawn/join path.
- `src/shell_bridge.ds`
  - shell bridge entrypoints for xdv-os integration.
- `src/shell_boot_units.ds`
  - boot-safe emitted shell launch/unit messages.

## Builtins

- `src/shell_builtin/builtin_cd.ds`
- `src/shell_builtin/builtin_ls.ds`
- `src/shell_builtin/builtin_cat.ds`
- `src/shell_builtin/builtin_mkdir.ds`
- `src/shell_builtin/builtin_rm.ds`
- `src/shell_builtin/builtin_echo.ds`
- `src/shell_builtin/builtin_ps.ds`
- `src/shell_builtin/builtin_help.ds`

Builtin test modules are provided under `src/shell_builtin/*_tests.ds`.

## Tests

Core module tests are present in:

- `src/shell_main_tests.ds`
- `src/shell_loop_tests.ds`
- `src/shell_prompt_tests.ds`
- `src/shell_lexer_tests.ds`
- `src/shell_parser_tests.ds`
- `src/shell_executor_tests.ds`
- `src/shell_completion_tests.ds`
