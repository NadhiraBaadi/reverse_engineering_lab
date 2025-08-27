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



###  Modifying Variables
```gdb
set variable x = 99
 TUI (Text UI Mode)
Command	What it does
layout split	Source + asm + cmd
layout src	Source only
layout asm	Assembly view
layout reg	Add registers
tui reg general	General-purpose regs

Feels like a text-based IDE inside terminal.

🛠 Misc Tools

backtrace / bt → Show call stack

attach <PID> / detach → Debug a running process

info registers → Show registers

 Core Dumps
ulimit -c unlimited    # enable core files
gdb -tui -c core ./program


Think of it as post-crash forensics 🕵️.

⚡ Advanced
gdb --interpreter=mi


Run in machine-readable mode for building tools.

 About this Cheat Sheet

Compiled & rewritten by Nadhira Baadi

Inspired by Beej’s Guide to GDB

For learners in C programming, reverse engineering, and cybersecurity

Focused on hands-on debugging

 Back to Repo Overview


---

 Next step for you:  

```bash
mkdir -p tools/gdb
nano tools/gdb/README.md
