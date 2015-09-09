#Windows PowerShell in a month of lunches#

*PAGE 12*
##Chapter 01##
* On a U.S. keyboard, the backtick (or grave accent) is usually near the upper left, under the Escape key, on the same key as the tilde character (~). When you see the backtick in a code listing, type it exactly as is. Furthermore, when it appears at the end of a line—as in the preceding example—make sure that it’s the very last character on that line. If you allow any spaces or tabs to appear after it, the backtick won’t work correctly, and neither will the code example.
* Most of the main content chapters include a short lab for you to complete. You’ll be given instructions, and perhaps a hint or two, but you won’t find any answers in the book. The answers are online, at MoreLunches.com, but try your best to complete each lab without looking at the online answers
* Change the font to Lucidia. The default font makes is difficult to identify few characters.
* you can also use ISE version of Power shell that has 3 windows in its layout. Ignore the one which is a file "untitled.ps1*"

##Chapter 02##
* DIR, DIR | MORE for directory.
* Technically, Cd.. is incorrect because it doesn’t include a space, and Cd .. is correct. In reality, PowerShell v2 catches the Cd.. error and will do the right thing (move up one level in the directory hierarchy) because that’s such a commonly typed command, but that’s the only exception that PowerShell will catch that way for you. It won’t catch something like Dir..
* Dir > file.txt will create the new file (or use an existing one) and dump data from Dir Command into the file.txt (Always overwrites). Dir >> file.txt will Append the data.
* The shell always starts with the same PSDrives mapped. You can run the command Get-PSDrive to see them. This shows that shell is not all about just file system and there are things like Registry, Environment variables, Aliases that we can access through Power shell. Remember that all these are PSDrives and should be given a colon at the end to access them. Example: CD HKCU:
* 
