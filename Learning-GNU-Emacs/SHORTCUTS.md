# Shortcuts
This file contains a list of all the shortcuts in the book as well as what they
do and what chapter they are from.

Commands are listed as what it does, the shortcut and then the long command name. A
short note on the command may be appended.

# Chapter 1: Emacs Basics

Open a file
     C-x C-f 'filename'
     find-file

Open a file based on this filename
     C-x C-v (current-filename)
     find-alternate-file
     Similar to find-file but inserts the currently opened file's name

Insert a file
     C-x i 'filename'
     insert-file
     Inserts the file at the position of the cursor
     
Save buffer
     C-x C-s
     save-buffer
     Saves the buffer to the file name

Write a file (Save as)
     C-x C-w 'filename'
     write-file
     Saves the current buffer to a new file. Not entering a filename just saves (not save as)
     
Exit Emacs and Save
     C-x C-c
     save-buffers-kill-emacs
     Will ask to save changes and exits emacs
     
Enter Help Menu
     C-h
     help-command
     
Start tutorial
     C-h t
     help-with-tutorial
     
Get information about keystroke
    C-h k (keystroke)
    describe-key
    Gives a page of information about the keystroke
    
Get information about function
    C-h f (functionname)
    describe-function
    Gives a page of information about the function

Browse information reader
    C-h i
    info-goto-emacs-command-node
    Starts the info documentation reader

# Chapter 2
## Cursor Movement Commands
Forward Char
    C-f
    forward-char
    Moves forward one character

Backward Char
    C-b
    backward-char
    Moves backward one character

Previous line
    C-p
    previous-line

Next Line
    C-n
    next-line

Forward Word
    M-f
    forward-word

Backward Word
    M-b
    backward-word

Beginning of Line
    C-a
    beginning-of-line

End of Line
    C-e
    end-of-line

Forward sentence
    M-e
    forward-sentence

Backward sentence
    M-a
    backward-sentence

Forward paragraph
    M-}
    forward-paragraph

Backward paragraph
    M-{
    backward-paragraph

Scroll up
    C-v
    scroll-up

Scroll down
    M-v
    scroll-down

Forward Page
    C-x ]
    forward-page

Backward Page
    C-x [
    backward-page

Beginning of buffer
    M-<
    beginning-of-buffer

End of buffer
    M->
    end-of-buffer

Goto line
    (none)
    goto-line

Goto character
    (none)
    goto-char

Recenter
    C-l
    recenter

Repeat command n times
    M-(number of times)
    digit-argument

Repeat command n times or default 4
    C-u (number of times)
    universal-argument

## Deleting Text Commands
Delete Character under cursor
    C-d
    delete-char

Delete previous (backward) character
    Del
    delete-backward-char

Kill Word
    M-d
    kill-word

Backward Kill Word
    M-Del
    backward-kill-word

Kill Line
    C-k
    kill-line

Kill Sentence
    M-k
    kill-sentence

Kill Previous Sentence
    M-Del
    backward-kill-sentence

Yank
    C-y
    yank

Kill a Marked Region
    C-w
    kill-region

Kill a Paragraph
    (none)
    kill-paragraph

Kill Previous Paragraph
    (none)
    backward-kill-paragraph

## Commands for Working with Regions
Set Mark Command
    C-@ or C-Space
    set-mark-command

Exchange Point and Mark
    C-x C-x
    exchange-point-and-mark

Kill Region
    C-w
    kill-region

Yank
    C-y
    yank

Kill Ring Save (Copy)
    M-w
    kill-ring-save

Mark Paragraph
    M-h
    mark-paragraph

Mark page
    C-x C-p
    mark-page

Mark Entire Buffer
    C-x h
    mark-whole-buffer

Cycle Kill Ring Yank
    M-y
    yank-pop

## Editing Tricks and Shortcuts
Transpose Characters
    C-t
    transpose-chars

Transpose Words
    M-t
    transpose-words

Transpose Lines
    C-x C-t
    transpose-lines

Transpose Sentences
    (none)
    transpose-sentences

Transpose Paragraphs
    (none)
    transpose-paragraphs

## Changing Capitalization
Capitalize the first letter of a word
    M-c
    capitalize-word

Uppercase word after cursor
    M-u
    upcase-word

Downcase word
    M-l
    downcase-word

Capitalize the Previous Word
    Meta- (meta - "-") M-c
    negative-argument; capitalize-word

Uppercase the previous word
    Meta- M-u
    negative-argument; upcase-word

Downcase the previous word
    Meta- M-l
    negative-argument; downcase-word

## Stopping and Undoing Commands
Abort Current Command
    C-g
    keyboard-quit

Advertised Undo
    C-x u
    advertised-undo
    No real difference between this and undo

Undo
    C-_
    undo

Revert buffer to the saved file
    (none)
    revert-buffer

# Chapter 3: Search and Replace
Incremental Search Forward
    C-s
    isearch-forward
    Enter to exit the search, C-g to cancel and Del to remove a char from the search string

Incremental Search Backward
    C-r
    isearch-backward

Incremental Search with Word On Cursor
    C-s C-w
    isearch-yank-word

Incremental Search Line of Cursor
    C-s C-y
    isearch-yank-line
    Uses the cursor to the end of line for search text

Incremental Search with Kill Ring Yank
    C-s M-y
    isearch-yank-kill

Repeat Previous Search
    C-s C-s
    isearch-repeat-forward

Repeat Previous Search Backward
    C-r C-r

## Simple Searches
Simple Search
    C-s Enter
    ?

Simple Search Backward
    C-r Enter