#Windows PowerShell in a month of lunches#

*PAGE 33*
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
* Windows PowerShell provides a cmdlet, Get-Help, that accesses the help system. You may see examples of people using the Help keyword instead, or even the Man keyword (which comes from Unix and means “Manual”). Man and Help aren’t aliases at  all—they are functions, which are basically wrappers around the core Get-Help cmdlet. Help works much like the base Get-Help, but it pipes the help output to More so that you get a nice paged view instead of seeing all the help fly by at once.
* By the way, sometimes that paginated display gets annoying—you’ve got the information you need, but it still wants you to hit the spacebar to display the remaining information. If that’s ever the case, press Ctrl-C to cancel the command and return to the shell prompt. Within the shell’s console window, Ctrl-C always means “break” rather than “copy to the clipboard”. In the more graphically oriented Windows Power- Shell ISE, however, Ctrl-C does in fact copy to the clipboard. There’s a red “stop” button in the toolbar that will stop a running command.
* Like most commands, Get-Help (and therefore Help) has several parameters. One of those—perhaps the most important one—is -Name. It’s a positional parameter, so you don’t have to type -Name and can simply provide the name you’re looking for. This parameter specifies the name of the help topic you’d like to access, and it accepts wildcards. This ability to handle wildcards is what makes the help system useful for discovering commands.
* PowerShell offers: tab completion. This enables you to type a portion of a command name, and then press Tab. The shell will complete what you’ve typed with the closest match; you can continue pressing Tab to cycle through alternative matches.
* run the cmdlet help Get-Eventlog. Notice that the command is listed twice. so it accepts two sets of parameters. you should follow any one set. You cannot combine parameters from both sets and run the command. Sometimes it’s possible to run a command with only parameters that are shared between multiple sets. In those cases, the shell will usually select the first-listed parameter set.
* You’ll notice that, in help file,  every parameter set for every PowerShell cmdlet ends with [<CommonParameters>]. This refers to a set of eight parameters that are available on every single cmdlet, no matter how you’re using that cmdlet
* optional parameters have [] boxed for parameter name and value combined, in the help file. Example: [-ComputerName <string[]>]. Mandatory parameter do not have [] for name and value combined. Example: [-Logname] <string>. In this example, if <string> is not present, then Logname becomes a parameter which does not need any value, Just like the -Recurse parameter in DIR. This type of parameters all called SWITCH parameters.
* A parameter is said to be a positional Parameter when the parameter name in help file is explicitly boxed with []. If a parameter is positional, then while running the cmdlet, we can directly provide the value of the parameter in that position rather than having to provide the parameter name and adding a value. Examples: [-LogName] <string> is a mandatory Positional paramater. [[-InstanceId] <Int64[]>] is an optional positional parameter. [-Message <string>] is an optional non-positional parameter. if i have to give -message value in the commang, the i need to mention the -message parameter (atleast a part of it till it becomes obvious to the shell that its a message parameter. In case of get-eventlog, just providing -m is enough since there are no other parameters starting with 'm') explicitly before providing the value. SWITCH parameters which also have [] on thier name, but they are never positional. Also, SWITCHES are always optional.
* If you call all parameters with names, then even positional parameters can be called at positions not assigned to them. That is acceptable. Only when you dont explicitly mention the parameter name, then the positional parameters come into picture. 
* if you need more details of a command, we can use the common parameter -full. example: get-eventlog -full. This will tell you which parameters are positional, mandatory etc and also let you know which parameters accept widl card entries. 
* [[-InstanceId] <Int64[]>], here, the [] after the datatype Int64 means that it can accept an array, collection or list of integers. PowerShell treats all comma-separated lists as arrays of values 
* while using array, we have to give quotes to each value and not for the entire string. Example: Get-EventLog Security -computer 'Server-R2','Files02' is correct. Get-EventLog Security -computer 'Server-R2,Files01' is logically wrong since the cmdlet will be looking for computer named Server-R2,Files01 which is not what we aimed for. We can also pass arrays by saving the values in a file (one in each line) and calling and reading the file from parameter value by using (). Example: Get-EventLog Application -computer (Get-Content names.txt) 
Here, we store the values Server-R2 and Files01 one in each line and save it as names.txt and use it as an array using ().
* 
* 

