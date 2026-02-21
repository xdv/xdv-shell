# Runtime Flow

This document describes current `xdv-shell` behavior.

## Entry and Init

- `shell_main.ds`
  - `main()` calls `init()`, then `run()`.
  - `init()` emits shell initialize status and registers default builtin IDs.
  - `run()` emits banner + prompt mode and enters loop.

## Boot-Bridge Path

- `shell_bridge.ds`
  - `shell_bridge_init()` emits bridge status and calls `shell_boot_units_prepare()`.
  - `shell_bridge_launch()` emits launch status and emits banner/catalog/prompt via boot units.
- `shell_boot_units.ds`
  - emits boot-safe shell lines used in xdv-os bare-metal integration path.

## Interactive Loop

- `shell_loop.ds`
  - `run_loop()` drives bounded cycle recursion.
  - each cycle:
    1. renders prompt (`render_prompt()`),
    2. reads command code (`read_command_code()`),
    3. tokenizes/parses command ID,
    4. dispatches execution (`execute(...)`),
    5. repeats until stop condition (`exit` command path).

## Dispatch

- `shell_executor.ds`
  - `execute()` routes known IDs to `run_builtin(...)`.
  - unknown IDs route to process spawn path (`spawn_process(...)`).
  - `edx` routes through spawn process path.

## Note on Current Scope

Current lexer/parser/completion modules provide shell structure and normalized
command-ID handling; parts of their behavior are model-level rather than full
argv/AST shell semantics.
