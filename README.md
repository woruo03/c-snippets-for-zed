# C Snippets for Zed

## Installation

1. Clone this repo:

```shell
git clone https://github.com/woruo03/c-snippets-for-zed
```

2. Go to the Extensions menu in the Zed IDE
3. Click "Install Dev Extension"
4. Select the folder you cloned

## Available Snippets

### Program Structure

| Prefix | Description |
|--------|-------------|
| `main` | `main(int argc, char *argv[])` with return |
| `mains` | Simple `main(void)` with return |

### Preprocessor

| Prefix | Description |
|--------|-------------|
| `include` | `#include <...>` |
| `incs` | `#include <...>` with placeholder |
| `incl` | `#include "..."` local header |
| `guard` | `#ifndef` / `#define` / `#endif` header guard (linked placeholders) |
| `once` | `#pragma once` header guard |
| `def` | `#define NAME value` constant |
| `defm` | `#define NAME(args) (body)` function-like macro |
| `ifdef` | `#ifdef ... #endif` conditional block (linked placeholders) |
| `arrsize` | `ARRAY_SIZE(arr)` macro — element count of a fixed array |
| `minmax` | `MIN(a, b)` and `MAX(a, b)` macros |

### Control Flow

| Prefix | Description |
|--------|-------------|
| `if` | `if` statement |
| `ifelse` | `if`-`else` block |
| `for` | Indexed `for` loop (loop variable is a linked placeholder) |
| `forr` | Reverse indexed `for` loop |
| `while` | `while` loop |
| `dowhile` | `do`-`while` loop |
| `switch` | `switch` statement with `default` |
| `case` | Single `case` label with `break` |

### Functions

| Prefix | Description |
|--------|-------------|
| `fn` | C function definition |
| `sfn` | `static` function definition |
| `proto` | Function prototype declaration |
| `fnptr` | `typedef` for a function pointer type |

### Types

| Prefix | Description |
|--------|-------------|
| `struct` | `typedef struct` definition (tag and typedef name linked) |
| `enum` | `typedef enum` definition |
| `union` | `typedef union` definition |

### Memory

| Prefix | Description |
|--------|-------------|
| `malloc` | `malloc` with NULL check and `free` |
| `calloc` | `calloc` (zero-initialized) with NULL check and `free` |
| `realloc` | Safe `realloc` via temp pointer — avoids leak on failure |
| `memset` | `memset` — fill memory with a constant byte |
| `memcpy` | `memcpy` — copy a memory region |

### I/O

| Prefix | Description |
|--------|-------------|
| `printf` | `printf` to stdout |
| `eprintf` | `fprintf(stderr, ...)` for error output |
| `scanf` | `scanf` from stdin |
| `snprintf` | Size-bounded `snprintf` into a buffer |
| `perror` | `perror` — system error message via `errno` |
| `fopen` | `fopen` / `fclose` with NULL check and `perror` |

### Patterns & Utilities

| Prefix | Description |
|--------|-------------|
| `nullchk` | NULL pointer check with error branch |
| `assert` | `assert(condition)` (requires `<assert.h>`) |
| `goto` | `goto`-based cleanup / error-handling pattern |
| `strtol` | `strtol` string-to-long with full error detection |

## Recommend

### Problem

When expanding a snippet in Zed, typing inside a placeholder (like `$1`) opens
the completion popup (`showing_completions`). At this point, pressing `Tab`
triggers code completion instead of moving to the next snippet tabstop (`$2`),
breaking the flow. Standard `Ctrl+J` also defaults to toggling the bottom dock.

### Solution

Add the following rule to `~/.config/zed/keymap.json` to allow `Ctrl+J` and
`Ctrl+K` to bypass completion popups and jump between snippet placeholders
seamlessly:

```json
[
    {
        "context": "Editor",
        "bindings": {
            "ctrl-j": "editor::NextSnippetTabstop",
            "ctrl-k": "editor::PreviousSnippetTabstop"
        }
    }
]
```
