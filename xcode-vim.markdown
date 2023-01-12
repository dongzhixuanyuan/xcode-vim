# Xcode VIM
Learning VIM in Xcode comes with its own set of challenges and limitations, but there is enough there for you to give your mousing hand a break and master the keyboard.

A limited set of commands are available in Xcode, and this document attempts help ease the learning curve of using VIM in Xcode by providing a handy reference as well as what I find works for me in practice.

**NOTE:**
Commands are case-sensitive. A command of `N` means pressing `shift + n` on the keyboard.

*This document is a work in progress! Leave a comment if you would like to see a change.*

--- 
### Normal Mode Commands
#### Basic Navigation
| Vim Input | Xcode Standard | Action |
| :---: | :---: | :--- |
| h | ← | move left |
| l | → | move right |
| k | ↑ | move up |
| j | ↓ | move down |
| {N}j | - | move down N lines |
| {N}k | - | move up N lines |
| 0 | ↖ | move to first character in line. e.g. "move to column zero" |
| $ | ↘ | move to last character in line |
| ^ | ⌘← | move to first non-whitespace character in line |
| g0 | ⌘←← | <ins>g</ins>oto before first non-whitespace character in line |
| g_ | ⌘→ | <ins>g</ins>oto to last printed character in line |
| gg | ⌘↑ | <ins>g</ins>oto to first line in file |
| G | ⌘↓ | <ins>g</ins>oto to last line in file |
| % | - | move to matching character in pair, e.g. `{}`, `()` | 
| { | - | jump to next paragraph above |
| } | - | jump to next paragraph below |

#### Word Navigation
| Vim Input | Xcode Standard | Action |
| :---: | :---: | :--- |
| w | ⇧→ | jump forward to start of <ins>w</ins>ord |
| W | ⌃→ | jump forward to start of <ins>W</ins>ord, ignoring punctuation |
| e | - | jump forward to <ins>e</ins>nd of word |
| E | - | jump forward to <ins>E</ins>nd of word, ignoring punctuation |
| b | ⇧← | jump <ins>b</ins>ackward to start of word |
| B | - | jump <ins>B</ins>ackward to start of word, ignoring punctuation |

#### Special keys in Insert Mode
| Vim Input | Xcode Standard | Action |
| :---: | :---: | :--- |
|cmd-left|-|jump backword to where first not-blank character.|
|alt-left|-|jump backward to start of word.|
|cmd-right|-|jump forward to the end of current Line.|
|alt-right|-|jump forward to end of word.|
| ^h |-| Delete previous character from the character position.|
| ^d |-|Delete character at current cursor position.|
| ^k |-| Delete line where the cursor at.|
| ^p |-| move up|
| ^n |-| move down|
| ^b |-| move left|
| ^f |-| move right|
| ^e |-| move to last character in line.|
| ^a |-| move to first character in line.|


#### Scrolling the Viewport
Actions that scroll the code viewport without moving the cursor.
| Vim Input | Action |
| :---: | :--- |
| zz | scroll viewport to center on current line |
| zt | scroll line to top of viewport |
| zb | scroll line to bottom of viewport |
| z⏎ | position viewport so the current line is at the top. e.g. Show me what is below this line. |
| z. | position viewport so the current line is in the middle. e.g. Center on this line. |
| z- | position viewport so the current line is at the bottom. e.g. Show me what is above this line |
| H | move cursor to top of viewport |
| M | move cursor to middle of viewport |
| L | move cursor to bottom of viewport |

#### Jumping the Cursor
Actions that scroll the code viewport by moving the cursor.

'^' denotes Control Key.
| Vim Input | Action |
| :---: | :--- |
| ^e | scroll one line down |
| ^y | scroll one line up |
| ^d | scroll one half page <ins>d</ins>own |
| ^u | scroll one half page <ins>u</ins>p |
| ^f | scroll one page <ins>f</ins>orward |
| ^b | scroll one page <ins>b</ins>ack |

#### Cut, Copy, and Paste
Vim uses `yank` as a naming convention analgous to the `copy` clipboard command. The delete command is analogous to the `cut` command as it places the deleted content into a buffer that can be pasted.

| Vim Input | Action |
| :---: | :--- |
| yy | Copies the current line and places it into a buffer that can be used with `p` to paste. |
| y | Copies characters from the current cursor position. |
| Y | Copies the entire line at the cursor position. |
| p | Pastes characters copied from `y` or `d` commands at the current cursor position. |
| P | Pastes characters copied from `y` or `d` commands before the current cursor position. |
| J | Join the next line to current line,and insert one space between them.|

