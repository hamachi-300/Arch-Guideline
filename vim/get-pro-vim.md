# Vim Complete Guide — Professional Reference

> A complete reference for using Vim efficiently like a professional.

---

## Table of Contents

1. [Modes](#1-modes)
2. [Cursor Movement](#2-cursor-movement)
3. [Editing](#3-editing)
4. [Visual Mode](#4-visual-mode)
5. [Search & Replace](#5-search--replace)
6. [Marks & Jumps](#6-marks--jumps)
7. [Moving Lines](#7-moving-lines)
8. [File & Buffer Commands](#8-file--buffer-commands)
9. [Macros](#9-macros)
10. [Useful Tricks](#10-useful-tricks)
11. [Best Practices](#11-best-practices)

---

## 1. Modes

| Key | Mode | Purpose |
|-----|------|---------|
| _(default)_ | **Normal** | Navigate and run commands |
| `i` | **Insert** | Type and edit text |
| `v` | **Visual** | Select text |
| `:` | **Command** | Run file/editor commands |

### Entering Insert Mode

| Key | Action |
|-----|--------|
| `i` | Insert **before** cursor |
| `a` | Insert **after** cursor |
| `I` | Insert at **start** of line |
| `A` | Insert at **end** of line |
| `o` | New line **below** and insert |
| `O` | New line **above** and insert |

> **Always press `Esc` to return to Normal mode.**

---

## 2. Cursor Movement

### Basic (Never use arrow keys!)

```
h  ←      j  ↓      k  ↑      l  →
```

### Word Movement

| Key | Action |
|-----|--------|
| `w` | Next word start |
| `b` | Previous word start |
| `e` | End of current word |
| `W` `B` `E` | Same but ignore punctuation |

### Line Movement

| Key | Action |
|-----|--------|
| `0` | Start of line |
| `^` | First non-blank character |
| `$` | End of line |
| `gg` | Top of file |
| `G` | Bottom of file |
| `50G` | Jump to line 50 |

### Screen Movement

| Key | Action |
|-----|--------|
| `Ctrl+d` | Half page down |
| `Ctrl+u` | Half page up |
| `Ctrl+f` | Full page down |
| `Ctrl+b` | Full page up |
| `zz` | Center screen on cursor |
| `H` `M` `L` | Cursor to top / middle / bottom of screen |

### Search to Move _(Most Powerful)_

| Key | Action |
|-----|--------|
| `/word` | Search forward |
| `?word` | Search backward |
| `n` / `N` | Next / previous match |
| `f{char}` | Jump TO next char on line |
| `t{char}` | Jump BEFORE next char on line |
| `;` / `,` | Repeat f/t forward / backward |
| `*` | Search word under cursor |
| `%` | Jump to matching bracket |

---

## 3. Editing

### Deleting

| Key | Action |
|-----|--------|
| `x` | Delete character under cursor |
| `X` | Delete character before cursor |
| `dd` | Delete (cut) entire line |
| `3dd` | Delete 3 lines |
| `dw` | Delete word |
| `d$` | Delete to end of line |
| `dG` | Delete to end of file |
| `dgg` | Delete to start of file |
| `di"` | Delete inside quotes |
| `di(` | Delete inside parentheses |

### Changing _(delete + go to insert mode)_

| Key | Action |
|-----|--------|
| `cc` | Change entire line |
| `cw` | Change word |
| `c$` | Change to end of line |
| `ci"` | Change inside quotes |
| `ci(` | Change inside parentheses |
| `r{char}` | Replace single character |

### Copy & Paste

| Key | Action |
|-----|--------|
| `yy` | Yank (copy) line |
| `3yy` | Yank 3 lines |
| `yw` | Yank word |
| `yG` | Yank to end of file |
| `gg` then `yG` | Yank entire file |
| `:%y` | Yank entire file (command) |
| `p` | Paste below / after cursor |
| `P` | Paste above / before cursor |
| `ddp` | Swap line with line below |
| `yyp` | Duplicate current line |

### Undo & Redo

| Key | Action |
|-----|--------|
| `u` | Undo |
| `Ctrl+r` | Redo |

### Indenting

| Key | Action |
|-----|--------|
| `>>` | Indent right |
| `<<` | Indent left |
| `==` | Auto-indent line |
| `gg=G` | Auto-indent entire file |

---

## 4. Visual Mode

| Key | Action |
|-----|--------|
| `v` | Character select |
| `V` | Line select |
| `Ctrl+v` | Block / column select |
| `d` | Cut selected |
| `y` | Copy selected |
| `>` / `<` | Indent / un-indent |
| `~` | Toggle case |

---

## 5. Search & Replace

```vim
/pattern          " search forward
?pattern          " search backward
n / N             " next / previous match
:noh              " clear search highlight
```

### Replace Commands

| Command | Action |
|---------|--------|
| `:s/old/new/` | Replace first on current line |
| `:s/old/new/g` | Replace all on current line |
| `:%s/old/new/g` | Replace all in file |
| `:%s/old/new/gc` | Replace all, confirm each |
| `:5,10s/old/new/g` | Replace in lines 5–10 |

---

## 6. Marks & Jumps

| Key | Action |
|-----|--------|
| `ma` | Set mark 'a' |
| `'a` | Jump to line of mark 'a' |
| `` `a `` | Jump to exact position of mark 'a' |
| `''` | Jump back to previous position |
| `Ctrl+o` | Jump to older position |
| `Ctrl+i` | Jump to newer position |
| `:marks` | List all marks |

---

## 7. Moving Lines

```vim
:m +1         " move current line down 1
:m -2         " move current line up 1
:m 0          " move to top of file
:m $          " move to bottom of file
:5,10m 20     " move lines 5–10 to after line 20
```

---

## 8. File & Buffer Commands

| Command | Action |
|---------|--------|
| `:w` | Save file |
| `:w filename` | Save as |
| `:q` | Quit |
| `:q!` | Quit without saving |
| `:wq` or `:x` | Save and quit |
| `ZZ` | Save and quit (normal mode) |
| `ZQ` | Quit without saving (normal mode) |
| `:e filename` | Open file |
| `:split file` | Horizontal split |
| `:vsplit file` | Vertical split |
| `Ctrl+w w` | Switch between splits |

---

## 9. Macros

```
qa        → start recording macro into register 'a'
q         → stop recording
@a        → play macro 'a'
@@        → repeat last macro
10@a      → run macro 'a' 10 times
```

> Use macros for any repetitive multi-step edits.

---

## 10. Useful Tricks

| Key | Action |
|-----|--------|
| `.` | **Repeat last change** _(most powerful!)_ |
| `~` | Toggle case of character |
| `guw` | Lowercase word |
| `gUw` | Uppercase word |
| `J` | Join line below to current |
| `Ctrl+a` | Increment number under cursor |
| `Ctrl+x` | Decrement number under cursor |
| `:set number` | Show line numbers |
| `:set paste` | Paste mode (avoids indent issues) |

---

## 11. Best Practices

### Think Like a Pro

1. **Never use arrow keys** — use `h` `j` `k` `l`
2. **Think in motions** — `w` `b` `e` `f` `t` `/` `?`
3. **Use `.`** to repeat last action — saves many keystrokes
4. **Use macros** for repetitive multi-step edits
5. **Use marks** to jump between distant locations
6. **Prefer** `ci"` `cw` `cc` over going into insert and backspacing
7. **Use** `:%s` for find & replace instead of editing manually
8. **Use** `gg=G` to auto-fix indentation of whole file
9. **Use** `Ctrl+o` / `Ctrl+i` to navigate jump history
10. **Combine numbers** with commands: `5j` `3dd` `10@a`

---

### Quick Cheat Sheet

| Task | Command |
|------|---------|
| Swap line with line below | `ddp` |
| Duplicate current line | `yyp` |
| Copy entire file | `gg` then `yG` |
| Delete entire file | `gg` then `dG` |
| Replace entire file with clipboard | `gg` → `dG` → `p` |
| Auto-indent entire file | `gg=G` |
| Search and replace all | `:%s/old/new/g` |
| Repeat last change | `.` |

---

> **Golden Rule:** The goal is always the fewest keystrokes to get the job done.
> Master motions and operators — everything else follows.
