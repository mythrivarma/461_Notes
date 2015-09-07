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
* 
