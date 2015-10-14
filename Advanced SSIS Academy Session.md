#Day 1#
* ispak - what is this extension?
* Bulk Insert Task is Very Quick (bcp command). Only catch here is it will not validate the source data and simply Dumps data from source to Target. 
* WMI Task - Powerfull Task to get to know Windows OS/Harware related information. WMI Data reader task and WMI Event Watcher task. 
* Execute Process Task Just like Post Success Command in INformatica . We can run a Batch file with parameters. 
* Execute Package Task can run pacakges stored in MSDB OR those pacakges which are available in File System. 
* If there is source that we dont have a driver for, We can do it ourself using SDK provided as a part of SSIS. -- Check this. Even we are not able to do it, we can get it from third party vendors. 
* CDC source is newly added in 2012 in SSIS. CDC feauture is available in SQL server and Oracle. We also need CLR for using this task.
*   Raw files are propriety Files of Microsoft. We cannot open thourgh any other tool. We use Raw files to compress the files. 
*   'Packet Size' Option in OLEDB Connection Manager. --Check.  It is available in 'ALL' tab once you double click the connection.
* SQL server destination will fasten up the DataLoad by 30% since it uses same code page?? Only drawback of SQL Server Destination is that SSIS and Target DB should be on the same server.
* 'Partition Processing' Destination. Is it same as Informatica Session partitions? - Check this. Even we create Partitions, important thing is we need to have enough COREs (Processors?) on the server to run the partitions parallelly. -- check this as well.
* If you dont want to use SORT even when you have Flat File as a source, You can load Flat file to a STG table and then use ORDER BY Clause in OLEDB Source.
* THere is a RESET COLUMNS option in flatfile Connection Manager. This should be used if you are doing any changes to the Source file. There is also a SUGGEST TYPES option in ADVANCED tab of file Connection. BY using it, SSIS Will Suggest us which type or length should be used. 
