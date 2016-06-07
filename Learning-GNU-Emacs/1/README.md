# Chapter 1: Emacs Basics
Pages 1-20

- Emacs is much more that just an editor

## Understanding Files and Buffers
- You don't really edit files in emacs but instead it pastes it to a buffer and you save that

## A Word About Modes
- Modes are for different modes of editing
- There are modes for different styles of text editing and modes for specific languages
  - These are major modes
  - emacs tries to put you in the correct mode based on the end of the filename (.c, .java, etc.)
- There are also minor modes that set specific behavior within major modes

## Starting Emacs
- Type emacs in the terminal or click on the icon

## About the Emacs Display
- Cursor/Point: the block indicating where you are in the text

### The Toolbar
- Only for GUI Emacs
- Icons provide basic functionality

### The Menus
- Use the menus on top of emacs for other basic functionality

### The Mode Line
- Mode Line: Second-to-last line that contains a lot of information about how emacs is currently
running
- Contains:
  - The coding system emacs is using for the file, but you'll usually just see "--:"
  - Two asterisks "**" to show you have edited the buffer
  - The name of the buffer
  - Where you are in the file
    - L5 -> Line 5
    - % of file you are through
  - Major mode

### The Minibuffer
- Used to echo commands, control emacs, display error messages, etc.

## Emacs Commands
- Commands are names of Lisp routines but also have short sequence of keystrokes (binding)
- Ctrl used for the most common commands
- Meta used for slightly less common commands
- Ctrl-X (something) used for other common commands
- Ctrl-C (something) for specialized commands
- Meta-X long-command-name (enter) for everything else

## Opening a File
- C-x C-f filename to open a file
- C-x C-v to open an alternative file
- Features Tab completion

### Inserting and Appending Files
- C-x C-i to insert a file

### How Emacs Chooses a Default Directory
- Emacs chooses based on what directory it was opened in

## Saving Files
- C-x C-s save a file
- C-x C-w write a file (save as)

## Leaving Emacs
- C-x C-c to quit emacs

## Getting Help
- C-h to get help
  - C-h t start tutorial
- C-h k [key-command] describes the key-command
  - To make *Help* buffer disappear, press C-x 1

### The Help Menu
- Can also use the help menu GUI

[END CHAPTER]