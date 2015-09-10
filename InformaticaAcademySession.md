#Academy Session on Informatica 9.0 #

##Day 1##
* Informatica is not just about Power Center. It has various tools for B2B, Data Quality, Cloud, Data Vitualization etc. This Training is just about the product 'Power Center'
* Client Server Architechture and not a Stand Alone desktop Applications. Server should be there and Client components should be installed on your machine. The client components will interact with the server.
* Informatica follows SOA (Service oriented Architechture). Which means informatica has various services to do the things it does. 
* Key Architecture Components: Domain, Node, Repository, Service Manager, Application Services.
* Domain: Collection of Services in Server and the nodes (machines on which server is installed). Domain is only logical(Not physical).
* Node: Informatica Server Can be installed in a distributed way (on Multiple Machines). So, Node is logical representation of all machines on which Informatica Server is installed. 
* Repository: Holds metadata needed For its tasks to be done. All metadata (logins, Groups, Mappings etc). Its a relational Database. This Repository should be configured on the server (As of now, informatica supports only Oracle and Sql Server as repository)
* Service Manager : An Administrative tool for Domain related things. 
* Applications Service: The Actuall services (like Model Repository Service and Data Integration Services)
* Client Components in Power Center: Informatica PC Designer, Workflow Manager, WorkFlow Monitor, Repository Manager. informatica Developer and Informatica DataTransformation are also Client componets but they are not part of Power Center.
* When informatica Server is installed across multiple Nodes, We need to define atleast one node as Gateway node(Only one of them will be Master Getway others will be Backup Getway nodes which will be called when Master is not available). The service Manager needs to run on All nodes. As soon as any request comes, Master getway node receives it and it will take care of majority of Domain operations and pass on the remaining work to Worker Nodes (Non Gateway nodes). The worker nodes perform the task asigned to them by gateway node. 'Load Balancing' comes into picture here where informatica automatically balances the load to the Worker Nodes based on the available resources with in them.  
* Grid : A logical Name given to a group of Nodes. Using Grids, We can ensure High Availability and Effective Load Balancing.
* High Availability has three options: Failover, Resiliency and Recovery. Resiliency (Tries to re-connect after waiting for certain time instead of disconnecting everthing and loose all the work that has been done). Failover (if a node fails, the work will be moved to other available node and continue the work from there). Recovery (acts like a Checkpoint in SSIS and starts from where it stopped before failure, on a restart)
* Mapping is not a Runnable entity. We need to create a workflow and session to run a mapping. 
* Informatica Repository Manager (From Developers stand point, we dont need this much). Using this We can do the Structural (Folders, Logins etc) for where Mappings will be stored etc. 
* Informatica Developer (Client Component): THis is not directly integrated with power Center. Inorder to do ETL, we need Three Client tools (Designer, WorkFlow Manager, Monitor). Informatica is coming up with one interface to do everything (Just like SSDT in Sql Server/Visual Studio??). This Informatica Developer is introduced in V9.0, eventually all Developmental Activities will be done here and all existing client tools will be decomissioned.
* We can configure more than single repository for a domain.
* In Sources, if we import from File, we must remember that we are just getting the Metadata from the file, We will not be using that file while we run the job. Also, when we are reading from a Text file, it is recommended that we define all columns as Text. otherwise, if we define a columns as a number and if there is some bad data, then informatica will skip that row. So, better define as text and later do data type conversions in Mapping.
* Two ways to create Source/Target. Import OR Create. Import will get metadata from the file/Table that we browse and pick. Create will provide option to define the MetaData manually. 
* Whether Mapping is valid or invalid, we can see in Bottom window (in Save Tab) after saving the mapping. 
* When we have source file in a mapping, the source file should be present in the informatica Server (There is an option if file does not exist on server, but its not covered in session) and in the Session-Mapping Properties, we have to specify the Directory of the Source file (which is a directory on the INformatica Server). Same goes with the target. 
* If we want to do something like 'Shared Data Sources' (one source is being used in multiple projects), then instead of creating a souces in our project folder, We need to create a Global Folder (accessible by all projects in the ambit) and create a source there. 
* While picking data from Source file, We have two options: Direct and Indirect. Direct means actual file. Indirect option means, we will prepare a list of Paths and file names and place them in a text file and point to that text file. 
* I-O-V in ports corresponding to Input, Output and Variable.
* To concatinate two Strings, we can use || or we can use Concat Function
* To Comment something in Expressions, We can use --
* After creating a Variable in Ports, we again need to assign it to Output POrt by creating a new column.
* You have to SAVE the mapping for it to be able to appear in the mapping selection in the Session. 
* Everytime we change a Mapping, we need to go to the WorkFlowManager and right click the Mapping and Refresh it as well. 
 
