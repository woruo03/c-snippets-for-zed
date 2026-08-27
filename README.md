# C Snippets for Zed

## Installation

1. Clone this repo:

```shell
git clone https://github.com/woruo03/c-snippets-for-zed
```

1. Go to the Extensions menu in the Zed IDE
2. Click "Install Dev Extension"
3. Select the folder you cloned

## Available Snippets

- `main` Initialize the main function with stdio
- `include` Include a C header
- `fori` Initialize an indexed for loop
- `while` Initialize a while loop
- `ifelse` Initialize an if else block
- `fn` Define a C function
- `printf` Print formatted output
- `scanf` Read formatted input
- `struct` Define a typedef struct
- `malloc` Allocate memory with malloc
- `switch` Initialize a switch statement
- `guard` Initialize a C header include guard

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
        "context": "Editor && (snippet_active || showing_completions)",
        "bindings": {
            "ctrl-j": "editor::NextSnippetTabstop",
            "ctrl-k": "editor::PreviousSnippetTabstop"
        }
    }
]
```
