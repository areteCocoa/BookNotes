# Chapter 2: Editing

- Refill mode keeps paragraphs neat as you type them
  - Enable/disable with M-x refill-mode Enter
- Auto fill mode formats paragraphs as you type them but NOT edit them
  - Enable/disable with M-x auto-fill-mode Enter
- Undo: C-_ or C-x u

## Moving the cursor
- (Commands in shortcuts index)
### Other ways to Move the Cursor
- (Commands also in shortcuts index)

### Moving a Screen (or More) at a Time
- C-v or PgDown for down a page
- M-v or PgUp for up a page
- M-> End of buffer
- M-< beginning of buffer
- M-x goto-line Enter n Enter where n is the line in the file
- M-x goto-char Enter n Enter where n is the char in the file

### Repeating Commands
- M-n before a command to repeat the command n times
- C-u n before a command to repeat n times
  - Or C-u before a command to repeat 4 times
  - Can chain like C-u C-u for 16 times

### Centering the Display
- C-l recenters the display

### Emacs Commands and Your Keyboard
- Use the C- commands because PgUp may not work on remote machines