#### Editing Text
| Vim Input | Action |
| :---: | :--- |
| r | Replaces the character at the cursor position with the next input character. |
| S | Clears all text on the current line and enters insert mode. |

#### Deleting Text
| Vim Input | Xcode Standard | Action |
| :---: | :---: | :--- |
| d`P` | N/A | Pressing `d` begins a delete that matches a selection based on the next position command of `P`. For example, `dw` deletes all characters jumping forward to the start of the next word. Usable for most all cursor position commands such as `w`, `e`, `b`, `B`. |
| dd | ⌘D | Deletes the current line. |
| d`N` | N/A | Deletes `N` number of lines where `N` from the cursor position. e.g.: `d5` deletes the next 5 lines. |
| D | – | Deletes characters to the end of the line from the current cursor position. |
| x | – | Deletes the character at the current cursor position. |
| X | Backspace | Deletes the previous character from the character position. | 
|d`j`|-|Delete next line|
|d`k`|-|Delete previous line|
|J|-|Delete the blank between two lines.|


#### Navigating Characters in Line
| Vim Input | Action |
| :---: | :--- |
| f{char} | move to next character ahead of cursor in line | 
| F{char} | move previous character behind cursor in line |
| t{char} | move behind next character ahead of cursor in line | 
| T{char} | move ahead of next character behind cursor in line |
| ; | repeat previous f, t, F or T movement |
| , | repeat previous f, t, F or T movement, backwards |

#### Selecting Text
| Vim Input | Action |
| :---: | :--- |
| v`P` | Selects text up to the next position, `P`. e.g. `ve` selects from the cursor to the end of the word. | 
| V | Selects the current line. Subsequent position commands will extend the selection. Very handy for beginning multi-line selections and edits. |

#### Indentation
`NOTE:` Xcode will drop the current selection after the action is performed, which makes these commands not as good as a standard Xcode indentation command with ⌘+(`[` or `]`) which retains the selection. Its really only useful for making the indent once, unlike the built-in action which can indent multiple times.
| Vim Input | Action |
| :---: | :--- |
| << | Indent line(s) left |
| >> | Indent line(s) right |

#### Misc. Handy Actions
| Vim Input | Action |
| :---: | :--- |
| ~ | Changes the case of the character at the cursor position and moves the cursor to the next character. |
|{visual} ~ |Change the case of the highlighted text.|

#### Undo and Redo
| Vim Input | Xcode Standard | Action |
| :---: | :---: | :--- |
| u | ⌘z | Undo last action. |
| `N`u | – | Undo last `N` number of actions. e.g. `3u` undo 3 times. |
| ^r | ⌘Z | Redo last action |

#### Search
| Vim Input | Xcode Standard | Action |
| :---: | :---: | :--- |
| / | ⌘f | Begin a forward text search. |
| ? | ⌘G | Begin a backward text search. |
| n | ⌘g | Move to next search result. |
| N | ⌘G | Move to previous search result. |

#### Changing Modes
| Vim Input | Action |
| :---: | :--- |
| i | "Insert here". Enter visual mode at the start of the current cursor position. |
| a | "Append here". Enter visual mode at the end at the current cursor position. |
| I | "Insert at start". Enter visual mode at the beginning of the line. |
| A | "Append at end". Enter visual mode at the end of the line. |

--- 
### Visual Mode Commands
#### Section 
| Vim Mode | Action |
| :---: | :--- |
| esc | exit to normal mode |


# VIM Usage in Practice
Below are tips for using and combining the commands in VIM to perform common actions.

## Very Basic Usage
Move up and down holding down `^` Control and tapping `u` and `d` (Up and Down) to move the cursor in 1/2 viewport increments.

Vertically move to the line to edit using `j/k`.

Horizontally move to where you want to edit using `e/E/w/b/B/h/l`.

Start editing text with `a/A/i/I`.

Exit insert mode with `esc` and repeat. 

## New Lines
`O` - add a new line above the cursor and enter insert mode

`o` - add a new line below the cursor and enter insert mode

## Selecting Text
`ce` - Edit from cursor to end of word and replace

`v$` - Select from cursor to end of line

## Find & Replace
Basic finding
1. `/` Start the find, enter the text to fnid and press `Enter`
2. `n` and `N` to move between the occurences found in the file

Replace
1. `vey` - Selects a word and yanks (copies) it
2. `viwp` - Selects a word and puts (pastes) the copied text


## Copy/Paste Lines
To copy 2 lines…
`2yy` - Copies 2 lines

To cut 2 lines
`2cc` - Cuts two lines

Duplicate line
`Yp` - Copies the current line and puts (pastes) it