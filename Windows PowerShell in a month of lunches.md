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
* PSDrive providers can be added into the shell, so that the shell can learn to see other forms of storage. For example, if you install the SQL Server 2008 administrative tools on your computer, you’ll gain the ability to map a SQL: drive to SQL Server databases. It’s pretty cool, and you can use most of the same commands—Dir, Cd, and so forth—within any PSDrive that you map.
* here’s a way to run a command that will ensure its parameters work properly:
$exe = "C:\Vmware\vcbMounter.exe"
$host = "server"
$user = "joe"
$password = "password"
$machine = "somepc"
$location = "somelocation"
$backupType = "incremental"
& $exe -h $host -u $user -p $password -s "name:$machine" -r $location -t
$backupType

* PowerShell doesn’t actually contain a Dir command, or a Type command, or any of those other commands. Instead, PowerShell defines those as aliases to some of PowerShell’s native cmdlets. Aliases are just nicknames for cmdlet names. This way most of the unix commands are alaises to the PowerShell cmdlets. So, For Unix users, it wont be a disappointment. However, this ends with Aliases. the parameter calling will be different between unix shell and Powershell.
* Parameter names are used consistently throughout the shell. If one cmdlet has a -computerName parameter, which is used for specifying a computer name, then most cmdlets that need a computer name will also have a -computerName parameter.
* PowerShell isn’t normally picky about upper- and lowercase, meaning that dir and DIR are the same, as are -RECURSE and -recurse and -Recurse. But the shell sure is picky about those spaces and dashes.
* get-content cmdlet to dispay the content in a file.
* Rename-Item cmdlet for renaming any item. 

##Chapter 3: Using Help System##
* 

