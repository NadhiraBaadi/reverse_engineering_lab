# GDB Basics

## GDB Debugger Cheat Sheet (Beginner-Friendly)

> Just getting started with GDB debugging?  
This cheat sheet is made for **new C programmers, reverse engineering learners, and cybersecurity students**.  
It’s clean, beginner-friendly, and inspired by **Beej’s Guide to GDB**, rewritten from my own notes.


### Getting Help
| Command | What it does |
|---------|---------------|
| `help <command>` | Explain a GDB command |
| `apropos <keyword>` | Search for commands related to a keyword |

- Example: `help run` or `apropos breakpoint`.


###  Starting & Quitting GDB
| Command | What it does |
|---------|---------------|
| `gdb ./program` | Start with a program |
| `gdb -tui ./program` | Launch with split view (source + registers) |
| `gdb -c core ./program` | Analyze a crash dump |
| `file ./program` | Load/switch executable |
| `run arg1 arg2` | Run program with args |
| `quit` | Exit |

-> **Tip**: Use `-tui` for a text-based IDE feel.


###  Breakpoints & Watchpoints
| Command | What it does |
|---------|---------------|
| `break main` | Break at start of `main()` |
| `break 42` | Break at line 42 |
| `break file.c:15` | Break at specific file/line |
| `watch x` | Break when variable changes |
| `rwatch x` | Break when variable is read |
| `awatch x` | Break on read/write |
| `info breakpoints` | List breakpoints |
| `enable <n>` / `disable <n>` | Toggle breakpoints |
| `clear` | Clear breakpoints at location |
| `delete <n>` | Delete a specific breakpoint |



###  Running & Stepping
| Command | What it does |
|---------|---------------|
| `next` / `n` | Next line (skip functions) |
| `step` / `s` | Step *into* functions |
| `continue` / `c` | Run until next breakpoint |
| `finish` | Run until current function returns |
| `advance <loc>` | Run until location |
| `jump <loc>` | Force jump (⚠ dangerous) |
| `stepi` | Step 1 assembly instruction |
| `CTRL-C` | Pause manually |
| `RETURN` | Repeat last command |

-> Think: **`next` = overview, `step` = details.**



###  Examining Variables
| Command | What it does |
|---------|---------------|
| `print x` | Print variable |
| `display x` | Show after every step |
| `info display` | Show all displayed vars |
| `undisplay <n>` | Stop displaying var |
| `printf "x=%d", x` | Format output |



### Changing Variables While Running

| Command         | What It Does |
|-----------------|--------------|
| `set variable x = 99` | Set variable `x` to 99 |
| `set (x = 99)` | Alternate syntax — same result |
| | Useful for testing how your program reacts to different values — no recompiling! |



### Working with TUI (Text UI Mode)

| Command         | What It Does |
|-----------------|--------------|
| `info win` | Show available windows |
| `focus SRC / fs` | Focus the source window (`CMD`, `ASM`, `REG`, `next`, etc.) |
| `layout split` | View source, assembly, and command views at once |
| `layout src` | Just source code + command interface |
| `layout asm` | Assembly view on top, command on bottom |
| `layout reg` | Adds register window to your layout |
| `winheight +3 / wh +3` | Increase window height |
| `tui reg general` | Show general-purpose registers |
| `tui reg float / system` | Show floating-point / system registers |
| `tui reg next` | View the next page of registers |

-> **Tip:** TUI mode feels like a text-based IDE — try it with:  
```bash
gdb -tui yourfile
```
### Misc Tools

| Command          | What It Does |
|------------------|--------------|
| `backtrace` / `bt` | Show the call stack |
| `attach <PID>`  | Attach GDB to a running process |
| `detach`        | Detach from the attached process |
| `info registers` | Display CPU registers |
| `info all-registers` | Show extended register info |


### Core Dumps (Post-Crash Analysis)

| Command               | What It Does |
|-----------------------|--------------|
| `ulimit -c unlimited` | Allow your system to generate core files |
| `gdb -tui -c core ./program` | Load the core dump with the program |

💡 **Note:** Core dumps are like crime scenes — use GDB to figure out what went wrong.

---

### Writing a GDB Front-End (Advanced)

| Command                 | What It Does |
|-------------------------|--------------|
| `gdb --interpreter=mi` | Start GDB in machine-readable mode for tooling |