##Day 2##
* If we want to connect to a different souce (which is not in Power Center Designer), Like a mainfram, we need some other client tools like Informatica Power Express??
* Active and Passive Transformations (Active= no of incoming rows may be different from Outgoing rows (example Filter); passive = incoming and outgoing rows are equal, Example Expression transformation.)
* Router Transformation has Groups where we can give conditions. CHeck router transformation and compare it with Conditional Split (Example if a>100 and a>200 and the value is 300, then will it go to both parts? Check in both SSIS and Informatica)
* 'Currently Processing FileName' option can be used to do any action specific to the file that is being processed (like Capturing the number of records etc)
* WHen we use BULK Load operation, Performance will imporve at the cost of not Logging the transaction and hence recovery cannot be done. So, It is preferable NOT to use Bulk Load option.
* 'Truncate Target Table' option should be enabled in the Session when we need the Target to be truncated before loading.
* 'Recovery Strategy' in Session Properties lets us do Check-point(in SSIS) like Actions.
* Session Level Connections will overwrite the connections defined in Designer. For Example, if we define a Delimiter as ',' in Designer and '|' in Session, When we run the Job, it will be looking for '|' only from the source file.
* Re-usable Session can be used across Workflows. You can aslo Ctrl-C and Ctrl-V to use a session from one work in other flow. But doing so will not come under reusability since changing one instance of the session will not affect the other instance. Also, a non re-usble session can be promoted to a re-usable session but vice-versa is not possible.
* Sort Transformation is an 'Active' transformation since it has an option to select 'Distinct' records which may affect the output row count. Sorting will be performed in the port order.
* Two Types of Lookup. Connected and UnConnected. Unconnected will make use of LookUp in Functions. The 'R' in Lookup ports corresponds to 'return' when the LKP is used as Function in Unconnected mode. UnConnected will be usefull if the same lookup has to be used multiple times in a Mapping (and when Look up has to be performed only when some condition is successfull-> here condition will be given where the LKP: function will be called and if the condition is not satisfied, LKP will not even be needed and hence no need to create a cache). For Each Lookup, Cache will be Built by Informatica. So, if we use Unconnected Lokkup, Cache will be created only once, which is useful. Disadvantage of Unconnected Lookup is it can return only one port. If we have to return Multiple ports from a look up, then we can only use Connected (We can also use Unconnected by concatenating all return ports to a single port and then splitting later. But thats clumpsy). 
* $$ specifies a Variable. Varibles can be assigned values in Parameter File. The parameter File can be Specified in Session so that the Session will pick the Variables from Parameter File.
* Lookup Cache can be Static or Dynamic. Static Lookup, Caching will be done at the beginning of Workflow Execution and it will remain static. In Dynamic Lookup, based on the conditions, the Cache will get updated as the Work Flow Progresses. In Dynamic lookup, when the match is not found, we can Insert that entry into the Lookup table and then the lookup flow will continue (key ports and Associated Ports concept will be used in Dynamic Lookup)
* 'Union' Transformation is actually UNION ALL. If we want Distinct Values, we can use Sort Transformation down stream and select distinct records. 

##Day 3##
* IN lookup, 'Return All Values on Multiple Match' and 'lookup policy on multiple Match' options are available to do more actions when there are multiple matches in lookup. This is unlike SSIS where always first match is taken into consideration. Using these settings, Lookup will become active?
* In Aggregate Transformation, using Sorted input option will be benefecial since caching will be easy for informatica. Also, the order of ports (which have Group By Enabled) will be important if this option is enabled.
* Normalizer Transformation -> like pivot and unpivot? check this. here GK_ and GCID_ ports will be created for internal purpose by informatica and generally we dont need them. 
* For Any Transformation, in properties there is a setting called 'Tracing Level'. by default in session log, we see summary level information. If situation demands, for debugging, if we need detail information, we can change this setting to 'Verbose'.
* Java transformation: We can add our own log statemetes to the session log using java. There is no looping functionality in-built in informatica (like for-each in SSIS). We can use java transformation for looping-> check how.
* PMCMD command to trigger workflow (command line utility for informatica)
* Joiner Transformation: Master, Detail, Index Cache and Data Cache - Check. Index Cache will always be created on Join Condition. It is preferable to use Sorted input for joiner just like for Aggregator due to performance reasons.
* In Work Flow TASKS, apart from session, we can also create Command task and Mail Task. In command task, we cannot give Multiple command lines in a single command port. we have to write only one command per command port. Instead of creating multiple command ports, we can just create a file with all commands and then write a single command to call the file. The command ports will be run sequentially so if you want to run multiple commands parallelly then you need to create a new command task.
* SQL Transformation is like 'OLEDB Command Task' in SSIS. This is a performance spoiler and try to avoid it. if it is used, check the COMMIT option since informatica will not commit the SQL by default. This behaviour is explicit only to this transformation.
* In work flow monitor, options STOP and ABORT are different just like DELETE and TRUNCATE. ABORT doesnt care about transactions and all and just kills everything. 
* In work Flow, we can give and expression in LINK properties so that if status = FAILED, then proceed to next task. This can be used for Error Handling. 
* Check 'suspend on error' option and recovery options in work flow. 

##Day 4##
* 
