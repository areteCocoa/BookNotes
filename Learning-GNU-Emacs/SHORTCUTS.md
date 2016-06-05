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