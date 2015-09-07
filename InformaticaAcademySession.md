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
* 
